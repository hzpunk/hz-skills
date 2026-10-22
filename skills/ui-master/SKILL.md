---
name: ui-master
description: >
  Hard gate for master-level UI/UX. Forces reading and applying craft-ui, design-system,
  better-ui, apple-design, transitions-dev, transitions-polish, high-end-visual-design,
  and design-taste-frontend-v1 before any visual or interaction change. Use ALWAYS when
  building, redesigning, polishing, or reviewing UI, UX, pages, forms, dashboards, auth screens,
  cards, motion, mobile layouts, or when the user attaches craft/better-ui/apple/transitions skills —
  or says «как на главной», «красиво», «UX», «анимации», «редизайн», «мобилка». Do not ship UI
  without completing this skill's gate checklist.
---

# UI Master (hard gate)

**Orchestrator:** for multi-domain HZ tasks start at `hz-orchestrator` (`~/.agents/skills/hz-orchestrator/SKILL.md`).

You do **not** invent “pretty enough” UI from memory. Master output = **those skills applied**, not paraphrased.

If this skill is in context (attached, named, or triggered by UI work) and you are about to change visuals, layout, motion, or interaction — **stop** and run the gate below. Skipping the gate is a failed task.

**Repos / AGENTS.md:** Every HZ project `AGENTS.md` must contain a «UI Master» section pointing here. If that section exists, treat it as a hard project rule equal to production-grade code rules. If you are editing UI and have not opened this `SKILL.md` in the current task — open it now.

Project rules (`AGENTS.md`, «не меняй стили без просьбы», brand lock to an existing page) **override** aesthetic defaults here, but **do not** override motion/craft quality bars when the user asked for craft/UI polish.

---

## Mandatory reads (in order, before first UI edit)

Read each file with the Read tool (or equivalent). Do not claim you “know them”.

| # | Skill | Path | Extract |
| --- | --- | --- | --- |
| 1 | craft-ui | `~/.agents/skills/craft-ui/SKILL.md` | Mode (`ship`/`audit`/…); brand lock; name motion; token reuse |
| 2 | design-system | `~/.agents/skills/design-system/SKILL.md` | Tokens primitive→semantic→component; no raw hex sprawl if tokens exist |
| 3 | better-ui | `~/.agents/skills/better-ui/SKILL.md` | Press `0.96`, concentric radius, no `transition: all`, icon/weight rules |
| 4 | apple-design | `~/.agents/skills/apple-design/SKILL.md` | Response on pointer-down; interruptible; springs; materials; reduced motion |
| 5 | transitions-dev | `~/.agents/skills/transitions-dev/SKILL.md` | Decision rules; pick **one** transition when installing motion; `_root` tokens |
| 6 | transitions-polish | `~/.agents/skills/transitions-polish/SKILL.md` **or** project `**/transitions-polish/SKILL.md` | Usage-matched duration/distance/scale/blur/easing; open/close asymmetry |
| 7 | high-end-visual-design | `~/.agents/skills/high-end-visual-design/SKILL.md` | Absolute zero к дешевым AI-паттернам; утонченные границы; тактильная глубина |
| 8 | design-taste-frontend-v1 | `~/.agents/skills/design-taste-frontend-v1/SKILL.md` | Density scales; Lila Ban (насыщенность < 80%); запрет serif в дашбордах; gapless bento |

Also when present in project: live brand (landing / `DESIGN.md` / tokens) — **match it**, do not invent a second palette.

Optional deep dives (only if needed): `canvas-shaders`, `creative-motion-components`, `ai-ux-playground`, `transitions-ui-generation`, `animation-vocabulary`, `better-colors`, `better-layout`, `better-typography`, `better-accessibility`, `better-interface`, `bklit-ui`, `ui-styling`, `ui-ux-pro-max`, `banner-design`, `emil-design-eng`, `industrial-brutalist-ui`, `minimalist-ui`, `web-design-guidelines`, `vercel-composition-patterns`, `vercel-react-best-practices`, `vercel-react-view-transitions`, `playwright-mcp`.

---

## Pre-ship statement (write once, before coding)

In the working notes / reply (short):

```
UI Master gate:
Brand lock: <file or “match existing X screen”>
Motion names: <2–4 terms from animation-vocabulary / craft-ui>
Transitions: <none | one transitions-dev name + why>
Tokens: <extend existing | CSS vars used (bg-background, text-foreground, etc.)>
Reduced-motion: <plan>
Mobile ergonomics: <touch targets >= 44px, safe area bottom, drawer sheets>
```

