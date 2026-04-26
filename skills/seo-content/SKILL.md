---
name: seo-content
description: >
  Optimize page text for Google rankings and AI citation (GEO/AEO).
  Use when the user wants to improve an article, product page, homepage, or any text
  that needs to drive organic traffic or be cited by AI engines.
  Trigger on: "optimize this text for SEO", "rewrite for Google", "make this rank for [keyword]",
  "I want to appear in AI Overviews", "optimize for ChatGPT/Perplexity citations",
  "improve this article", "make this content rank", "add an FAQ section",
  "optimize for featured snippets", "GEO", "AEO".
  Also trigger when creating new content from scratch that must be SEO-optimized.
argument-hint: "Paste the text to optimize, or describe the page topic and target keyword"
---

# SEO Content

Optimize existing text or write new content that ranks on Google and gets cited by AI engines (GEO) and answer engines (AEO).

## Before You Start

Identify:
- Target keyword / main topic
- Audience (end consumer, professional, student…)
- Existing text to optimize, or new content to write from scratch?

If writing from scratch, ask for the topic and keyword first, then produce directly in optimized form.

## Optimization Rules

### Title tag
- Target keyword first, 50–60 chars max
- Action-oriented beats descriptive: "How to X in 5 Steps" > "Guide to X"
- Unique per page — never duplicate across the site

### H1
- One per page, mirrors (not duplicates) the title
- Must make the page topic unmistakably clear

### Headings (H2/H3)
- Divide content into logical sections with descriptive headings
- Each heading should be self-explanatory out of context (AI engines use them to build page structure)

### Body text
- Target keyword in the first 100 words
- Use natural synonyms and variants — avoid keyword stuffing
- Sentences: 20–25 words max; paragraphs: 3–4 lines max
- Lead with the answer, then explain: "Yes, it works this way. Here's why…"

### GEO — Generative Engine Optimization
AI engines (Google AI Overviews, ChatGPT, Perplexity) cite content that:
- Gives a direct answer in the opening paragraph
- Contains citable, standalone statements: specific numbers, clear definitions, verifiable claims
- Names an author or recognizable brand
- Has sections that make sense when extracted out of context

Required for GEO citability:
- At least one statistic or concrete data point per section
- A "Quick answer" or "TL;DR" block at the top

### AEO — Answer Engine Optimization
For featured snippets, voice search, and AI answer boxes:
- Explicit definition: "X is…" or "By X we mean…"
- FAQ section with questions phrased as real users type them
- Numbered lists for processes ("How to do X in N steps")
- Comparison tables when evaluating options

### Meta description
- 150–160 chars, sell the click — not a summary, a pitch
- Include the target keyword naturally

## Output Format

**For existing text:** show key changes with a one-line rationale for each, then provide the full optimized text ready to use.

**For new content:** write it directly optimized; add a brief note on keyword placement and structural choices made.

## Handoff

- Add structured data → suggest `/seo-schema`
- Apply to project files → suggest `/seo-fix`
