---
name: hz-books
description: "Canonical HZCompany Book Knowledge Base extracted from /Users/hzpunk/books (11 unique books / 12 volumes / 14 files): HBR Change Management (Vol. 1 & 2), Boss (Immelman), Value Proposition Design (Osterwalder/Pigneur), HBR Innovation Management, HBR Decision Making, HBR Platforms & Ecosystems, HBR Strategic Marketing, HBR People Management, HBR Risk Management, HBR Emotional Intelligence, and HBR Effective Communication. Includes full Role-to-Book distribution across all 19 Boardroom/CLI agents and core skills."
---

# HZ Books — Каноническая библиотека знаний (`hzpunk/books`)

Единая база выжимки из бизнес-библиотеки `/Users/hzpunk/books/` (все 14 файлов = 11 уникальных книг / 12 томов с учётом Vol. 2). Каждая книга прочитана по главам и статьям, структурирована с реальными фреймворками, цифрами и кейсами и закреплена за профильными субагентами и скиллами `hz-skills`.

> **Правило экономии токенов (`token-economy`):** Не загружайте все 11 файлов сразу. Каждый агент и скилл читает **только свои закреплённые книги** из `~/.agents/skills/hz-books/references/<slug>.md` (или `~/.gemini/config/plugins/hz-rules-plugin/skills/hz-books/references/<slug>.md`).

---

## 1. Каталог книг (`references/`)

| # | Файл в `references/` | Книга и авторы | Источник в `/Users/hzpunk/books/` |
|---|---|---|---|
| 1 | `osterwalder-value-proposition-design.md` | **Разработка ценностных предложений** (А. Остервальдер, И. Пинье, Г. Бернарда, А. Смит) | `razrabotka-cennostnyh-predlozhenij-...epub` |
| 2 | `hbr-innovation-management.md` | **Инновационный менеджмент** (HBR: 10 статей — Мартин, Говиндараджан/Тримбл, Ульвик, Дей, Томке/Рейнертсен, Кантер, Макграт, Друкер, Кристенсен) | `Инновационный менеджмент.epub` + `.fb2` |
| 3 | `hbr-decision-making.md` | **Методы принятия решений** (HBR: 10 статей — Хэммонд/Кини/Райффа, Канеман/Ловалло/Сибони, Тинсли, Чаран, Гарвин/Роберто, Роджерс/Бленко, Банаджи, Дэвенпорт, Кемпбелл, Мэнкинс/Стил) | `Методы принятия решений.epub` |
| 4 | `hbr-platforms-ecosystems.md` | **Платформы и экосистемы** (HBR: 12 статей — Ван Альстайн/Паркер/Чаудари, Айзенман, Хаджиу/Олтман/Йоффи/Ротман, Якобидес, Аднер/Капур, Янсити/Лакхани/Жу, Эдельман, Мин Цзэн, Фисман/Лука) | `Платформы и экосистемы.epub` |
| 5 | `hbr-strategic-marketing.md` | **Стратегический маркетинг** (HBR: 10 статей — Раст/Мурман/Бхалла, Эдельман, Левитт, Кристенсен/Кук/Холл, Келлер, Сильверстайн/Сейр, Андерсон/Нарус, Фурнье/Ли, Райххелд, Котлер/Рекхем) | `Стратегический маркетинг.epub` |
| 6 | `hbr-risk-management.md` | **Управление рисками** (HBR: 12 статей — Каплан/Майкс, Гиротра/Нетесин, Талеб/Гольдштейн/Шпицнагель, Симчи-Леви, Дей, Шумейкер/Тетлок, Райс/Зегарт, Хили/Серафейм, Солтес, Гилберт/Эйринг, Аптон/Криз, Олди/Джанфрате) | `Управление рисками.epub` + `.fb2` |
| 7 | `hbr-change-management.md` | **Управление изменениями (Том 1 RU + Том 2 EN)** (HBR: 21 статья — Коттер, Гарвин/Роберто, Хемп/Стюарт, Мейерсон, Ким/Моборн, Хейфец/Лински, Киган/Лейхи, Бир/Нориа, Сиркин DICE, Катценбах, Лорш, Баттилана, Браун/Мартин, Фурр, Ригби/Сазерленд, Ашкенас, Хейдари-Робинсон, Фуллер) | `Управление изменениями.epub` + `HBRs 10 Must Reads on Change Management 2-Volume Collection.epub` |
| 8 | `hbr-people-management.md` | **Управление персоналом** (HBR: 10 статей — Гоулман, Герцберг, Манзони/Барсу, Уокер, Бакингем, Ким/Моборн, Аргирис, Банаджи, Катценбах/Смит, Габарро/Коттер) | `Управление персоналом.epub` |
| 9 | `hbr-emotional-intelligence.md` | **Эмоциональный интеллект** (HBR: 10 статей — Гоулман, Бояцис/Макки, Брокнер, Кемпбелл, Драскэт/Вулфф, Порат/Пирсон, Кутю, Дэвид/Конглтон, Джекман/Стробер, Банкер/Крэм/Тинг) | `Эмоциональный интеллект.pdf` |
| 10 | `hbr-effective-communication.md` | **Эффективные коммуникации** (HBR: 10 статей — Уильямс/Миллер, Чалдини, Таннен, Конджер, Перлоу/Уильямс, Морган, Деннинг, Элсбах, Хэмм, Уикс) | `Эффективные коммуникации.epub` |
| 11 | `immelman-boss.md` | **Boss: бесподобный или бесполезный** (Рэймонд Иммельман — 16 глав) | `Immelman Reymond. Boss bespodobnyy ili bespoleznyy.epub` |

