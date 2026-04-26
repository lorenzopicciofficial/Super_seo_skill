---
name: seo-audit
description: >
  Analizza una pagina web o un sito intero e produce un report chiaro
  con i problemi trovati e le priorità di intervento.
  Usa questa skill quando vuoi capire perché una pagina non si posiziona bene,
  cosa ostacola la visibilità su Google, o quando vuoi un punto di partenza
  prima di ottimizzare qualcosa.
  Si attiva con frasi come: "analizza questa pagina", "audit SEO di",
  "perché questo sito non va su Google", "cosa non va con il posizionamento",
  "controlla la visibilità di", "fammi un'analisi SEO".
---

# seo-audit — Analisi SEO completa

Hai ricevuto una richiesta di analisi SEO. Il tuo obiettivo è produrre un report chiaro, concreto e facile da leggere — non un documento tecnico, ma una guida pratica su cosa sistemare e perché.

## Come lavorare

### 1. Capisci il contesto prima di tutto
Prima di analizzare, chiediti (o chiedi all'utente):
- È una singola pagina o un intero sito?
- C'è una parola chiave o un argomento principale su cui si vuole posizionare?
- Il sito è già online o è in fase di sviluppo?

Se hai accesso al codice HTML/sorgente della pagina, analizza quello direttamente.
Se hai solo l'URL, descrivi cosa analizzeresti e cosa richiederebbe strumenti esterni.

### 2. Cosa controllare

**Visibilità su Google (SEO tradizionale)**
- Il titolo della pagina (tag `<title>`) è descrittivo, lungo 50-60 caratteri, contiene la parola chiave principale?
- La descrizione (meta description) è presente, invoglia al clic, è lunga 150-160 caratteri?
- I titoli interni (H1, H2, H3) sono usati in modo logico e descrivono il contenuto?
- Le immagini hanno il testo alternativo (attributo `alt`) compilato?
- I link interni al sito sono presenti e sensati?
- L'URL è leggibile e descrittivo?

**Visibilità sulle AI — Google AI Overviews, ChatGPT, Perplexity (GEO)**
- Il contenuto risponde direttamente a domande concrete? Le AI citano pagine che danno risposte nette.
- Ci sono frasi brevi e autonome che si possono estrarre e citare?
- L'autore o il brand è riconoscibile e presente nella pagina?
- Ci sono dati, statistiche o affermazioni verificabili?

**Visibilità nelle risposte veloci — featured snippet, voice search (AEO)**
- Il contenuto include definizioni chiare ("Cos'è X: …")?
- Ci sono liste o tabelle che rispondono a domande del tipo "Come fare X" o "Quali sono i migliori Y"?
- Le domande frequenti (FAQ) sono presenti e ben formulate?

**Aspetti tecnici base**
- La pagina ha il tag canonical? Punta a sé stessa o a un'altra URL?
- Ci sono tag robots che potrebbero bloccare l'indicizzazione?
- La pagina carica velocemente? (Valuta da eventuali segnali nel codice)
- Il sito è mobile-friendly? (Valuta dai meta viewport e dai CSS)

### 3. Come presentare il report

Usa questo formato — senza tecnicismi, come se spiegassi a qualcuno che non è sviluppatore:

---
**Cosa hai** — una riga che riassume lo stato attuale

**Priorità alta** (sistemi subito)
- [problema] → [perché conta] → [cosa fare]

**Priorità media** (sistemi nelle prossime settimane)
- [problema] → [perché conta] → [cosa fare]

**Priorità bassa** (miglioramenti futuri)
- [problema] → [perché conta] → [cosa fare]

**Punti di forza** — cosa già funziona bene

**Prossimo passo consigliato** — una sola azione concreta da fare oggi
---

### 4. Tono e linguaggio
- Spiega ogni problema come se l'utente non sapesse cos'è un "canonical" o un "H1"
- Usa analogie semplici quando servono ("Il titolo è come il nome di un negozio: se non si capisce cosa vendi, la gente passa oltre")
- Non elencare problemi senza spiegare l'impatto reale
- Se qualcosa richiede strumenti esterni che non hai (Google Search Console, PageSpeed), dillo chiaramente e spiega cosa andare a controllare

### 5. Alla fine dell'analisi
Proponi sempre il passo successivo logico:
- Se ci sono problemi di testo → suggerisci `/seo-content`
- Se ci sono problemi tecnici → suggerisci `/seo-technical`
- Se mancano dati strutturati → suggerisci `/seo-schema`
- Se l'utente vuole applicare le correzioni direttamente → suggerisci `/seo-fix`
