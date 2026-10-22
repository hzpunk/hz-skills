---
name: hz-master
description: >-
  Мультикомандный автономный рабочий процесс HZ Master. Объединяет планирование,
  интервью, агентскую оркестрацию, исследование кодовой базы (codegraph-first), live-документацию (context7),
  high-end дизайн, anti-slop фронтенд, brutalist & minimalist UI, Supabase/Postgres архитектуру, Remotion/Hyperframes видео,
  image-to-code, full-output enforcement, Playwright E2E автоматизацию, LangGraph графы, Superpowers TDD, веб-разработку, обучение и верификацию.
---

# HZ Master Autonomous Pipeline

Мультикомандный режим разработки активируется полной согласованной цепочкой скиллов экосистемы HZ:

**1. Discovery, Interview & Specs:**
`/plan` · `/grill-me` · `batch-grill-me` · `grill-with-docs` · `to-spec` · `to-tickets` · `to-questionnaire` · `brainstorming` · `writing-plans`

**2. Architecture, CodeGraph & Live Docs:**
`/codegraph` (`codegraph_explore`) · `context7` (`@upstash/context7-mcp`) · `improve-codebase-architecture` · `codebase-design` · `domain-modeling` · `ubiquitous-language` · `setup-ts-deep-modules` · `turborepo`

**3. High-End UI/UX Design System & Master Gate:**
`/ui-master` · `craft-ui` · `design-system` · `better-ui` · `apple-design` · `canvas-shaders` · `creative-motion-components` · `ai-ux-playground` · `transitions-dev` · `transitions-polish` · `transitions-ui-generation` · `animation-vocabulary` · `better-colors` · `better-layout` · `better-typography` · `better-accessibility` · `better-interface` · `bklit-ui` · `ui-styling` · `ui-ux-pro-max` · `banner-design` · `emil-design-eng` · `high-end-visual-design` · `design-taste-frontend-v1` · `gpt-taste` · `industrial-brutalist-ui` · `minimalist-ui` · `stitch-design-taste` · `brandkit` · `image-to-code` · `imagegen-frontend-web` · `imagegen-frontend-mobile` · `redesign-existing-projects`

**4. Engineering Standards, Full Output & Vercel Performance:**
`/full-output-enforcement` · `/modern-web-guidance` · `/generative_ui` · `vercel-composition-patterns` · `vercel-react-best-practices` · `vercel-react-view-transitions` · `web-design-guidelines` · `vercel-optimize` · `writing-guidelines` · `better-writing`

**5. Database & High-Load Postgres:**
`supabase` · `supabase-postgres-best-practices`

**6. Video, Motion & Procedural Canvas:**
`remotion-create` · `remotion-best-practices` · `remotion-render` · `remotion-interactivity` · `remotion-captions` · `remotion-saas` · `hyperframes` · `hyperframes-creative` · `canvas-shaders` · `mediabunny` · `media-use`

**7. Forms Anti-Bot, Input Masks & Mandatory Feedback:**
`hz-forms-anti-bot` · `hz-input-masks-mandatory` · `hz-mandatory-user-feedback` · `hz-compact-data-display-and-details-view` · `hz-buyer-only-lead-qualification` · `hz-admin-charts` · `hz-forms-as-modals` · `hz-theme-palette`

**8. Multi-Agent Orchestration, TDD, Browser Automation & Superpowers:**
`using-superpowers` · `subagent-driven-development` · `test-driven-development` · `systematic-debugging` · `verification-before-completion` · `using-git-worktrees` · `finishing-a-development-branch` · `requesting-code-review` · `receiving-code-review` · `dispatching-parallel-agents` · `playwright-mcp` · `langgraph` · `/teamwork-preview` · `/boost`

**9. SEO, Infrastructure, Production Truth & Memory:**
`seo-crawler-audit` · `seo-geo-optimization` · `seo-productive` · `deploy-to-vercel` · `vercel-cli-with-tokens` · `hz-cicd` · `hz-rules` · `/learn` · `/goal`

---

## Регламент исполнения:

