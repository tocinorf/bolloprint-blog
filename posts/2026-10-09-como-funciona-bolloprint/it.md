---
slug: how-bolloprint-works
title: "Design, Pezzo, Variante, Prodotto: la mappa di BolloPrint in cinque minuti"
description: Le quattro cose che ci sono dietro ogni ordine, a quale domanda risponde ognuna e perché sono quattro e non una sola scheda. Con un supporto per telefono come esempio, dall'inizio alla fine.
date: 2026-10-09
updated: 2026-10-12
tags: [tutorial]
cover: 01-el-mapa.webp
draft: true
---

Arriva un ordine: **due supporti per telefono, bianchi**.

E prima che tu muova un dito, BolloPrint sa già tre cose: **quanto ti costa**
produrli, **quanto ti lascia** venderli e **dove sono i file** per stamparli.

Come fa a saperlo? Perché dietro quella riga dell'ordine ci sono quattro cose
che hai preparato una volta sola: un **Design**, un **Pezzo**, una **Variante**
e un **Prodotto**. Sono le quattro parole che vedrai più spesso in BolloPrint.
Qui ti raccontiamo cos'è ognuna, perché sono quattro e non una, e come finiscono
in un ordine.

::animation{id="how-it-works"}

## Quattro domande, quattro cose

Il modo più facile per non confonderle è pensare alla domanda a cui risponde
ognuna:

| | Risponde a… | Cosa contiene |
|---|---|---|
| **Design** | Cos'è? | I file 3D (STL, 3MF…), le foto e le tue note. Né costo né prezzo. |
| **Pezzo** | Come lo produco? | Il materiale, il colore, la finitura, il peso e il tempo. **Ha un costo.** |
| **Variante** | A quanto lo vendo? | Il prezzo e il margine. **È quello che entra in un ordine.** |
| **Prodotto** | Come lo mostro? | Il nome, le foto e la descrizione. Raggruppa le varianti. |

Se ti ricordi solo questa tabella, hai già metà dell'articolo.

## Lo costruiamo: un supporto per telefono

Prepariamo il supporto dell'ordine, nello stesso ordine in cui lo faresti tu.

**1. Il Design.** Carichi l'STL del supporto e un paio di foto. Questo è il
Design: il modello e niente di più. Non hai ancora deciso in cosa stamparlo,
quindi non ha un costo.

**2. I Pezzi.** Adesso decidi come produrlo. Lo vuoi in **PLA nero** e in **PETG
bianco**: sono due Pezzi dello stesso Design. Ognuno ha il suo materiale, il suo
peso e il suo tempo di stampa, quindi ognuno ha **il suo costo**, e BolloPrint
lo calcola da solo.

![Il dettaglio del design del supporto, con i suoi due pezzi sotto: PLA nero e PETG bianco](/blog/media/2026-10-09-como-funciona-bolloprint/02-diseno-y-piezas.png)

:::info 💡 Un Pezzo dipende sempre da un Design
Per questo non c'è un elenco di Pezzi a sé: li trovi dentro il Design a cui
appartengono.
:::

**3. Le Varianti.** Adesso decidi a quanto venderlo. Crei la Variante «PLA nero»
a **12,90 €** e la Variante «PETG bianco» a **15,90 €**. Ognuna sa di quale
Pezzo è fatta, quindi sa quanto costa, e con il prezzo calcola da sola **il
margine**.

**4. Il Prodotto.** Infine, quello che vede il cliente: il Prodotto «Supporto
telefono regolabile», con il suo nome, le sue foto e la sua descrizione. Dentro
ci sono le due Varianti, come le opzioni di colore di qualsiasi negozio online.
È quello che pubblichi, per esempio, su Etsy.

![Il prodotto Supporto telefono regolabile, con le sue due varianti, ognuna con il suo prezzo e il suo margine](/blog/media/2026-10-09-como-funciona-bolloprint/03-producto-y-variantes.png)

## Perché quattro e non una sola scheda?

È la domanda che si fanno tutti, e la risposta è semplice: **ognuna delle
quattro cose cambia per un motivo diverso.**

- Il **Design** cambia quando correggi il modello.
- Il **Pezzo**, quando cambi materiale o ti sale il costo orario.
- La **Variante**, quando cambi il prezzo.
- Il **Prodotto**, quando cambi le foto o la descrizione.

Se tutto stesse in una sola scheda, correggere l'STL ti costringerebbe a
modificarlo in ogni colore che vendi. Separato, lo correggi una volta, nel
Design, e vale per tutto quello che ne dipende.