---

## 2. Матрица распределения книг по агентам и скиллам

### Агенты Совета Директоров и CLI (`agents/*.md`)

| Агент | Основные книги (Primary) | Дополнительные книги (Secondary) | Ключевые модели из книг |
|---|---|---|---|
| `boardroom-cpo` | `osterwalder-value-proposition-design.md`, `hbr-innovation-management.md` | `hbr-platforms-ecosystems.md`, `hbr-decision-making.md` | Customer Profile (Jobs/Pains/Gains), ODI Job Map, R-W-W, 6 мифов Томке/Рейнертсена, Core Interaction, Sunk Cost & Premortem |
| `boardroom-cmo` | `hbr-strategic-marketing.md`, `osterwalder-value-proposition-design.md` | `hbr-platforms-ecosystems.md`, `hbr-effective-communication.md` | Customer Equity, CDJ вместо воронки, анти-близорукость, JTBD-бренды, 10 критериев Келлера, комьюнити, NPS, Smarketing |
| `boardroom-cro` | `hbr-effective-communication.md`, `hbr-strategic-marketing.md` | `hbr-decision-making.md`, `osterwalder-value-proposition-design.md` | 5 стилей ЛПР (Уильямс/Миллер), 6 принципов Чалдини, B2B Resonating Focus, Smarketing, RAPID, борьба со скидочной близорукостью |
| `boardroom-pmo` | `hbr-effective-communication.md`, `hbr-strategic-marketing.md` | `hbr-people-management.md`, `immelman-boss.md` | B2B Resonating Focus, CDJ-контент, 5 стилей ЛПР при аутриче, Fair Process 3E, устранение племенной вражды |
| `boardroom-cfo` | `hbr-risk-management.md`, `hbr-innovation-management.md` | `hbr-platforms-ecosystems.md`, `hbr-decision-making.md` | 3 ловушки Кристенсена (DCF/предельные издержки/EPS), Discovery-Driven Planning (Reverse P&L), 6 ошибок Талеба, Subsidy vs Money side |
| `boardroom-ir` | `hbr-innovation-management.md`, `hbr-effective-communication.md` | `hbr-platforms-ecosystems.md`, `hbr-risk-management.md` | Матрица риска и R-W-W, DDP-вехи, 3 архетипа питча Элсбах (за 150 мс) + соавторство, Network Bridging & Moat, 12 вопросов Канемана |
| `boardroom-clo` | `hbr-risk-management.md`, `hbr-platforms-ecosystems.md` | `hbr-people-management.md`, `hbr-decision-making.md` | Предотвратимые риски, антикоррупция и честность (Хили/Солтес), GR маркетплейсов (Хаджиу/Ротман), антидискриминация, этические слепые пятна |
| `boardroom-ciso` | `hbr-risk-management.md`, `hbr-decision-making.md` | `hbr-platforms-ecosystems.md` | Внутренняя угроза / инсайдеры (Аптон/Криз), Near-Misses (Тинсли) и борьба с нормализацией отклонений, хвостовые риски Талеба |
| `boardroom-secops` | `hbr-risk-management.md`, `hbr-decision-making.md` | `hbr-emotional-intelligence.md` | Мониторинг инсайдеров/подрядчиков (кейс Target), 7 стратегий Near-Misses, разбор первопричин, жизнестойкость и «бриколаж» в инцидентах |
| `boardroom-backend` | `hbr-platforms-ecosystems.md`, `hbr-innovation-management.md` | `hbr-risk-management.md`, `hbr-change-management.md` | Smart Business (Datafication, API-first, ML-петли), анти-ловушка legacy (middleware/API), теория очередей и малые партии (Томке/Рейнертсен), TTR |
| `boardroom-devops` | `hbr-risk-management.md`, `hbr-change-management.md` | `hbr-innovation-management.md`, `immelman-boss.md` | TTR и REI для скрытых зависимостей, избыточность против хрупкости (Талеб), Agile at Scale, лимит WIP и буфер мощностей 15–20%, без бункеров |
| `boardroom-frontend` | `osterwalder-value-proposition-design.md`, `hbr-change-management.md` | `hbr-platforms-ecosystems.md` | Landing Page MVP, A/B-тесты и воронки CTA, middleware-интеграция без сноса ядра, «виртуальные ширмы» и снижение трения в UI |
| `boardroom-ux` | `osterwalder-value-proposition-design.md`, `hbr-emotional-intelligence.md` | `hbr-effective-communication.md`, `hbr-platforms-ecosystems.md` | Антропологические исследования, 8 правил интервью, «Моторная лодка» / «Коробка», модель IDEO (групповой EQ), лингвистические ритуалы в интервью, «виртуальные ширмы» |
| `boardroom-motion` | `hbr-effective-communication.md`, `osterwalder-value-proposition-design.md` | `hbr-emotional-intelligence.md` | «Второй разговор» Моргана (естественность и тайминг), springboard stories Деннинга, визуальные прототипы, управление вниманием и эмоциональный резонанс |
| `boardroom-native` | `hbr-platforms-ecosystems.md`, `hbr-innovation-management.md` | `osterwalder-value-proposition-design.md` | Мультиплатформенная стратегия («Google-стратегия» Хаджиу/Йоффи), API-мост к legacy, обратная инновация под ограничения устройств |
| `boardroom-ai` | `hbr-decision-making.md`, `hbr-platforms-ecosystems.md` | `hbr-risk-management.md` | Дэвенпорт (запрет «чёрного ящика», явные допущения, модельный менеджмент), Smart Business (Alibaba ML), аудит предвзятости (Фисман/Лука), индекс Бриера |
| `boardroom-data` | `hbr-decision-making.md`, `hbr-strategic-marketing.md` | `hbr-risk-management.md`, `hbr-platforms-ecosystems.md` | Суперпрогнозирование (индекс Бриера, байесовская калибровка), Customer Equity & CLV, NPS в реальном времени, роль «Разведчика» в CDJ, TTR/REI |
| `boardroom-deeptech` | `hbr-innovation-management.md`, `hbr-platforms-ecosystems.md` | `hbr-risk-management.md` | 7-й источник Друкера (научные знания), R-W-W и Discovery-Driven Planning, Аднер/Капур (co-innovation & adoption chain risk), Матрица риска |
| `cli-orchestrator` | `hbr-people-management.md`, `immelman-boss.md` | `hbr-change-management.md` | Шахматы vs шашки (выбор раннера под сильную сторону), вертикальные задачи, DICE ($D, I, E \le 10\%$), честное управление вверх и без микроменеджмента |

