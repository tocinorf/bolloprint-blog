---
slug: connect-printers-local-network-agent
title: "Collega le tue stampanti tramite la tua rete: l'agente locale, passo passo"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu… Un piccolo agente su un computer del laboratorio, tutto il tuo parco macchine dentro BolloPrint e senza toccare il router.
date: 2026-10-12
tags: [tutorial]
cover: 01-portada.webp
---

Le tue stampanti sono in laboratorio, ma tu non sempre. E per sapere se una sta
ancora stampando, se è venuta bene o se le resta materiale, devi esserci davanti.

Per questo c'è l'**agente locale**: un piccolo programma che gira su un computer
del tuo laboratorio, parla con le tue stampanti tramite la tua rete e comunica a
BolloPrint quello che vede.

- **Non tocchi il router**: niente porte aperte, niente IP fisso, niente firewall.
- **È molto leggero**: gli va bene qualsiasi computer che hai già acceso.
- **Ne basta uno per tutto il parco macchine**, di qualsiasi dimensione.

::animation{id="local-agent"}

## Dove installarlo

L'agente vive su **qualsiasi computer del laboratorio che non spegni**: un NAS, un
mini-PC, un Raspberry Pi o il PC del laboratorio. Gli basta che sia **sempre
acceso** e che abbia **Docker**.

L'ideale è che sia **nella stessa rete delle stampanti**, perché così le trova da
solo. Se non è possibile, le aggiungi a mano e funzionano allo stesso modo.

## Crea l'agente in BolloPrint

Si parte da BolloPrint. Vai su **Impostazioni → Stampanti**, apri la scheda
**Agente locale** e premi **Nuovo agente**.

Dagli un nome che ti dica ancora qualcosa tra sei mesi: **chiamalo in base a dove
si trova, non a cosa è**. «Piano terra» o «Capannone 2» vanno bene; «Agente 1»,
no.

