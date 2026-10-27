---
name: patronview-botshield
description: "Edge defense against scrapers and fake traffic: datacenter ASN blocking, Cloudflare Turnstile, and client-only telemetry isolation."
---

# PatronView BotShield (`/patronview-botshield`)

Эшелонированная защита веб-ресурсов от паразитного трафика скраперов и ботов (Инвариант PatronView: 99% трафика — боты).

## 3 Эшелона Защиты:
1. **Edge WAF & Datacenter ASN Blocking:**
   - Блокировка входящих запросов от датацентровых провайдеров (AWS, Hetzner, DigitalOcean, OVH) к мутирующим API (`/api/v1/*`).
   - Блокировка агрессивных AI-скраперов (Bytespider, GPTBot, ClaudeBot, CCBot).
2. **Invisible Cloudflare Turnstile:**
   - Умная проверка пользователя без надоедливых капч при отправке форм.
3. **Изоляция Аналитики:**
   - Бизнес-метрики и воронка строятся строго по событиям браузера (JS Client Events), сырые серверные логи изолируются.
