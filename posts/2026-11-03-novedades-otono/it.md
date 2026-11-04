---
slug: whats-new-september-november-2026
title: "BolloPrint si aggiorna! Le novità che ti aiutano nel tuo laboratorio di stampa 3D"
description: "Tutte le novità di BolloPrint dal 14 settembre al 3 novembre 2026: dall'agente locale senza container alle fatture a norma e alle nuove Finanze."
date: 2026-11-03
tags: [novita]
cover: 01-bollo.webp
---

Da metà settembre abbiamo pubblicato **41 aggiornamenti** di BolloPrint. Alcuni
sono cambiamenti grandi e importanti. Altri sono piccoli miglioramenti che rendono
più comodo il tuo lavoro di tutti i giorni. Ecco i più importanti.

![In sette settimane: più di 400 miglioramenti che si notano, più di 250 modifiche sullo schermo, circa 190 errori corretti, 11 paesi con fatture a norma, 9 lingue nell'app e 102 stampanti di 15 marchi](/blog/media/2026-11-03-novedades-otono/02-cifras-it.webp)

## Cominciamo dalla parte più interessante: ciò che cambia il tuo modo di lavorare

### 1. L'agente locale, ora senza sapere nulla di container

Sappiamo che usare Docker può essere complicato. Per questo ora è più facile.
Installa l'agente su ciò che hai già: il tuo NAS, il computer del laboratorio o il
tuo Home Assistant.

![I loghi di Synology, QNAP, Windows, Home Assistant e TrueNAS](/blog/media/2026-11-03-novedades-otono/03-agentes.webp)

| Dove | Come si installa |
|---|---|
| **Synology e QNAP** | Scarica il pacchetto del tuo NAS e installalo a mano dal suo centro pacchetti. |
| **Windows** | Un programma di installazione per il computer del laboratorio. |
| **Home Assistant** | Il pulsante «Aggiungi a Home Assistant» e hai finito. |
| **TrueNAS** | Incolla nelle sue app la configurazione che ti diamo. |

Poi apri la sua pagina e premi **«Collega a BolloPrint»**: il proprietario del
laboratorio lo conferma con un clic, senza copiare codici. Come tutti gli agenti,
si aggiorna da solo. Docker e Kubernetes continuano a funzionare come sempre.

:::info
Lo trovi in **Impostazioni → Stampanti → Agente locale → «Nuovo agente»**.
[Come installare l'agente](/help/el-agente-local)
:::

---

### 2. Le tue stampanti, più visibili e conteggiate meglio

- **Telecamera in diretta** e una foto finale di ogni stampa nel suo storico.
- **Ogni stampa racconta tutto**: quanto è durata rispetto alla stima, ogni bobina con il suo slot dell'AMS e il nome del modello di MakerWorld con il suo link.
- **Il consumo reale**: una stampa fallita o annullata non viene più conteggiata per intero, e quelle in resina registrano i loro millilitri.
- **Bambu Lab**, tramite cloud senza password (la tua email e un codice, e la sessione si rinnova da sola) e tramite rete locale con pausa, ripresa e annullamento da BolloPrint, con la Modalità sviluppatore attiva.
- **Aggiungi per IP** ora è una procedura guidata per marchio; non serve più sapere quale «protocollo» parla la tua macchina.
- **L'agente locale si aggiorna da solo**, mai a metà di una stampa, e ogni marchio di stampanti migliora per conto suo.
- **Anycubic** (Kobra 3, S1, 4 e X) e **Creality** con il firmware di fabbrica (K1, K2, Ender-3 V3 e Hi) si aggiungono, in beta.

[Vedi le stampanti compatibili](/help/impresoras-compatibles)

---

### 3. Migrazione Smart

Porta clienti, modelli, pezzi, prodotti, ordini, preventivi e stock dalle cartelle
e dai fogli di calcolo del tuo computer. BolloPrint legge quello che porti e ti
propone come inserirlo; tu lo controlli prima che entri qualsiasi cosa, e se
sbagli, si annulla.

:::warning
Sono tre passaggi: **Prepara · Capisci · Migra**. Dal piano Pro, in Chrome o Edge
da computer. Con Max e Business, se preferisci, lo facciamo noi per te.
:::

---

### 4. Fatture a norma direttamente dall'ordine

Emetti la fattura di un ordine senza uscire da BolloPrint: con la sua numerazione,
la sua imposta e il tuo logo. Prima di emetterla vedi la fattura **esattamente come
uscirà**, e se manca qualcosa ti diciamo cosa e dove correggerlo.

- **Incassi**: in attesa, scaduta o pagata, e uno ZIP con tutte le tue fatture.
- **Vendite senza IVA ad aziende dell'UE**, con la dicitura legale inclusa e il
  numero verificato su VIES.
- **Fattura elettronica tedesca, QR-bill svizzera** e fatture in un'altra valuta.

Già disponibile in 11 paesi: Austria, Cechia, Cipro, Germania, Irlanda,
Lussemburgo, Paesi Bassi, Polonia (tramite KSeF), Regno Unito, Svezia e Svizzera.

:::warning
**In Spagna non ancora**: arriverà quando avremo integrato VeriFactu, e te lo
diremo.
:::

[Vedi i paesi con fatturazione](/help/paises-con-facturacion)

---

### 5. Preventivi più professionali

- Il PDF del preventivo ha **la forma di una fattura**: numero, data, validità e,
  nei piani a pagamento, il tuo logo.
- **Numerazione per anno** («2026-00001») e senza buchi, anche se ne elimini uno.
- **Sconto** in € o in %, che compare come una riga in più.
- Schede cliente **Privato o Azienda**, e dati fiscali più semplici.
- Creazione automatica di un **ordine quando il preventivo viene accettato**.

[Vedi i preventivi](/help/presupuestos)

---

### 6. Finanze completamente nuove

Sei schede in cui vedere entrate, spese, imposte e utile nel periodo che vuoi
(mensile, trimestrale, annuale…).

Carica le tue spese con il nostro agente IA e archivia le fatture dei tuoi
fornitori per vedere a colpo d'occhio dove vanno i tuoi soldi. Tieni sotto
controllo le imposte che devi pagare in ogni periodo.

:::info
**Il meglio:** esporta questi dati per il tuo commercialista in uno ZIP con un solo clic.
:::

[Vedi Finanze](/help/financiero)

---

### 7. «Avvisi»: i problemi del tuo laboratorio, a colpo d'occhio

Una stampante ferma per un errore, un negozio Etsy scollegato, un pagamento non
andato a buon fine, lo spazio di archiviazione quasi pieno… Ti avvisiamo solo di
ciò che richiede davvero qualcosa, e ogni avviso si chiude da solo quando lo
risolvi.

Puoi silenziare un avviso per qualche giorno o per sempre. Quelli rossi, che
bloccano qualcosa di importante, li mostriamo in rosso solo a chi può risolverli;
il resto del team li vede con un «Avvisa il proprietario del laboratorio».

---

### 8. Esporta il tuo inventario, in Excel o in PDF

Ora puoi ottenere un elenco di ciò che hai in magazzino: stock, filamenti, resine,
forniture…

| Formato | Cosa ottieni |
|---|---|
| **Excel** | Una cartella con un riepilogo e un foglio per sezione, con filtri, totali e ciò che è esaurito in rosso. |
| **PDF** | Un documento per sezione, con il tuo logo, le foto dei tuoi pezzi e i colori di ogni bobina. |

In tutti i piani, e sempre con tutte le righe, non solo quelle che vedi sullo
schermo.

---

### 9. Nella tua lingua e a modo tuo

BolloPrint ora parla **🇵🇱 polacco, 🇳🇱 olandese e 🇨🇿 ceco**. Con queste, le lingue
sono nove in totale.

Date e importi si scrivono **come nel paese del tuo laboratorio**, sullo schermo,
nel PDF e nelle email.

E c'è una **nuova Home** che parte dalle cose urgenti, con «Crea nuovo» per un
ordine, un preventivo o una creazione rapida, e «Primi passi» con la sua barra di
avanzamento.

## E inoltre, perché anche i piccoli cambiamenti si notano

| Dove | Cosa cambia |
|---|---|
| **Schermate** | Mentre qualcosa si carica ne vedi la forma, mai un falso elenco vuoto; se fallisce, un «Riprova». I filtri sono uguali in tutti gli elenchi, anche su mobile. |
| **Caricamenti** | Ogni file mostra il suo avanzamento e riprende da solo dopo un'interruzione di rete. I file slicer possono pesare fino a 5 GB. |
| **Costi** | 29 famiglie di filamento e 9 di resina, con prezzi al chilo aggiornati; i margini, con una barra colorata e un esempio. |
| **Clienti** | L'elenco cerca e ordina per qualsiasi colonna, e un cliente senza alias si vede con il nome completo. |
| **Etsy** | Importare un annuncio è fino a 8 volte più veloce, entrano gli ordini con due variazioni e, prima di sincronizzare un annuncio, vedi valore per valore cosa cambierà. Impostazioni → Marketplace ora è una galleria, con una pagina per negozio. |
| **Spedizioni** | Corrieri e canali di vendita propri per Austria, Germania, Regno Unito, Polonia, Cechia e Paesi Bassi. |
| **Manuale e blog** | Il manuale passa da 49 a 70 pagine, in tutte e nove le lingue, e sul blog ci sono sei nuovi articoli: dall'agente locale a quanto costa davvero un pezzo. |
| **Ogni giorno** | L'app regge meglio i picchi, si riprende da sola dopo un'interruzione di rete, il traduttore di Chrome non la rompe più e una stampante il cui agente si spegne a metà non lascia più stampe fantasma. |

## Dove siamo

| Cosa | Dove e quanto |
|---|---|
| 🧾 **Fatture a norma in 11 paesi** | 🇦🇹 Austria · 🇨🇿 Cechia · 🇨🇾 Cipro · 🇩🇪 Germania · 🇮🇪 Irlanda · 🇱🇺 Lussemburgo · 🇳🇱 Paesi Bassi · 🇵🇱 Polonia · 🇬🇧 Regno Unito · 🇸🇪 Svezia · 🇨🇭 Svizzera |
| 🌍 **Un laboratorio si può aprire da 53 paesi europei** | Con la sua valuta, le sue imposte e i suoi corrieri. Si paga in euro, sterline, złoty o corone ceche. |
| 🖨️ **102 modelli di stampante, a filamento e a resina** | Bambu Lab · Prusa · Elegoo · FlashForge · Anycubic · Creality · QIDI · Snapmaker · Voron · RatRig · Sovol · Artillery · Longer · Phrozen · Two Trees |
| ✅ **10 provate da noi su macchine reali** | Bambu Lab A1, A2L, P1P, P1S, P2S, X1 Carbon, X2D, H2C, H2D e H2S. |

## Ti manca qualcosa?

Raccontacelo a
[info@bolloprint.com](mailto:info@bolloprint.com) o sul nostro
[canale Discord](/help/soporte-por-discord). Leggiamo tutto. Molto di quello che
vedi qui è nato da messaggi come il tuo.

Se vuoi più dettagli su come funziona, trovi tutto nel [manuale](/help).

E non ci fermiamo: continuiamo a lavorare ogni giorno per fare di BolloPrint il
miglior strumento per il tuo laboratorio di stampa 3D.

![Bollo, la mascotte di BolloPrint, con occhiali da laboratorio e cintura degli attrezzi, su un progetto](/blog/media/2026-11-03-novedades-otono/01-bollo.webp "60%")
