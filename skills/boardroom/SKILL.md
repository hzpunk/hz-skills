---
name: boardroom
description: "Use when running the full autonomous end-to-end venture/feature development cycle: PRD hypotheses, CFO unit economics, CLO legal clearance, CTO/Backend architecture, UX/Security audit gate, and CRO/PMM GTM sales execution. Triggers the Autonomous Boardroom pipeline."
---

# Boardroom: Команда Запуска Полного Цикла

Этот скилл запускает **полный сквозной цикл разработки продукта или бизнеса** силами Автономного Совета Директоров. Вместо ручного вызова десятка специалистов одной командой инициируется последовательный конвейер с состязательными дебатами (Red Team vs Blue Team) и сохранением всех 7 артефактов в папку `boardroom/`.

Триггеры вызова:
- `/boardroom`
- `полный цикл` / `запусти полный цикл`
- `совет директоров` / `прогони идею по совету директоров`
- `hz boardroom "<идея>"` (из терминала)

---

## 1. Схема Работы Через 4 Комитета Совета Директоров

```
                  ┌───────────────────────────────┐
                  │    ВЕРХОВНЫЙ АРБИТР (CEO)     │
                  │          businesman           │
                  └──────────────┬────────────────┘
         ┌───────────────────────┼───────────────────────┐
         ▼                       ▼                       ▼                       ▼
┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐
│  1. РОСТ & РЫНОК │    │  2. ФИН & ПРАВО  │    │  3. ИНЖЕНЕРИЯ    │    │ 4. ДОВЕРИЕ & ИБ  │
│ Product & Growth │    │ Finance & Legal  │    │   Engineering    │    │ Experience&Trust │
├──────────────────┤    ├──────────────────┤    ├──────────────────┤    ├──────────────────┤
│ • CPO (Продукт)  │    │ • CFO (Финансы)  │    │ • Backend        │    │ • UX (Эргономика)│
│ • CMO (Спрос)    │    │ • CLO (Право)    │    │ • Frontend       │    │ • CISO (ИБ/ZeroT)│
│ • CRO (Продажи)  │    │                  │    │ • DevOps / SRE   │    │ • AI Architect   │
│                  │    │                  │    │                  │    │ • Data Officer   │
└──────────────────┘    └──────────────────┘    └──────────────────┘    └──────────────────┘
```

---

## 2. Пошаговый Регламент Выполнения (4 Комитета)

1. **Инициализация:** `bash ~/.agents/scripts/init-boardroom-artifacts.sh docs/boardroom`.
2. **Комитет Роста и Рынка (Product & Growth):**
   - `cpo` + `cmo` + `cro` формируют `01-PRD-AND-HYPOTHESIS.md` и `07-GTM-SALES-PLAYBOOK.md`.
   - Шлюз: подтверждение боли клиента, УТП (Obviously Awesome), расчет CAC каналов и MEDDPICC.
3. **Финансово-Юридический Комитет (Finance & Legal):**
   - `cfo` + `clo` заполняют `02-FINANCIAL-UNIT-MODEL.md` и `03-LEGAL-CLEARANCE-152FZ.md`.
   - Шлюз: LTV/CAC $\ge 3:1$, Runway $> 12$ мес., защита прав ст. 1295 ГК РФ, 152-ФЗ.
4. **Инженерно-Технический Комитет (Engineering & DevOps):**
   - `backend` + `frontend` + `devops` формируют `04-ADR-AND-DATA-CONTRACTS.md`.
   - Шлюз: Идемпотентность API, схемы Postgres, Core Web Vitals (LCP $< 2.5$ с), 120fps CSS, CI/CD деплой, бэкапы (RTO $< 15$ мин).
5. **Комитет Доверия, Безопасности и Данных (Trust & Safety):**
   - `ux` + `ciso` + `ai` + `data` формируют `05-SECURITY-THREAT-MODEL.md` и `06-UX-HEURISTIC-AUDIT.md`.
   - Шлюз: 10 эвристик Нильсена (SUS $\ge 80$), STRIDE Zero Trust, защита от спама, FinOps токенов LLM, маскирование PII.
6. **Консолидированный вердикт Основателя (CEO / Businessman):**
   - Сборка Executive Dashboard (`hz dashboard`) и монолитного досье (`hz export`). План действий на 7 дней.
