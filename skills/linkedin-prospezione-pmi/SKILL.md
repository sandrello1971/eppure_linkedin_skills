---
name: linkedin-prospezione-pmi
description: Individua su LinkedIn titolari di PMI e decisori a cui proporre i tuoi servizi, valutando pochi profili alla volta con una griglia di punteggio e preparando i messaggi. Lavoro a lotti, sempre con la tua approvazione.
---

# LinkedIn – Prospezione PMI (a basso volume, con conferma)

Aiuta l'utente a trovare e qualificare, su LinkedIn, titolari di PMI e altre figure decisionali a cui proporre i suoi servizi. Lavora tramite Claude in Chrome nella sessione LinkedIn dell'utente.

## Principi non negoziabili

LinkedIn vieta lo scraping e l'automazione. Un account limitato o chiuso è un danno reale per l'utente. Quindi:

1. **Solo lavoro assistito, mai massivo.** Claude legge i profili come farebbe una persona che li apre uno alla volta. Niente script che scorrono centinaia di pagine, niente estensioni di esportazione, niente servizi esterni di scraping.
2. **Lotti piccoli.** Massimo **25 profili al giorno** per sessione di lavoro e **non più di 10 per lotto**, poi pausa. Con account gratuito o Premium base meglio **15**. Il limite si abbassa, mai si alza, se LinkedIn mostra segnali di allarme.
3. **Ritmo umano.** Tra un profilo e l'altro aspetta alcuni secondi, apri solo ciò che serve alla valutazione (intestazione, Informazioni, esperienze, attività recente), non percorrere tutti i collegamenti del profilo.
4. **Nessuna azione senza conferma.** Claude non invia inviti, messaggi, commenti o reazioni da solo. Prepara bozze e l'utente decide. Se l'utente chiede di inviare, si invia **un'azione alla volta**, dopo la sua conferma esplicita su testo e destinatario.
5. **Stop immediato ai segnali di allarme.** Se compaiono verifica d'identità, CAPTCHA, avviso di "attività insolita", limite di ricerca raggiunto o caricamenti anomali, Claude **si ferma**, lo dice e non riprova nella stessa giornata. Non risolve CAPTCHA e non aggira i blocchi.
6. **Dati minimi.** Si registra solo ciò che serve a decidere: nome, ruolo, azienda, link al profilo, punteggio, motivo, stato del contatto. Niente telefoni, email o dati personali non pubblici raccolti altrove, niente profili di persone non rilevanti.
7. **Nessun invio di massa.** Un invito con nota personalizzata ha senso solo se c'è un motivo concreto. Niente modelli identici a tutti.

## Cosa chiedere all'utente (prima di iniziare)

Fai le domande in un unico messaggio. Se l'utente ha già un profilo cliente ideale salvato, riutilizzalo.

1. **Cosa vende**: servizio, a chi serve, risultato concreto, prezzo indicativo o fascia.
2. **Cliente ideale (PMI)**: settori, zona (province o regioni), dimensione (dipendenti), ruoli da cercare (titolare, amministratore, direttore generale, HR, formazione, responsabile operativo).
3. **Segnali di opportunità**: cosa rende un profilo "caldo" (assume, sta crescendo, parla di digitale o AI, ha un problema che il servizio risolve, ha appena cambiato ruolo).
4. **Esclusioni**: settori, aziende, persone da non contattare (clienti attuali, concorrenti, contatti già avuti).
5. **Tipo di account**: gratuito, Premium o Sales Navigator. Con Sales Navigator si usano le ricerche salvate; senza, la ricerca standard con filtri.
6. **Tono**: formale o diretto, come vuole presentarsi (nome, ruolo, sito).
7. **Obiettivo del contatto**: una chiacchierata di 15 minuti, un audit, una demo, un invito a un evento.
8. **Dove salvare il risultato**: foglio nuovo (CSV/Excel) o uno esistente da aggiornare.

## Flusso di lavoro

