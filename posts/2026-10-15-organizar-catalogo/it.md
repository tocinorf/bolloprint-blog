---
slug: organize-your-3d-printing-catalog
title: "Dai file STL ai prodotti del tuo negozio: come organizzare il tuo catalogo di stampa 3D"
description: Scopri come strutturare i tuoi file STL, calcolare i costi di ogni pezzo e creare le varianti dei prodotti per il tuo negozio di stampa 3D senza complicazioni.
date: 2026-10-18
tags: [tutorial]
cover: 01-portada.webp
---

Se stampi in 3D per vendere, conosci di sicuro questa scena: decine di cartelle
sul computer con file chiamati `llavero_V2_FINAL_definitivo.stl`, senza ricordare
quanto filamento consumava quella versione né quale profilo di slicing hai usato.
E quando arriva un ordine su Etsy, calcoli i costi a occhio e speri di non
perderci.

In un laboratorio o in una farm di stampa 3D, il disordine tecnico e quello
commerciale si intrecciano se non li tieni separati. Per questo BolloPrint li
gestisce separatamente. In questa guida ti spieghiamo come si incastrano
**Design, Pezzi, Prodotti e Varianti**, così passi da un mucchio di file sparsi a
un catalogo ordinato.

::animation{id="how-it-works"}

## Separa la parte tecnica da quella commerciale

Uno degli errori più comuni nella gestione di un laboratorio è trattare un file
STL come se fosse il prodotto che vendi. In pratica, uno stesso modello 3D si può
stampare in materiali diversi, essere composto da più parti o essere venduto in
confezioni multiple.

Per questo BolloPrint organizza il tuo catalogo su tre livelli.

### Design: la libreria tecnica

Il **Design** è il contenitore dei tuoi file sorgente: gli STL, gli OBJ o i
progetti 3MF, insieme alle foto del modello e alle tue note interne.

- **Pensa al Design come al progetto o all'idea.** Non contiene tempi né grammi di
  filamento, perché uno stesso STL si può stampare a scale diverse o con materiali
  diversi.

