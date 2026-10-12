---
slug: connect-printers-local-network-agent
title: "Collega le tue stampanti tramite la tua rete: l'agente locale, passo passo"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu… Un piccolo agente su un computer del laboratorio, tutto il tuo parco macchine dentro BolloPrint e senza toccare il router.
date: 2026-09-08
updated: 2026-10-12
tags: [tutorial]
cover: 01-portada.webp
draft: true
---

Le tue stampanti sono in laboratorio. Tu, non sempre. E ogni volta che vuoi
sapere se una sta ancora stampando, se è venuta bene o se le resta materiale,
devi esserci davanti.

Che siano nella tua rete non vuol dire che debba esserci anche tu. Per questo
c'è l'**agente locale**: un piccolo programma che vive su un computer del tuo
laboratorio, parla con le tue stampanti tramite la tua rete e racconta a
BolloPrint quello che vede.

- **Non tocchi il router.** Niente porte da aprire, niente IP fisso, niente
  firewall.
- **Leggerissimo.** Gli va bene qualsiasi computer che hai già acceso.
- **Uno per tutto il parco macchine**, per quanto grande sia.

::animation{id="local-agent"}

## Dove lo metti

Su **qualsiasi computer del laboratorio che non spegni**: un NAS, un mini-PC, un
Raspberry Pi, il PC del laboratorio. Gli chiedi solo due cose: che sia **sempre
acceso** e che abbia **Docker**.

Ancora meglio se è **nella stessa rete delle stampanti**, perché così le trova
da solo. Se non ci riesce, le aggiungi a mano e funzionano esattamente uguale.

## Passaggio 1 — Crealo in BolloPrint

Vai su **Impostazioni → Stampanti**, apri la scheda **Agente locale** e premi
**Nuovo agente**.

Dagli un nome che ti dica qualcosa tra sei mesi. Un consiglio: **chiamalo in
base a dove si trova, non a cosa è**. «Piano terra» o «Capannone 2» vanno bene;
«Agente 1», no.

