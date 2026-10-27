---
name: designsystems-tokens
description: "Production design token architecture: 3-tier token hierarchy (primitive -> semantic -> component), CSS variables, and dark/light modes."
---

# Design Systems Tokens (`/designsystems-tokens`)

3-уровневая архитектура дизайн-токенов по методологии DesignSystems.one.

## Иерархия токенов:
1. **Tier 1 (Primitives):** Абсолютные значения (`--color-blue-500: #3b82f6`, `--space-4: 16px`).
2. **Tier 2 (Semantics):** Назначение в контексте темы (`--bg-primary: var(--color-blue-500)`, `--text-muted: var(--color-gray-400)`).
3. **Tier 3 (Components):** Специфика конкретного виджета (`--button-primary-bg: var(--bg-primary)`).

## Инвариант HZ:
Запрещен прямой хардкод цветов в верстке. Все стили собираются строго через семантические классы Tailwind (`bg-background`, `text-foreground`, `border-border`).
