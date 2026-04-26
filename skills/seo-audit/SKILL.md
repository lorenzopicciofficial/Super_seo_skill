---
name: seo-audit
description: >
  Analyze a web page or entire site and produce a prioritized report of SEO issues.
  Use when the user wants to understand why a page isn't ranking, needs a starting point
  before optimizing, or wants a full visibility check.
  Trigger on: "analyze this page", "SEO audit", "why isn't this site on Google",
  "what's wrong with my ranking", "check visibility", "audit this URL",
  "what should I fix first for SEO".
  Do NOT trigger for content rewriting (use seo-content) or code fixes (use seo-fix).
argument-hint: "URL or paste the HTML source of the page to analyze"
---

# SEO Audit

Produce a clear, prioritized report — not a technical document, but a practical guide on what to fix and why.

## Before You Start

Identify:
- Single page or full site?
- Target keyword or topic? (ask if not provided)
- Is the site live or under development?

If HTML source is available, analyze it directly. If only a URL is given, describe what you would check and flag what requires external tools (Google Search Console, PageSpeed Insights).

## What to Check

**Indexing blockers — check first**
- `robots.txt`: does it contain `Disallow: /`? If so, flag as critical.
- `<meta name="robots" content="noindex">` on important pages?
- `<link rel="canonical">`: present, correct, not pointing to a different URL?

**On-page essentials**
- `<title>`: 50–60 chars, target keyword near the start, unique per page?
- `<meta name="description">`: 150–160 chars, present, click-worthy?
- One `<h1>` per page containing the main keyword?
- `<h2>`/`<h3>` used logically to structure content?
- Images: `alt` attribute present and descriptive on all `<img>` tags?
- Internal links: present and using descriptive anchor text?
- URL: readable and descriptive?

**GEO signals** (Google AI Overviews, ChatGPT, Perplexity)
- Does the content answer questions directly in the first paragraph?
- Are there concrete, citable statements (statistics, clear definitions)?
- Is an author or brand name present on the page?

**AEO signals** (featured snippets, voice search)
- Explicit definitions ("X is…")?
- Numbered lists or step-by-step instructions?
- FAQ section with real user questions?

**Technical baseline**
- `<meta name="viewport">` present (mobile-friendly)?
- Scripts loaded with `defer` or `async`?
- Images have explicit `width`/`height` attributes?

## Output Format

```
Summary — one sentence on overall state

HIGH PRIORITY (fix immediately)
- [issue] → [why it matters] → [what to do]

MEDIUM PRIORITY (fix this week)
- [issue] → [why it matters] → [what to do]

LOW PRIORITY (future improvements)
- [issue] → [why it matters] → [what to do]

What's already working
- [strength 1]
- [strength 2]

Recommended next step — one concrete action to take today
```

Avoid jargon in the report. Use plain analogies where helpful.

## Handoff

- Text issues → suggest `/seo-content`
- Technical issues → suggest `/seo-technical`
- Missing structured data → suggest `/seo-schema`
- Ready to apply fixes → suggest `/seo-fix`
