# Super SEO Skill

Cinque skill per Claude Code che coprono tutto il ciclo SEO — dall'analisi iniziale alle correzioni concrete nel codice — ottimizzate anche per la visibilità sulle AI come ChatGPT, Perplexity e Google AI Overviews.

Leggere per design: ~15.000 token totali contro i ~145.000 di soluzioni equivalenti.

---

## Le 5 skill

### `/seo-audit` — Capire cosa non va
Analizza una pagina o un sito intero e restituisce un report chiaro, con i problemi ordinati per priorità e spiegati in modo comprensibile. È il punto di partenza: ti dice cosa guardare prima di toccare qualsiasi cosa.

**Quando usarla:**
- "Perché questa pagina non appare su Google?"
- "Fai un'analisi SEO di questo sito"
- "Cosa devo migliorare per posizionarmi meglio?"
- Prima di ottimizzare: per sapere dove concentrarsi

---

### `/seo-content` — Migliorare i testi
Ottimizza i testi per essere trovati su Google, ma anche per essere citati dalle AI. Copre SEO classico (titoli, struttura, parole chiave), GEO (come farsi citare da Google AI Overviews, ChatGPT, Perplexity) e AEO (come comparire nelle risposte rapide e vocali).

**Quando usarla:**
- "Ottimizza questo articolo per SEO"
- "Voglio che questa pagina venga citata da Google AI"
- "Riscrivi questo testo per posizionarsi su [parola chiave]"
- "Aggiungi una sezione FAQ ottimizzata"
- Per qualsiasi testo che deve portare traffico organico

---

### `/seo-schema` — Aiutare Google a capirti
Genera il codice che permette a Google di mostrare informazioni arricchite nei risultati: stelle, prezzi, FAQ direttamente nella pagina dei risultati, breadcrumb, informazioni sull'autore. Le AI usano questi dati per citare le fonti in modo più preciso.

**Quando usarla:**
- "Voglio le stelle nei risultati di Google"
- "Aggiungi i dati strutturati alla pagina prodotto"
- "Fai comparire le FAQ direttamente su Google"
- "Aggiungi lo schema markup all'articolo"
- Tipi supportati: Article, Product, FAQ, Organization, LocalBusiness, Breadcrumb

---

### `/seo-technical` — Risolvere i problemi tecnici
Controlla e corregge tutto ciò che impedisce a Google di trovare e leggere le pagine: robots.txt, sitemap, canonical, tag noindex, redirect, ottimizzazione mobile, velocità di caricamento. Spesso i siti non si indicizzano per errori tecnici banali, non per mancanza di contenuto.

**Quando usarla:**
- "Il sito non appare su Google"
- "Controlla il robots.txt"
- "La sitemap è corretta?"
- "Ho problemi di indicizzazione"
- Dopo un lancio di sito nuovo, per verificare che tutto sia a posto

---

### `/seo-fix` — Applicare le correzioni
Entra nei file del progetto e applica concretamente le modifiche: aggiunge meta tag mancanti, corregge canonical, inserisce dati strutturati, aggiorna robots.txt e sitemap. Non dà istruzioni — fa le modifiche direttamente nel codice.

**Quando usarla:**
- Dopo `/seo-audit`, per implementare quanto emerso
- "Aggiungi i meta tag a tutte le pagine"
- "Applica le correzioni SEO al progetto"
- "Correggi il canonical su questa pagina"
- Quando vuoi le modifiche fatte, non spiegate

---

## Flussi di lavoro tipici

### Nuovo sito da ottimizzare
```
/seo-audit  →  /seo-content  →  /seo-schema  →  /seo-fix
```
Prima capisci cosa manca, poi ottimizzi i testi, aggiungi i dati strutturati e applichi tutto.

### Sito che non si indicizza
```
/seo-technical  →  /seo-fix
```
Spesso è un problema di robots.txt o noindex — si risolve in pochi minuti.

### Articolo da ottimizzare
```
/seo-content  →  /seo-schema  →  /seo-fix
```
Ottimizzi il testo, aggiungi lo schema Article o FAQ, applichi le modifiche.

### Pagina prodotto e-commerce
```
/seo-audit  →  /seo-schema  →  /seo-content  →  /seo-fix
```
Analisi, dati strutturati con prezzo e stelle, testo ottimizzato, tutto applicato.

### Vuoi essere citato dalle AI (GEO/AEO)
```
/seo-content  →  /seo-schema
```
`/seo-content` ottimizza il testo per la citabilità da AI. `/seo-schema` aggiunge i dati strutturati che le AI usano come segnali di affidabilità.

---

## Differenze rispetto a soluzioni più grandi

| | Super SEO Skill | claude-seo completo |
|---|---|---|
| Token per sessione | ~15.000 | ~145.000 |
| Skill | 5 mirate | 23 |
| Copertura | SEO · GEO · AEO · Technical | + backlinks, e-commerce, local, hreflang, maps, programmatic… |
| Adatto a | Siti, blog, e-commerce standard | Agenzie SEO, audit enterprise |

Se hai bisogno di funzionalità avanzate (analisi backlink, SEO locale multi-sede, SEO e-commerce avanzato, programmatic SEO su larga scala), valuta di integrare skill specifiche aggiuntive.

---

## Installazione

```
/plugins add marketplace super-seo lorenzopicciofficial/Super_seo_skill
```

Poi installa le skill che ti servono:

```
/plugins install seo-audit@super-seo
/plugins install seo-content@super-seo
/plugins install seo-schema@super-seo
/plugins install seo-technical@super-seo
/plugins install seo-fix@super-seo
```

---

## Glossario rapido

**SEO** — Search Engine Optimization. Tutto ciò che fa sì che Google trovi e mostri le tue pagine.

**GEO** — Generative Engine Optimization. Ottimizzare i contenuti per essere citati dalle AI (Google AI Overviews, ChatGPT, Perplexity) invece che solo per comparire nei link tradizionali.

**AEO** — Answer Engine Optimization. Ottimizzare per comparire nelle risposte dirette: featured snippet di Google, risposte vocali, box FAQ nei risultati.

**Schema markup / Dati strutturati** — Codice invisibile agli utenti che aiuta Google e le AI a capire il tipo e il significato del contenuto.

**Canonical** — Tag che dice a Google qual è la versione "ufficiale" di una pagina quando esistono più URL che puntano allo stesso contenuto.

**robots.txt** — File di testo che dice ai motori di ricerca quali parti del sito possono visitare.

**Sitemap** — File che elenca tutte le pagine del sito che vuoi far indicizzare a Google.