### 1. Интервью, План и Упреждающие Уточнения (`/grill-me` + `/plan` + `batch-grill-me` + `to-spec` + `to-tickets` + `brainstorming` + `hz-proactive-clarifications` + `hz-ask-before-delete`)
- **Запрет на додумывание**: Если данных не хватает, если формулировка допускает двоякое толкование или есть развилка в логике/дизайне/контенте — **не гадать молча**.
- **Запрет на удаление без спроса (`hz-ask-before-delete`)**: Если пользователь критикует фичу или называет её неудачной, **строго запрещено удалять её под корень**. Сначала спросить: «Удалить полностью или исправить?», и если исправить — спросить «Как именно переделать?».
- **Проактивные вопросы**: Заранее задать уточняющие вопросы пользователю (через `ask_question` или четкий список вариантов), подсвечивая скрытые нюансы (юридическая чистота, недостающий контент, поведение на смартфонах).
- **Спецификации и Декомпозиция (`to-spec` + `to-tickets`)**: Перед началом объемной работы формализовать функциональные требования, критерии приемки и разбить проект на атомарные задачи/тикеты.
- **Брейншторминг (`brainstorming`)**: Исследовать альтернативные подходы и нестандартные архитектурные решения до утверждения плана.
- Оформить артефакт `implementation_plan.md` с описанием задачи, архитектуры и плана проверок.
- Запросить подтверждение пользователя перед вносом изменений.

---

### 1.1. Исследование Кодовой Базы (`hz-codegraph-first` + `codegraph_explore`)
- **CodeGraph First**: При наличии директории `.codegraph/` в корне проекта ВСЕГДА обращаться к CodeGraph (`codegraph_explore` MCP tool или CLI `codegraph explore "<query>"`) ПЕРЕД grep/find или прямым чтением файлов.
- **Точные символы и динамические цепочки вызовов**: Получать исходный код с номерами строк и отслеживать сквозные пути вызовов, включая динамическую диспетчеризацию, в один запрос без блуждания по файлам.
- **Трассировка зависимостей перед рефакторингом**: Найти всех вызывающих затронутую функцию (callers), понять полное поведение и проверить архитектурные границы до внесения первого диффа.
- **Fallback**: grep/find использовать только для статических файлов конфигураций, markdown и env-файлов, либо при отсутствии индекса `.codegraph/`.

---

### 1.2. Актуальная Документация в Реальном Времени (`context7` + `@upstash/context7-mcp`)
- **Live Docs First**: При работе с внешними библиотеками, SDK, API или обновленными версиями фреймворков (Next.js 15, React 19, Supabase, Tailwind, Framer Motion, LangGraph) ВСЕГДА запрашивать актуальную документацию через Context7 MCP.
- **Защита от галлюцинаций**: Использовать `resolve_library_id` и `get_library_docs` для получения верифицированных сигнатур методов и актуальных сниппетов вместо устаревших данных из весов модели.

---

### 2. Модульная Архитектура и Чистый Код (`improve-codebase-architecture` + `domain-modeling` + `setup-ts-deep-modules` + `turborepo`)
- **Domain-Driven Design (DDD)**: Выделять богатые доменные модели, защищать инварианты сущностей и поддерживать единый язык предметной области (`ubiquitous-language`).
- **Глубокая инкапсуляция модулей (`setup-ts-deep-modules`)**: Скрывать внутреннюю реализацию за публичными фасадами (`index.ts`), предотвращать протекание кишок модулей наружу.
- **Масштабирование в монорепозиториях (`turborepo`)**: Настраивать кэширование сборки, параллельные конвейеры задач и оптимизировать границы пакетов.
- **Безопасный рефакторинг (`request-refactor-plan`)**: Готовить структурированный план изменений перед масштабной перестройкой кодовой базы.

---

### 3. Гарантия Полного Вывода Кода (`full-output-enforcement`)
- **Полный запрет на плейсхолдеры и усечения**: Категорически запрещены комментарии вида `// TODO`, `// ... остальной код без изменений`, `/* rest of styles */`, `<!-- same as before -->`.
- Код всегда генерируется целиком, в готовом к запуску виде.
- При редактировании больших файлов через инструменты точечной замены заменять строго конкретный блок с сохранением контекста.
- При создании новых файлов или компонентов никогда не оставлять «заглушек» на потом — вся логика и разметка должны быть полноценными.

---

