---
name: obsidian-mind
description: "Structured persistent PKM & project memory architecture for Obsidian: North Star, Key Decisions, Gotchas, Active Sprints, and graph linking."
---

# Obsidian Mind (`/obsidian-mind`)

Архитектурный стандарт ведения долгосрочной памяти, проектных решений и графов знаний в Obsidian Vault.

## Структура Хранилища:
```
Obsidian Vault/
├── brain/
│   ├── North Star.md          # Стратегические цели, инварианты экосистемы
│   ├── Key Decisions.md       # ADR (Архитектурные решения) с контекстом и последствиями
│   ├── Patterns.md            # Проверенные рецепты кода и архитектуры
│   └── Gotchas.md             # Баги, подводные камни, уроки инцидентов
├── work/
│   ├── active/                # Текущие спринты и активные задачи
│   ├── archive/               # Завершенные задачи с датой и итогами
│   └── incidents/             # Постмортемы и отчеты по сбоям
└── perf/
    └── audits/                # Замеры Core Web Vitals, p99 latency, token stats
```

## Инварианты:
1. **Wikilinks:** Все связанные сущности соединяются через `[[Имя заметки]]`.
2. **Атомарность:** 1 заметка = 1 концепция или 1 решение.
3. **MCP-доступ:** Доступен через `hz-memory-mcp` (инструменты `memory_read_note`, `memory_write_note`, `memory_list_notes`).
