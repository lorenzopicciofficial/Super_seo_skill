---
name: seo-schema
description: >
  Generate JSON-LD structured data that enables rich results on Google and improves AI citation accuracy.
  Use when the user wants stars, prices, FAQs, breadcrumbs, or author info to appear directly
  in search results, or wants AI engines to understand page context more precisely.
  Trigger on: "add schema markup", "I want stars on Google", "add structured data",
  "FAQ in search results", "rich snippet", "JSON-LD", "breadcrumb markup",
  "product schema", "article schema", "local business schema", "help Google understand the page".
argument-hint: "Page type (article, product, FAQ, local business, organization…) and URL or page content"
---

# SEO Schema

Generate correct, ready-to-paste JSON-LD structured data for the appropriate page type.

## Before You Start

Identify:
- **Page type** — article, product, FAQ, organization, local business, event, breadcrumb?
- **What data is already on the page?** — schema must reflect visible content; never add data not present in the page body
- **Goal** — stars in results? FAQ accordion on Google? Brand knowledge graph? AI citation signal?

## Schema by Page Type

### Article / Blog Post
Enables: author, date, image in Google News and Discover.
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Article title",
  "author": { "@type": "Person", "name": "Author Name" },
  "datePublished": "YYYY-MM-DD",
  "dateModified": "YYYY-MM-DD",
  "image": "https://example.com/image.jpg",
  "publisher": {
    "@type": "Organization",
    "name": "Site Name",
    "logo": { "@type": "ImageObject", "url": "https://example.com/logo.png" }
  }
}
```

### Product
Enables: price, availability, star ratings in search results.
```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Product Name",
  "description": "Short description",
  "image": "https://example.com/product.jpg",
  "offers": {
    "@type": "Offer",
    "price": "29.99",
    "priceCurrency": "EUR",
    "availability": "https://schema.org/InStock"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5",
    "reviewCount": "128"
  }
}
```

### FAQ
Enables: questions displayed directly in Google results. High GEO/AEO value — AI engines use FAQ schema as an authoritative Q&A signal.
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Question text?",
      "acceptedAnswer": { "@type": "Answer", "text": "Complete, self-contained answer." }
    }
  ]
}
```

### Organization
Enables: brand Knowledge Graph, improves AI citation trustworthiness.
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Company Name",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "sameAs": ["https://linkedin.com/company/name", "https://instagram.com/name"]
}
```

### Local Business
Enables: Google Maps, local pack, voice search answers.
```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Business Name",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main St",
    "addressLocality": "City",
    "postalCode": "00000",
    "addressCountry": "IT"
  },
  "telephone": "+39-00-0000000",
  "openingHours": "Mo-Fr 09:00-18:00",
  "url": "https://example.com"
}
```

### Breadcrumb
Enables: navigation path shown in search results. Use on every page with multi-level navigation.
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://example.com" },
    { "@type": "ListItem", "position": 2, "name": "Category", "item": "https://example.com/category" },
    { "@type": "ListItem", "position": 3, "name": "Current Page", "item": "https://example.com/category/page" }
  ]
}
```

## How to Insert

Always inside a `<script>` tag in the `<head>`:
```html
<script type="application/ld+json">
{ ...generated JSON-LD... }
</script>
```

Multiple blocks on the same page are fine — one per type.

## Output Format

1. One-line explanation of what the generated schema enables
2. Full JSON-LD block, values filled from the actual page content
3. Insertion instruction
4. Flag any data present in the schema but missing from the visible page body (Google penalizes mismatches)

## Handoff

Apply to project files → suggest `/seo-fix`
