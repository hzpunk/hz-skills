---
name: ub-mode
description: "Uncle Bob Clean Code discipline: Red-Green-Refactor TDD, CRAP complexity < 10, DRY factor < 0.8, single responsibility, and zero warnings."
---

# Uncle Bob Mode (`/ub-mode`)

Режим строгой инженерной дисциплины Clean Code (Роберт Мартин).

## 5 Заповедей Режима:
1. **Red-Green-Refactor:** Ни строчки продуктового кода без предварительно падающего теста.
2. **Small Functions:** Функция делает только одну вещь и делает ее хорошо (длина $\le$ 20 строк).
3. **No Duplication:** DRY фактор $< 0.8$. Дублирование бизнес-логики карается немедленным рефакторингом.
4. **Low Complexity:** Цикломатическая сложность (CRAP) $< 10$. Никаких вложенных тернарников и лестниц `if/else`.
5. **Zero Warnings:** Код компилируется без единого ворнинга линтера и TypeScript.
