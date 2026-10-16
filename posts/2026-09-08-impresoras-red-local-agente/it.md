---
slug: connect-printers-local-network-agent
title: "Collega le tue stampanti tramite la tua rete: l'agente locale, passo passo"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper… Un piccolo agente su un computer del laboratorio, tutto il tuo parco macchine dentro BolloPrint e senza toccare il router.
date: 2026-10-12
updated: 2026-10-16
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
- **Si aggiorna da solo**: quando esce una nuova versione, la installa lui.

::animation{id="local-agent"}

## Dove installarlo

L'agente vive su **qualsiasi computer del laboratorio che non spegni**: un NAS, un
mini-PC, un Raspberry Pi o il PC del laboratorio. Gli basta che sia **sempre
acceso** e che abbia **Docker**.

L'ideale è che sia **nella stessa rete delle stampanti**, perché così le trova da
solo. Se non è possibile, le aggiungi a mano e funzionano allo stesso modo.

## Crea l'agente in BolloPrint

Si parte da BolloPrint. Vai su **Impostazioni → Stampanti**. Vedrai tre schede:
**Stampanti** (tutte le tue macchine, comunque siano collegate), **Agente locale**
e **Bambu Cloud**. Apri **Agente locale** e premi **Nuovo agente**.

Dagli un nome che ti dica ancora qualcosa tra sei mesi: **chiamalo in base a dove
si trova, non a cosa è**. «Piano terra» o «Capannone 2» vanno bene; «Agente 1»,
no. Poi premi **Crea agente**.

![La scheda Agente locale, con due agenti online e il pulsante Nuovo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-it.png)

## Copia il manifesto

Quando lo crei, BolloPrint ti mostra un **manifesto**: un testo che contiene **già
scritto** tutto quello che è tuo, le chiavi del tuo agente e la versione giusta.
Non c'è niente da sostituire né da compilare.

Scegli il formato che usi (**Docker Compose** è quello abituale), premi **Copia**
e, quando l'hai messo al sicuro, **Salva**.

![Il manifesto di installazione del nuovo agente, con il pulsante Copia](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-it.png "75%")

:::warning 🔐 Copialo adesso: le chiavi si vedono una sola volta
Non le conserviamo, quindi non possiamo mostrartele di nuovo. Se perdi il
manifesto, niente di grave: apri l'agente con **Modifica** (nel suo menu **⋮**),
vai alla scheda **Installazione** e premi **Rigenera le chiavi**. Se non si è mai
collegato, non si interrompe nulla.
:::

## Incolla il manifesto sul tuo computer

Questo si fa sul tuo computer, non in BolloPrint, e dipende da dove lo installi:

- **NAS Synology**: installa **Container Manager** dal **Centro pacchetti**, vai
  su **Progetto → Crea**, incolla il manifesto e crea il progetto. Senza scrivere
  nessun comando.
- **Windows o Mac**: installa **Docker Desktop**, salva il manifesto in una
  cartella come `docker-compose.yml` e, da quella cartella, esegui
  `docker compose up -d`.
- **Linux**: installa **Docker** con il gestore di pacchetti della tua
  distribuzione, salva il manifesto come `docker-compose.yml` ed esegui lì
  `docker compose up -d`.
- **Portainer**: incolla lo stesso manifesto in uno stack e fai il deploy.

:::info 💡 Su Windows e Mac, le stampanti non vengono trovate da sole
Lì Docker gira dentro una macchina virtuale, che non vede gli annunci che le
stampanti mandano alla tua rete. L'agente funziona uguale, ma le stampanti le
aggiungi tu, come spiegato più sotto.
:::

## Ti sei bloccato? Premi «Installa»

Finché l'agente non si è collegato almeno una volta, la sua riga dice **Non
installato**. Non è un errore: non è caduto niente, manca solo l'installazione.

Su quella stessa riga hai il pulsante **Installa**. Premendolo si aprono i passi
che hai appena letto, in breve, con un link all'**Aiuto**, un altro a questo
**Articolo del blog** e un pulsante per chiederci aiuto su **Discord**. Se non hai
conservato il manifesto, il passo 3 ti porta dritto a generarne uno nuovo.

