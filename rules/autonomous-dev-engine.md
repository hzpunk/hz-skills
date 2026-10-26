# HZ Autonomous Development & Self-Evolution Protocol

Whenever working on any development, bugfix, refactoring, or feature request in this project, the agent MUST automatically execute this full-cycle pipeline without waiting for manual commands:

## 1. Autonomous Pre-flight Recall & Zero-to-One Setup
Before writing or modifying code:
- Check past invariants and anti-patterns relevant to the task using `hz vault query "<keywords>"` or reading `.hz/invariants.json`.
- Ensure you do NOT repeat documented mistakes (e.g., animating `filter: blur` on scroll, hardcoding `slate-950/900`, omitting honeypot fields).
- **Zero-to-One Project Standard:** For any new project or venture launched via `/dev`, immediately execute the full Boardroom pre-dev package (`01-07` artifacts, SOPs, executive dashboard), create the private GitHub repository with 5 Milestones (due dates), seed issues with acceptance criteria, deploy CI/CD workflows (CI, Gitleaks, CodeQL, Preview), configure environments (`staging`, `production`), and wire the Google Jules autonomous pipeline (`jules-automation.yml`).

## 2. Invariant Code Architecture (Quality Gates)
Enforce the project standards natively:
- **Palette (`hz-theme-palette`):** Only semantic CSS variables (`bg-background`, `text-foreground`, `bg-card`, `border-border`). Banned: `slate-950`, `slate-900`, `bg-black`, raw hex colors.
- **Forms (`hz-forms-as-modals`):** All forms must be modal dialogs unless explicitly specified as inline.
- **Admin & Analytics (`hz-admin-charts`):** Admin screens must include charts and period toggles (day / week / month / year).
- **Anti-Bot (`hz-forms-anti-bot`):** All lead/contact forms require a honeypot field (`z.string().max(0)`) and client-side throttle.

## 3. Autonomous Verification Before Completion
Before reporting completion to the user:
- Run `hz review` to guarantee 0 violations of theme, CISO, and form standards.
- Run `npm run build` (or relevant test suite) to guarantee 0 compile, type, or export errors.

## 4. Autonomous Self-Evolution (`hz-learn-from-mistakes`)
- If a bug, build failure, or performance issue was diagnosed and resolved during the turn, call `hz learn "<Title>" "<Problem>" "<Solution>"` to permanently evolve the knowledge vault.

## 5. Autonomous Commit (`hz-commit-after-global`)
- Run `hz commit` immediately upon feature completion (never `git push` unless explicitly asked).

## 6. Response Discipline (`hz-brief-responses`)
- Keep output concise, factual, without fluff, ending with one short line.

## 7. Cloudflare Platform Standards
- When interacting with Cloudflare, use the `cf` CLI unless the project has a Wrangler configuration file.

## 8. Webhook & MCP Gateway Standards (ngrok & Cloudflare Free Superpowers)
- Use `ngrok` CLI or Cloudflare Workers/Tunnel for exposing local MCP servers and real-time webhook ingestion instead of noisy local polling loops.
- Deliver reactive event payloads to active sessions via `agentapi send-message`.
- **Form Anti-Bot:** Integrate Cloudflare Turnstile (`hz-forms-anti-bot`) on public forms (0 cost, invisible bot defense).
- **Zero-Egress Storage:** Use Cloudflare R2 for user documents/diplomas with 30-day lifecycle auto-deletion (152-ФЗ compliance).
- **Workers AI:** Use Workers AI (`@cf/openai/whisper`) for free speech-to-text crisis intake.
- **Tunnel Economy (`hz-tunnels-economy`):** Use Cloudflare Quick Tunnel (`npm run tunnel:quick` / `cloudflared tunnel --url http://localhost:3000`) for public previews and mobile testing without burning ngrok credits. Use `ngrok` (`npm run tunnel:dev`) strictly for webhook debugging with local replay inspector (`localhost:4040`).

## 9. Sensitive Domain & Psychological Safety Standards (`hz-sensitive-safety-first` & `hz-wcag-contrast-aa`)
- **Signal Colors:** In psychological assistance contexts, never use alarming red (`#EF4444`). Use soothing terracotta/brick (`#A23B0B`) for crisis and error states to minimize anxiety.
- **Privacy & 152-ФЗ:** Isolate crisis question texts strictly within the moderator card; never log raw crisis text to general application logs or consoles.
- **Mandatory Safety Circuit:** Include clear emergency service disclaimers («112 при опасности для жизни») and automated crisis keyword detection.
- **WCAG AA Contrast:** Maintain minimum 4.5:1 text contrast on soft/paper card backgrounds (`#F5F3EF`, `#ECE9E3`); avoid low-contrast faded greys.
- **Youth ToV & Zero Friction (`hz-youth-tov-zero-friction`):** For student and youth funnels, adopt an empathetic, direct "friend's voice" without medical condescension, utilizing validating situational hooks and zero-login first-question submission.

