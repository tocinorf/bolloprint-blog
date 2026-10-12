---
slug: connect-bambu-lab-printers-cloud
title: "Collega le tue stampanti Bambu Lab a BolloPrint in cinque minuti"
description: Senza installare niente. Colleghi il tuo account Bambu Lab, confermi un codice e le tue stampanti compaiono da sole, con quello che stanno stampando e tutto il loro storico.
date: 2026-09-08
updated: 2026-10-12
tags: [tutorial]
cover: 01-portada.webp
draft: true
---

Se hai diverse Bambu al lavoro, probabilmente conosci la routine: per sapere
come stanno andando, vai da ognuna e guardi il suo schermo. La prima ha finito?
Alla seconda resta materiale? Quante ore hai stampato questo mese?

Puoi avere tutto questo in un'unica schermata e **senza installare niente**.
Colleghi il tuo account Bambu Lab a BolloPrint e le tue stampanti compaiono da
sole. Bastano circa cinque minuti.

::animation{id="bambu-cloud"}

## Cosa vedrai di ogni stampante

In tempo reale e senza toccare niente:

- se è accesa e collegata;
- cosa sta stampando, la **percentuale** raggiunta e quanto le manca;
- le temperature di ugello e piano;
- i **materiali** caricati, vassoio per vassoio, se hai l'AMS;
- gli avvisi della macchina stessa.

E quello che si nota di più a fine mese: **ogni stampa viene registrata**, con la
sua durata, il suo materiale e il suo costo. Non devi annotare niente.