### 4. Дизайн-Система, Айдентика и Документация (`stitch-design-taste` + `brandkit` + `DESIGN.md` First)
- **`DESIGN.md` First**: На старте проекта или крупной фичи обязательно создавать/актуализировать файл `DESIGN.md` в корне репозитория по стандартам `stitch-design-taste`.
- В `DESIGN.md` фиксировать философию стиля, цветовую палитру (токены), типографику, сетку, правила мобильной адаптации и анатомию ключевых блоков. Вся дальнейшая верстка ведется строго по `DESIGN.md`.
- **Премиальная айдентика (`brandkit`)**: Осознанная разработка систем логотипов, выверенная композиция, сдержанная благородная типографика, сильный символизм и модульные дизайн-системы под характер проекта.

---

### 5. High-End Визуальный Вкус и Anti-Slop Стандарты (`high-end-visual-design` + `design-taste-frontend` + `design-taste-frontend-v1` + `gpt-taste` + `ui-master`)
- **Полное искоренение Generic AI Slop**:
  - Никаких одинаковых 3-колоночных карточек с сине-фиолетовыми градиентами и дефолтными иконками в кружочках.
  - Никаких монотонных чередований «текст слева / картинка справа».
  - Никакого невидимого низкоконтрастного текста или мусорных плашек «SECTION 01», «FEATURE 04».
  - **Запрет мета-стилевых пометок в скобках (`hz-no-meta-style-labels`)**: Категорически запрещено писать в UI пояснения в скобках вроде `(n8n style)`, `(Notion-подобный)`, `(как в Telegram)`. Все названия обязаны быть самодостаточными и на чистом доменном языке продукта.
- **Динамическая калибровка и строгий baseline (`design-taste-frontend-v1`)**:
  - Базовые шкалы: `DESIGN_VARIANCE: 8`, `MOTION_INTENSITY: 6`, `VISUAL_DENSITY: 4`.
  - Строгий запрет шрифтов с засечками (Serif) для дашбордов и панелей управления (строго чистые Sans-Serif + Monospace).
  - Максимум 1 акцентный цвет с насыщенностью < 80% (полный Lila Ban).
  - При высокой плотности данных (`VISUAL_DENSITY > 7`) запрет упаковки каждой цифры в карточку — использовать чистое структурное разделение (`divide-y`, `border-t`).
  - Обязательная реализация полного цикла состояний: skeletal loader, осмысленный empty state, четкие inline errors.
- **Широкая монументальная типографика (`gpt-taste` + `better-typography`)**: Запрет на узкие контейнеры заголовков с 5–6 строчными переносами. Заголовки плотные, выразительные и легко сканируемые.
- **Плотные бенто-сетки (Gapless Bento Grids)**: Выверенные пропорции ячеек без случайных дыр.
- **Awwwards-уровень интерактивности (`transitions-dev` + `transitions-polish` + `animation-vocabulary`)**: Аппаратные анимации с пиннингом, стэкингом и плавным скраббингом без дерганий и layout thrashing. Нажатие `scale(0.96)`, вход `cubic-bezier(0.22, 1, 0.36, 1)`, запрет `transition: all`.

---

### 5.1. Креативный Motion, Холст-Шейдеры и Премиальные Компоненты (`canvas-shaders` + `creative-motion-components` + `ai-ux-playground` + `transitions-dev` + `emil-design-eng`)
- **Paper Design WebGL Shaders (`@paper-design/shaders-react`)**:
  - Каталог из 30 процедурных шейдеров: `MeshGradient`, `LiquidMetal`, `NeuroNoise`, `GodRays`, `FlutedGlass`, `Metaballs`, `Dithering`, `HalftoneDots`, `LensDistortion`, `Water`, `Waves`, `PerlinNoise`, `SimplexNoise`, `Voronoi`, `Warp`, `PulsingBorder`.
  - Запуск строго на GPU через HTML5 Canvas без Three.js; динамический импорт (`next/dynamic` с `ssr: false`).
- **Библиотека 43+ UI-анимаций Transitions.dev (`transitions-dev`)**:
  - Полный импорт эталонных микро-анимаций: 3D-tilt, gooey plus menu morph, dropdown morph, smoky dissolve delete, drag-and-drop physics, thinking states, reasoning stream, matrix dot loader, banner stacking, donut chart, skeleton loader & reveal, tabs sliding, number pop-in.