## 10. GitHub Project Governance & Jules Orchestration (`hz-github-project-governance` & `hz-jules-webhook-sentinel`)
- **Document-to-Task Pipeline:** Automatically decompose PRDs, architecture specs, and UI mockups into structured GitHub Milestones (M1–M5 with hard due dates) and atomic Issues with explicit Definition of Done.
- **Team Workload Allocation:** Assign each issue to available human contributors (`@hzpunk`, `@VladislavSCV`) or autonomous workers (`@google-jules[bot]`). Maintain zero unassigned or deadline-free tasks.
- **Reactive Surveillance (Webhook Sentinel):** Monitor repo events sub-second via local webhook hub (`scripts/webhook-receiver.py` + `ngrok http 4567`) hooked to `agentapi send-message`. Never resort to polling loops.
- **Jules PR Gatekeeping:** Rigorously audit automated PRs from Jules before merging:
  1. Strip accidental secrets, uncommitted local `.env` files, database dumps, and heavy test artifacts (`playwright-report/`).
  2. Verify all CI pipelines, test suites, and production builds pass 100%.
  3. Squash merge with linked `Fixes #<issue>` semantics.
- **YAML multiline hygiene:** Escape multi-line script strings cleanly in GitHub Actions YAML; avoid CodeQL on private free tier repositories (HTTP 403) and enforce Gitleaks.

## 11. Skills Sync to hz-skills (`hz-skills-sync`)
**When any of the following are created or modified, immediately commit and push to `hzpunk/hz-skills`:**
- A new **skill** (`SKILL.md`) in `skills/`
- A new or updated **global rule** in `rules/`
- A new or updated **subagent** (`.md`) in `agents/`
- A new **MCP server** integration, tool reference, or capability reference
- A new **GEMINI.md** rule addition

**Sync protocol:**
```bash
cd ~/.gemini/config/plugins/hz-rules-plugin
git add -A
git commit -m "feat(skills|rules|agents): <short description>"
git push
```

**This repository is the single source of truth for all HZ agent capabilities.** Any skill or rule that lives only on the local machine is considered incomplete until pushed.

## 12. Multi-Layer Bot & Scraper Defense (`hz-bot-shield` / PatronView Invariant)
- **Edge WAF & ASN Filtering:** Block or challenge datacenter ASNs (AWS, Hetzner, DigitalOcean, OVH) on mutating API endpoints (`/api/*`). Legitimate end-users connect via mobile and residential ISPs.
- **AI-Scraper & Rogue Crawler Blocking:** Proactively block aggressive AI scrapers (`Bytespider`, `GPTBot`, `ClaudeBot`, `CCBot`) to protect confidential user prompts and knowledge bases.
- **Geo-fencing & Managed Challenges:** For regional Russian/CIS services (152-ФЗ compliance), enforce invisible Cloudflare Turnstile (`Managed Challenge`) on foreign/suspicious traffic, mitigating headless bots without annoying humans with CAPTCHAs.
- **Telemetry Isolation (Client Events vs Raw Server Logs):** Construct product funnels strictly from authenticated client browser events (JS/Client events), insulating business metrics from distorted raw server logs where up to 99% of requests are bots.

## 13. HZ Weekly Planner MCP Server (`hz-planner-mcp`)
- **Автономный трекер задач:** Все AI-агенты и нейросети (Antigravity, Cursor, Claude, Jules) используют единый локальный MCP-сервер `hz-planner-mcp` (`~/.local/bin/hz-planner-mcp` или `HZWeekPlannerApp --mcp`) для отслеживания и реализации задач по 7 проектам (typeGO, Т-Банк Хакатон, Frazly, HZ.Support, Юристы, Психологи psycu, SVO, Planner).
- **Инструменты агента:**
  - `planner_list_tasks`: чтение задач с фильтрацией по проекту, дню, статусу, приоритету.
  - `planner_get_weekly_plan`: чтение сводного тактического плана в Markdown.
  - `planner_create_task`: постановка новых задач с привязкой к репозиторию GitHub и календарю.
  - `planner_update_task` / `planner_toggle_status`: перевод в `inProgress` перед началом и `done` после 100% тестов.
  - `planner_get_projects`: список отслеживаемых репозиториев и их ролей.