### Ключевые скиллы (`skills/*/SKILL.md`)

- **`businesman` & `boardroom` & `venture`:** вся библиотека из 11 книг как фундамент CEO/Основателя (особенно `hbr-innovation-management.md`, `osterwalder-value-proposition-design.md`, `hbr-decision-making.md`, `hbr-risk-management.md`, `hbr-change-management.md`, `immelman-boss.md`).
- **`hz-marketing` & `marketing-skills`:** `hbr-strategic-marketing.md`, `osterwalder-value-proposition-design.md`, `hbr-effective-communication.md`.
- **`investor-readiness`:** `hbr-innovation-management.md` (R-W-W, DDP), `hbr-effective-communication.md` (Элсбах, Уильямс/Миллер), `hbr-platforms-ecosystems.md` (Moat/Network Effects), `hbr-risk-management.md`.
- **`pmo-leadgen` & `stealth-prospecting`:** `hbr-effective-communication.md` (5 стилей ЛПР, Чалдини), `hbr-strategic-marketing.md` (B2B Resonating Focus, CDJ).
- **`text-humanizer`:** `hbr-effective-communication.md` (Хэмм, Деннинг, Конджер, Уикс — удаление клише, сторителлинг, ясность и нейтральность).
- **`hz-master` & `planexe`:** `hbr-change-management.md` (DICE, выстраивание задач, Quest Audit), `hbr-decision-making.md` (RAPID, 12 вопросов Канемана), `hbr-people-management.md` (командная дисциплина, 3E).
