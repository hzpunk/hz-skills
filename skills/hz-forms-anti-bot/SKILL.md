---
name: hz-forms-anti-bot
description: >-
  Обязательный стандарт 5-уровневой анти-бот защиты любых веб-форм (hz-forms-anti-bot).
  Включает Honeypot-поле, проверку времени заполнения (>= 5 сек), JS challenge токен,
  двухфакторный Rate-limit по IP + Client Fingerprint, и серверную валидацию с Silent Drop.
---

# 5-Уровневая Анти-Бот Защита Форм HZ (`hz-forms-anti-bot`)

Обязательный архитектурный стандарт для всех публичных веб-форм (контактные формы, сбор заявок, корзина, индивидуальный расчет, ТЗ, опросники, формы обратной связи).

Применяется **всегда при создании или обновлении любых форм в пайплайне `hz-master`**.

---

## 5 Уровней Защиты

### 1. Honeypot-поле (`companyWebsite`)
- **Клиент**: В форму добавляется скрытое поле с правдоподобным именем (по умолчанию `companyWebsite`).
- **Скрытие**: Поле полностью скрыто от человека (`style={{ display: 'none' }}`, `tabIndex={-1}`, `aria-hidden="true"`, `autoComplete="off"`).
- **Логика**: Настоящий пользователь не видит поле и оставляет его пустым. Боты и автоматические парсеры сканируют DOM и заполняют все поля. Если поле заполнено любым значением — это бот.

### 2. Временная метка (Timestamp >= 5 секунд)
- **Клиент**: Фиксируется время открытия / монтирования формы (`formStartedAt: Date.now()`).
- **Логика**: Заполнение формы живым человеком (чтение, ввод имени, телефона, города) занимает минимум 5–15 секунд. Если отправка происходит быстрее **5 секунд** (`MIN_LEAD_SUBMIT_MS = 5000`) — это бот.
- **Срок жизни**: Максимальный срок действия сессии формы — 24 часа (`MAX_LEAD_SUBMIT_MS = 24 * 60 * 60 * 1000`). Значения из будущего (с допуском дрейфа часов до 10с) или старше 24ч бракуются.

### 3. Простая JS-проверка (Challenge Token)
- **Клиент**: Вычисление детерминированного хэш-токена в JavaScript на основе `formStartedAt`.
- **Логика**: Примитивные спам-скрипты и cURL/Python запросы не исполняют браузерный JS и не могут вычислить валидный токен.
- **Алгоритм**: Синхронный целочисленный хэш (например, Murmur/FNV или 64-bit Bitwise хэш), работающий абсолютно идентично и без внешних библиотек на клиенте и в Node.js / Edge Runtime.

### 4. Двухфакторный Rate-Limit (IP + Client Fingerprint)
- **IP Rate Limit**: Ограничение по IP клиента из заголовков `x-forwarded-for` / `x-real-ip` (например, не более 12 заявок в час).
- **Client Fingerprint Rate Limit**: Формирование отпечатка клиента `ip::user-agent::accept-language` (хеш 32-bit hex) с более строгим лимитом (например, не более 4 заявок за 10 минут). Защищает от распределенных ботнетов и частых повторных отправок.
- При превышении отдается статус `429 Too Many Requests` с заголовком `Retry-After`.

### 5. Серверная проверка и Бесшумный Сброс (Silent Drop)
- **Серверная валидация**: Никогда не полагаться только на клиент! Все 4 уровня обязательно валидируются в API endpoint (`POST /api/...`).
- **Silent Drop**: Если запрос классифицирован как бот (`isBot: true`), сервер **не возвращает ошибку 400/403** (чтобы бот не адаптировал алгоритм и не перебирал поля).
- Сервер возвращает успешный ответ (например, HTTP 201 Created с фиктивным id: `drop_xxx` и статусом `SUSPECT_BOT`), но:
  1. **НЕ сохраняет заявку в базу данных** (Prisma / SQLite / Postgres).
  2. **НЕ отправляет уведомления** (Telegram-боты, email, CRM, Webhook).
  3. Логирует факт спам-атаки в `console.warn` для аналитики.

### 6. Edge WAF, Datacenter ASN & Scraper Shield (Инвариант PatronView)
- **Блокировка датацентровых ASN**: В правилах Cloudflare WAF блокировать или челенджить трафик с датацентровых сетей (AS16509 AWS, AS14061 DigitalOcean, AS24940 Hetzner, AS16276 OVH) на мутирующих роутах (`/api/*`).
- **Блокировка AI-скраперов**: Блокировать известных агрессивных ботов (`Bytespider`, `GPTBot`, `ClaudeBot`, `CCBot`) на динамических маршрутах.
- **Managed Challenge (Cloudflare Turnstile)**: Для подозрительного или внешнего трафика применять невидимый Turnstile перед приемом чувствительных форм (0 капч для людей, 100% отсечение headless-скриптов).

---

## Эталонная Реализация

### Клиентский Хук (`src/lib/leadAntiBotClient.ts`)
```tsx
'use client';

import { useEffect, useRef, useState } from 'react';
import { computeLeadJsToken, LEAD_HONEYPOT_FIELD } from '@/lib/leadAntiBot';

export function useLeadAntiBot() {
  const formStartedAtRef = useRef<number | null>(null);
  const [honeypot, setHoneypot] = useState<string>('');

  useEffect(() => {
    formStartedAtRef.current = Date.now();
  }, []);

  const getAntiBotPayload = () => {
    const startedAt = formStartedAtRef.current ?? (Date.now() - 10_000);
    return {
      [LEAD_HONEYPOT_FIELD]: honeypot,
      formStartedAt: startedAt,
      clientToken: computeLeadJsToken(startedAt),
    };
  };

  const resetAntiBot = () => {
    formStartedAtRef.current = Date.now();
    setHoneypot('');
  };

  return {
    honeypot,
    setHoneypot,
    getAntiBotPayload,
    resetAntiBot,
  };
}
```

### Разметка Honeypot в Компоненте Формы
```tsx
<div style={{ display: 'none' }} aria-hidden="true">
  <input
    type="text"
    name="companyWebsite"
    value={honeypot}
    onChange={(e) => setHoneypot(e.target.value)}
    tabIndex={-1}
    autoComplete="off"
  />
</div>
```

### Серверный Endpoint (`POST /api/requests`)
```ts
// 1. Rate Limits
const rl = checkLeadRateLimits(request);
if (!rl.ok) {
  return NextResponse.json({ error: 'Too many requests' }, { status: 429 });
}

// 2. Anti-Bot Verification
const antiBot = verifyLeadAntiBot(body);
if (antiBot.isBot) {
  console.warn(`[AntiBot] Silent drop: ${antiBot.reason}`);
  return NextResponse.json({ id: `drop_${Date.now()}`, status: 'NEW' }, { status: 201 });
}

// 3. Сохранение в БД и уведомления только для реальных людей
await prisma.request.create({ data: ... });
await notifyTelegram({ ... });
```
