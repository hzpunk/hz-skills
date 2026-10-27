---
name: pmo-leadgen
description: "Automated browser-based lead generation, market intelligence scraping via Playwright MCP, prospect enrichment, and B2B communication workflows for PMO / PMM."
---

# PMO Lead Generation & Prospecting Skill

This skill governs automated web research, lead data mining via Playwright MCP, contact enrichment, and outbound communication playbooks across the HZ ecosystem products (`psycu`, `HZLAW`, `typeGO`, `hzsupport`).

## Workflow:

### 1. Define Ideal Customer Profile (ICP) & Target Query
- **psycu**: Practicing clinical psychologists, psychoanalysts, master's students in psychology, psychological crisis centers.
- **HZLAW**: Practicing attorneys, legal consultancies, legal departments of SMEs, Minyust registered advocates.
- **typeGO**: Corporate HR recruiters, assessment leads, EdTech platforms, career consultants.
- **hzsupport**: Founders and CTOs of SaaS startups, e-commerce stores, digital agencies.

### 2. Browser Extraction with Playwright MCP
When gathering data from public registers, websites, or search engines:
1. `browser_navigate`: Navigate to target directory or directory search page.
2. `browser_snapshot`: Capture DOM structure and accessibility tree.
3. `browser_evaluate` / selectors: Extract name, company, email, telegram, phone, city, and specialties.
4. Normalize and clean contacts (remove duplicate domains, clean phone formats).

### 3. Structured Output & Notion Sync
Always structure leads into an actionable CSV/JSON format:
- `Name`: Full name of contact or firm
- `Role`: Specialty / title
- `Target Project`: `psycu` / `HZLAW` / `typeGO` / `hzsupport`
- `Contact`: Email / Telegram / Phone
- `Source URL`: URL where discovered
- `ICP Fit Score`: 1-5
- `Status`: `New` / `Contacted` / `Qualified`

Sync records to the target Notion workspace database via `ntn api -X POST v1/pages`.

### 4. Communication Playbook (Value-First Outreach)
- **Zero-Friction Hook**: Reference specific context (e.g. Minyust registry listing, publication, article, or company product).
- **Clear Value Proposition**: 1-2 sentence solution to their bottleneck (e.g., automated client intake, verified leads without commission markup, 24/7 SLA support).
- **Single Low-Barrier CTA**: "Ready to review a 2-minute demo link?" or "Can I send the direct test link?".
