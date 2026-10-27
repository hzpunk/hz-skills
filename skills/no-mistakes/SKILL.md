---
name: no-mistakes
description: "Zero-slop verification gate: rigorous pre-flight checklist, invariant validation, and reality checking before claiming task completion."
---

# No Mistakes Gate (`/no-mistakes`)

Шлюз нулевых ошибок и валидации фактов перед утверждением о готовности.

## Обязательный чек-лист перед сдачей любой задачи:
- [ ] Проверил ли я реальный вывод команд, а не предположил его?
- [ ] Запущен ли реальный билд проекта (`npm run build` / `cargo build`)?
- [ ] Прошли ли все unit и e2e тесты (100% pass)?
- [ ] Нет ли захардкоженных секретов или пустых заглушек (`TODO`, `throw 501`)?
- [ ] Соблюдены ли инварианты темы и дизайн-системы?
