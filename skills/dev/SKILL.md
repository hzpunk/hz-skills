---
name: dev
description: "Use when starting any development, refactoring, bugfix, or feature task with 100% test coverage, strict TDD, Boardroom quality gates, edge-case audit, and production build verification. Triggers the HZ Deep Dev Protocol."
---

# HZ Deep Dev Protocol (100% Coverage & Zero Regression)

Этот скилл активирует строгий протокол разработки и доработки с гарантией 100% покрытия сценариев, опорой на базу знаний Zettelkasten и отсутствием регрессий.

## Как вызвать в диалоге:
- `/dev [описание задачи]`
- `по протоколу 100%: [описание задачи]`
- `разработай по полному циклу: [описание задачи]`

---

## 5 Обязательных Этапов Исполнения:

### Этап 0. Консультация с Базой Знаний Zettelkasten
Перед написанием кода обязательно выполнить:
- Запрос к семантической памяти: `hz vault query "<суть задачи>"`
- Изучить связанные инварианты и антипаттерны (`[[anti-pattern-...]]`, `[[rule-...]]`), чтобы гарантированно не повторить прошлых ошибок.

### Этап 0.1. Предпроектный Конвейер Boardroom & GitHub Orchestration (Стандарт запуска любого проекта)
Для любого нового проекта / венчура / крупного продукта перед началом разработки ОБЯЗАТЕЛЬНО разворачивается полный комплекс:
1. **Пакет Документации Boardroom (`docs/boardroom/`):**
   - 7 сквозных артефактов: `01-PRD-AND-HYPOTHESIS.md` (Lean Canvas, Mom Test, RICE), `02-FINANCIAL-UNIT-MODEL.md` (LTV/CAC >= 3:1, Runway > 12 мес), `03-LEGAL-CLEARANCE-152FZ.md` (152-ФЗ, РИД ст. 1295 ГК РФ, оферта), `04-ADR-AND-DATA-CONTRACTS.md` (PostgreSQL DDL, REST API, Next.js, Redis), `05-SECURITY-THREAT-MODEL.md` (STRIDE, hz-forms-anti-bot), `06-UX-HEURISTIC-AUDIT.md` (Nielsen 10, WCAG 2.2 AA), `07-GTM-SALES-PLAYBOOK.md` (AARRR, скрипты).
   - Сквозные регламенты `docs/BUSINESS-PROCESSES-AND-SOP.md`.
   - Компиляция сводного досье `00-EXECUTIVE-DOSSIER.md` + `.html` и интерактивного дашборда `00-EXECUTIVE-DASHBOARD.html` через `hz export`.
2. **Инфраструктура GitHub:**
   - Создание приватного репозитория `gh repo create` и привязка ветки `main`.
   - Разметка 5 вех (Milestones) с жесткими календарными дедлайнами.
   - Декомпозиция задач в GitHub Issues со строгими критериями приемки, лейблами (P0/P1, legal, safety, growth) и назначением исполнителей.
   - Подключение CI/CD автоматизации:
     * `.github/workflows/ci.yml` (проверка DDL, целостности документации, линтер).
     * `.github/workflows/security.yml` (сканирование секретов gitleaks без зависимости от квот хранилища артефактов).
     * `.github/workflows/preview.yml` (Staging preview комментарии в PR).
     * `.github/workflows/codeql.yml` (SAST сканирование уязвимостей).
     * `.github/dependabot.yml` (контроль безопасности зависимостей).
     * `.github/PULL_REQUEST_TEMPLATE.md` (шлюз качества 152-ФЗ и HZ).
     * `.github/ISSUE_TEMPLATE/` (YAML-шаблоны тикетов).
     * `SECURITY.md` и `.gitignore`.
     * Создание окружений `staging` и `production` с эталоном `.env.example`.
3. **Автономное плечо Google Jules:**
   - Интеграция `.github/workflows/jules-automation.yml`: реактивный запуск по метке `jules`, генерация тестов по `needs-tests`, еженедельный крон ночной оптимизации кода и БД.
   - Делегирование автономного написания кода, миграций Neon и сидирования.

### Этап 1. Предварительный аудит и шлюзы Совета Директоров
1. **UX & Стилистика:**
   - 10 эвристик Нильсена + WCAG 2.2 AA доступность.
   - Формы — строго модальные окна (`hz-forms-as-modals`).
   - Палитра — строго системные семантические токены темы без хардкода (`hz-theme-palette`).
2. **Архитектура & Бэкенд:**
   - Контракты API, схемы данных, идемпотентность мутирующих операций (`Idempotency-Key`).
3. **Безопасность (CISO):**
   - Валидация Zod на всех входах, санитизация, анти-бот защита форм (`hz-forms-anti-bot`).
   - Эшелонированная защита от ботов и скраперов (`hz-bot-shield` / Инвариант PatronView): блокировка датацентровых ASN (AWS, Hetzner, DO) на роутах мутаций, фильтрация агрессивных AI-ботов (Bytespider, ClaudeBot), невидимый Turnstile (Managed Challenge).
4. **Аналитика:**
   - Если создается админка — наглядные графики с переключателем периодов (`hz-admin-charts`).
   - Изоляция продуктовой воронки: клиентские JS-события (таблица `events`) отделены от сырых серверных логов, чтобы бот-трафик не загрязнял метрики конверсий.

### Этап 2. Матрица граничных случаев (Edge Cases)
Перед кодом зафиксировать и закрыть:
- Пустые состояния (Empty states).
- Ошибки сети, таймауты, падения API (Graceful degradation).
- Экстремальный / невалидный ввод.
- Состояния гонки при быстрых кликах (Race conditions / Debounce).
- Адаптивность от 320px до 4K + `prefers-reduced-motion`.

### Этап 3. Реализация строго через TDD (Red-Green-Refactor)
1. **Red:** Написать падающие тесты (Unit / Integration / Component) на позитивные и негативные сценарии.
2. **Green:** Реализовать минимальный рабочий код. Запрещены любые заглушки, моки в прод-коде или плейсхолдеры.
3. **Refactor:** Оптимизировать без изменения интерфейсов до 100% прохождения тестов.

### Этап 4. Верификация, Самоэволюция и Сдача
1. Запустить состязательный аудит `hz review` и пре-коммит шлюз `hz check`.
2. Запустить полную производственную сборку (`npm run build`).
3. Если в процессе был получен новый опыт или исправлена ошибка — зафиксировать через `hz learn`.
4. Сделать Git Commit сразу после успеха (`hz commit` по правилу `hz-commit-after-global`).
5. Предоставить краткий отчёт по факту без лишней теории (`hz-brief-responses`).
