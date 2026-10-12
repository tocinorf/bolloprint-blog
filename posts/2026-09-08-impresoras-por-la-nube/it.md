---
slug: connect-bambu-lab-printers-cloud
title: "Collega le tue stampanti Bambu Lab a BolloPrint in cinque minuti"
description: Senza installare niente. Colleghi il tuo account Bambu e le tue macchine compaiono da sole, con quello che stanno stampando e tutto il loro storico.
date: 2026-09-08
updated: 2026-10-12
tags: [tutorial]
cover: 01-portada.webp
draft: true
---

Hai tre Bambu al lavoro e, per sapere come stanno andando, ti alzi e guardi lo
schermo di ognuna. La prima avrà finito? Alla seconda resta materiale? Quante
ore hai stampato questo mese?

C'è un modo per vedere tutto da un solo schermo, e **non bisogna installare
niente**. Colleghi il tuo account Bambu Lab a BolloPrint e le tue macchine
compaiono da sole. Cinque minuti.

::animation{id="bambu-cloud"}

## Ecco cosa avrai

Di ogni stampante, in diretta e senza toccare niente:

- se è accesa e collegata;
- cosa sta stampando, la **percentuale** e quanto le manca;
- le temperature di ugello e piano;
- i **materiali** caricati, vassoio per vassoio, se hai l'AMS;
- gli avvisi della macchina stessa.

E in più, quello che fa davvero la differenza a fine mese: **ogni stampa viene
registrata**, con la sua durata, il suo materiale e il suo costo. Senza annotare
niente a mano.

