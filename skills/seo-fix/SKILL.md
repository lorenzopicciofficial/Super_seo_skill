---
name: seo-fix
description: >
  Applica concretamente le correzioni SEO ai file del progetto:
  modifica il codice HTML, aggiunge o corregge meta tag, inserisce
  dati strutturati, aggiorna robots.txt e sitemap.
  Usa questa skill dopo aver fatto un'analisi con seo-audit,
  oppure quando sai già cosa correggere e vuoi che venga fatto direttamente.
  Si attiva con frasi come: "applica le correzioni SEO", "correggi il codice",
  "aggiungi i meta tag mancanti", "sistema il canonical",
  "implementa le modifiche", "aggiorna il robots.txt", "applica l'audit".
---

# seo-fix — Applica le correzioni SEO

Hai ricevuto una richiesta di applicare correzioni SEO. Il tuo obiettivo è modificare direttamente i file del progetto — non dare istruzioni, ma fare le modifiche concrete e mostrare cosa è cambiato.

## Prima di iniziare

Identifica sempre:
1. **Cosa correggere** — hai già un report da `/seo-audit`? Usa quello. Altrimenti chiedi cosa va sistemato.
2. **Dove sono i file** — esplora la struttura del progetto per trovare HTML, template, configurazioni.
3. **Che tecnologia usa il sito** — HTML statico, Next.js, WordPress, altro? Cambia dove e come fare le modifiche.

## Ordine di priorità

Applica le correzioni in quest'ordine:

### 1. Blocchi all'indicizzazione (risolvi prima di tutto il resto)
Se trovi `noindex` su pagine importanti o `Disallow: /` nel robots.txt, sistemali subito — tutto il resto è inutile finché Google non riesce ad entrare.

### 2. Tag essenziali su ogni pagina
Per ogni pagina HTML controlla e aggiungi/correggi questi tag nel `<head>`:

```html
<!-- Titolo: 50-60 caratteri, parola chiave all'inizio -->
<title>Parola Chiave - Descrizione Breve | Brand</title>

<!-- Descrizione: 150-160 caratteri, invoglia al clic -->
<meta name="description" content="Descrizione che convince l'utente a cliccare, con la parola chiave inclusa in modo naturale.">

<!-- Canonical: punta sempre all'URL ufficiale della pagina -->
<link rel="canonical" href="https://esempio.com/pagina">

<!-- Viewport mobile (se mancante) -->
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- Open Graph per social e AI (se mancanti) -->
<meta property="og:title" content="Titolo della pagina">
<meta property="og:description" content="Descrizione per social e AI">
<meta property="og:image" content="https://esempio.com/immagine.jpg">
<meta property="og:url" content="https://esempio.com/pagina">
```

### 3. Struttura dei contenuti
- Verifica che ogni pagina abbia un solo `<h1>` con la parola chiave principale
- Controlla che i titoli di sezione (`<h2>`, `<h3>`) siano presenti e descrittivi
- Aggiungi `alt` alle immagini che ne sono prive: `<img src="foto.jpg" alt="descrizione significativa">`

### 4. Dati strutturati (JSON-LD)
Se nel report mancano dati strutturati, inserisci il blocco `<script type="application/ld+json">` appropriato. Usa `/seo-schema` per generarli se non li hai già.

### 5. robots.txt
Se il file non esiste o è mal configurato, crealo o correggilo:

```
User-agent: *
Disallow: /admin/
Disallow: /login/
Disallow: /checkout/
Allow: /

Sitemap: https://tuosito.com/sitemap.xml
```

### 6. sitemap.xml
Se manca o è obsoleta, generala includendo tutte le pagine pubbliche con `<lastmod>` aggiornato. Escludi pagine con `noindex`, carrello, login, admin.

### 7. Ottimizzazioni performance
Applica solo se richiesto o se l'impatto è chiaramente alto:
- Aggiungi `defer` agli script non critici
- Aggiungi `width` e `height` alle immagini principali
- Aggiungi `preconnect` per risorse esterne (Google Fonts, CDN)

## Come presentare le modifiche

Per ogni file modificato:
1. Mostra le righe cambiate con una riga di spiegazione
2. Fornisci il file completo o il blocco modificato pronto da incollare
3. Se la modifica richiede azioni esterne (inviare la sitemap a Google Search Console, testare un URL con Google), indicalo chiaramente

**Formato diff preferito:**
```
File: index.html
Modifica: aggiunto tag title e meta description mancanti

Prima:
  <head>
    <meta charset="UTF-8">
  </head>

Dopo:
  <head>
    <meta charset="UTF-8">
    <title>Nome Prodotto - Acquista Online | Brand</title>
    <meta name="description" content="...">
    <link rel="canonical" href="https://esempio.com/prodotto">
  </head>
```

## Alla fine

Riepiloga in 3-5 punti cosa hai fatto, con una riga per ciascuno.
Se ci sono correzioni che non puoi applicare direttamente (es. configurazione server, Google Search Console), elencale come "Da fare manualmente" con istruzioni precise.
