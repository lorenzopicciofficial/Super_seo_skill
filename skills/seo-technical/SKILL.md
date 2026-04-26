---
name: seo-technical
description: >
  Individua e corregge i problemi tecnici che impediscono a Google
  di trovare, leggere e indicizzare correttamente le pagine del sito.
  Usa questa skill quando il sito non compare su Google nonostante
  i contenuti siano buoni, quando vuoi verificare che tutto sia
  configurato correttamente, o quando hai appena lanciato un sito nuovo.
  Si attiva con frasi come: "il sito non si indicizza", "controlla il robots.txt",
  "ottimizza la sitemap", "canonical non funziona", "meta robots",
  "redirect 301", "problemi tecnici SEO", "il sito non appare su Google".
---

# seo-technical — Problemi tecnici di indicizzazione

Hai ricevuto una richiesta di analisi o correzione tecnica SEO. Il tuo obiettivo è individuare e risolvere i problemi che impediscono a Google di trovare e capire le pagine — spiegando ogni problema in modo comprensibile, senza dare per scontata la conoscenza tecnica.

## I problemi tecnici più comuni

### 1. Il sito dice a Google di non entrare (robots.txt)
Il file `robots.txt` è come un cartello all'ingresso del sito che dice ai motori di ricerca cosa possono visitare.

**Cosa controllare:**
```
User-agent: *
Disallow: /
```
Se trovi `Disallow: /` senza limitazioni, significa che stai dicendo a Google di non indicizzare nulla — un errore gravissimo spesso fatto per sbaglio durante lo sviluppo e dimenticato in produzione.

**Configurazione corretta per un sito normale:**
```
User-agent: *
Disallow: /admin/
Disallow: /login/
Disallow: /checkout/

Sitemap: https://esempio.com/sitemap.xml
```

Blocca solo le sezioni che non vuoi su Google (admin, login, pagine interne). Tutto il resto deve essere accessibile.

---

### 2. Le pagine si escludono da sole (meta robots)
Dentro il `<head>` di ogni pagina può esserci un tag che dice a Google di non indicizzarla.

**Da cercare:**
```html
<meta name="robots" content="noindex, nofollow">
```

`noindex` = Google non mostra questa pagina nei risultati
`nofollow` = Google non segue i link in questa pagina

**Quando usarlo** (solo in questi casi):
- Pagine di conferma ordine, pagina carrello, area riservata
- Pagine duplicate intenzionali
- Pagine di test o staging

**Quando NON usarlo:** mai su homepage, pagine prodotto, articoli, pagine categoria.

---

### 3. Pagine duplicate senza indicazione di quale preferire (canonical)
Se la stessa pagina è raggiungibile da più URL diversi, Google non sa quale indicizzare e disperde il "peso" tra tutte.

Esempi di duplicati tipici:
- `https://esempio.com/prodotto` e `https://esempio.com/prodotto?ref=newsletter`
- `https://esempio.com` e `https://www.esempio.com`
- `http://esempio.com` e `https://esempio.com`

**La soluzione — tag canonical:**
```html
<link rel="canonical" href="https://esempio.com/prodotto">
```

Va inserito nel `<head>` di ogni pagina, punta sempre alla versione "ufficiale" dell'URL.

---

### 4. La mappa del sito non esiste o non è aggiornata (sitemap XML)
La sitemap è un file che elenca tutte le pagine del sito che vuoi su Google — come un indice che gli mandi direttamente.

**Dove deve stare:** `https://tuosito.com/sitemap.xml`

**Struttura base:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://esempio.com/</loc>
    <lastmod>2026-04-01</lastmod>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://esempio.com/chi-siamo</loc>
    <lastmod>2026-03-15</lastmod>
    <priority>0.8</priority>
  </url>
</urlset>
```

**Cosa NON includere:** pagine con `noindex`, pagine di errore, pagine di amministrazione.

**Come dirlo a Google:** aggiungi questa riga nel `robots.txt`:
```
Sitemap: https://esempio.com/sitemap.xml
```

---

### 5. Il sito non va bene su mobile (mobile-friendliness)
Google indicizza prima la versione mobile del sito. Se non è ottimizzata, penalizza anche i risultati su desktop.

**Controllo base nel `<head>`:**
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Se questo meta tag manca, il sito probabilmente non è ottimizzato per mobile.

Segnala se manca e suggerisci di testare con lo strumento Google Mobile-Friendly Test.

---

### 6. Redirect errati o catene di redirect
Un redirect 301 dice a Google "questa pagina si è spostata definitivamente qui". Va bene.
Una catena di redirect (A → B → C → D) rallenta la scansione e può disperdere autorità.

**Come identificarla:** se analizzando il codice trovi redirect annidati o multipli, segnalalo.

**Regola:** ogni URL deve portare direttamente alla destinazione finale, senza passaggi intermedi.

---

### 7. Pagine lente (Core Web Vitals)
Google penalizza i siti lenti, specialmente su mobile. I segnali da cercare nel codice:
- Immagini senza attributo `width` e `height` (causano spostamento del layout)
- JavaScript che blocca il caricamento (script senza `async` o `defer`)
- Immagini troppo grandi (non ottimizzate in formato WebP/AVIF)
- Font caricati da Google Fonts senza `preconnect`

**Fix rapidi da applicare:**
```html
<!-- Preconnect per Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">

<!-- Script non bloccanti -->
<script src="script.js" defer></script>

<!-- Immagini con dimensioni esplicite -->
<img src="foto.jpg" width="800" height="600" alt="descrizione">
```

---

## Come presentare il risultato

Per ogni problema trovato:
1. **Cosa c'è** — descrivi il problema in modo semplice
2. **Perché è un problema** — l'impatto concreto sull'indicizzazione
3. **Come sistemarlo** — codice o istruzione precisa

Alla fine proponi `/seo-fix` per applicare le correzioni direttamente ai file del progetto.
