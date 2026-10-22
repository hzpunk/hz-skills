# Архетипы Субагентов Автономного Совета Директоров (Boardroom Subagents)

Этот справочник содержит эталонные системные промпты, зоны ответственности, протоколы вызова и критерии наложения вето для всех специализированных субагентов, запускаемых через `invoke_subagent`.

---

## 1. Реестр Архетипов

| Имя Субагента | Роль (Role) | Миссия и Компетенция | Инструменты |
|---|---|---|---|
| `boardroom-cfo` | Chief Financial Officer | Финансовый аудит, юнит-экономика ($LTV/CAC \ge 3:1$), Runway ($>12$ мес.), налоги | WriteTools, MCP |
| `boardroom-clo` | Chief Legal Officer | Правовой щит, SHA, вестинг, служебные РИД (ст. 1295 ГК РФ), 152-ФЗ / GDPR | WriteTools, MCP |
| `boardroom-ciso` | Head of Cybersecurity / Red Team | Zero Trust, OWASP Top 10, STRIDE Threat Modeling, криптография, аудит форм | WriteTools, MCP |
| `boardroom-ux` | Principal UX Evaluator | 10 эвристик Нильсена, Fitts/Hick/Tesler, SUS/SEQ, доступность WCAG 2.2 AA | WriteTools, MCP |
| `boardroom-backend` | Staff Backend Engineer | High-Load API, идемпотентность, PostgreSQL MVCC, Kafka Outbox, Redis XFetch | WriteTools, MCP |
| `boardroom-cro` | Chief Revenue Officer | B2B продажи, MEDDPICC, Challenger Sale, преодоление Procurement, ценообразование | WriteTools, MCP |
| `boardroom-cmo` | Chief Marketing Officer | Привлечение, каналы трафика, CAC, PLG-воронки, позиционирование (Obviously Awesome) | WriteTools, MCP |
| `boardroom-cto` | Chief Technology Officer | Техстратегия, DORA-метрики, архитектурный арбитраж, Zero SPOF, FinOps | WriteTools, MCP |
| `boardroom-pm` | Chief Product Officer | Continuous Discovery, Opportunity Solution Tree, RICE, 1-Page PRD, Retention | WriteTools, MCP |
| `boardroom-marketer` | Growth Marketer | Воронка AARRR, Growth Loops, MER / Blended CAC, креативная скорость | WriteTools, MCP |
| `boardroom-pr` | Head of PR & Communications | Tier-1 СМИ питчинг, миф основателя, протокол «Золотого часа», Newsjacking | WriteTools, MCP |

---

## 2. Формат Состязательного Заключения Субагента (Boardroom Gate Verdict)

Каждый субагент при вызове обязан предоставить структурированное заключение строго по форме:

```markdown
### Заключение Субагента: [Имя Роли]
**Вердикт:** [APPROVED / CONDITIONAL APPROVAL / VETOED]

#### 1. Ключевые риски и несоответствия (Findings):
- [Критический риск 1 со ссылкой на стандарт/формулу]
- [Риск 2]

#### 2. Математический / Аналитический расчет:
- [Таблица метрик / расчетов юнит-экономики / CVSS скоринга / эвристик Нильсена]

#### 3. Обязательные условия для снятия замечаний (Actionable Fixes):
1. ...
2. ...
```

---

## 3. Программный Запуск через Python (`boardroom_subagents.py`)

Для автоматического спавна субагентов в скриптах используется модуль `~/.agents/scripts/boardroom_subagents.py`.
