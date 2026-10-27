---
name: planexe
description: "Autonomous plan execution engine: breaks complex objectives into strictly sequential, verifiable milestones with automated checkpoints."
---

# PlanExe Engine (`/planexe`)

Детерминированный движок пошагового выполнения сложных планов без сходов с траектории (PlanExe2).

## Механика работы:
1. **Декомпозиция на Фазы M1–M5:** Каждая фаза имеет четкий Definition of Done.
2. **Checkpoints:** Переход к следующему шагу разрешен только после 100% прохождения тестов текущего шага.
3. **Rollback Safety:** Любая непредвиденная ошибка локализуется без повреждения ранее созданных компонентов.
