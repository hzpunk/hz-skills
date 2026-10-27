# HZ Skills — Antigravity Agent Customizations

> **HZ is a unified skills, rules, and agents library** for Antigravity AI agent.
> Pluggable into any project with a single directory reference.

---

## What's inside

| Directory | Contents |
|-----------|----------|
| `skills/` | HZ custom skills — protocol-driven behaviors (boardroom, dev, seo, hz-rules, etc.) |
| `agents/` | Boardroom subagents — 12 C-suite agents for adversarial project reviews |
| `rules/` | Global autonomous dev engine rules & token economy protocols |

---

## Skills

| Skill | Description |
|-------|-------------|
| `skills/venture` | Master pipeline: from Idea & PRD to Scrollytelling, Live Telegram Gateway, B2B sales, and hz-planner |
| `skills/dev` | HZ Deep Dev Protocol: TDD, UB-Mode (CRAP < 10), No-Mistakes zero-slop gate, Boardroom gates |
| `skills/stealth-prospecting` | Autonomous B2B client hunting and cold outreach via Stealth Browser (Cloudflare Turnstile bypass) |
| `skills/boardroom` | Full autonomous venture cycle: PRD → CFO → CLO → CTO → UX → GTM |
| `skills/hz-scrollytelling` | Interactive scrollytelling, Canvas image sequence, Sticky pin, Parallax, Reveal, GSAP + ScrollTrigger, Lottie |
| `skills/hz-ui-craft` | Anti-slop visual craft, Apple fluid motion (WWDC), Impeccable surface modes, DesignSystems.one tokens & WCAG 2.2 AA |
| `skills/hz-marketing` | High-conversion CRO, Elaya Design 1-offer framework, anti-AI humanization, Corey Haines growth suite router |
| `skills/hz-rules` | Global HZ design & development rules reference |
| `skills/hz-master` | Master orchestrator — activates superpowers & hz-rules automatically |
| `skills/hz-orchestrator` | Multi-agent orchestration with grand unified skill atlas |
| `skills/ui-master` | End-to-end UI craftsmanship: design tokens, animation, accessibility |
| `skills/businessma` | Business strategy, Lean Canvas, CFO unit economics, CLO clearance |
| `skills/seo-crawler-audit` | Full SEO crawler audit with Core Web Vitals |
| `skills/seo-geo-optimization` | Geo-targeted SEO optimization |
| `skills/hz-forms-anti-bot` | Anti-bot: Turnstile + honeypot + throttle for all public forms |
| `skills/deeptech-rd` | Deep tech R&D planning and execution |

---

## Boardroom Agents

12 adversarial C-suite subagents for startup/product audits:

| Agent | Role |
|-------|------|
| `boardroom-ai` | Chief AI Architect & LLM FinOps |
| `boardroom-backend` | Staff Backend / Distributed Systems |
| `boardroom-cfo` | CFO & Solvency Auditor |
| `boardroom-ciso` | CISO & Red Team Pentester |
| `boardroom-clo` | Chief Legal Officer |
| `boardroom-cmo` | CMO & Head of Growth |
| `boardroom-cpo` | Chief Product Officer |
| `boardroom-cro` | CRO & Head of Enterprise Sales |
| `boardroom-data` | Chief Data Officer |
| `boardroom-devops` | Staff DevOps & SRE |
| `boardroom-frontend` | Staff Frontend & Client Architecture |
| `boardroom-ux` | Principal UX Evaluator |
| `boardroom-motion` | Chief Motion Director & Scrollytelling Engineer (GSAP, Canvas Scrub, 120fps) |
| `boardroom-secops` | Staff DevSecOps & Red Team Pentester (Nuclei, FRP, Bot Shields, 152-ФЗ) |
| `boardroom-native` | Staff Mobile & Cross-Platform Architect (Swift, Realm, Dioxus, Flutter) |
| `boardroom-deeptech` | Chief Scientist & Quantitative Systems Architect (PyBroker, Biometrics, DeepSeek) |
| `cli-orchestrator` | Free CLI Runners Autonomous Dispatcher (Goose, Vibe, Gemini, Copilot, Q) |

---

## Rules

| Rule | What it enforces |
|------|-----------------|
| `rules/autonomous-dev-engine.md` | Full 10-section autonomous dev pipeline: pre-flight recall, quality gates, sensitive-domain safety, GitHub project governance, Jules orchestration, webhook sentinel |
| `rules/token-economy.md` | Token economy and context budget guidelines |

---

## Global Rules (`GEMINI.md` / `user_rules`)

15 named global rules active across all projects:

1. `hz-admin-charts` — Admin = charts from day 1 (with period toggle: day/week/month/year)
2. `hz-forms-as-modals` — Forms = modal dialogs (unless landing page or inline explicitly requested)
3. `hz-brief-responses` — Concise answers ending with one actionable line
4. `hz-commit-after-global` — Auto-commit after every feature/fix (no push until asked)
5. `hz-domains-from-deploy` — Public URLs only from deploy/DNS configs
6. `hz-env-sync-after-commit` — Secrets sync via approved workflow after each commit
7. `hz-learn-from-mistakes` — Verify before recording lessons; never argue about errors
8. `hz-verify-live-before-claiming` — Check live/deploy before claiming ready
9. `hz-theme-palette` — Strict semantic CSS variables; banned: `slate-950`, `slate-900`, raw hex
10. `hz-tunnels-economy` — Cloudflare Quick Tunnel for previews; ngrok strictly for webhook debugging
11. `hz-sensitive-safety-first` — Psych/sensitive projects: terracotta errors, isolated crisis logs, 112 disclaimer
12. `hz-wcag-contrast-aa` — WCAG AA minimum 4.5:1 contrast on all text
13. `hz-youth-tov-zero-friction` — Student funnels: friend voice, no forced registration on first question
14. `hz-github-project-governance` — Decompose docs → GitHub Project + Milestones M1–M5 + Assignees + DoD
15. `hz-jules-webhook-sentinel` — Reactive webhook hub, Jules PR gatekeeping, CI/CD hygiene

---

## Installation

Clone into your Antigravity plugins directory:

```bash
git clone https://github.com/hzpunk/hz-skills ~/.gemini/config/plugins/hz-rules-plugin
```

Or link a specific project's skill set:

```bash
ln -s ~/.gemini/config/plugins/hz-rules-plugin/skills/dev ~/.agents/skills/dev
```

---

## Contributing

This is a private HZ team repository. PRs welcome from `@hzpunk` and `@VladislavSCV`.
