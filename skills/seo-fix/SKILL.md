---
name: seo-fix
description: >
  Apply SEO corrections directly to project files: add or fix meta tags, canonicals,
  structured data, robots.txt, and sitemap. Does not give instructions — makes the changes.
  Use after seo-audit to implement findings, or when the user knows what to fix
  and wants it done directly in the code.
  Trigger on: "apply the SEO fixes", "add the missing meta tags", "fix the canonical",
  "implement the audit corrections", "update robots.txt", "add JSON-LD to the page",
  "insert the structured data", "apply SEO changes to the project".
argument-hint: "Paste the audit report or describe fixes to apply; optionally paste the HTML files to modify"
---

# SEO Fix

Edit project files to implement SEO corrections. Produce diffs and ready-to-use code — not instructions.

## Before You Start

1. Identify what to fix — use an existing `/seo-audit` report if available, or ask
2. Locate the files — explore the project structure to find HTML templates, config files, and layouts
3. Identify the technology — static HTML, Next.js, Nuxt, WordPress, other? This determines where and how to apply each change

## Fix Priority Order

Apply in this sequence:

### 1. Indexing blockers (always first)
- Remove `noindex` from public pages
- Fix `Disallow: /` in `robots.txt` that blocks the whole site

### 2. Essential head tags (every page)

Add to `<head>` where missing or incorrect:
```html
<!-- Title: 50–60 chars, keyword first -->
<title>Target Keyword - Brief Description | Brand</title>

<!-- Meta description: 150–160 chars, click-worthy -->
<meta name="description" content="Description that earns the click, with keyword included naturally.">

<!-- Canonical: always points to the official URL of this page -->
<link rel="canonical" href="https://example.com/page">

<!-- Viewport (if missing) -->
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- Open Graph (if missing) -->
<meta property="og:title" content="Page title">
<meta property="og:description" content="Description for social and AI">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:url" content="https://example.com/page">
```

### 3. Content structure
- Ensure one `<h1>` per page with the main keyword
- Add `alt` attributes to images missing them: `<img src="img.jpg" alt="descriptive text">`

### 4. Structured data (JSON-LD)
Insert inside `<head>` after generating with `/seo-schema`:
```html
<script type="application/ld+json">
{ ...schema... }
</script>
```

### 5. robots.txt
Create or fix at site root:
```
User-agent: *
Disallow: /admin/
Disallow: /login/
Disallow: /checkout/
Allow: /

Sitemap: https://example.com/sitemap.xml
```

### 6. sitemap.xml
Generate or update including all public pages with current `<lastmod>`. Exclude `noindex` pages, admin, login, cart.

### 7. Performance (only if impact is clear)
```html
<!-- Non-blocking scripts -->
<script src="script.js" defer></script>

<!-- Images with explicit dimensions -->
<img src="photo.jpg" width="800" height="600" alt="description">

<!-- Preconnect for external resources -->
<link rel="preconnect" href="https://fonts.googleapis.com">
```

## Output Format

For each modified file:
```
File: path/to/file.html
Change: [one-line description]

Before:
  [original snippet]

After:
  [modified snippet]
```

End with a 3–5 point summary of what was changed.

List any fixes that require external action (Google Search Console submission, server configuration) under **Manual steps required** with precise instructions.