![La scheda Agente locale, con il pulsante Nuovo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Copia il modello

Quando lo crei, BolloPrint ti mostra un **modello**: un testo che contiene **già
scritto** tutto quello che è tuo, le chiavi del tuo agente e la versione giusta.
Non c'è niente da sostituire né da compilare.

Scegli il formato che usi (**Docker Compose** è quello abituale) e premi
**Copia**.

![Il modello di deploy, con il pulsante per copiarlo](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Copialo adesso: si vede una sola volta
Le chiavi non scadono, ma non te le mostriamo più. Se perdi il modello, apri
l'agente e usa **Rigenera le chiavi** per ottenerne uno nuovo.
:::

## Incolla il modello sul tuo computer

Questo si fa sul tuo computer, non in BolloPrint, e dipende da dove lo installi:

- **NAS Synology**: installa **Container Manager** dal **Centro pacchetti**, vai
  su **Progetto → Crea**, incolla il modello e crea il progetto. Senza scrivere
  nessun comando.
- **Windows o Mac**: installa **Docker Desktop**, salva il modello in una cartella
  come `docker-compose.yml` e, da quella cartella, esegui
  `docker compose up -d`.
- **Linux**: installa **Docker** con il gestore di pacchetti della tua
  distribuzione, salva il modello come `docker-compose.yml` ed esegui lì
  `docker compose up -d`.
- **Portainer**: incolla lo stesso modello in uno stack e fai il deploy.

:::info 💡 Su Windows e Mac, le stampanti non vengono trovate da sole
Lì Docker gira dentro una macchina virtuale, che non vede gli annunci che le
stampanti mandano alla tua rete. L'agente funziona uguale, ma le stampanti le
aggiungi tu, come spiegato più sotto.
:::

## Controlla che sia online

Torna in BolloPrint: in meno di un minuto, l'agente passa a **Online**.

![L'agente nello stato Online](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Se non succede, quasi sempre è per una di tre cause: il modello **incollato a
metà**, il computer **senza internet** oppure un **firewall** che blocca l'uscita.

## Le tue stampanti compaiono da sole

Da quel momento, l'agente **cerca le stampanti nella tua rete** per conto suo ogni
15 minuti. Quelle che trova compaiono in un elenco con la loro marca e il loro
modello, e decidi tu:

- **Aggiungi**: la registri e inizia a inviare dati.
- **Ignora**: non è tua o non la vuoi qui.

![Le stampanti trovate nella rete, con i pulsanti per aggiungere e ignorare](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Se hai appena acceso una macchina e non vuoi aspettare, premi **Cerca ora**.
Alcune marche chiedono una **password** quando aggiungi la stampante; lo vediamo
più sotto.

## Se qualcuna non compare, aggiungila tu

Che una stampante non compaia da sola è **normale** in due casi:

- **È in un'altra rete.** Gli annunci delle stampanti non passano da una rete
  all'altra.
- **L'agente gira su Windows o Mac.** Lì Docker gira in una macchina virtuale.

Non ci perdi niente: la aggiungi tu e funziona esattamente uguale, con telecamera
e comandi se quella macchina li ha. Premi **Aggiungi per IP** e indica il tipo di
stampante, il suo indirizzo nella tua rete e, se la chiede, la sua password.

![Il modulo per aggiungere una stampante tramite il suo IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Riservale l'IP nel router
Se il router cambia l'indirizzo a una stampante, la ritroviamo da soli, ma per
un po' resterà offline. Riservarle l'indirizzo evita quel buco. È
un'impostazione del router, non di BolloPrint.
:::

## Cosa ti chiede ogni marca

È qui che nascono più dubbi. In sintesi:

| Marca | Cosa devi fare sulla macchina | Telecamera | Puoi mettere in pausa e annullare? |
|---|---|---|---|
| **Bambu Lab** | Attivare la **Modalità LAN** dal suo schermo e usare il **codice di accesso** che ti mostra | Sì | Sì, se attivi anche la **Modalità sviluppatore** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Usare la **password** che mostra la stampante stessa | Non ancora | Sì |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Di solito niente: in genere si collega senza password | Sì, se hai una webcam sul tuo Klipper | Sì |
| **Elegoo a resina** (Mars, Saturn, Jupiter) | Niente, non chiede password | Nei modelli che ce l'hanno | Sì |
| **Elegoo Centauri Carbon 2** | Solo se gli hai impostato tu un codice dal suo schermo | Sì | Non ancora |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Attivare **LAN Only** e usare il codice del suo schermo | Sì | Non ancora |

:::warning ⚠️ Bambu Lab: il codice di accesso cambia
Ogni volta che attivi o disattivi la Modalità LAN, Bambu **genera un codice
nuovo**. Se una Bambu che andava bene smette all'improvviso di collegarsi, nove
volte su dieci il motivo è questo: guarda di nuovo il codice sul suo schermo e
aggiornalo in BolloPrint.
:::

:::info 💡 Non trovi il tuo modello nella tabella?
Consulta le [stampanti compatibili](/help/impresoras-compatibles). Se ha
**Klipper** dentro (qualsiasi macchina autocostruita o modificata), è
compatibile anche se la marca non compare in nessun elenco.
:::

## Cosa ti offre l'agente locale

Con l'agente in funzione, ottieni:

- **Quasi tutte le marche**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron… Il cloud non lo offre, perché esiste solo per Bambu Lab.
- **Telecamera**: in diretta mentre hai la pagina aperta, una foto quando vuoi e
  una foto finale salvata nello storico di ogni stampa. Non è videosorveglianza:
  non si registra niente.
- **Comandi**: mettere in pausa, riprendere e annullare da BolloPrint, senza
  andare fino alla macchina, in quelle che lo permettono (guarda la tabella qui
  sopra). Su Bambu Lab, con la stampante in **Modalità LAN** e **Modalità
  sviluppatore**.
- **Resistenza ai cali di internet**: se la tua linea cade, l'agente **continua a
  leggere le stampanti e salva quello che succede**. Quando la connessione torna
  manda tutto, e non perdi quelle ore di storico.
- **Indipendenza dal produttore** e dal fatto che il suo cloud continui a
  funzionare.

Quello che nessuna via permette è **mandare lavori in stampa**: il file continui a
inviarlo dal tuo slicer.

## Domande frequenti

I dubbi che ci arrivano più spesso.

### Devo aprire porte nel router?

No. Né porte, né IP fisso, né regole del firewall. Funziona dietro un normale
router di casa.

### Serve un agente per ogni stampante?

No. **Uno solo gestisce tutto il parco macchine.** Ha senso averne più di uno solo
se hai due sedi o due reti separate.

### Cosa succede se spengo il computer o esce una nuova versione?

Quando lo riaccendi, l'agente riparte da solo. Si aggiorna anche da solo: quando
esce una nuova versione la scarica e si riavvia con quella. Dovrai fare qualcosa
solo se te lo segnaliamo sullo schermo.

:::info 💡 Ti serve aiuto?
Scrivici dalla [pagina dei contatti](/contact) o apri un thread sul
[nostro Discord](/help/soporte-por-discord). Se ci dici che stampanti hai, ti
diciamo esattamente cosa fare con ognuna.
:::

Buon lavoro con tutto il tuo parco macchine sotto controllo, ovunque tu sia.

![Bollo, la mascotte di BolloPrint, con gli occhialini da officina, davanti a una farm di stampanti 3D al lavoro](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp)

## Documentazione correlata

- [Collegare le stampanti](/help/conectar-impresoras): le due vie e quale ti conviene
- [L'agente locale](/help/el-agente-local): il riferimento completo
- [Installare l'agente](/help/desplegar-el-agente): il dettaglio tecnico, se ti serve
- [Tipi di connessione](/help/tipos-de-conexion): cosa permette ogni famiglia di stampanti
- [Stampanti compatibili](/help/impresoras-compatibles): cerca qui il tuo modello
