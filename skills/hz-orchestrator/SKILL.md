---
name: hz-orchestrator
description: >-
  Routes HZ-ecosystem work to the right skills: hz-master, hz-rules, ui-master, hz-cicd,
  hz-forms-anti-bot, seo-crawler-audit, seo-geo-optimization, seo-productive. Use at task
  start when the request touches architecture, full-feature cycle, UI/UX, forms, deploy/CI/CD,
  SEO/GEO, crawling audit, or site promotion; when the user invokes /hz-orchestrator;
  or when AGENTS.md says to orchestrate via this skill.
---

# HZ Orchestrator

Единая точка входа для всей экосистемы из 287 навыков HZ, Antigravity, Superpowers, Science, Mobile и Cloud.  
**Не изобретай** параллельные правила — читай и выполняй целевой skill.

Полный справочник связей и сквозных конвейеров:
- [`references/grand-unified-skill-atlas.md`](file:///Users/hzpunk/.agents/skills/hz-orchestrator/references/grand-unified-skill-atlas.md) — исчерпывающий атлас 13 кластеров, 7 кросс-доменных рецептов и матрицы синергии всех 287 навыков.

Project `AGENTS.md` + явные указания пользователя в чате **важнее** дефолтов ниже.

---

## 1. Classify (сначала)

Выбери **один primary** skill. Secondary — только если задача явно смешанная.

### 1.1. Стратегия, Бизнес и Совет Директоров (Executive Board)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Запуск полного цикла продукта/бизнеса через Совет Директоров, состязательные дебаты, 7 артефактов, `/boardroom` | **boardroom** | `~/.agents/skills/boardroom/SKILL.md` |
| Валидация бизнес-идеи, Lean Idea Lab, юнит-экономика, 100K-стартап опыт, PMF, стадии продукта и фазы бизнеса, `/businesman` | **businesman** | `~/.agents/skills/businesman/SKILL.md` |
| Финансовый директор, CFO, P&L, Cash Flow, юнит-экономика (LTV/CAC, Payback, NDR), Runway, фандрейзинг (SAFE, Cap Table), налоги IT (Минцифры/Сколково), `/cfo` | **cfo** | `~/.agents/skills/cfo/SKILL.md` |
| Главный юрист, CLO, корпоративное право, SHA, вестинг, передача прав на IP (ст. 1295 ГК РФ), 152-ФЗ/GDPR комплаенс, SaaS-договоры, `/clo` | **clo** | `~/.agents/skills/clo/SKILL.md` |
| Управление выручкой, CRO, Enterprise B2B-продажи, квалификация MEDDPICC, Challenger Sale, воронка SDR/AE/CSM, закупки (Procurement), `/cro-sales` | **cro-sales** | `~/.agents/skills/cro-sales/SKILL.md` |
| Продуктовая стратегия, CPO, Customer Discovery (Mom Test, JTBD), приоритизация (RICE, WSJF), когортный анализ, 1-Page PRD, `/product-manager` | **product-manager** | `~/.agents/skills/product-manager/SKILL.md` |
| Продуктовый маркетинг, PMM, позиционирование Obviously Awesome, Strategic Narrative, GTM-лончи Tier 1/2/3, Win-Loss, Sales Battlecards, ценообразование, `/product-marketing-manager` | **product-marketing-manager** | `~/.agents/skills/product-marketing-manager/SKILL.md` |
| Маркетинговая стратегия, CMO, Performance (ROAS, MER), позиционирование (Данфорд), SEO/GEO (AI Search), CRM/Lifecycle, воронки CRO, `/marketer` | **marketer** | `~/.agents/skills/marketer/SKILL.md` |
| Связи с общественностью, Head of PR, Tier-1 СМИ (РБК/Forbes), антикризисный Золотой час, Holding Statements, Data-Driven PR, Newsjacking, `/pr-specialist` | **pr-specialist** | `~/.agents/skills/pr-specialist/SKILL.md` |
| Поисковая инженерия, Head of SEO & GEO, Information Gain, Core Web Vitals, Schema.org, AI Search (Perplexity/ChatGPT), pSEO, `/seo-specialist` | **seo-specialist** | `~/.agents/skills/seo-specialist/SKILL.md` |
| Генеративная оптимизация (GEO/GGO), цитируемость в LLM (ChatGPT Search/Perplexity/AI Overviews), RAG-чанкинг, llms.txt, агентный рост, `/ggo-specialist` | **ggo-specialist** | `~/.agents/skills/ggo-specialist/SKILL.md` |
| Продвижение сайта, кластеры, контент-план, рост трафика, маркетинг-бот, `/seo-productive` | **seo-productive** | `~/.agents/skills/seo-productive/SKILL.md` |

### 1.2. Кастдев, Спецификации и Исследования (Discovery & Spec)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Глубокое интервью, вскрытие скрытых допущений и рисков, `/grill-me`, `/grilling` | **grill-me** / **grilling** | `~/.agents/skills/grill-me/SKILL.md` |
| Интервью с глубоким изучением сторонней документации и стандартов | **grill-with-docs** | `~/.agents/skills/grill-with-docs/SKILL.md` |
| Пакетное тестирование гипотез через серию структурированных вопросов | **batch-grill-me** | `~/.agents/skills/batch-grill-me/SKILL.md` |
| Преобразование сырых требований/идей в строгое ТЗ со спецификациями | **to-spec** | `~/.agents/skills/to-spec/SKILL.md` |
| Декомпозиция спецификаций на атомарные тикеты задач для разработчиков | **to-tickets** | `~/.agents/skills/to-tickets/SKILL.md` |
| Создание кастдев-опросников для интервью пользователей и валидации болей | **to-questionnaire** | `~/.agents/skills/to-questionnaire/SKILL.md` |
| Генерация альтернатив и творческих концепций ДО начала проектирования | **brainstorming** | `~/.agents/skills/brainstorming/SKILL.md` |

### 1.3. Платформа, Бэкенд, Фронтенд и Кибербезопасность (Engineering)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Сквозная разработка, комплексные фичи, мультикомандный режим, /goal, аудит всех фич, редизайн системы, `/hz-master` | **hz-master** | `~/.agents/skills/hz-master/SKILL.md` |
| Технологическая стратегия, CTO, архитектура систем, закон Галла, DORA-метрики, Team Topologies, Zero SPOF, FinOps, LLMOps, Incident Command, `/cto` | **cto** | `~/.agents/skills/cto/SKILL.md` |
| Архитектура систем и платформ, админ-панели (графики, модалки, data grid), 100 практик кибербеза и DevOps, `/tech-platform-architect` | **tech-platform-architect** | `~/.agents/skills/tech-platform-architect/SKILL.md` |
| Бэкенд-инженерия, Staff Backend, High-Load API, PostgreSQL (MVCC, индексы, CONCURRENTLY), Apache Kafka (Outbox), Redis, распределенный консенсус, `/backend-engineer` | **backend-engineer** | `~/.agents/skills/backend-engineer/SKILL.md` |
| Фронтенд-инженерия, Staff Frontend, React 19 RSC, Server Actions, FSD, Core Web Vitals, 120fps анимации, TanStack Query, Zustand, a11y, `/frontend-engineer` | **frontend-engineer** | `~/.agents/skills/frontend-engineer/SKILL.md` |
| Кибербезопасность, CISO, Zero Trust (NIST SP 800-207), AppSec (OWASP Top 10), Cloud Security, K8s hardening, криптография, комплаенс 152-ФЗ/SOC 2, `/cybersecurity` | **cybersecurity** | `~/.agents/skills/cybersecurity/SKILL.md` |
| Глобальные проектные правила, проверка стандартов (графики, модалки, палитра темы, коммиты, codegraph-first), `/hz-rules` | **hz-rules** | `~/.agents/skills/hz-rules/SKILL.md` |
| Любые веб-формы (лиды, заявки, опросники, ТЗ), защита от ботов/спама, `/hz-forms-anti-bot` | **hz-forms-anti-bot** | `~/.agents/skills/hz-forms-anti-bot/SKILL.md` |
| CI/CD, deploy, VPS, GitHub Actions, secrets, systemd, nginx, `/hz-cicd` | **hz-cicd** | `~/.agents/skills/hz-cicd/SKILL.md` |
| Проектирование БД Supabase, RLS политики безопасности, оптимизация Postgres | **supabase** / **supabase-postgres-best-practices** | `~/.agents/skills/supabase/SKILL.md` |
| Графовые агенты с циклами, чекпоинтами и human-in-the-loop, LangGraph | **langgraph** | `~/.agents/skills/langgraph/SKILL.md` |
| Рефакторинг архитектуры, DDD, модульные границы, монорепозитории Turborepo | **improve-codebase-architecture** / **turborepo** | `~/.agents/skills/improve-codebase-architecture/SKILL.md` |

### 1.4. Дизайн, UX-Оценка и Доступность (Design & UI/UX)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| UI, UX, вёрстка, анимации, формы, дашборд, auth-экраны, «сделай красиво», `/ui-master` | **ui-master** | `~/.agents/skills/ui-master/SKILL.md` |
| Оценка юзабилити, UX-аудит продукта, эвристики Нильсена, законы восприятия, замер SUS/SEQ/Lostness, WCAG 2.2 AA, формы и анти-dark patterns, `/ux-product-evaluator` | **ux-product-evaluator** | `~/.agents/skills/ux-product-evaluator/SKILL.md` |
| Глобальные стандарты веб-дизайна, сетки, иерархия, отступы (Web Design Guidelines) | **web-design-guidelines** | `~/.agents/skills/web-design-guidelines/SKILL.md` |
| Превращение любительского UI в премиальный, полировка сеток и контрастов | **better-ui** / **better-interface** | `~/.agents/skills/better-ui/SKILL.md` |
| Цветовые палитры, гармония теней, отсутствие грязи в темной теме | **better-colors** | `~/.agents/skills/better-colors/SKILL.md` |
| Типографика, шрифтовые пары, ритм строк, акциденция и кернинг | **better-typography** | `~/.agents/skills/better-typography/SKILL.md` |
| Доступность интерфейсов WCAG 2.2 AA, клавиатурная навигация, скринридеры | **better-accessibility** / **a11y-debugging** | `~/.agents/skills/better-accessibility/SKILL.md` |
| Инженерные секреты анимаций, микровзаимодействий и Apple HIG (Эмиль Ковальски) | **emil-design-eng** | `~/.agents/skills/emil-design-eng/SKILL.md` |
| Стилистические диалекты: минимализм, брутализм, Apple-стиль, премиальный глянец | **minimalist-ui** / **apple-design** / **high-end-visual-design** | `~/.agents/skills/apple-design/SKILL.md` |

### 1.5. Моушн, Шейдеры, Интерактив и Видео (Motion & Video)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Премиальные анимированные компоненты (Magic UI, Aceternity UI, Motion Primitives) | **creative-motion-components** | `~/.agents/skills/creative-motion-components/SKILL.md` |
| WebGL шейдеры холста (MeshGradient, LiquidMetal, FlutedGlass, GodRays) | **canvas-shaders** | `~/.agents/skills/canvas-shaders/SKILL.md` |
| Физические эксперименты (Liquid Gooey, Dialkit rotary physics, Thinking Orbs) | **ai-ux-playground** | `~/.agents/skills/ai-ux-playground/SKILL.md` |
| 43+ кинематографичных микроперехода между экранами и секциями | **transitions-dev** / **transitions-polish** | `~/.agents/skills/transitions-dev/SKILL.md` |
| Оптимизация 120fps GPU-анимаций, устранение лагов скролла и перерисовок | **animation-performance** / **animate** | `~/.agents/skills/animation-performance/SKILL.md` |
| Программная генерация видео на React (субтитры, титры, анимация графиков) | **remotion-best-practices** / **remotion-create** | `~/.agents/skills/remotion-best-practices/SKILL.md` |
| Генеративный видеодвижок Hyperframes (аудио, кейфреймы, видеорендер) | **hyperframes** | `~/.agents/skills/hyperframes/SKILL.md` |

### 1.6. Облако, Деплой, Vercel и Firebase BaaS
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Деплой на Vercel (Preview/Production), Vercel CLI с токенами, проверка live URL | **deploy-to-vercel** / **vercel-cli-with-tokens** | `~/.agents/skills/deploy-to-vercel/SKILL.md` |
| Оптимизация затрат и рантайма Vercel (Function Invocations, Fast Data Transfer, CWV) | **vercel-optimize** | `~/.agents/skills/vercel-optimize/SKILL.md` |
| Оптимизация React / Next.js (70 правил производительности, устранение waterfalls) | **vercel-react-best-practices** | `~/.agents/skills/vercel-react-best-practices/SKILL.md` |
| Проектирование документов и коллекций Cloud Firestore, кэширование, индексы | **firebase-firestore** | `~/.agents/skills/firebase-firestore/SKILL.md` |
| Аутентификация Firebase (OAuth, Phone, Email/Password, кастомные клеймы) | **firebase-auth-basics** | `~/.agents/skills/firebase_auth_basics/SKILL.md` |
| Реляционный SQL бэкенд на PostgreSQL в экосистеме Firebase (Data Connect) | **firebase-data-connect-basics** | `~/.agents/skills/firebase_data_connect_basics/SKILL.md` |
| Аудит безопасности и авторство правил `firestore.rules` (Zero-privilege) | **firestore-rules-creation** / **firebase-security-rules-auditor** | `~/.agents/skills/firestore_rules_creation/SKILL.md` |
| Хостинг статики и SSR-приложений (Next.js/Angular) в Firebase App Hosting | **firebase-app-hosting-basics** | `~/.agents/skills/firebase_app_hosting_basics/SKILL.md` |

### 1.7. Мобильная Разработка (Flutter, Dart, Android & Swift)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Чистая 3-слойная архитектура мобильных приложений на Flutter (UI, Logic, Data) | **flutter-apply-architecture-best-practices** | `~/.agents/skills/flutter-apply-architecture-best-practices/SKILL.md` |
| Адаптивные мобильные и планшетные интерфейсы Flutter (`LayoutBuilder`, `MediaQuery`) | **flutter-build-responsive-layout** | `~/.agents/skills/flutter-build-responsive-layout/SKILL.md` |
| Устранение багов верстки Flutter ("RenderFlex overflowed", unbounded constraints) | **flutter-fix-layout-issues** | `~/.agents/skills/flutter-fix-layout-issues/SKILL.md` |
| Тестирование виджетов Flutter и E2E тесты с `integration_test` | **flutter-add-widget-test** / **flutter-add-integration-test** | `~/.agents/skills/flutter-add-widget-test/SKILL.md` |
| Юнит-тесты на Dart с моками (`mockito`) и проверки (`dart analyze`) | **dart-add-unit-test** / **dart-run-static-analysis** | `~/.agents/skills/dart-add-unit-test/SKILL.md` |
| Управление Android AVD, запуск эмуляторов, сборка APK, скриншоты UI | **android-cli** | `~/.agents/skills/android-cli/SKILL.md` |
| Нативная разработка под iOS на Swift / SwiftUI, интеграция Xcode | **write-swift** / **xcode-project-setup** | `~/.agents/skills/write-swift/SKILL.md` |
| Кроссплатформенная мобильная разработка на React Native / Expo | **vercel-react-native-skills** / **animate-expo** | `~/.agents/skills/vercel-react-native-skills/SKILL.md` |

### 1.8. Корпоративная Автоматизация (Google Workspace)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Управление встречами, проверка свободных слотов, бронирование в Google Календаре | **gcalendar** | `~/.agents/skills/gcalendar/SKILL.md` |
| Создание, форматирование и экспорт документов, договоров и ТЗ в Google Docs | **gdocs** | `~/.agents/skills/gdocs/SKILL.md` |
| Поиск, выгрузка, структурирование файлов и папок в Google Drive | **gdrive** | `~/.agents/skills/gdrive/SKILL.md` |
| Создание финансовых моделей, когортных анализов и таблиц в Google Sheets | **gsheets** | `~/.agents/skills/gsheets/SKILL.md` |
| Автоматическая генерация презентаций и питч-деков в Google Slides | **gslides** | `~/.agents/skills/gslides/SKILL.md` |
| Настройка повторяющихся фоновых задач и автоматизаций в Antigravity | **automation** | `~/.agents/skills/automation/SKILL.md` |

### 1.9. AI Модели, Gemini SDK и Платформа Antigravity
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Интеграция Gemini API (Python/TS): мультимодальность, Structured Output, Function Calling | **gemini-api-dev** | `~/.agents/skills/gemini-api-dev/SKILL.md` |
| Двусторонний потоковый звук/видео стриминг в реальном времени (Gemini Live API) | **gemini-live-api-dev** | `~/.agents/skills/gemini-live-api-dev/SKILL.md` |
| Генеративное редактирование и создание видео через Gemini Omni 1.1 Flash | **gemini-omni-flash-api** | `~/.agents/skills/gemini-omni-flash-api/SKILL.md` |
| Проектирование автономных агентов на базе Google Antigravity SDK | **google-antigravity-sdk** | `~/.agents/skills/google-antigravity-sdk/SKILL.md` |
| Поиск по официальной документации Google Cloud, Firebase, Chrome и Web | **retrieving-developer-knowledge** | `~/.agents/skills/retrieving-developer-knowledge/SKILL.md` |
| Интерактивные HTML/JS виджеты и Generative UI в чате Antigravity | **generative_ui** | `~/.agents/skills/generative_ui/SKILL.md` |
| Конфигурация плагинов, хуков и правил среды Antigravity | **agy-customizations** / **antigravity-guide** | `~/.agents/skills/agy-customizations/SKILL.md` |

### 1.10. Научный R&D, Биоинформатика и Анализ Данных (Science)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Интерактивный 3D просмотр молекул и белков в Mol* Sidecar | **biomolecular-structure_viewer** | `~/.agents/skills/biomolecular_structure_viewer/SKILL.md` |
| Предсказание 3D структур белков AlphaFold, анализ pLDDT и доменов | **alphafold_database_fetch_and_analyze** | `~/.agents/skills/alphafold_database_fetch_and_analyze/SKILL.md` |
| Оценка патогенности мутаций и эффектов на РНК через AlphaGenome | **alphagenome_single_variant_analysis** | `~/.agents/skills/alphagenome_single_variant_analysis/SKILL.md` |
| Поиск химических соединений, биоактивности, формул и мишеней (ChEMBL / PubChem) | **chembl_database** / **pubchem_database** | `~/.agents/skills/chembl_database/SKILL.md` |
| База клинических исследований ClinicalTrials.gov (статусы, фазы, критерии) | **clinical_trials_database** | `~/.agents/skills/clinical_trials_database/SKILL.md` |
| Поиск научной литературы и статей (PubMed, ArXiv, BioRxiv, EuropePMC, OpenAlex) | **pubmed_database** / **literature_search_arxiv** | `~/.agents/skills/pubmed_database/SKILL.md` |
| Регуляторные данные FDA по лекарствам, побочным эффектам и отзывам | **openfda_database** / **opentargets_database** | `~/.agents/skills/openfda_database/SKILL.md` |
| Геномные последовательности, гены, белки (NCBI, Ensembl, UniProt) | **ensembl_database** / **uniprot_database** | `~/.agents/skills/ensembl_database/SKILL.md` |
| Структурный рендеринг молекул в PyMOL и поиск сходства Foldseek | **pymol** / **foldseek_structural_search** | `~/.agents/skills/pymol/SKILL.md` |
| Нейросетевое восстановление и датировка древних текстов (Aeneas / Ithaca) | **predictingthepast** | `~/.agents/skills/predictingthepast/SKILL.md` |

### 1.11. Фабрика Навыков и Метапрограммирование (Skill Factory)
| Сигнал пользователя / контекст | Primary skill | Path |
| --- | --- | --- |
| Кристаллизация завершенного взаимодействия или воркфлоу в постоянный скилл | **workflow-skill-creator** | `~/.agents/skills/workflow-skill-creator/SKILL.md` |
| Создание новых навыков по методологии TDD для документации | **writing-skills** / **writing-great-skills** | `~/.agents/skills/writing-skills/SKILL.md` |
| Поиск подходящего существующего навыка в реестре экосистемы | **find-skills** | `~/.agents/skills/find-skills/SKILL.md` |
| Миграция устаревших воркфлоу в современные модульные скиллы | **migrate-workflows** | `~/.agents/skills/migrate-workflows/SKILL.md` |
| Ультра-плотное общение без потери смысла (Caveman режим) | **caveman** | `~/.agents/skills/caveman/SKILL.md` |
| Передача эстафеты контекста между сессиями или моделями | **claude-handoff** / **handoff** | `~/.agents/skills/handoff/SKILL.md` |
| Циклы автономного самосовершенствования до идеала | **loop-me** | `~/.agents/skills/loop-me/SKILL.md` |

Зеркала Cursor: `~/.cursor/skills/<name>/`.  
Карта сайтов CI/CD: `~/.agents/skills/hz-cicd/SITES.md`.

---

## 2. Mixed tasks (порядок)

Если в одном запросе несколько доменов — **последовательность**, не параллельный хаос:

1. **hz-master / hz-rules** — верхнеуровневое планирование (`implementation_plan.md`), CodeGraph First анализ зависимостей, фиксация дизайн-системы в `DESIGN.md`.
2. **hz-cicd** — только если без деплоя/инфры нельзя проверить остальное (редко в начале).
3. **ui-master** — любые визуальные/interaction правки (hard gate до первого UI-диффа).
4. **hz-forms-anti-bot** — обязательный 5-уровневый контур для любой формы (honeypot, timing >= 5s, JS challenge токен, IP+fingerprint rate limit, silent drop).
5. **seo-crawler-audit & seo-geo-optimization** — после/вместе с публичным контентом страницы (metadata/copy structure/crawl check).
6. **seo-productive** — стратегия/план роста; page edits из плана → снова seo-geo (+ ui-master если трогаем вёрстку).
7. **hz-feature-matrix-qa-loop (/goal)** — канонический реестр фич, цикл тестирования всех сценариев, исправление и повторная верификация.

Пример: «переделай лендинг и продвинь» → hz-master (план + DESIGN.md) → ui-master (landing lock!) → seo-geo на публичных блоках → seo-crawler-audit → seo-productive plan.  
Пример: «задеплой HZschool» → hz-cicd only.  
Пример: «добавь форму заявки» → ui-master (модалка по hz-forms-as-modals) + hz-forms-anti-bot (5 уровней защиты).

---

## 3. Hard rules

1. **CodeGraph First (`hz-codegraph-first`)**: В репозиториях с `.codegraph/` ВСЕГДА использовать `codegraph_explore` / `codegraph explore` до grep/find.
2. **UI без ui-master gate = провал задачи** (даже если tsc/build зелёный).
3. **Не меняй стили/лендинг**, если пользователь не просил (AGENTS «не меняй стили» + brand lock).
4. **Формы = модалки (`hz-forms-as-modals`)**: Вне лендинга создавать модальные окна (Dialog/Drawer), а не инлайн-блоки в разметке.
5. **Админка = графики с первого дня (`hz-admin-charts`)**: Наглядные метрики и графики с 5 периодами (день/неделя/месяц/квартал/год).
6. **Палитра темы (`hz-theme-palette`)**: Только системные семантические переменные темы (`bg-background`, `text-foreground`, `bg-card`, `border-border`). Запрет hardcoded slate-950/zinc-900.
7. **Секреты** не писать в файлы/чат — только имена env / sync script (`hz-cicd`).
8. **SEO страницы ≠ продвижение**: meta/JSON-LD → seo-geo; «продвинь сайт» → seo-productive.
9. **Сразу git commit после изменений (`hz-commit-after-global`)**: Фиксация коммита в каждом затронутом репозитории сразу после готовности логической части.
10. После выбора primary — **Read** его `SKILL.md` целиком (и linked refs по skill), затем действуй.

---

## 4. Agent startup checklist

```
HZ Orchestrator:
Primary: <skill>
Secondary: <none | list>
CodeGraph: <codegraph_explore / skip (.codegraph absent)>
Brand / deploy lock: <n/a | file | «не трогать лендинг»>
Next action: Read <path>/SKILL.md
```

Нет classification → не начинай крупные правки.

---

## 5. Downstream (делегирование)

| Skill | Delegates further to |
| --- | --- |
| hz-master | brandkit, high-end-visual-design, gpt-taste, industrial-brutalist-ui, minimalist-ui, stitch-design-taste, image-to-code, hz-forms-anti-bot, hz-feature-matrix-qa-loop, codegraph, vercel-react-best-practices, vercel-composition-patterns, vercel-optimize, vercel-react-view-transitions, web-design-guidelines, writing-guidelines, deploy-to-vercel, vercel-cli-with-tokens |
| hz-rules | все обязательные глобальные инженерные и UI стандарты HZ (1-52) |
| ui-master | craft-ui, design-system, better-ui, apple-design, transitions-dev, transitions-polish, high-end-visual-design, design-taste-frontend-v1, web-design-guidelines, vercel-composition-patterns, vercel-react-best-practices, vercel-react-view-transitions |
| hz-forms-anti-bot | honeypot, formStartedAt timing (>=5s), JS challenge token, rate-limiter (IP+UA), server silent drop |
| hz-cicd | эталонные workflows hellpsychologist / lawyer_landing / automarketing / lykon |
| seo-crawler-audit | crawler checks, HTTP 200, title <=60, description 120-160, sitemap.xml, noindex |
| seo-geo-optimization | project `src/lib/seo/*`, JSON-LD, FAQ, llms.txt, AI search engine visibility |
| seo-productive | automarketing bot + seo-geo for page ship |

---

## 6. Failure modes

- Начинаешь править код без проверки CodeGraph (`codegraph_explore`) при наличии `.codegraph/` → abort, запусти исследование графа.
- Правишь UI «из головы» без Mandatory reads ui-master → abort, открой skill.
- Делаешь форму без 5-уровневой анти-бот защиты → abort, подключи hz-forms-anti-bot.
- Деплой «как на Vercel» без hz-cicd → abort, читай hz-cicd.
- Пишешь контент-план в seo-geo или meta-теги в seo-productive → переключи skill.
