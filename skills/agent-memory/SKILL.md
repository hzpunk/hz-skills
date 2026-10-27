---
name: agent-memory
description: "Long-term episodic and semantic memory system for autonomous AI agents: vector clustering, persistent recall, and state tracking."
---

# Agent Memory (`/agent-memory`)

Долгосрочная эпизодическая и семантическая память для автономных агентов. Предотвращает амнезию между сессиями.

## Архитектура:
1. **Short-Term (Context):** Текущий диалог и буфер задач.
2. **Episodic Memory:** Хронологические логи выполненных действий и постмортемов.
3. **Semantic Memory:** Векторизованные правила, знания и предпочтения пользователя.

## Интеграция с Obsidian:
Все долгосрочные инварианты сохраняются в `/Users/hzpunk/Documents/Obsidian Vault/brain/` и индексируются локальным MCP `hz-memory-mcp`.