![Il design «Keyring BolloPrint», con il suo file STL, la sua foto, le sue note interne e i suoi due pezzi: da 5 cm e da 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Pezzi: l'oggetto fisico

Un **Pezzo** è il risultato di prendere un Design e dargli una configurazione di
stampa concreta: il materiale e il suo consumo (per esempio, PLA nero), le misure
e il tempo di stampa.

- **Un Design, più Pezzi.** Con lo stesso STL puoi stampare una statuina in due
  misure, 5 cm e 10 cm: quel Design avrà due Pezzi, «Portachiavi piccolo» e
  «Portachiavi grande». Lo stesso vale per colori o materiali diversi.
- **Il tuo file di slicing fa i conti.** Se carichi nel Pezzo il file dello slicer
  (`.gcode`, `.gcode.3mf`, `.bgcode` o `.goo` per la resina), BolloPrint legge il
  peso e il tempo di stampa e te li propone. Quando li applichi, calcola quanto ti
  costa produrre esattamente quel pezzo. Puoi anche inserire o correggere i dati a
  mano.

:::info 💡 Un 3MF di progetto qui non va bene
Per conoscere il peso e il tempo, lo slicer deve aver già processato il piatto. Un
`.3mf` di progetto non li contiene: va nel Design. Nel Pezzo carica il
`.gcode.3mf` esportato dallo slicer.
:::

### Prodotti e Varianti: quello che il tuo cliente vede e compra

Il **Prodotto** è la tua vetrina: quello che pubblichi nel tuo negozio o in un
marketplace come Etsy. La **Variante** è l'opzione concreta che sceglie il
cliente.

- **Una Variante può avere uno o più Pezzi**, ognuno con la sua quantità.
- **Per esempio:** il tuo Prodotto è «Statuina di Bollo», il nostro cane. Una
  Variante può essere «Verde», un'altra «Arancione» e un'altra la confezione
  «Verde + Arancione», con i due Pezzi dentro. Puoi combinare materiali, misure,
  finiture o lotti come preferisci.

![La variante Green+Orange, con i suoi due pezzi dentro, uno arancione e uno verde, e il suo costo, il suo margine e il suo prezzo](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

:::info 💡 Un pack può combinare più Design
Una Variante può contenere Pezzi di Design diversi: per esempio, un «Pack ufficio»
con il supporto telefono e l'organizer per cavi.
:::

- **Il margine si calcola da solo.** Dato che ogni Variante sa di quali Pezzi è
  fatta, BolloPrint confronta il tuo prezzo di vendita con il costo reale di
  produzione e ti mostra il margine. Se cambi il prezzo, il margine si aggiorna, e
  viceversa.

![La variante Green, con un solo pezzo: costo di 7,06 €, margine del 70 % e prezzo di 23,54 €](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## Hai fretta? Usa la Creazione rapida

Se stai iniziando o hai centinaia di modelli da caricare, configurare Design, Pezzi
e Prodotti uno per uno richiede tempo.

Per questo c'è il pulsante **Creazione rapida** del
catalogo. In una sola schermata carichi il tuo file 3D, indichi il materiale, il
peso, il tempo e il prezzo, e BolloPrint crea in un colpo solo il Design, il Pezzo,
il Prodotto e la sua Variante. Il risultato è lo stesso che otterresti procedendo
passo dopo passo, quindi dopo puoi rifinire quello che vuoi.

![Il modulo di Creazione rapida: il file 3D, le foto, il materiale, il peso, il tempo, i colori, il costo e il prezzo](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## I tuoi tag passano da soli al prodotto

Un altro dettaglio che ti risparmia lavoro: i **tag** (etichette) di un Design
passano da soli ai suoi Prodotti.

Se assegni a un Design il tag «Portachiavi» o «Statuine», quando aggiungi i suoi
Pezzi a una Variante, quei tag si aggiungono al Prodotto. E se vendi su Etsy,
quando pubblichi l'inserzione li trovi già inseriti come *tag*, che aiutano i
clienti a trovarti. Etsy ne accetta fino a 13, di 20 caratteri al massimo, e puoi
ritoccarli prima di pubblicare.

## Inizia a mettere in ordine il tuo catalogo

Avere un catalogo ben organizzato non è solo una questione di ordine: è il modo
per sapere quanto ti costa ogni pezzo, quanto guadagni su ogni ordine e per far
crescere il tuo laboratorio senza perdere il controllo.

Se vuoi vedere più nel dettaglio come configurare il tuo catalogo o creare varianti
avanzate, dai un'occhiata alla
[documentazione del catalogo](/help/catalogo). E se ti chiedi da dove viene il
costo di ogni Pezzo, lo spieghiamo in
[quanto costa davvero un pezzo stampato](/blog/calculate-your-3d-printing-costs).

Scopri [come controllare la produzione del tuo laboratorio con BolloPrint](/features),
il tuo software per farm di stampa 3D.

Che il tuo catalogo cresca ordinato come quando è nato.

![Bollo, la mascotte di BolloPrint, con gli occhiali da laboratorio, accanto al suo modello 3D in wireframe](/blog/media/2026-10-15-organizar-catalogo/07-bollo.webp "60%")

## Documentazione correlata

- [Catalogo](/help/catalogo): i livelli del catalogo, nel riferimento
- [Design](/help/disenos): i file, le foto e i tag
- [Pezzi](/help/piezas): il materiale, il file di slicing e il costo
- [Prodotti e Varianti](/help/productos-y-variantes): il prezzo, il margine e i pezzi di ogni variante
- [Creazione rapida](/help/creacion-rapida): tutto in un colpo solo
- [Tag](/help/etiquetas): come si creano e si gestiscono
