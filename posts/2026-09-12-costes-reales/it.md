---
slug: calculate-your-3d-printing-costs
title: "Quanto costa davvero un pezzo stampato (e come calcolarlo senza impazzire)"
description: Quel pezzo da 1,60 € di filamento ti costa 9,36 €. Ti mostriamo come ripartire le spese del tuo laboratorio tra le tue ore di stampa e come farlo applicare da BolloPrint a ogni pezzo, da solo.
date: 2026-09-12
updated: 2026-10-12
tags: [tutorial]
cover: 01-portada.webp
draft: true
---

Un pezzo da 6 ore e 80 grammi di PLA. Quanto ti costa?

Se hai pensato «80 grammi a 20 € al chilo, **1,60 €**», hai calcolato quanto
costa il **materiale**. Che in un laboratorio normale è **una piccola parte** di
quello che ti costa davvero quel pezzo.

Il conto completo, in un laboratorio con tre stampanti e con il pezzo dipinto e
imballato, viene così:

| | |
|---|---|
| Materiale | 1,60 € |
| 6 ore di stampante | 5,16 € |
| Finitura (dipinta) | 2,00 € |
| Costi extra (imballaggio) | 0,60 € |
| **Costo reale del pezzo** | **9,36 €** |

**Quasi sei volte tanto.** E la differenza non è un arrotondamento: è l'affitto,
la luce, le stampanti che si consumano, il commercialista e i pezzi che vengono
male. Tutto questo lo stai pagando. La domanda è se lo stai facendo pagare.

Qui si tratta di sistemare proprio questo. E la buona notizia è che **si
configura una volta** e poi si applica da solo a ogni pezzo che crei.

::animation{id="part-cost"}

## Da dove vengono quei 5,16 €

Da un'idea semplice: prendi **tutto quello che ti costa il laboratorio al
mese**, lo dividi per **le ore in cui stampi davvero**, e così sai quanto ti
costa **un'ora di stampante**. Poi moltiplichi per le ore del pezzo.

Nell'esempio qui sopra:

> Tre stampanti, dieci ore al giorno, venticinque giorni al mese → **750 ore**.
>
> Tra affitto, commercialista, software e ammortamento delle macchine se ne
> vanno circa **516 € al mese**. Ripartiti: 0,69 € l'ora. Con la luce, il
> **costo base** arriva a **0,72 €**.
>
> Più un 5% di manutenzione, un 10% di tasso di fallimento e un 5% di
> imprevisti: **0,86 € l'ora**. Per sei ore, 5,16 €.

È esattamente quello che calcola la sezione **Costi** di BolloPrint, in
**Impostazioni → Costi**. La vedono solo il **Proprietario** e gli **Admin**.