![La scheda di una stampante in stampa, con l'avanzamento e le temperature](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png)

## Cosa ti serve

- Entrare in BolloPrint come **Proprietario** o **Admin**. Con un altro ruolo
  questa schermata non ti compare.
- Il tuo account **Bambu Lab**, con la sua **email e la sua password**.
- Poter aprire l'**email** di quell'account: Bambu ti manderà un codice.

:::warning ⚠️ Se entri in Bambu con Google, Apple o Facebook, questo non ti funzionerà
BolloPrint ha bisogno dell'**email e della password** del tuo account Bambu. Se
non hai mai impostato una password perché premi sempre «Continua con Google»,
creala prima sul sito di Bambu Lab e torna qui con quella.
:::

## Passaggio 1 — Apri la schermata delle stampanti

Vai su **Impostazioni → Stampanti**. Vedrai tre schede:

- **Stampanti** — l'elenco di tutte le tue macchine, da qualunque via arrivino.
- **Agente locale** — per collegarle tramite la tua rete. Quello è [un altro tutorial](/blog/connect-printers-local-network-agent).
- **Bambu Cloud** — quella che ci interessa oggi.

Apri **Bambu Cloud**.

![La schermata Impostazioni → Stampanti con le sue tre schede](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Passaggio 2 — Scrivi l'email e la password di Bambu

Quelle del tuo account Bambu Lab —quell'email, non un'altra tua— e premi
**Connetti con BambuLab**.

![Il modulo di Bambu Cloud, con l'email dell'account inserita e la password ancora da scrivere](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 La tua password non viene salvata
Resta **solo nel tuo browser**, e solo finché non finisci di verificare.
:::

## Passaggio 3 — Inserisci il codice che ti arriva per email

Bambu ti manda un **codice di 6 cifre** da `noreply@bambulab.com`. **Guarda
anche nello spam**: ci finisce più spesso di quanto dovrebbe.

Scrivi le sei cifre nella stessa schermata e premi **Verifica e connetti**.

![Il campo del codice di 6 cifre e il pulsante Verifica e connetti](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Due dettagli che ti risparmiano un secondo tentativo: **il codice scade in circa
5 minuti** —se ci metti troppo, premi **Rinvia codice**— e **incollalo intero
così com'è**: se ha spazi o trattini, vengono ripuliti da soli.

Quando lo accetta, vedrai **Account verificato e connesso**.

## Passaggio 4 — Eccole lì

Non c'è bisogno di registrare le stampanti una a una. **Tutte le macchine di
quell'account compaiono da sole** nella scheda **Stampanti**, ognuna con il suo
nome e il suo numero di serie.

![L'elenco delle stampanti con le macchine Bambu appena comparse](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

In alto c'è un contatore come `3 / 6 attive`: le stampanti incluse nel tuo
piano. Con l'interruttore di ogni riga accendi e spegni quelle che vuoi. Una
spenta non conta per il limite, ma **resta nell'elenco con tutto il suo
storico**.

E se colleghi un intero parco macchine e non ci sono posti per tutte, quelle in
più entrano **disattivate** invece di sforare il tuo piano.

## Cosa NON potrai fare da qui

Meglio saperlo ora che cercare il pulsante per mezz'ora:

- **È in sola lettura.** Dal cloud non si può mettere in pausa, riprendere né
  annullare da BolloPrint: Bambu accetta questi comandi solo dalla tua rete
  locale, e con la stampante in una modalità speciale. Lo vediamo alla fine.
- **Non c'è la telecamera.** Dal cloud non arriva. Arriva invece l'immagine del
  laminato del lavoro, che è l'anteprima, non quello che sta succedendo dentro.
- **Dipende da internet due volte:** dal tuo e da quello di Bambu. Se uno dei
  due viene meno, la stampante appare scollegata anche se sta stampando
  perfettamente.
- **La sessione scade ogni tanto** e bisogna ricollegare l'account. Te lo
  segnaliamo sullo schermo.

E una che vale per tutte le vie: **BolloPrint non manda lavori in stampa**. Il
file continui a inviarlo dal tuo slicer. Quello che facciamo è leggere cosa fa
la macchina e registrarlo.

## Se non riesci a collegarti

| Quello che vedi | Cos'è di solito |
|---|---|
| «Account o password di Bambu Lab errati» e sei sicuro che sia quella giusta | **È l'errore che fa perdere più tempo.** Se hai appena creato quella password e non l'hai mai usata, l'account ha l'email ancora da verificare e Bambu non te lo dice. Entra **una volta** sul sito di Bambu con quelle credenziali, completa quello che ti chiede e torna. |
| «Account o password di Bambu Lab errati» ed entri in Bambu con Google o Apple | Quella via qui non serve. Crea una password sul sito di Bambu. |
| «Non esiste alcun account Bambu Lab con questa email» | L'email non è quella dell'account Bambu. Controlla con quale entri nella sua app. |
| Ti parla di verifica in due passaggi | Devi disattivarla in Bambu per poter collegare l'account. |
| Il codice non arriva | Guarda nello spam e premi **Rinvia codice**. |
| Il codice non viene accettato | Sarà scaduto. Chiedine un altro e incollalo intero. |

## Vuoi di più? Prova l'agente locale

Il cloud ti mostra tutto, ma non ti lascia toccare niente, ed esiste solo per
Bambu Lab. Se vuoi di più, quello che fa per te è l'**agente locale**: un
piccolo programma su un computer del tuo laboratorio che parla con le stampanti
tramite la tua rete. Ne basta uno per tutto il parco macchine, e ti dà:

- **quasi tutte le marche**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron…;
- la **telecamera**, in diretta mentre la guardi e con una foto finale salvata a
  ogni stampa;
- **mettere in pausa, riprendere e annullare** da BolloPrint, senza andare fino
  alla macchina;
- e **resiste ai cali di internet**: continua a leggere le tue stampanti e ti
  racconta tutto quando torna la linea.

:::info 💡 Per mandare comandi a una Bambu
La stampante deve essere in **Modalità LAN** e in **Modalità sviluppatore**.
Entrambe si attivano dal suo schermo. Attenzione: con la Modalità LAN, Bambu la
scollega dal suo cloud, quindi da quel momento BolloPrint la vede tramite
l'agente. Resta comunque **la stessa stampante**, con il suo nome e tutto il suo
storico, e occupa **un solo posto** nel tuo piano.
:::

Lo trovi passo passo nel prossimo tutorial:
[collegare le tue stampanti tramite la rete locale](/blog/connect-printers-local-network-agent).

:::info 💡 Dubbi?
Scrivici dalla [pagina dei contatti](/contact) o apri un thread sul
[nostro Discord](/help/soporte-por-discord).
:::

## Documentazione correlata

- [Collegare le stampanti](/help/conectar-impresoras) — le due vie e quale ti conviene
- [Stampanti tramite cloud](/help/impresoras-por-la-nube) — il riferimento completo di questa schermata
- [Stampanti compatibili](/help/impresoras-compatibles) — cerca qui il tuo modello
- [Tipi di connessione](/help/tipos-de-conexion) — cosa permette ogni famiglia di stampanti