- **Креативные компоненты нового поколения (`creative-motion-components`)**:
  - **Superdesign.dev**: Portal hero раскрытие (раздвигающиеся створки с синхронным зумом фонового изображения).
  - **UI-Layouts (`ui-layouts.com`)**: Bento-сетки, sticky scroll card stacking (липкие карточки с наплывом), 3D-карусели.
  - **React Bits (`reactbits.dev`)**: Кинетическая типографика (SplitText, BlurText, ShinyText, DecryptedText, TrueFocus), физические карточки (SpotlightCard, TiltedCard, Magnet), фоновые паттерны (Aurora, Hyperspeed, Particles).
  - **Magic UI (`magicui.design`)**: BorderBeam, Marquee, Animated Grid Pattern, Retro Grid, Number Ticker, Animated Beam, Orbiting Circles.
  - **Aceternity UI (`ui.aceternity.com`)**: 3D Card Effect, Background Beams, Background Boxes, Hero Parallax, Lamp Effect, Tracing Beam, Canvas Reveal, Wobble Card.
  - **Motion Primitives (`motion-primitives.com`)**: Text Morpher, Dynamic Island, Magnetic Container, Border Trail, Animated Tabs.
  - **Codrops Tympanus (`tympanus.net/codrops/demos/`)**: Жидкие искажения (SVG feTurbulence + feDisplacementMap), WebGL морфинг страниц, кинетический скролл.
  - **HeroUI (`heroui.com`)**: Доступные примитивы, модалки с флюидным блюром, Compound Components.
- **AI UX Playground (`ai-ux-playground`)**:
  - 17 передовых экспериментов: Liquid Gooey (SVG feColorMatrix), Chenglou Pretext (жидкая верстка без reflow), Dialkit (ротационная физика и крутилки с детентами), Tenor (многослойная глубина), Dot Matrix LED, Liquid Metal Logo, Patchwork Bento, Kinetics Colorion, Floating Books (3D свет), VGPU, Noman Dot Shader, Thinking Orbs (пульсирующие сферы рассуждений ИИ), ItsHover (курсор-параллакс), Robot Node Grid (тактические кибернетические панели).
- **Дизайн-инженерия Эмиля Ковальски (`emil-design-eng`)**:
  - `animate`, `animation-performance`, `apple-design`, `ask-sonner`, `break-ui`, `find-animation-opportunities`, `improve-animations`, `mobile-native`, `pick-ui-library`, `prototype`, `review-animations`, `write-swift` и `performance-cheatsheet.md`.

---

### 6. Стилистические Направления: Brutalism & Minimalism (`industrial-brutalist-ui` + `minimalist-ui`)
- **Industrial Brutalism & Tactical Telemetry (`industrial-brutalist-ui`)**:
  - Для дашбордов, торговых терминалов, мониторинга, финтеха и систем реального времени.
  - Жесткие сетки, моноширинные акценты, тактическая информационная плотность, микро-бейджи статусов, высокая контрастность, отсутствие декоративного «мыла».
- **Premium Utilitarian Minimalism (`minimalist-ui`)**:
  - Для лендингов, портфолио, медиа и SaaS продуктов.
  - Чистая editorial-эстетика, спокойный монохром, приглушенные акценты, архитектурный баланс белого пространства (留白 Liu Bai), отказ от грязных теней.

---

### 7. Image-First Пайплайн и Экспертный Редизайн (`image-to-code` + `imagegen-frontend-web` + `imagegen-frontend-mobile` + `redesign-existing-projects`)
- **Image-to-Code Pipeline (`image-to-code`)**: Для визуально ответственных интерфейсов сначала генерировать концепт-арт/референс, глубоко анализировать сетку, цвета, свет и типографику, затем воплощать в коде с максимальной точностью.
- **One Horizontal Image Per Section (`imagegen-frontend-web`)**: При генерации референсов веб-сайта создавать отдельное горизонтальное изображение под каждую смысловую секцию, гарантируя единую цветовую гамму.
- **App-Native Mobile Framing (`imagegen-frontend-mobile`)**: Мобильные интерфейсы проектировать с акцентом на эргономику под большой палец, консистентные экраны и аккуратную подачу.
- **Audit-First Редизайн (`redesign-existing-projects`)**: При обновлении существующих проектов сначала проводить аудит generic-паттернов, выявлять узкие места верстки и переводить интерфейс на премиальный уровень без слома бизнес-логики.

