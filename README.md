# Super SEO Skill

Five Claude Code skills covering the full SEO cycle — from initial analysis to concrete code fixes — with built-in support for AI visibility (GEO) and answer engine optimization (AEO).

Lightweight by design: ~15,000 tokens total vs ~145,000 for equivalent all-in-one solutions.

---

## The 5 Skills

### `/seo-audit` — Understand what's wrong
Analyzes a page or entire site and returns a prioritized report with issues explained in plain language. The right starting point: tells you where to focus before touching anything.

**When to use:**
- "Why isn't this page showing up on Google?"
- "Do an SEO audit of this site"
- "What should I improve to rank better?"
- Before optimizing — to know what actually needs attention

---

### `/seo-content` — Improve the text
Optimizes copy for Google rankings and for being cited by AI engines. Covers classic SEO (titles, structure, keywords), GEO (how to get cited by Google AI Overviews, ChatGPT, Perplexity), and AEO (how to appear in featured snippets and voice search answers).

**When to use:**
- "Optimize this article for SEO"
- "I want this page cited by Google AI"
- "Rewrite this to rank for [keyword]"
- "Add an optimized FAQ section"
- Any text that needs to drive organic traffic

---

### `/seo-schema` — Help Google and AI understand you
Generates the code that lets Google display rich results: stars, prices, FAQs directly in search results, breadcrumbs, author information. AI engines use this data to cite sources more accurately and to identify authoritative content.

**When to use:**
- "I want stars in Google results"
- "Add structured data to the product page"
- "Make FAQs appear directly on Google"
- "Add schema markup to the article"
- Supported types: Article, Product, FAQ, Organization, LocalBusiness, Breadcrumb

---

### `/seo-technical` — Fix technical blockers
Checks and corrects everything that prevents Google from finding and reading pages: robots.txt, sitemap, canonical tags, noindex, redirects, mobile optimization, and page speed. Sites often fail to rank due to trivial technical errors, not lack of content.

**When to use:**
- "The site doesn't appear on Google"
- "Check the robots.txt"
- "Is the sitemap correct?"
- "I have indexing problems"
- After launching a new site, to verify everything is configured correctly

---

### `/seo-fix` — Apply the fixes
Edits project files directly: adds missing meta tags, fixes canonicals, inserts structured data, updates robots.txt and sitemap. Doesn't give instructions — makes the actual changes in the code.

**When to use:**
- After `/seo-audit`, to implement the findings
- "Add meta tags to all pages"
- "Apply SEO fixes to the project"
- "Fix the canonical on this page"
- When you want the changes done, not explained

---

## Typical Workflows

### New site to optimize
```
/seo-audit  →  /seo-content  →  /seo-schema  →  /seo-fix
```
Understand what's missing, optimize the text, add structured data, apply everything.

### Site not showing on Google
```
/seo-technical  →  /seo-fix
```
Usually a robots.txt or noindex issue — resolved in minutes.

### Article to optimize
```
/seo-content  →  /seo-schema  →  /seo-fix
```
Optimize the text, add Article or FAQ schema, apply changes.

### E-commerce product page
```
/seo-audit  →  /seo-schema  →  /seo-content  →  /seo-fix
```
Audit, structured data with price and ratings, optimized copy, everything applied.

### Appear in AI results (GEO/AEO)
```
/seo-content  →  /seo-schema
```
`/seo-content` optimizes text for AI citability. `/seo-schema` adds the structured data signals that AI engines use to evaluate source authority.

---

## Comparison

| | Super SEO Skill | Full claude-seo |
|---|---|---|
| Tokens per session | ~15,000 | ~145,000 |
| Skills | 5 focused | 23 |
| Coverage | SEO · GEO · AEO · Technical | + backlinks, e-commerce, local, hreflang, maps, programmatic… |
| Best for | Sites, blogs, standard e-commerce | SEO agencies, enterprise audits |

For advanced needs (backlink analysis, multi-location local SEO, programmatic SEO at scale), consider adding dedicated skills on top.

---

## Installation

```
/plugins add marketplace super-seo lorenzopicciofficial/Super_seo_skill
```

Install individual skills as needed:

```
/plugins install seo-audit@super-seo
/plugins install seo-content@super-seo
/plugins install seo-schema@super-seo
/plugins install seo-technical@super-seo
/plugins install seo-fix@super-seo
```

---

## Glossary

**SEO** — Search Engine Optimization. Everything that makes Google find and surface your pages in traditional search results.

**GEO** — Generative Engine Optimization. Optimizing content to be cited by AI engines (Google AI Overviews, ChatGPT, Perplexity) instead of just appearing as a link.

**AEO** — Answer Engine Optimization. Optimizing to appear in direct answers: Google featured snippets, voice search results, AI answer boxes.

**Schema markup / Structured data** — Code invisible to users that helps Google and AI engines understand the type and meaning of content.

**Canonical** — A tag that tells Google which is the "official" version of a page when multiple URLs point to the same content.

**robots.txt** — A text file that tells search engine crawlers which parts of the site they can visit.

**Sitemap** — A file listing all the pages you want Google to index, sent directly as a map of your site.