![La scheda di una stampante in stampa, con l'avanzamento e le temperature](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## Cosa ti serve

Prima di iniziare, tieni a portata di mano queste tre cose:

- L'accesso a BolloPrint come **Proprietario** o **Admin**. Con un altro ruolo
  questa schermata non compare.
- L'**email e la password** del tuo account Bambu Lab.
- La **casella email** di quell'account aperta: Bambu ti manderà un codice.

:::warning ⚠️ Se entri in Bambu con Google, Apple o Facebook
BolloPrint ha bisogno dell'**email e della password** dell'account. Se non hai
mai impostato una password perché usi sempre «Continua con Google», creala prima
sul sito di Bambu Lab e poi torna qui.
:::

## Apri la schermata delle stampanti

Tutto si fa da un unico punto: **Impostazioni → Stampanti**. Lì vedrai tre
schede:

- **Stampanti**: l'elenco di tutte le tue macchine, da qualunque via arrivino.
- **Agente locale**: per collegarle tramite la tua rete. Lo spieghiamo in
  [un altro articolo](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: quella che ti serve adesso.

Apri **Bambu Cloud**.

![La schermata Impostazioni → Stampanti con le sue tre schede](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Scrivi l'email e la password di Bambu

Usa quelle del tuo account Bambu Lab (quell'email, non un'altra tua) e premi
**Connetti con BambuLab**.

![Il modulo di Bambu Cloud, con l'email dell'account inserita e la password ancora da scrivere](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 La tua password non viene salvata
Resta **solo nel tuo browser**, e solo finché non finisci la verifica.
:::

## Conferma il codice dell'email

Bambu ti manderà un **codice di 6 cifre** da `noreply@bambulab.com`. Se non lo
vedi, **controlla la cartella dello spam**: spesso finisce lì. Inseriscilo nella
stessa schermata e premi **Verifica e connetti**.

![Il campo del codice di 6 cifre e il pulsante Verifica e connetti](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Due dettagli ti risparmiano un secondo tentativo:

- Il codice **scade in circa 5 minuti**. Se è scaduto, premi **Rinvia codice**.
- Puoi **incollarlo così come arriva**: spazi e trattini vengono rimossi
  automaticamente.

Quando lo accetta, vedrai **Account verificato e connesso**.

## Le tue stampanti sono già dentro

Non serve registrarle una a una: **tutte le stampanti di quell'account compaiono
da sole** nella scheda **Stampanti**, ognuna con il suo nome e il suo numero di
serie.

![L'elenco delle stampanti con le macchine Bambu appena comparse](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

In alto vedrai un contatore come `3 / 6 attive`: sono le stampanti incluse nel
tuo piano. Con l'interruttore di ogni riga attivi o disattivi quelle che vuoi.
Una stampante disattivata non conta per il limite, ma **conserva tutto il suo
storico**. E se colleghi un intero parco macchine e non ci sono posti per tutte,
quelle che non ci stanno entrano disattivate invece di superare il limite del tuo piano.

## Cosa non puoi fare tramite il cloud

Conviene saperlo fin dall'inizio, per non cercare opzioni che non esistono:

- **È in sola lettura.** Tramite il cloud non puoi mettere in pausa, riprendere
  né annullare da BolloPrint: Bambu accetta questi comandi solo dalla tua rete
  locale e con la stampante in una modalità specifica. Lo vediamo alla fine.
- **Non c'è la telecamera.** Vedi però l'immagine di slicing del lavoro, che è
  un'anteprima, non quello che succede dentro la macchina.
- **Dipende da due connessioni internet**, la tua e quella di Bambu. Se una delle
  due cade, la stampante risulta scollegata anche se sta stampando normalmente.
- **La sessione scade ogni tanto** e bisogna ricollegare l'account. Te lo
  segnaliamo sullo schermo.

E una cosa che vale per qualsiasi tipo di connessione: **BolloPrint non manda
lavori in stampa**. Il file continui a inviarlo dal tuo slicer; BolloPrint legge
cosa fa la macchina e lo registra.

## Problemi frequenti

### Perché Bambu dice che la password è errata se è quella giusta?

È il problema più comune. Il messaggio **«Account o password di Bambu Lab
errati»** compare quasi sempre con una password appena creata e mai usata:
l'account ha l'email ancora da verificare e Bambu non lo segnala. Entra **una
volta** sul sito di Bambu con quell'email e quella password, completa quello che
ti chiede e riprova.

### E se entri in Bambu con Google o Apple?

Per quella via non si può. Crea una password sul sito di Bambu Lab e usa l'email
con quella password.

### Perché dice che non esiste un account con quell'email?

Se compare **«Non esiste alcun account Bambu Lab con questa email»**, l'email non
è quella del tuo account Bambu. Controlla con quale entri nella sua app.

### Cosa faccio se mi chiede la verifica in due passaggi?

Dovrai disattivarla nel tuo account Bambu per poterlo collegare.

### Cosa faccio se il codice non arriva o non viene accettato?

Se non arriva, controlla la cartella dello spam e premi **Rinvia codice**. Se non
viene accettato, molto probabilmente è scaduto: chiedine un altro e incollalo
intero.

## Se ti serve di più: l'agente locale

Il cloud ti mostra tutte le informazioni, ma non ti permette di intervenire sulle
stampanti, ed esiste solo per Bambu Lab. Se ti serve di più, l'opzione è
l'**agente locale**: un piccolo programma che installi su un computer del tuo
laboratorio e che comunica con le stampanti tramite la tua rete. Ne basta uno per
tutto il parco macchine, e ti offre:

- **quasi tutte le marche**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron…;
- la **telecamera**, in diretta e con una foto finale salvata a ogni stampa;
- **mettere in pausa, riprendere e annullare** da BolloPrint, senza andare fino
  alla macchina;
- **resistenza alle interruzioni di internet**: continua a leggere le tue
  stampanti e invia tutto quando torna la connessione.

:::info 💡 Per mandare comandi a una Bambu
La stampante deve essere in **Modalità LAN** e in **Modalità sviluppatore**.
Entrambe si attivano dal suo schermo.
:::

Lo spieghiamo passo passo in
[collegare le tue stampanti tramite la tua rete](/blog/connect-printers-local-network-agent).

Per qualsiasi dubbio, scrivici dalla [pagina dei contatti](/contact) o sul
[nostro Discord](/help/soporte-por-discord).

## Documentazione correlata

- [Collegare le stampanti](/help/conectar-impresoras): i due modi per farlo e quale ti conviene
- [Stampanti tramite cloud](/help/impresoras-por-la-nube): il riferimento completo di questa schermata
- [Stampanti compatibili](/help/impresoras-compatibles): cerca qui il tuo modello
- [Tipi di connessione](/help/tipos-de-conexion): cosa permette ogni tipo di stampante
