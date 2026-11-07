# eppure_linkedin_skills – Skill LinkedIn per Claude

Cinque skill in italiano per lavorare su LinkedIn con Claude, più una skill di strategia video e una generica per il giornale PDF di marca. Ognuna è una cartella in `skills/` con un `SKILL.md`: istruzioni che Claude legge e segue quando le richiami.

Tutte chiedono all'utente di caricare logo e immagini da usare e non rigenerano né alterano mai un logo esistente. Nessuna contiene dati di un cliente specifico.

## Le skill

| Skill | A cosa serve |
|---|---|
| [`linkedin-profilo-efficace`](skills/linkedin-profilo-efficace/SKILL.md) | Audit e riscrittura del profilo personale (headline, Informazioni, esperienze, in evidenza, competenze, banner) verso un obiettivo e un target. |
| [`linkedin-pagina-aziendale`](skills/linkedin-pagina-aziendale/SKILL.md) | Creazione o ottimizzazione di una pagina aziendale: testi, impostazioni, immagini, post di lancio e primo piano editoriale. |
| [`linkedin-articoli-da-sito`](skills/linkedin-articoli-da-sito/SKILL.md) | Articoli o newsletter LinkedIn con Tone of Voice e argomento presi da un sito di riferimento. |
| [`linkedin-piano-editoriale`](skills/linkedin-piano-editoriale/SKILL.md) | Piano editoriale (1 post al giorno + 1 articolo a settimana), bozze, immagini con ChatGPT o Nano Banana, pubblicazione via Chrome con conferma. |
| [`linkedin-prospezione-pmi`](skills/linkedin-prospezione-pmi/SKILL.md) | Individua titolari di PMI e decisori a cui proporre i tuoi servizi: lavoro a lotti piccoli, griglia di punteggio, bozze di contatto, nessuna azione senza conferma e limiti pensati per non mettere a rischio l'account. |
| [`strategia-video-organico`](skills/strategia-video-organico/SKILL.md) | Strategia di digital marketing e piano di video organici (Reels, TikTok, LinkedIn, Shorts): questionario, pilastri, calendario, schede con copioni. Generazione dei video con Higgsfield, se collegato. |
| [`giornale-di-marca`](skills/giornale-di-marca/SKILL.md) | Giornale PDF personale con l'identità di un marchio (logo, palette, font, voce), personalizzato con un questionario. Si appoggia alla skill `leaderai-giornale`, che va installata a parte. |

## Come installare

### Installazione rapida (consigliata) – un solo comando, nessuna copia

Serve solo Node.js (per `npx`). Nessun account, nessuna pubblicazione su npm: il comando legge direttamente questo repository.

```bash
# Tutte le skill, per tutti i tuoi progetti, in Claude Code
npx skills add sandrello1971/eppure_linkedin_skills --all -g -a claude-code -y

# Vedere l'elenco senza installare
npx skills add sandrello1971/eppure_linkedin_skills --list

# Solo una skill
npx skills add sandrello1971/eppure_linkedin_skills --skill linkedin-piano-editoriale -g -a claude-code
```

Per aggiornare o rimuovere:

```bash
npx skills update
npx skills remove
```