## 14. Zero Cringe Copywriting & No Condescension (`hz-no-cringe-copy`)
- **Запрет инфантилизирующего и бюрократического кринжа:** Категорически запрещено использовать снисходительные, принижающие, канцелярские и псевдо-заботливые ярлыки вроде «студенческий слот», «льготная запись для бедных студентов», «льготные места» и т.п.
- **Взрослый и уважительный тон:** Использовать прямое, уважительное, зрелое позиционирование: «первая сессия», «индивидуальная консультация», «запись к специалисту», понятная фиксированная стоимость («1 200 ₽ за консультацию») без принижающих ярлыков.

## 15. Logical Integrity & Completeness Gate (`hz-logical-integrity-gate`)
Перед началом написания кода И перед сдачей любой задачи агент ОБЯЗАН провести самоаудит по двум обязательным контрольным вопросам:
1. **«Всё ли я проработал?» (Exhaustive Scope & Completeness):**
   - Учтены ли все роли и акторы системы (клиент, специалист, модератор, анонимный гость)?
   - Проработан ли весь путь пользователя (CJM) от первого экрана до финального результата без оборванных веток?
   - Реализованы ли каналы доставки, подтверждения и обратной связи (уведомления автору, алерты админу, публичная лента)?
   - Предусмотрены ли сценарии отмены, возврата, повторной отправки, пустые состояния и ошибки?
2. **«Всё ли реализовано логически и нет ли элементов, которые могли бы быть логически ошибочными?» (Logical Coherence & Invariant Audit):**
   - Не противоречит ли решение базовой ценности и инвариантам продукта? (Если сервис позиционируется «только проверенные дипломированные психологи» — категорически запрещен авто-пропуск для кого бы то ни было, включая админа/создателя).
   - Нет ли ложных допущений и принудительного хардкода? (Не навязывать специалистам единый метод вроде «КПТ» или фиксированную цену «1 200 ₽», давать настраивать свои условия).
   - Логичны ли переходы состояний конечного автомата (State Machine) — исключить любые лазейки обхода обязательных шагов (например, верификации диплома).
   - Не сломает ли реализация доверие пользователя при реальном живом использовании?

## 16. HZ Foundation Engineering Standard (`hz-foundation-standard`)
- **Единая кодовая база и репозиторий:** Шаблоны клиентских сайтов, SDK, UI-библиотека и шлюз разворачиваются на основе `hz_foundation` (`https://github.com/hzpunk/hz_foundation`, локальный путь: `~/Downloads/hz_foundation`).
- **Архитектурный инвариант лендингов (Landing):** Static Export + Nginx. Строгий запрет Node.js runtime на production для лендингов.
- **Инвариант базы данных для Store/Platform:** SQLite + Drizzle ORM (`@johann1s/db` via libSQL) по умолчанию с автоматизированными бэкапами и миграциями. PostgreSQL выступает исключительно как опциональный адаптер для крупных инсталляций, но никогда не default.
- **Шлюз событий и приватность (152-ФЗ):** Вся браузерная телеметрия (pageviews, leads, telegram alerts) направляется строго через `hz-gateway`. Категорически запрещено помещать секреты сервера (`SITE_TRACKING_TOKEN`) в клиентские JS-бандлы. Контактные данные из форм изолируются и не попадают в открытые аналитические журналы.
- **Модульная генерация через CLI (`hz create` / `hz deploy`):** Один базовый шаблон (`templates/base`) + тип проекта (`landing`, `store`, `platform`) + подключаемые фичи (`features/*`). Запрещено создавать независимые монолитные копии.
- **Доступность и UI:** Дизайн-токены темы без хардкода, обязательная доступность WCAG 2.2 AA (axe checks), `LazyMotion` для оптимизации размера бандла (<210 KiB gzip), уважение системной настройки `prefers-reduced-motion`.

## 17. Multi-Agent CLI Orchestration & Token Economy (`hz-cli-runners-orchestration`)
- **Разрешенные бесплатные CLI-раннеры:** Для рутинного кодинга, тестов, рефакторинга и фоновой автоматизации разрешено и рекомендуется делегировать задачи бесплатным CLI-агентам: `gemini` (1 000 бесплатных запросов/день от Google), `copilot` (GitHub Copilot CLI), `goose` (Block Goose с Codestral/MCP), `opencode` (свободные промо-модели), `mimo` (Xiaomi Mimocode с MCP), `qoder` (Qoder CLI с MCP), `q` (Amazon Q Developer через AWS Builder ID), `aider` (с бесплатными/локальными моделями Ollama/LM Studio или промо Qwen).
- **СТРОГИЙ ЗАПРЕТ НА АВТОМАТИЧЕСКИЙ ВЫЗОВ CLAUDE:** Категорически запрещено автоматически вызывать или тратить платные токены `claude` (Claude Code) без прямого явного указания пользователя в текущем запросе.
- **Единый центр задач:** Все используемые CLI-раннеры обязаны быть интегрированы с единым тактическим центром задач `hz-planner` через MCP.