---

### 8. Базы Данных, Postgres и Supabase (`supabase` + `supabase-postgres-best-practices`)
- **Безопасность по умолчанию (RLS)**: Row Level Security обязателен на всех таблицах. Политики пишутся осознанно для `SELECT`, `INSERT`, `UPDATE`, `DELETE` с проверкой `auth.uid()`.
- **Индексы и производительность**: Создание B-tree и GIN индексов под частые выборки и внешние ключи. Исключение seq scans через `EXPLAIN ANALYZE`.
- **Атомарность и миграции**: Все изменения схемы ведутся через версионируемые SQL-миграции. Использование транзакций и ограничений целостности (`FOREIGN KEY ON DELETE CASCADE/SET NULL`, `CHECK`).

---

### 9. Программное Видео и Motion Engine (`remotion-*` + `hyperframes-*` + `mediabunny`)
- **Автоматизация видео на React (`remotion-best-practices`)**: Рендеринг 60fps видео, композиция таймлайнов, предзагрузка ассетов, динамические субтитры (`remotion-captions`) и адаптивный рендеринг через CLI/Serverless.
- **Процедурная графика и Canvas (`hyperframes`)**: Создание сложных процедурных анимаций, аудиовизуализации и keyframe-анимаций на базе чистого WebGL/Canvas.

---

### 10. Веб-стандарты, App-like UX и Компоненты (`modern-web-guidance` + `generative_ui` + `vercel-composition-patterns` + `vercel-react-best-practices` + `web-design-guidelines` + `vercel-react-view-transitions`)
- **Масштабируемые паттерны композиции React (`vercel-composition-patterns`)**:
  - Строгий отказ от «разрастания boolean-пропсов» (`isOpen`, `isCompact`, `withBorder`, `hasHeader`, `isSecondary` в одном компоненте).
  - Использование составных компонентов (Compound Components: `<Dialog.Root>`, `<Dialog.Trigger>`, `<Dialog.Content>`), поднятие состояния (lifting state), render-пропсы и контекст.
  - Нативные паттерны React 19: хуки `useActionState`, `useOptimistic`, распаковка промисов через `use()`, Server Actions.
- **70 правил инженерной производительности Vercel & Next.js (`vercel-react-best-practices`)**:
  - Приоритет Server Components (RSC): рендеринг данных на сервере, изоляция клиентской интерактивности в листьях дерева (`'use client'`).
  - Устранение водопадов запросов (Waterfall Elimination): параллельный fetching (`Promise.all`), предварительный запуск запросов до рендера.
  - Оптимизация бандла: динамический импорт тяжелых библиотек и диалогов (`next/dynamic` с `ssr: false`), удаление мертвых импортов.
  - Оптимизация шрифтов и картинок: `next/font`, `next/image` с `priority` для LCP, явными `width`/`height` для нулевого CLS.
- **Аудит по Web Interface Guidelines (`web-design-guidelines` + `better-accessibility`)**:
  - Семантические теги (`nav`, `main`, `header`, `footer`), клавиатурная навигация (Tab/Esc/Enter), ARIA-атрибуты для кастомных контролов (`aria-expanded`, `aria-selected`), минимальный размер тач-таргетов 44×44px, контрастность текста по WCAG AA.
- **Нативные бесшовные анимации View Transitions (`vercel-react-view-transitions`)**:
  - Применение нативного браузерного `document.startViewTransition` и `<ViewTransition>` для анимации переходов между маршрутами и состояниями.
- **App-like Mobile Experience (`hz-mobile-first-app-like`)**: Мобильная версия верстается с приоритетом эргономики под большой палец, тач-таргетами от 44px, выдвижными шторками Drawer вместо десктопных выпадашек и нулевым горизонтальным скроллом.
- **Округлая плавающая мобильная навигация и Zero-Reflow динамика (`hz-mobile-dynamic-pill-dock`)**: Мобильная навигация оформляется округлым плавающим островом (floating pill). Любые скролл-анимации выполняются строго на GPU (`scale`, `translateY`, `opacity`) без layout thrashing.
- **Мобильная эргономика, читаемость и запрет микро-шрифтов (`hz-mobile-first-readability`)**: Строгий запрет на шрифты 8-10px на смартфонах. Основной текст — от 14-16px, служебный — от 12px. Чистый воздушный поток без избыточных рамок.
- **Кастомный UI (`hz-custom-ui-exclusive`)**: Полный запрет на дефолтные HTML/браузерные элементы (`select`, `alert`, `confirm`). Все компоненты — авторские в дизайн-системе проекта.