Il CLI [`skills`](https://github.com/vercel-labs/skills) funziona anche con altri agenti (Codex, Cursor, Gemini CLI e altri): togli `-a claude-code` per scegliere dal menu.

### Installazione manuale – Claude Code (terminale o app desktop)

1. Scarica il repository: `git clone https://github.com/sandrello1971/eppure_linkedin_skills.git`
2. Copia le cartelle che ti servono dentro la cartella delle skill:
   - per averle in **tutti i progetti**: `~/.claude/skills/`
   - per averle solo in **un progetto**: `.claude/skills/` nella cartella del progetto

   Esempio per tutte e cinque:
   ```bash
   mkdir -p ~/.claude/skills
   cp -r eppure_linkedin_skills/skills/* ~/.claude/skills/
   ```
3. Riavvia Claude Code o apri una nuova sessione. Le skill compaiono nell'elenco delle skill disponibili.

### claude.ai e app Claude (web, desktop, mobile)

1. Comprimi in zip **la cartella di una singola skill**, in modo che lo zip contenga la cartella e, dentro, il file `SKILL.md`. Esempio da terminale:
   ```bash
   cd eppure_linkedin_skills/skills
   zip -r linkedin-pagina-aziendale.zip linkedin-pagina-aziendale
   ```
2. Apri **Impostazioni** e cerca la sezione dedicata alle skill (il nome del menu può cambiare tra versioni).
3. Scegli di caricare una skill e seleziona lo zip. Ripeti per ogni skill.
4. Attiva la skill, se richiesto.

Serve un account con le skill abilitate. Se non vedi la sezione, controlla il piano o le impostazioni dell'organizzazione.

## Come usare

Dopo l'installazione richiama la skill per nome, in italiano, descrivendo cosa vuoi. Claude ti farà le domande necessarie e ti chiederà i materiali (logo, immagini, sito di riferimento).

| Vuoi | Dì a Claude, per esempio |
|---|---|
| Migliorare il tuo profilo | «Usa linkedin-profilo-efficace: voglio posizionarmi come consulente per le PMI.» |
| Creare o sistemare la pagina aziendale | «Usa linkedin-pagina-aziendale per la pagina di questa azienda: il sito è …» |
| Scrivere un articolo | «Usa linkedin-articoli-da-sito: prendi il tono da questo sito e scrivi un articolo su …» |
| Pianificare i contenuti | «Usa linkedin-piano-editoriale: prepara il calendario di 30 giorni, un post al giorno e un articolo a settimana.» |
| Cercare clienti tra i titolari di PMI | «Usa linkedin-prospezione-pmi per cercare …» |
| Pianificare video organici | «Usa strategia-video-organico per il marchio …» |
| Fare un giornale di marca | «Usa giornale-di-marca per il marchio …» (serve prima `leaderai-giornale`) |

### Cosa serve per le funzioni avanzate

- **Pubblicare su LinkedIn**: serve Claude in Chrome collegato al tuo account LinkedIn. La pubblicazione **non avviene mai senza una tua conferma esplicita** nella chat.
- **Immagini**: le skill preparano prompt pronti per ChatGPT o Nano Banana (Gemini), oppure li usano direttamente in Chrome se sei già collegato. Il download dei file richiede il tuo permesso.
- **Caricare file su LinkedIn** (logo, cover, immagini dei post): l'automazione può essere bloccata. In quel caso la skill ti dice quale file allegare e dove, e lo alleghi tu.
- **Giornale di marca**: richiede la skill `leaderai-giornale`, Python con ReportLab e Pillow, e una cartella dati privata per ogni marchio.

### Consigli

- Parti dalla pagina aziendale o dal profilo, poi passa al piano editoriale.
- Controlla sempre date, numeri, norme e citazioni prima di pubblicare: le skill chiedono di segnare `[DA VERIFICARE]` e `[DA COMPLETARE]` ciò che non è confermato.
- Le dimensioni delle immagini indicate (logo 300×300, cover 1128×191, post 1200×627) sono indicative: LinkedIn può cambiarle.

## Crediti

Ideate e curate da **Stefano Andrello**, consulente, formatore e autore su intelligenza artificiale.

- Sito personale: [stefanoandrello.me](https://stefanoandrello.me)
- Eppure, formazione e consulenza su AI etica e professionale per PMI, scuole e formazione: [eppure.eu](https://eppure.eu)

Le skill sono state scritte con l'aiuto di Claude (Anthropic) e provate sul lavoro reale della pagina LinkedIn di Eppure.

## Licenza

Non è ancora stata scelta una licenza. Finché non viene aggiunta, il contenuto è visibile ma non è concesso un diritto esplicito di riuso: scrivi a Stefano Andrello prima di riutilizzarlo.