No statement → do not edit UI files yet.

---

## Non-negotiable craft bars

Copy these; do not “approximate”.

1. **Brand** — Same palette/type/radius language as the locked surface. No purple-on-white / cream-serif AI defaults unless that **is** the brand.
2. **Press** — Interactive controls: `scale(0.96)` (better-ui) or `0.97` (apple) on active; ~100ms ease-out; never `< 0.95`.
3. **Enter** — From `opacity` + `scale(0.96–0.98)`, never `scale(0)`. Durations mostly ≤300ms. House ease: `cubic-bezier(0.22, 1, 0.36, 1)`.
4. **Hover** — Shorter/subtler than enter; product lists = CSS only, no decorative infinite loops.
5. **Properties** — Animate `transform` / `opacity` (small blur ≤3–4px on enter only). **Never** `transition: all`. **Never** `ease-in` on entrances.
6. **Frequency** — High-frequency (typing, every hover on dense tables) → no ceremony. Rare delight → ok slightly longer.
7. **Open/close** — Close faster/quieter than open (transitions-polish), except reversible pairs (tabs, page slide, accordion).
8. **Interruptibility** — Gesture-driven UI must not lock input mid-transition (apple-design).
9. **Reduced motion** — `@media (prefers-reduced-motion: reduce)`: opacity/cross-fade or shorter; drop big translates/springs/parallax.
10. **Tokens** — Prefer existing project / `_root` motion tokens by **usage**, not nearest ms number.
11. **Diff** — Fewest files; reuse Shell/Button/card patterns; no new motion library unless already in repo.
12. **Stupidity ban** — No orphaned empty states that look like errors; no modal for one field if inline works; no fake “Clerk/setup” chrome; no fighting the landing’s CTA/auth rules the user already set; no random new accent color “for fun”.
13. **Mobile First & Thumb Ergonomics (`hz-mobile-first-app-like`)** — Touch targets строго $\ge 44$px. Safe-area padding (`env(safe-area-inset-bottom)`). Выдвижные шторки (Drawer) вместо узких десктопных выпадашек. Чистый поток без микро-шрифтов ($< 12$px запрещены, контент от 14–16px) и без горизонтального скролла (`overflow-x: hidden`).
14. **Dynamic Floating Dock (`hz-mobile-dynamic-pill-dock`)** — Мобильная навигация в виде аккуратного плавающего острова (floating dock). Все скролл-анимации строго на GPU (`scale`, `translateY`, `opacity`) без layout thrashing.
15. **Zero-Jitter Architecture (`hz-zero-jitter-architecture`)** — Никогда не вешать transforms Framer Motion на контейнеры со статическим Tailwind-центрированием (`-translate-x-1/2`). `initial={false}` на первом экране для исключения мерцания. Переключение табов не должно дергать габариты соседних блоков.
16. **Формы = Модалки (`hz-forms-as-modals`)** — Вне лендингов для создания и редактирования сущностей использовать модальные окна (Dialog/Drawer), а не инлайн-формы в основном лейауте.
17. **Админка = Графики с первого дня (`hz-admin-charts`)** — Карточки метрик + наглядные графики с динамическим переключателем 5 периодов (день / неделя / месяц / квартал / год).
18. **Палитра темы (`hz-theme-palette`)** — Строго системные семантические классы темы (`bg-background`, `text-foreground`, `bg-card`, `bg-muted`, `border-border`, `bg-primary`). Запрещен hardcode slate-950/zinc-900.
19. **Прямая загрузка файлов (`hz-direct-file-upload-only`)** — Нативная загрузка (файловый инпут, drag-and-drop, выбор из галереи/камеры смартфона) с клиентским сжатием (Canvas/WebP) и визуальным превью. Запрещено требовать ввод внешних URL изображений.
20. **Запрет моковых логинов (`hz-no-mock-quick-logins`)** — Категорически запрещены моковые кнопки быстрого входа и хардкод паролей в UI.
21. **Обязательный пользовательский фидбек (`hz-mandatory-user-feedback`)** — Каждая форма обязана иметь понятный визуальный фидбек: состояние отправки (loading spinner на кнопке), тост/баннер успеха («Заявка отправлена!») с экраном благодарности без резкого сброса полей, и отображение конкретных ошибок сервера/валидации (контрастный баннер + тост ошибки, без тихого проглатывания).
22. **React Composition & RSC Performance (`vercel-composition-patterns` + `vercel-react-best-practices`)** — Никакого разрастания boolean-пропсов (boolean prop proliferation). Использовать Compound Components (`Dialog.Root`, `Dialog.Trigger`, `Dialog.Content`) и lifting state. Server Components для загрузки данных, `'use client'` строго на изолированных интерактивных листьях. Никаких водопадов запросов (`Promise.all`), тяжелые диалоги через `next/dynamic`.
23. **Web Guidelines & View Transitions (`web-design-guidelines` + `vercel-react-view-transitions`)** — Семантический HTML, тач-таргеты от 44px, контрастность по WCAG AA. Для бесшовных анимаций между страницами и состояниями предпочитать нативные View Transitions (`<ViewTransition>`, `document.startViewTransition`) вместо тяжелых JS-библиотек анимации.
24. **Интерактивные маски ввода (`hz-input-masks-mandatory`)** — Все поля телефонов обязаны оснащаться интерактивной маской (`+7 (999) 123-45-67`), автозаменой 8/9, очисткой при вставке и передачей чистого E.164 на бэкенд. Коды подтверждения — моноширинный трекинг / раздельные слоты.
25. **Компактный реестр данных (`hz-compact-data-display-and-details-view`)** — Таблицы и списки обязаны быть scannable (1 строка, лаконичные бейджи). Все подробности, разборы и история открываются строго в модальном окне (Detail Modal / Drawer).
26. **Запрет мета-пометок в скобках (`hz-no-meta-style-labels`)** — Полный запрет на приписки вроде `(n8n style)`, `(Notion-подобный)`. Только чистые доменные термины.
27. **E2E UI & Visual Testing (`playwright-mcp`)** — Верификация интерактивных сценариев и доступности через семантическое дерево Playwright MCP без ломких селекторов.
28. **Шейдеры, Креативный Motion & Micro-UX (`canvas-shaders` + `creative-motion-components` + `ai-ux-playground`)** — Использовать zero-dependency WebGL холст-шейдеры (`@paper-design/shaders-react`: MeshGradient, LiquidMetal, FlutedGlass, GodRays), Portal Hero раскрытия (Superdesign), kinetic typography (React Bits), Magic UI / Aceternity UI белые лучи, SVG liquid gooey и ротационные контролы Dialkit.