![La scheda Agente locale, con il pulsante Nuovo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Passaggio 2 — Copia il modello

Quando lo crei, BolloPrint ti mostra un **modello**: un testo che contiene già
tutto quello che è tuo —le chiavi del tuo agente e la versione giusta— **già
scritto**. Non c'è niente da sostituire né da compilare.

Scegli il formato che usi (**Docker Compose** è quello normale) e premi
**Copia**.

![Il modello di deploy, con il pulsante per copiarlo](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Copialo adesso: si vede una sola volta
Le chiavi non scadono, ma non te le mostriamo più. Se perdi il modello non
succede niente di grave: apri l'agente e usi **Rigenera le chiavi** per
ottenerne uno nuovo.
:::

## Passaggio 3 — Incollalo dove lo farai girare

Questo ormai si fa sul tuo computer, non in BolloPrint. Dipende da dove lo metti:

**Su un NAS Synology.** Installa **Container Manager** dal **Centro pacchetti**.
Vai su **Progetto → Crea**, incolla il modello e clicca su crea. Senza scrivere
un solo comando.

**Su Windows o Mac.** Installa **Docker Desktop**, salva il modello in una
cartella come `docker-compose.yml` e avvialo da quella cartella con
`docker compose up -d`.

**Su Linux.** Installa **Docker** con il gestore di pacchetti della tua
distribuzione, salva il modello come `docker-compose.yml` e, da quella cartella,
`docker compose up -d`.

Usi **Portainer**? Incolli lo stesso modello in uno stack e fai il deploy.

:::info 💡 Su Windows e Mac, le stampanti non vengono trovate da sole
Lì Docker gira dentro una macchina virtuale, che non vede gli annunci che le
stampanti mandano alla tua rete. L'agente funziona uguale, ma le stampanti le
aggiungi tu, come nel passaggio 6.
:::

## Passaggio 4 — Controlla che sia online

Torna in BolloPrint. In meno di un minuto, l'agente passa a **Online**.

![L'agente nello stato Online](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Se non compare, quasi sempre è una di queste tre: il modello **incollato a
metà**, il computer **senza internet**, oppure un **firewall** che blocca
l'uscita.

## Passaggio 5 — Le tue stampanti compaiono da sole

L'agente **cerca le stampanti nella tua rete** per conto suo, ogni 15 minuti.
Quelle che trova escono in un elenco con la loro marca e il loro modello, e
decidi tu:

- **Aggiungi** — la registri e inizia a inviare dati.
- **Ignora** — non è tua, o non la vuoi qui.

![Le stampanti trovate nella rete, con i pulsanti per aggiungere e ignorare](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Se hai appena acceso una macchina e non vuoi aspettare, c'è un pulsante **Cerca
ora**.

Alcune ti chiederanno una **password** quando le aggiungi. Dipende dalla marca,
e lo vediamo tra un attimo.

## Passaggio 6 — Se qualcuna non compare, la aggiungi tu

Che una stampante non compaia da sola è **normale** in due casi:

- **È in un'altra rete.** Gli annunci delle stampanti non passano da una rete
  all'altra, quindi non vengono trovate da sole.
- **L'agente gira su Windows o Mac.** Lì Docker gira in una macchina virtuale, e
  nemmeno così vengono trovate da sole.

**Non ci perdi niente.** La aggiungi tu e funziona esattamente uguale, con
telecamera e comandi se quella macchina li ha. Premi **Aggiungi per IP** e
indichi il tipo di stampante, il suo indirizzo nella tua rete e, se la chiede,
la sua password.

![Il modulo per aggiungere una stampante tramite il suo IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Riservale l'IP nel router
Se il router cambia l'indirizzo a una stampante, la ritroviamo da soli, ma per
un po' resterà offline. Riservarle l'indirizzo evita quel buco. È
un'impostazione del router, non di BolloPrint.
:::

## Cosa ti chiede ogni marca

Qui è dove la gente si blocca. Lo riassumiamo:

| Marca | Cosa devi fare sulla macchina | Telecamera | Puoi mettere in pausa e annullare? |
|---|---|---|---|
| **Bambu Lab** | Attivare la **Modalità LAN** dal suo schermo e usare il **codice di accesso** che ti mostra | Sì | Sì, se attivi anche la **Modalità sviluppatore** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Usare la **password** che mostra la stampante stessa | Non ancora | Sì |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Di solito niente: in genere si collega senza password | Sì, se hai una webcam sul tuo Klipper | Sì |
| **Elegoo a resina** (Mars, Saturn, Jupiter) | Niente, non chiede password | Nei modelli che ce l'hanno | Sì |
| **Elegoo Centauri Carbon 2** | Solo se gli hai impostato tu un codice dal suo schermo | Sì | Non ancora |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Attivare **LAN Only** e usare il codice del suo schermo | Sì | Non ancora |

:::warning ⚠️ Bambu Lab: il codice di accesso CAMBIA
Ogni volta che attivi o disattivi la Modalità LAN, Bambu **genera un codice
nuovo**. Se una Bambu che andava bene smette all'improvviso di collegarsi, nove
volte su dieci è questo: guarda di nuovo il codice sul suo schermo e aggiornalo
in BolloPrint.
:::

:::info 💡 Non trovi il tuo modello nella tabella?
Guarda tra le [stampanti compatibili](/help/impresoras-compatibles). E se ha
**Klipper** dentro —qualsiasi macchina autocostruita o modificata— va bene lo
stesso, anche se la marca non compare in nessun elenco.
:::

## Se avevi già le Bambu via cloud, non duplicarle

Quando l'agente trova nella tua rete una macchina che **avevi già collegato via
cloud**, BolloPrint se ne accorge e te lo dice: *«È "P1S-02", che hai già tramite
Bambu Cloud»*. Il pulsante è **Collega anche via LAN**.

Premilo, e non la avrai due volte:

- Resta **una sola stampante**, con il suo numero, il suo nome e tutto il suo
  storico.
- Occupa **un solo posto** nel tuo piano.
- E guadagna la **telecamera**, che è quello che via cloud non avevi.

![L'avviso che quella stampante è già in Bambu Cloud, con il pulsante per collegarla anche via LAN](/blog/media/2026-09-08-impresoras-red-local-agente/07-tambien-por-lan.png)

:::warning ⚠️ La Modalità LAN scollega il cloud di Bambu
Quando la attivi, la stampante smette di parlare con il cloud di Bambu Lab. Da
quel momento, BolloPrint la vede tramite l'agente.
:::

## Cosa ci guadagni, in concreto

- **Quasi tutte le marche.** Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron… Questo il cloud non te lo dà: esiste solo per Bambu Lab.
- **Telecamera.** Guardarla in diretta mentre hai la pagina davanti, scattare
  una foto quando vuoi, e una foto finale salvata nello storico di ogni stampa.
  Non è videosorveglianza: non si registra niente.
- **Comandi.** Mettere in pausa, riprendere e annullare da BolloPrint, senza
  andare fino alla macchina, in quelle che lo permettono (guarda la tabella qui
  sopra). Su Bambu Lab, con la stampante in **Modalità LAN** e **Modalità
  sviluppatore**.
- **Resiste ai cali di internet.** Se la tua linea cade, l'agente **continua a
  leggere le stampanti e salva quello che succede**. Quando torna, manda tutto.
  Non perdi quelle ore di storico.
- **Non dipendi dal produttore** né dal fatto che il suo cloud continui a
  funzionare.

Quello che non si può fare da nessuna via: **mandare lavori in stampa**. Il file
continui a inviarlo dal tuo slicer.

## Domande che ci fanno spesso

**Devo aprire porte nel router?** No. Né porte, né IP fisso, né regole del
firewall. Funziona dietro un normale router di casa.

**Serve un agente per ogni stampante?** No. **Uno solo gestisce tutto il parco
macchine.** Ha senso averne più di uno solo se hai due sedi o due reti separate.

**E se spengo il computer, o esce una nuova versione?** Quando lo riaccendi,
l'agente riparte da solo. E si aggiorna da solo: quando esce una nuova versione
la scarica e si riavvia con quella. Dovrai fare qualcosa tu solo se te lo
segnaliamo sullo schermo.

:::info 💡 Ti sei bloccato?
Scrivici dalla [pagina dei contatti](/contact) o apri un thread sul
[nostro Discord](/help/soporte-por-discord). Se ci dici che stampanti hai, ti
diciamo esattamente cosa fare con ognuna.
:::

## Documentazione correlata

- [Collegare le stampanti](/help/conectar-impresoras) — le due vie e quale ti conviene
- [L'agente locale](/help/el-agente-local) — il riferimento completo
- [Installare l'agente](/help/desplegar-el-agente) — il dettaglio tecnico, se ti serve
- [Tipi di connessione](/help/tipos-de-conexion) — cosa permette ogni famiglia di stampanti
- [Stampanti compatibili](/help/impresoras-compatibles) — cerca qui il tuo modello