### 1. Definire la ricerca
- Costruisci insieme all'utente i filtri (ruolo, zona, settore, dimensione azienda). Meglio ricerche strette che producono pochi profili buoni.
- Usa query mirate: una ricerca generica come "titolare PMI Milano" restituisce soprattutto multinazionali, consulenti e reti di professionisti. Meglio settore + ruolo + zona, oppure partire da aziende già individuate fuori da LinkedIn.
- Apri la ricerca in Chrome (nuova scheda) oppure usa quella che l'utente ha già impostato. Non aggirare i limiti di ricerca: se LinkedIn li segnala, fermati.

### 2. Lotto di valutazione (max 10 profili)
Per ogni profilo raccogli, dalla pagina pubblica visibile all'utente:
- nome, ruolo attuale, azienda, zona, anzianità nel ruolo;
- dimensione e settore dell'azienda, verificati come descritto in «Verifica della dimensione aziendale»;
- sezione Informazioni e ultimi post o attività, per capire temi e momento;
- se c'è già un collegamento in comune o una relazione precedente.

### Verifica della dimensione aziendale (prima di leggere il resto)

Controlla l'azienda **prima** di leggere post e attività: se è fuori target, scarta il profilo e risparmi pagine su LinkedIn. Fonti, in ordine:

0. **API Openapi (solo se disponibile).** Openapi (openapi.com) offre un'API a pagamento sulle imprese italiane, con dati ufficiali da Registro Imprese e bilanci: fatturato, utili, numero di dipendenti, stato attivo/non attivo. Usala **solo se** l'utente ha un account e le credenziali sono già disponibili in modo sicuro (variabili d'ambiente o un connettore) e c'è uno strumento che può chiamarla; altrimenti salta questo punto senza insistere. Non chiedere di incollare token o chiavi in chat, non scriverli in file e non stamparli. Cerca per partita IVA o denominazione e provincia (servizio `IT-advanced` sul host `company.openapi.com`; per prove c'è l'ambiente di test `test.company.openapi.com`). Controlla nella documentazione di Openapi campi, limiti e costi per chiamata prima di usarla, e informa l'utente del costo prima di un lotto. Un dato da Openapi vale come fonte ufficiale: con una sola fonte, se recente (ultimo bilancio depositato), l'affidabilità è **confermata**. Usa solo i servizi su **imprese**, mai quelli su persone.
1. **Pagina aziendale LinkedIn**: fascia dichiarata (es. "11-50") e numero di persone che la indicano come datore di lavoro. Il numero di persone è un **minimo**: se supera la fascia, la fascia è sbagliata.
2. **Ricerca web** (WebSearch, non il browser di LinkedIn): `<ragione sociale> <città> fatturato dipendenti`. Se Openapi non è disponibile, esistono portali che ripubblicano i dati del Registro Imprese (es. aziende.it, la parte pubblica di Atoka, Ufficio Camerale). Usa il **fatturato** come riscontro principale: i dati sui dipendenti dei portali gratuiti sono spesso a fasce, datati o incoerenti (in un test la stessa pagina riportava 0-9 dipendenti in tabella e 20-49 nel testo). Riferimento: piccola impresa sotto 50 dipendenti e 10 milioni di fatturato; media sotto 250 dipendenti e 50 milioni.
3. **Sito aziendale**: pagina del team, "chi siamo", offerte di lavoro.

Per ogni azienda registra la dimensione, la fonte e un grado di affidabilità:
- **confermata**: almeno due fonti indipendenti concordano;
- **stimata**: una sola fonte, oppure fonti incoerenti (scrivi l'intervallo e non scegliere il dato più comodo);
- **non verificabile**: nessuna fonte utile.

Scarta subito se l'azienda è chiaramente fuori target (sotto i 10 o sopra i 250 dipendenti, gruppo o multinazionale). Nel punteggio «Azienda nel target»: affidabilità confermata = punteggio pieno, stimata = massimo 15 su 25, non verificabile = massimo 12 su 25. La ricerca riguarda l'azienda, non la persona.

### 3. Punteggio (0-100)
| Criterio | Peso |
|---|---|
| Ruolo decisionale (titolare/amministratore/DG = massimo) | 30 |
| Azienda nel target (dimensione, settore, zona) | 25 |
| Segnale di opportunità recente (post, assunzioni, crescita, tema affine) | 20 |
| Legame o terreno comune (collegamenti, contesto, interessi) | 15 |
| Raggiungibilità (profilo attivo, risponde, messaggi aperti) | 10 |

Fasce: **70+ = priorità**, 50-69 = da valutare, sotto 50 = scartare. Per ogni profilo scrivi in una riga **perché** quel punteggio. Se un dato manca, scrivi "non verificabile" e non indovinare.

### 4. Strategia di contatto (solo per i profili 70+)
Proponi la sequenza più leggera possibile:
1. interazione genuina su un loro contenuto (commento utile, non un "bel post");
2. richiesta di collegamento con nota breve, solo se c'è un motivo concreto;
3. messaggio dopo l'accettazione, senza vendere subito, con una domanda o un'osservazione utile;
4. un solo follow-up dopo 5-7 giorni, poi basta.

Per ogni profilo prepara:
- la nota di collegamento (massimo 300 caratteri);
- il primo messaggio (60-90 parole);
- il follow-up (30-50 parole).

I testi citano un elemento reale del profilo, parlano del problema del destinatario e non del servizio. Niente frasi da catena di montaggio, niente promesse non dimostrabili, niente lusinghe.

### 5. Consegna del lotto
Salva o aggiorna la tabella con queste colonne:
`data | nome | ruolo | azienda | zona | settore | dimensione | fonte e affidabilità dimensione | link profilo | punteggio | motivo | segnale | azione proposta | stato | prossimo passo`

Stati ammessi: `da valutare`, `scartato`, `da contattare`, `contattato`, `risposto`, `in corso`, `non interessato`, `non contattare`.

Poi mostra all'utente: i profili in priorità con motivo e bozze, quelli da valutare, il numero di profili guardati oggi rispetto al limite.

### 6. Pausa e ripresa
Dopo ogni lotto chiedi se continuare, fino al limite giornaliero. Alla ripresa, aggiorna prima la tabella con gli esiti reali (chi ha accettato, chi ha risposto).

## Conformità (Italia/UE)

- La prospezione B2B su dati professionali pubblici può reggersi sul **legittimo interesse**, ma richiede: motivo professionale pertinente, **informativa** al primo contatto (chi sei, perché scrivi, dove vengono i dati), **facilità di opposizione** ("se preferisci non ricevere altri messaggi, dimmelo e non scrivo più") e **conservazione limitata**.
- Chi dice di non voler essere contattato va marcato `non contattare` subito e non riproposto.
- Non conservare profili non contattati oltre il necessario: suggerisci all'utente di ripulire la tabella ogni 90 giorni.
- Per email e telefono valgono regole diverse (consenso o registro delle opposizioni): questa skill **non** raccoglie contatti fuori da LinkedIn.
- Claude non è un consulente legale: per un uso sistematico suggerisci di far verificare informativa e procedura.

## Alternative meno rischiose per trovare le aziende

Se serve volume, trova le **aziende** fuori da LinkedIn (registro imprese, siti aziendali, Google Maps, elenchi di associazioni di categoria; con Openapi anche il servizio di ricerca `IT-search` per provincia e codice ATECO) e usa LinkedIn solo per individuare il titolare di quelle aziende, una per volta. Riduce le ricerche su LinkedIn e migliora la qualità del target.

## Cose da non fare

- Non fingere di essere l'utente in conversazioni lunghe: ogni messaggio inviato passa dalla sua conferma.
- Non inventare dati su persone o aziende; se un dato non è visibile, scrivilo.
- Non cercare, dedurre o registrare dati sensibili (salute, opinioni politiche, religione, orientamento) né usarli per il punteggio.
- Non riprovare dopo un blocco nello stesso giorno, non cambiare scheda o browser per aggirarlo.
- Non superare i limiti di lotto e di giornata, nemmeno se l'utente ha fretta: spiega il rischio e proponi di continuare domani.
