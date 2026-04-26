---
name: seo-schema
description: >
  Genera il codice che aiuta Google e le AI a capire esattamente di cosa parla
  la pagina: che tipo di contenuto è, chi l'ha scritto, qual è il prezzo,
  le valutazioni, le domande frequenti e molto altro.
  Usa questa skill quando vuoi che Google mostri informazioni arricchite
  nei risultati (stelle, prezzi, FAQ, breadcrumb) o quando vuoi aumentare
  le probabilità di essere citato dalle AI.
  Si attiva con frasi come: "aggiungi schema markup", "voglio le stelle su Google",
  "aggiungi i dati strutturati", "FAQ nei risultati di ricerca",
  "rich snippet", "JSON-LD", "aiuta Google a capire la pagina".
---

# seo-schema — Dati strutturati per Google e AI

Hai ricevuto una richiesta di aggiungere o correggere dati strutturati. Il tuo obiettivo è generare codice JSON-LD corretto, pronto da incollare nel `<head>` della pagina, spiegando in modo semplice a cosa serve ogni blocco.

## Cos'è lo schema markup (spiegazione semplice)

È come una scheda informativa che metti nella pagina, scritta in un linguaggio che Google capisce direttamente. Non la vedono gli utenti, ma Google la usa per mostrare informazioni arricchite nei risultati — stelle, prezzi, FAQ, nomi degli autori, date degli eventi — e le AI la usano per capire meglio il contesto della pagina.

## Prima di generare il codice

Chiedi o identifica:
- **Che tipo di pagina è?** (articolo, prodotto, ricetta, servizio, evento, persona, azienda, FAQ, corso…)
- **Quali informazioni sono già presenti nella pagina?** (inutile mettere un prezzo nello schema se non è nella pagina)
- **Qual è l'obiettivo?** (stelle nei risultati? Comparire nelle FAQ di Google? Essere citato come fonte affidabile?)

## Tipi di schema per caso d'uso

### Articolo o blog post
Quando usarlo: qualsiasi pagina con contenuto editoriale (articoli, guide, news)
Cosa abilita: mostra autore, data, immagine nei risultati Google News e Discover

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Titolo dell'articolo",
  "author": {
    "@type": "Person",
    "name": "Nome Autore"
  },
  "datePublished": "2026-01-15",
  "dateModified": "2026-04-20",
  "image": "https://esempio.com/immagine.jpg",
  "publisher": {
    "@type": "Organization",
    "name": "Nome Sito",
    "logo": {
      "@type": "ImageObject",
      "url": "https://esempio.com/logo.png"
    }
  }
}
```

### Prodotto (e-commerce)
Quando usarlo: pagine prodotto con prezzo e disponibilità
Cosa abilita: prezzo, disponibilità e stelle nei risultati di ricerca

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Nome Prodotto",
  "description": "Descrizione breve",
  "image": "https://esempio.com/prodotto.jpg",
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
Quando usarlo: pagine con domande e risposte (assistenza, prodotti, servizi)
Cosa abilita: le domande compaiono direttamente nei risultati di ricerca e vengono usate dalle AI per rispondere

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Domanda uno?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Risposta chiara e completa alla domanda uno."
      }
    },
    {
      "@type": "Question",
      "name": "Domanda due?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Risposta chiara e completa alla domanda due."
      }
    }
  ]
}
```

### Organizzazione / Azienda
Quando usarlo: homepage o pagina "Chi siamo"
Cosa abilita: aiuta Google a costruire il Knowledge Graph del brand, aumenta la citabilità dalle AI

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Nome Azienda",
  "url": "https://esempio.com",
  "logo": "https://esempio.com/logo.png",
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+39-000-0000000",
    "contactType": "customer service"
  },
  "sameAs": [
    "https://www.linkedin.com/company/nome",
    "https://www.instagram.com/nome"
  ]
}
```

### Servizio locale (negozio, studio, ristorante)
Quando usarlo: attività fisiche con indirizzo e orari
Cosa abilita: comparire in Google Maps, risultati locali, risposte vocali

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Nome Attività",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Via Roma 1",
    "addressLocality": "Milano",
    "postalCode": "20100",
    "addressCountry": "IT"
  },
  "telephone": "+39-02-0000000",
  "openingHours": "Mo-Fr 09:00-18:00",
  "url": "https://esempio.com"
}
```

### Breadcrumb (percorso di navigazione)
Quando usarlo: sempre, su qualsiasi sito con più livelli di navigazione
Cosa abilita: mostra il percorso (Home > Categoria > Pagina) nei risultati Google

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://esempio.com"},
    {"@type": "ListItem", "position": 2, "name": "Categoria", "item": "https://esempio.com/categoria"},
    {"@type": "ListItem", "position": 3, "name": "Pagina attuale", "item": "https://esempio.com/categoria/pagina"}
  ]
}
```

## Come inserire il codice nella pagina

Il codice JSON-LD va sempre dentro un tag `<script>` nel `<head>` della pagina:

```html
<head>
  ...
  <script type="application/ld+json">
  { ...il codice generato... }
  </script>
</head>
```

Si possono inserire più blocchi separati — uno per tipo — nella stessa pagina.

## Come presentare il risultato

1. Spiega in una riga cosa abilita lo schema che stai generando
2. Fornisci il codice completo, già compilato con i dati della pagina
3. Indica dove incollarlo
4. Se ci sono dati mancanti che andrebbero aggiunti anche nel testo della pagina (es. il prezzo c'è nello schema ma non nella pagina), segnalalo — Google penalizza le incoerenze

Suggerisci `/seo-fix` se l'utente vuole applicare il codice direttamente ai file del progetto.