![Un agente non installato con il pannello Installa aperto: i tre passi, l'aiuto e Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-it.png)

## Controlla che sia online

Torna in BolloPrint: in meno di un minuto, l'agente passa a **Online**, con il
nome del computer su cui gira e la versione che ha.

![L'agente nello stato Online](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-it.png)

Se non succede, quasi sempre è per una di tre cause: il manifesto **incollato a
metà**, il computer **senza internet** oppure un **firewall** che blocca l'uscita.
Se vuoi vedere cosa racconta l'agente stesso, aprilo con **Modifica**: la scheda
**Stato** ti dà i dettagli.

## Le tue stampanti compaiono da sole

Da quel momento, l'agente **cerca le stampanti nella tua rete** per conto suo ogni
15 minuti. Quando ne trova una, ti avvisa sopra le schede e la vedi in fondo a
**Stampanti in rete locale**, con la sua marca e il suo modello. Decidi tu:

- **Aggiungi**: la registri e inizia a inviare dati.
- **Ignora**: non è tua o non la vuoi qui.

![Una stampante rilevata dall'agente, con i pulsanti Ignora e Aggiungi, e sopra Cerca ora e Aggiungi per IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-it.png)

Se hai appena acceso una macchina e non vuoi aspettare, premi **Cerca ora**. Se
una stampante ti chiederà un codice, la sua riga te lo dice prima («chiederà il
codice di accesso»), così lo tieni a portata di mano.

## Se qualcuna non compare, aggiungila tu

Che una stampante non compaia da sola è **normale** in due casi:

- **È in un'altra rete.** Gli annunci delle stampanti non passano da una rete
  all'altra.
- **L'agente gira su Windows o Mac.** Lì Docker gira in una macchina virtuale.

Non ci perdi niente: la aggiungi tu e funziona esattamente uguale, con telecamera
e comandi se quella macchina li ha. Premi **Aggiungi per IP**. Sono tre passi.

### 1. Scegli la marca

Scegli la marca della tua stampante: ognuna ha la sua scheda, e quelle con il logo
vengono prima. Non serve sapere come comunica la tua macchina: ci pensiamo noi.
Se scegli **Elegoo**, ti chiediamo **Quale Elegoo hai?**, perché ha più famiglie.
**Klipper** e **Altra a resina (ChituBox)** sono in fondo, in **Generiche**, per una
macchina autocostruita o una marca che non è nell'elenco.

Se non sei sicuro che il tuo modello vada bene, in fondo hai **Non ne sei sicuro?
Guarda l’elenco delle compatibili**; e se la tua stampante non c'è, diccelo su
Discord.

![Il primo passo di Aggiungi stampante per IP: le marche che puoi collegare](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-it.png)

### 2. Inserisci i suoi dati

Solo l'indispensabile:

- **Quale agente la collega?**, se ne hai più di uno. Puoi scegliere solo un
  agente online.
- **IP della stampante**. La trovi sullo schermo della stampante (Impostazioni →
  Rete) o nel tuo router.
- **Il codice della stampante**, se quella marca lo chiede. Il campo si chiama
  come lo chiama il produttore: su una Bambu, **Codice di accesso LAN**.
- **Nome**, se vuoi dargliene uno tuo. È facoltativo.

Il **modello e il numero di serie non li scrivi**: li chiede l'agente alla
stampante. I campi obbligatori hanno un **asterisco rosso** e restano bordati di
rosso finché sono vuoti. In fondo, il riquadro **Ricorda** ti dice cosa preparare
su quella marca prima di collegarla.

![Il secondo passo: l'agente, l'IP, il codice di accesso LAN obbligatorio e il riquadro Ricorda](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-it.png)

### 3. Collega

Premi **Collega** e vedrai come procede: l'agente riceve la richiesta, cerca la
stampante a quell'indirizzo e si collega. Alla fine vedrai **«Collegata. Ora è
nel tuo elenco di stampanti.»**

![Il terzo passo: la stampante collegata e già nell'elenco](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-it.png)

Se qualcosa va storto, te lo diciamo **con parole semplici**: cosa sta succedendo
e cosa controllare (a quell'IP non risponde niente, la stampante rifiuta il
codice…). Con **Indietro** correggi il dato e riprovi. Il messaggio originale
della stampante resta ripiegato in **Mostra dettaglio tecnico**: se ci scrivi,
copiacelo e arriviamo prima alla soluzione.

:::info 💡 Riservale l'IP nel router
Se il router cambia l'indirizzo a una stampante, la ritroviamo da soli, ma per
un po' resterà offline. Riservarle l'indirizzo evita quel buco. È
un'impostazione del router, non di BolloPrint.
:::

## Cosa ti chiede ogni marca

È qui che nascono più dubbi. È lo stesso che ti ricorda il passo 2, in sintesi:

| Marca | Cosa devi fare sulla macchina | Telecamera | Puoi mettere in pausa e annullare? |
|---|---|---|---|
| **Bambu Lab** | Attivare la **Modalità LAN** dal suo schermo (Impostazioni → Rete) e usare il **codice di accesso LAN** che ti mostra | Sì | Sì, se attivi anche la **Modalità sviluppatore** |
| **Prusa** (beta: MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Attivare **PrusaLink** e usare la **password** che mostra (non è quella di Prusa Connect) | No | Sì |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) e **altre a resina (ChituBox)** | Niente, non chiedono password | Nei modelli che ce l'hanno | Sì |
| **Elegoo Centauri Carbon 2** | Niente; solo se le hai impostato un codice dal suo schermo, scrivilo | Sì | No |
| **Anycubic** (beta: Kobra 3, Kobra S1, Kobra 4, Kobra X) | Attivare la **Modalità LAN** (Impostazioni → Rete). Così la stampante smette di usare il cloud e l'app di Anycubic | No | No |
| **FlashForge** (beta: Adventurer 5M, 5M Pro, AD5X, Creator 5) | Attivare **LAN Only** e usare il codice di verifica del suo menu di rete | Sì | No |
| **Snapmaker** (U1) | Niente | Sì | Sì |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Di solito niente: solo se hai impostato una chiave API in Moonraker | Sì, se hai una webcam sul tuo Klipper | Sì |

:::warning ⚠️ Bambu Lab: il codice di accesso cambia
Ogni volta che attivi o disattivi la Modalità LAN o la Modalità sviluppatore,
Bambu **genera un codice nuovo**. Se una Bambu che andava bene smette
all'improvviso di collegarsi, nove volte su dieci il motivo è questo: guarda di
nuovo il codice sul suo schermo e aggiornalo in BolloPrint. E tieni presente che
la **Modalità sviluppatore** la scollega da Bambu Cloud: da quel momento la vedrai
solo tramite l'agente.
:::

:::info 💡 Non trovi il tuo modello nella tabella?
Consulta le [stampanti compatibili](/help/impresoras-compatibles). Se ha
**Klipper** dentro (qualsiasi macchina autocostruita o modificata), è
compatibile anche se la marca non compare in nessun elenco.
:::

## Cosa ti offre l'agente locale

Con l'agente in funzione, ottieni:

- **Quasi tutte le marche**: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge,
  Snapmaker e tutto ciò che monta Klipper. Il cloud non lo offre, perché esiste
  solo per Bambu Lab.
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
se hai due sedi o due reti separate. In quel caso, **Aggiungi per IP** ti chiede
quale la collega.

### Cosa succede se spengo il computer o esce una nuova versione?

Quando lo riaccendi, l'agente riparte da solo. Si aggiorna anche da solo: quando
esce una nuova versione la scarica e si riavvia con quella, senza che tu debba
toccare il manifesto. Dovrai fare qualcosa solo se te lo segnaliamo sullo schermo.

### Perché non riesco a premere «Aggiungi per IP»?

Perché nessuno dei tuoi agenti è collegato, e te lo dice il testo sotto il
pulsante. Se non l'hai ancora installato, usa **Installa** sulla sua riga; se
funzionava già, controlla che il computer sia acceso e abbia internet.

:::info 💡 Ti serve aiuto?
Scrivici dalla [pagina dei contatti](/contact) o apri un thread sul
[nostro Discord](/help/soporte-por-discord). Se ci dici che stampanti hai, ti
diciamo esattamente cosa fare con ognuna.
:::

Buon lavoro con tutto il tuo parco macchine sotto controllo, ovunque tu sia.

![Bollo, la mascotte di BolloPrint, con gli occhialini da officina, davanti a una farm di stampanti 3D al lavoro](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Documentazione correlata

- [Collegare le stampanti](/help/conectar-impresoras): le due vie e quale ti conviene
- [L'agente locale](/help/el-agente-local): il riferimento completo
- [Installare l'agente](/help/desplegar-el-agente): il dettaglio tecnico, se ti serve
- [Tipi di connessione](/help/tipos-de-conexion): cosa permette ogni famiglia di stampanti
- [Stampanti compatibili](/help/impresoras-compatibles): cerca qui il tuo modello