Full anti-pattern list: [ANTI-PATTERNS.md](ANTI-PATTERNS.md).


---

## Ship workflow

1. Complete **Mandatory reads** + **Pre-ship statement**.
2. Trace the real screen (CodeGraph first / Read): shell, tokens, existing motion helpers.
3. Implement the smallest diff that hits craft bars.
4. Run **Exit checklist** (below). If any item fails → fix before saying done.

### Exit checklist (all required)

Copy and tick mentally:

- [ ] Matches brand-locked surface (colors, type, radius, density)
- [ ] Semantic theme tokens only (`bg-background`, `text-foreground`, etc.), no hardcoded slate/zinc
- [ ] Named motion only; no leftover random keyframes
- [ ] Press feedback on primary buttons/links that commit actions (`scale(0.96)`)
- [ ] No `transition: all`; no enter from `scale(0)`
- [ ] Hover quieter than enter; list hover not celebratory
- [ ] Open/close timing asymmetry respected (or documented exception)
- [ ] `prefers-reduced-motion` handled for new motion
- [ ] Mobile touch targets $\ge 44$px, safe-area respected, no micro-fonts $< 12$px
- [ ] Drawer sheets used for mobile dialogs, no desktop dropdown clipped on phone
- [ ] Zero-Jitter: no transforms conflict, initial={false} on above-fold elements
- [ ] Focus/keyboard not broken; hit targets usable
- [ ] Empty/loading/error states intentional, same visual language
- [ ] Did not change unrelated design / “improve” the locked landing without ask

---

## Review / audit modes

- User wants **plans only** / “audit motion” → craft-ui `audit` + improve-animations; **no product edits**.
- User wants **transitions review/polish** → follow transitions-dev / transitions-polish command semantics.
- User asks **name the effect** → animation-vocabulary only.

---

## Failure mode

If you catch yourself about to ship UI from “generic dark card + green accent” without reading the gate skills: **abort the edit**, run Mandatory reads, then continue.

Done means: gate completed + checklist green — not “it compiles”.