---

### 11. Формы, Маски, Анти-Бот Защита и Фидбек (`hz-forms-anti-bot` + `hz-input-masks-mandatory` + `hz-mandatory-user-feedback` + `hz-compact-data-display-and-details-view`)
- **Обязательная 5-уровневая анти-бот защита любых форм (`hz-forms-anti-bot`)**:
  1. **Honeypot-поле (`companyWebsite`)**: скрытое поле (`display: none`, `tabIndex={-1}`, `aria-hidden="true"`). Заполнено -> бот.
  2. **Временная метка (>= 5 секунд)**: `formStartedAt`. Если форма отправлена быстрее 5 секунд — бот.
  3. **Детерминированный JS challenge токен**: вычисляется синхронно в JS.
  4. **Двухфакторный Rate-limit**: по IP (до 12/час) и по Fingerprint `ip::user-agent::accept-language` (до 4/10мин).
  5. **Серверный Silent Drop**: возврат успешного HTTP 201 Created боту без сохранения в БД и без отправки уведомлений в Telegram/CRM.
- **Обязательные интерактивные маски ввода (`hz-input-masks-mandatory`)**:
  - Полный запрет на «голые» текстовые инпуты для телефонов, дат, сумм и кодов.
  - Живая маска телефона: дефолт `+7 (999) 123-45-67`. Автозамена первой `8` или `9` на `+7 (9...`, поддержка чистки при вставке (Paste), удобный Backspace. В UI отображается форматированная маска, на бэкенд передается канонический E.164 (`+79685462359`).
  - Коды подтверждения (SMS/OTP): только цифры, моноширинный трекинг (`font-mono tracking-widest text-center`) или раздельные ячейки.
- **Обязательный мгновенный фидбек для пользователя (`hz-mandatory-user-feedback`)**:
  - Кнопка при клике мгновенно блокируется (`disabled`) и показывает спиннер (`Loader2`) с текстом действия («Отправка...»).
  - Запрет тихого проглатывания ошибок (No Silent UI Failures): контрастный баннер (`AlertCircle`) с человекочитаемым описанием причины.
  - Подтверждение успеха: контрастный баннер, тост или плавный переход без резкого сброса полей.
- **Компактный реестр данных и модальный просмотр (`hz-compact-data-display-and-details-view`)**:
  - Таблицы и списки данных — 1 строка, scannable, лаконичные бейджи.
  - Подробные тексты, история, цитаты и детальный разбор открываются строго в модальном окне Detail Modal / Drawer.
- **Строгая квалификация только клиентов и покупателей (`hz-buyer-only-lead-qualification`)**:
  - В лидогенерации собирать только реальных покупателей со сформированным спросом.
  - Полный трехконтурный отсев продавцов, мастеров, фабрик, цехов, спамеров и рекламных менеджеров каналов.

---

### 12. Прагматизм, Тексты и Юридическая База (`writing-guidelines` + `better-writing` + `hz-anti-ai-slop-pragmatism` + `hz-legal-compliance`)
- **Стандарты продуктового текста (`writing-guidelines` + `better-writing`)**: Активный залог, короткие предложения, отсутствие «воды» и канцелярщины. Единый уверенный Tone of Voice.
- **Юридическая чистота (`hz-legal-compliance`)**: Чекбокс согласия на обработку ПДн (152-ФЗ РФ), модалка «Политика конфиденциальности», официальные реквизиты ООО «ЭЙЧЗЕТКОМПАНИ» в футере.

---

### 13. Стабильность Анимаций и Архитектура Zero-Jitter (`hz-zero-jitter-architecture`)
- **Разделение transforms и Framer Motion**: Никогда не вешать motion `y/scale` на контейнеры со статическим Tailwind-центрированием (`-translate-x-1/2`).
- **Zero-Jitter Inactive**: В переходах `inactive` анимируют исключительно `opacity`.
- **Zero First-Render Flash**: Использовать `initial={false}` на первом экране.
- **No Layout Reflow в табах**: Интерактивные шаги не должны дергать габариты соседних блоков.

