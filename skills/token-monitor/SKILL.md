---
name: token-monitor
description: "Real-time AI token telemetry and cost optimization: analyzes transcript logs, measures cache hit ratio, identifies heaviest tool calls, and auto-exports audit reports."
---

# HZ Token Monitor (`/token-monitor`)

Инструмент телеметрии и оптимизации расхода токенов для сессий Antigravity.

## Как запустить из терминала:
```bash
# Быстрый дашборд текущей сессии
hz-tokens

# Или полный вызов
hz-token-monitor
```

## Что анализирует:
1. **Токены и кэш:** Свежий Input vs Context Cache Hit vs Output.
2. **Стоимость:** Оценка затрат в долларах ($) и рублях (₽) на основе тарифов модели.
3. **Источники расхода:** Топ-5 самых «прожорливых» шагов (слишком большие файлы, вывод команд).
4. **Срочность сжатия (Compaction Urgency):** Рекомендация вызвать `/compact` при разрастании контекста выше 120k токенов.
5. **Авто-экспорт в Obsidian:** Сохраняет историю аудитов в `~/Documents/Obsidian Vault/perf/audits/`.
