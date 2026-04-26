---
name: seo-technical
description: >
  Find and fix technical issues that prevent Google from crawling, reading, or indexing pages correctly.
  Use when the site doesn't appear on Google despite good content, after launching a new site,
  or when verifying that indexing configuration is correct.
  Trigger on: "site not indexed", "check robots.txt", "fix sitemap", "canonical not working",
  "meta robots", "301 redirect", "technical SEO issues", "site doesn't appear on Google",
  "indexing problem", "crawl error", "noindex", "mobile SEO", "Core Web Vitals".
  Do NOT trigger for content optimization (use seo-content) or applying code changes (use seo-fix).
argument-hint: "URL, paste robots.txt/sitemap content, or paste the HTML source to inspect"
---

# SEO Technical

Identify and resolve technical issues that block Google from finding and understanding pages.

## Priority Order

Always resolve blockers first — everything else is irrelevant if Google can't get in.

### 1. Indexing blockers (fix before anything else)

**robots.txt**
Disallowing everything is a common mistake left over from development:
```
# WRONG — blocks entire site
User-agent: *
Disallow: /

# CORRECT — block only private sections
User-agent: *
Disallow: /admin/
Disallow: /login/
Disallow: /checkout/
Allow: /
Sitemap: https://example.com/sitemap.xml
```

**Meta robots noindex**
Check `<head>` for:
```html
<meta name="robots" content="noindex, nofollow">
```
`noindex` = page excluded from all results. Only acceptable on: checkout, login, account pages, staging. Flag on any public page as critical.

---

### 2. Duplicate content (canonical)

If the same page is reachable from multiple URLs, Google splits ranking authority between them.
Common duplicates: `?utm_source=`, `?ref=`, `http` vs `https`, `www` vs non-`www`.

Fix — add to `<head>` on every page:
```html
<link rel="canonical" href="https://example.com/the-official-url">
```
Always points to the single preferred version of the page.

---

### 3. Sitemap

The sitemap is the index you send directly to Google. It must exist and be linked from `robots.txt`.

Location: `https://example.com/sitemap.xml`

Minimal structure:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://example.com/</loc>
    <lastmod>2026-04-01</lastmod>
    <priority>1.0</priority>
  </url>
</urlset>
```

Exclude: `noindex` pages, admin, login, cart, error pages.

---

### 4. Mobile-friendliness

Google indexes the mobile version first. Check `<head>`:
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
If missing, flag as high priority.

---

### 5. Redirect chains

A single 301 redirect is fine. Chains (A → B → C) dilute crawl budget and ranking signals.
If found: flag each chain and provide the direct mapping from source to final destination.

---

### 6. Core Web Vitals signals

Look for common performance issues in the code:

| Issue | Fix |
|-------|-----|
| Images without `width`/`height` | Add explicit dimensions to prevent layout shift |
| Render-blocking scripts | Add `defer` or `async` to `<script>` tags |
| No `preconnect` for external fonts | Add `<link rel="preconnect" href="https://fonts.googleapis.com">` |
| Large unoptimized images | Recommend WebP/AVIF conversion |

## Output Format

For each issue found:
1. **What it is** — plain description
2. **Why it matters** — concrete impact on indexing or ranking
3. **How to fix it** — exact code or configuration change

## Handoff

Apply fixes to project files → suggest `/seo-fix`