Se ti aiuta pensarla così: il Design è la ricetta, il Pezzo è il piatto cucinato
e la Variante è quello che compare nel menù, con il suo prezzo.

### La prova: un pack

Immagina di vendere anche un **organizer per cavi**, e ti viene in mente un pack:
il supporto nero e l'organizer insieme, a 19,90 €.

Non devi preparare niente di nuovo. Crei una Variante «Pack ufficio» con **due
Pezzi dentro**: quello del supporto nero e quello dell'organizer. BolloPrint
somma quanto costano i due e, con il prezzo, ti calcola il margine del pack.

![La variante Pack ufficio, fatta di due pezzi; e il pezzo del supporto nero, usato sia dalla variante singola sia dal pack](/blog/media/2026-10-09-como-funciona-bolloprint/04-variante-de-dos-piezas.webp)

Guarda cos'è appena successo: **il Pezzo del supporto nero adesso lo usano due
Varianti**, quella singola e il pack. Se domani ti sale il PLA, cambi quel Pezzo
una volta sola, e BolloPrint ti avvisa di quali Varianti lo usano perché tu ne
controlli il prezzo. È proprio questo il motivo per cui Pezzo e Variante sono
cose diverse.

E funziona allo stesso modo per vendere più unità dello stesso: un «Pack x3» è
una Variante con tre volte lo stesso Pezzo.

![Il blocco Pezzi che compongono la variante, con i due pezzi del pack](/blog/media/2026-10-09-como-funciona-bolloprint/05-piezas-de-la-variante.png)

## L'ordine chiude il cerchio

Torniamo all'ordine dell'inizio.

Quando crei un ordine, quello che aggiungi **è una Variante**: cerchi
«supporto», scegli «PETG bianco», metti 2 unità, e il prezzo si compila da solo.

E siccome quella Variante sa di quali Pezzi è fatta, la riga dell'ordine porta
già con sé tutto il resto:

- **quanto costa e quanto ti lascia**, perché i Pezzi hanno un costo e la
  Variante ha un prezzo;
- **il materiale, il colore e il peso**, che vengono dai suoi Pezzi;
- e **i file da stampare**: dalla riga, l'opzione **Design** ti porta ai modelli
  3D di ogni Pezzo.

Quando l'hai stampato, segni la riga come **stampata**, e l'ordine prosegue il
suo percorso in Produzione.

![Un ordine con due righe, il supporto bianco e il pack, e sotto i pezzi da stampare per evaderlo](/blog/media/2026-10-09-como-funciona-bolloprint/06-del-pedido-a-la-impresora.webp)

Ecco cosa ti fanno risparmiare le quattro cose: non annoti il costo di ogni
ordine, non cerchi l'STL in una cartella e non ricalcoli il margine a mano.
L'hai preparato una volta, e ogni ordine lo eredita.

![Le righe di un ordine, con il menu aperto sull'opzione Design](/blog/media/2026-10-09-como-funciona-bolloprint/07-lineas-del-pedido.png)

## Tutto questo ogni volta? No

Se ti sembra tanto lavoro per un solo supporto, tranquillo: per questo c'è la
**Creazione express**. Le dai l'STL, il materiale, il colore e il prezzo in un
solo modulo, e BolloPrint crea in un colpo il Design, il Pezzo, la Variante e il
Prodotto.

La cosa migliore è che il risultato è esattamente lo stesso che se l'avessi
fatto passo passo. Così, il giorno in cui vorrai aggiungere un altro colore o
creare un pack, è già tutto al suo posto.

![Il modulo di Creazione express, con il file, il materiale, il colore e il prezzo](/blog/media/2026-10-09-como-funciona-bolloprint/08-creacion-express.png)

:::info 💡 Dubbi?
Scrivici dalla [pagina dei contatti](/contact) o apri un thread sul
[nostro Discord](/help/soporte-por-discord). Se ci racconti cosa vendi, ti
aiutiamo a impostarlo.
:::

## Documentazione correlata

- [Catalogo](/help/catalogo) — i quattro livelli, nel riferimento
- [Design](/help/disenos) — i file, le foto e le etichette
- [Pezzi](/help/piezas) — il materiale e come si calcola il costo
- [Prodotti e Varianti](/help/productos-y-variantes) — il prezzo, il margine e i pezzi di ogni variante
- [Ordini](/help/pedidos) — dalla vendita alla consegna
- [Creazione Express](/help/creacion-express) — tutti e quattro in una volta
- [Quanto costa davvero un pezzo stampato](/blog/calculate-your-3d-printing-costs) — da dove viene il costo di ogni Pezzo