![La sezione Costi dentro Impostazioni](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## Passaggio 1 — Le ore in cui stampi davvero

Questo è il numero che più persone calcolano male, e quello che cambia di più il
risultato. Si trova in **Costo orario → Ore di stampa**, e sono tre campi:

**Stampanti × Ore al giorno × Giorni al mese**

L'unico consiglio che conta: **non mettere il massimo teorico, metti quello che
succede davvero**. Se hai tre stampanti ma in media lavorano otto ore al giorno,
sono otto. Non ventiquattro.

È allettante mettere il numero grande, perché più è alto, più l'ora costa poco.
Ma se gonfi le ore menti a te stesso: quelle spese le paghi comunque, e quello
che non ripartisci tra i pezzi te lo mangi tu a fine mese.

![La scheda Ore di stampa, con i tre campi e il risultato](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Passaggio 2 — Quanto ti costa il laboratorio

In **Costo base** inserisci le tue spese. BolloPrint le ordina per tipo e di
ognuna ti chiede solo quello che serve:

| Tipo | Cosa ci metti |
|---|---|
| **Costo fisso** | Affitto, internet, commercialista, assicurazioni… l'importo al mese |
| **Stampante** | Quanto ti è costata e in quanti anni la ammortizzi |
| **Software** | L'abbonamento allo slicer, a BolloPrint, a quello che usi |
| **Stipendi** | Lo stipendio e quante persone |
| **Elettricità** | I kW che consuma una stampante e quanto ti fanno pagare il kWh |

Non serve che sia preciso al centesimo. Vale molto di più un numero ragionevole
oggi che il numero perfetto l'anno prossimo.

:::warning ⚠️ Non inserire la stessa spesa due volte
Gli importi **al mese** descrivono **tutto il laboratorio**: l'affitto si mette
una volta sola. Quelli **per ora stampata** —come l'elettricità a consumo—
descrivono **una sola stampante**: lì metti il consumo di una macchina media,
non quello di tutto il capannone.
:::

In fondo trovi il conto già fatto, che è quello dell'inizio:

> **spese del mese ÷ le tue ore di stampa = quanto ti costa un'ora «in pulito»**

Questo è il **costo base orario**. Nell'esempio qui sopra, 0,72 €.

## Passaggio 3 — Quello che sai che succederà

Il costo base lascia fuori cose che capitano e non hanno una fattura fissa: si
rompono ugelli, e **qualche pezzo viene male e va ristampato**.

Per questo c'è **Costo totale**: alcune percentuali sul costo base.
Manutenzione, tasso di fallimento e imprevisti.

Il tasso di fallimento è quello importante, e quello che più persone saltano. Se
su dieci pezzi uno finisce nel cestino, **i nove buoni stanno pagando quello
cattivo**. Se non lo metti qui, lo paghi tu.

Il risultato è il tuo **costo totale per ora** — 0,86 € nell'esempio. Questo è
il tuo numero vero, ed è quello che si applica a ogni pezzo.

:::info 💡 Il margine di profitto non va qui
Qui vanno solo i **costi**. Quanto vuoi guadagnare si decide dopo, nel prodotto,
perché è una decisione commerciale.
:::

## Passaggio 4 — Il materiale e gli extra

La parte facile, in **Valori predefiniti**:

- **Il prezzo di ogni materiale**, al chilo. È **per tipo**, non per famiglia:
  il PLA e il TPU non costano uguale.
- **Le finiture**: quanto aggiungi se è post-processato o dipinto.
- **I costi extra**: imballaggio, viteria, magneti, inserti, manodopera. Per
  ognuno scegli se si addebita **per unità** o **per piastra**.
- **I margini**: quello che vuoi di default, e da quale percentuale ti avvisiamo
  in rosso o in arancione.

:::info 💡 Se hai il materiale in inventario, comanda l'inventario
Questi prezzi sono di riferimento, per quando dietro non c'è niente. Se il pezzo
esce da una bobina registrata con il suo costo reale, usiamo quello.
:::

## Ed ecco come arriva al tuo pezzo

I quattro passaggi finiscono in un solo numero: **quanto ti costa un'ora di
stampante**. Da lì, ogni pezzo è una somma:

> le sue **ore × il tuo costo orario**
> **+** il **materiale** che porta
> **+** la **finitura**, se è post-processato o dipinto
> **+** i **costi extra** che gli aggiungi

C'è un dettaglio che conviene capire, perché spiega perché conviene riempire il
piano: **il conto si fa per piastra, non per pezzo**. BolloPrint calcola quanto
costa la piastra intera e lo **ripartisce tra i pezzi che ne escono**. Per
questo, tra i costi extra, quelli che segni **per piastra** si addebitano una
volta sola —che tu la stampi uno alla volta o venti alla volta— mentre quelli
**per unità** si addebitano su ogni pezzo.

E ogni pezzo **conserva il costo orario con cui è stato calcolato**. Non è una
svista: è quello che fa sì che il costo di quello che hai stampato l'anno scorso
resti quello di allora, ed è il motivo per cui esiste il pulsante **Ricalcola**,
che trovi poco più sotto.

## Adesso hai il tuo numero

In **Costi → Riepilogo**, il blocco **Esempio** prende una piastra di prova e ti
mostra il conto completo **con i tuoi valori**: quanto è materiale, quanto
stampa, quanto finitura, e quanto costa il pezzo.

![Il blocco Esempio con il dettaglio completo di un pezzo](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Quando cambiano le tue spese

Ti aumenta la luce, compri un'altra stampante, cambi locale. Modifichi i numeri
e… **i pezzi che avevi già non cambiano da soli**. È voluto: ogni pezzo conserva
il costo con cui è stato calcolato, e non vorresti che si riscrivesse quello di
tutto ciò che hai fatto l'anno scorso.

Quando vuoi applicarlo a tutto, in **Riepilogo** hai un contatore dei pezzi
**da ricalcolare** e un pulsante **Ricalcola**. Decidi tu quando.

:::info 💡 Non tocca i tuoi prezzi di vendita
Ricalcolare aggiorna il **costo** e il prezzo *suggerito*. Quello che hai messo
tu a mano resta com'è. Quello che vedrai muoversi è l'indicatore del **margine**.
:::

## Mi compro un'altra stampante?

Questa è **la** domanda, e adesso puoi rispondere con i numeri. In
**Comparatore di farm** muovi le stampanti, le ore o i giorni e vedi cosa
succederebbe al tuo costo orario. Non cambia niente della tua configurazione:
simula e basta.

C'è una cosa che mostra molto bene: **la curva smette di scendere**. Passare da
una stampante a cinque divide il costo orario quasi per cinque. Passare da venti
a cento lo sposta appena, perché ci sono spese —come la luce— che si pagano a
ogni ora stampata e non si ripartiscono tra nessuno.

![Il comparatore di farm, con la curva del costo orario](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Sono quattro schermate e un po' di tempo in un pomeriggio. In cambio, ogni pezzo
che crei porterà con sé il suo costo reale, e saprai se stai guadagnando senza
fare il conto a mano.

:::info 💡 Ti aiutiamo con i tuoi numeri?
Se non sai da dove iniziare, scrivici dalla [pagina dei contatti](/contact) o
passa dal [nostro Discord](/help/soporte-por-discord). L'abbiamo già fatto
parecchie volte.
:::

## Documentazione correlata

- [Costi](/help/costes) — il riferimento completo della sezione
- [Pezzi](/help/piezas) — come si calcola il costo di ogni pezzo
- [Prodotti e Varianti](/help/productos-y-variantes) — dal costo al prezzo di vendita
- [Inventario](/help/inventario) — perché il materiale esca dal suo costo reale