---

### 14. Автоматизация, Тестирование и Супер-Инструменты (`playwright-mcp` + `using-superpowers` + `test-driven-development` + `systematic-debugging` + `using-git-worktrees` + `langgraph`)
- **Браузерная E2E Автоматизация (`playwright-mcp`)**:
  - Проверка реального UI, доступности, заполнения форм и скриншот-тестирование через семантическое дерево доступности.
- **Методология Superpowers (`using-superpowers`)**:
  - **TDD (`test-driven-development`)**: Написание падающих тестов перед реализацией бизнес-логики.
  - **Систематический дебаггинг (`systematic-debugging`)**: Четырехфазный поиск причин (воспроизведение, изоляция, исправление, ретест) без слепых попыток «наудачу».
  - **Изолированные ворктри (`using-git-worktrees`)**: Изоляция веток для параллельных задач без порчи рабочего дерева.
  - **Верификация перед сдачей (`verification-before-completion`)**: Реальные доказательства работоспособности (прогон тестов, вызовы curl, сборка) до утверждения о готовности.
- **Сложные Графовые Агенты (`langgraph`)**:
  - Построение надежных рабочих процессов с циклами, персистентностью состояния в Postgres/SQLite, чекпоинтами и human-in-the-loop (`interrupt()`).
  - Локальная отладка через LangGraph CLI (`langgraph dev`) и Studio.

---

### 15. Производственный Цикл, SEO, Краулинг-аудит и Оптимизация Vercel (`hz-production-business-lifecycle` + `seo-crawler-audit` + `seo-geo-optimization` + `vercel-optimize`)
- **Оптимизация Vercel (`vercel-optimize`)**:
  - Профилирование времени серверных функций, минимизация Function Invocations, тегированное кэширование (`revalidateTag`). Core Web Vitals в зеленой зоне (LCP < 2.5s, INP < 200ms, CLS < 0.1).
- **SEO & Краулинг (`seo-crawler-audit` + `seo-geo-optimization`)**:
  - Meta Title строго $\le 60$ символов, Meta Description строго 120–160 символов.
  - Быстрый HTTP 200 при параллельном обходе роботов, валидные sitemap и robots.txt.
  - GEO-привязка и GGO (Generative Engine Optimization) под ChatGPT, Perplexity, Яндекс Нейро.

---

### 16. Глобальные Стандарты HZ (`/hz-rules` + `deploy-to-vercel` + `vercel-cli-with-tokens`)
- Палитра темы проекта (`hz-theme-palette`): строго системные семантические токены (`bg-background`, `text-foreground`, `bg-card`, `border-border`). Запрещен hardcode slate-950.
- Админка = Графики с первого дня (`hz-admin-charts`): переключатель 5 периодов (день/неделя/месяц/квартал/год).
- Формы = Модалки (`hz-forms-as-modals`): вне лендингов формы открываются в Dialog/Drawer.
- Git Commit сразу (`hz-commit-after-global`): коммит после каждой готовой фичи.
- Live Production Truth (`hz-verify-live-before-claiming`): проверка live/deploy перед заявлением о готовности.
- Краткие ответы (`hz-brief-responses`): без трёпа, в конце одна короткая строка.

---

### 17. Обучение (`/learn`)
- Фиксация выявленных ошибок и новых правил в глобальный плагин правил после согласования с пользователем.

---

### 18. Автономный Цикл Верификации и Завершение (`/goal` + `hz-feature-matrix-qa-loop`)
- **Директива сквозного аудита и верификации**:
  ```
  /goal go over every single feature in this app create a user story with expected behaviour based on the code keep a single canonical spreadsheet tracking the features status
  • when done switch loop to testing every user story and documenting all errors
  • when done fix every logistical error or ux error
  • test every user behaviour again post fix
  ```
- **Четырехэтапный цикл**:
  1. Инвентаризация и канонический реестр (User Stories & Spreadsheet).
  2. Сквозное тестирование всех позитивных и негативных сценариев.
  3. Устранение всех выявленных логистических и UX-ошибок.
  4. Повторное тестирование post-fix, подтверждение зеленой сборки (`npm run build`) и финализация.
