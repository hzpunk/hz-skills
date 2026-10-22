---
name: seo-geo-optimization
description: >-
  Applies SEO and GEO (Generative Engine Optimization) when generating or editing
  public pages, components, articles, landings, and metadata. Use for title,
  description, headings, canonical, JSON-LD, FAQ, llms.txt, AI-search visibility
  (ChatGPT, Perplexity, Claude, Gemini, AI Overviews), and Google/Yandex indexing.
  For whole-site promotion/content strategy use seo-productive instead.
---

# SEO + GEO Optimization

**Orchestrator:** for multi-domain HZ tasks start at `hz-orchestrator` (`~/.agents/skills/hz-orchestrator/SKILL.md`).

Применяется при создании/правке **конкретной** страницы, компонента, статьи, лендинга, метаданных.

Цель — классическое SEO (Google/Яндекс) + GEO (цитируемость в AI-поиске).

**Смежный skill:** стратегия продвижения сайта целиком → `seo-productive` (`~/.agents/skills/seo-productive/SKILL.md`).

**HZ эталон кода:** `~/hellpsychologist/src/lib/seo/` (не копируй вслепую на чужой стек — адаптируй).

## 1. Технический SEO-минимум (обязательно на каждой странице)

- Уникальный `<title>` 50–60 символов, ключевая фраза в начале.
- `<meta name="description">` 140–160 символов, с CTA, без keyword stuffing.
- Один `<h1>` на страницу, логичная иерархия h1→h2→h3 без пропусков уровней.
- `canonical` URL всегда указан явно.
- `alt` на всех `<img>` — описательный, не "image1.jpg".
- Semantic HTML: `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>` вместо голых `<div>`.
- Внутренние ссылки с осмысленным анкор-текстом (не "click here").
- Core Web Vitals: lazy-loading для изображений ниже fold, explicit width/height у медиа для избежания CLS.
- `robots.txt` и `sitemap.xml` актуальны при добавлении новых роутов.

## 2. Structured Data (Schema.org)

- Добавлять JSON-LD, не microdata.
- Обязательные типы под контекст:
  - `Organization` / `LocalBusiness` — на главной
  - `Article` / `BlogPosting` — для статей (author, datePublished, dateModified)
  - `Product` / `Offer` — для карточек товара/услуги
  - `FAQPage` — если на странице есть блок вопрос-ответ (усиливает GEO)
  - `BreadcrumbList` — для многоуровневой навигации
- Валидировать наличие обязательных полей (name, description минимум).

## 3. GEO (Generative Engine Optimization)

AI-модели **извлекают и переформулируют** факты, а не «ранжируют» как классический SERP:

- **Прямые ответы в тексте.** Первый абзац секции — самодостаточный ответ на вопрос из заголовка.
- **Чёткая атрибуция.** Цифры, даты, источники — не размытые формулировки.
- **Q&A формат.** Явные вопрос-ответ блоки (даже вне FAQPage).
- **Списки и таблицы** вместо простыни текста.
- **`llms.txt`** в корне — описание сайта, ключевые URL, правила использования контента.
- **Актуальность.** `dateModified` в schema; AI предпочитает свежие источники.
- **Не** keyword density — для GEO вредно.

## 4. Что НЕ делать

- Keyword stuffing.
- Дубли без canonical.
- Клоакинг / скрытый текст под AI-краулеры.
- Meta ради meta без соответствия контенту.
- Пустые JSON-LD-заглушки (лучше без разметки).

## 5. Чеклист перед коммитом публичной страницы

- [ ] title/description уникальны и в лимитах
- [ ] один h1, логичная структура заголовков
- [ ] alt на всех изображениях
- [ ] JSON-LD валиден
- [ ] canonical указан
- [ ] первый абзац смысловой секции — прямой ответ
- [ ] Q&A блок, если тематика позволяет
- [ ] CWV не деградировали (lazy-load, размеры)
- [ ] новый URL попал в sitemap (если статический роут)
