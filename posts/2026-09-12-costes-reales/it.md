---
slug: calculate-your-3d-printing-costs
title: "Quanto costa davvero un pezzo stampato (e come calcolarlo senza complicazioni)"
description: Quel pezzo da 1,60 € di filamento ti costa 9,36 €. Ti mostriamo come ripartire le spese del tuo laboratorio tra le tue ore di stampa perché BolloPrint lo applichi da solo a ogni pezzo.
date: 2026-10-15
tags: [tutorial]
cover: 01-portada.webp
---

Un pezzo da 6 ore e 80 grammi di PLA. Quanto ti costa?

Se hai pensato «80 grammi a 20 € al chilo, **1,60 €**», hai calcolato solo il
**materiale**. In un laboratorio normale, è **una piccola parte** di quello che
ti costa davvero il pezzo.

In un laboratorio con tre stampanti, con il pezzo dipinto e imballato, il conto
completo è questo:

| | |
|---|---|
| Materiale | 1,60 € |
| 6 ore di stampante | 5,16 € |
| Finitura (dipinta) | 2,00 € |
| Costi extra (imballaggio) | 0,60 € |
| **Costo reale del pezzo** | **9,36 €** |

**Quasi sei volte tanto.** La differenza non è un arrotondamento: è l'affitto,
la luce, l'usura delle stampanti, il commercialista e i pezzi che vengono male.
Tutto questo lo paghi; la domanda è se lo stai facendo pagare.

Qui vedrai come portare queste spese nel costo di ogni pezzo. **Si configura una
volta** e poi si applica da solo a ogni pezzo che crei.

::animation{id="part-cost"}

## Da dove vengono quei 5,16 €

L'idea è semplice: sommi **tutto quello che ti costa il laboratorio al mese** e
lo dividi per **le ore in cui stampi davvero**. Così ottieni quanto ti costa
**un'ora di stampante**, e resta solo da moltiplicarlo per le ore del pezzo.

Con i numeri dell'esempio:

- **Ore:** tre stampanti, dieci ore al giorno, venticinque giorni al mese →
  **750 ore**.
- **Spese:** tra affitto, commercialista, software e ammortamento delle macchine
  se ne vanno circa **516 € al mese**. Ripartiti: 0,69 € l'ora. Con la luce, il
  **costo base** arriva a **0,72 €**.
- **Maggiorazioni:** un 5% di manutenzione, un 10% di tasso di fallimento e un 5%
  di imprevisti lo portano a **0,86 € l'ora**. Per sei ore, 5,16 €.

È esattamente il conto che fa la sezione **Costi** di BolloPrint, in
**Impostazioni → Costi**. La vedono solo il **Proprietario** e gli **Admin**.

![La sezione Costi dentro Impostazioni](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## Le ore in cui stampi davvero

Comincia dalle ore: è il numero che più persone calcolano male, e quello che
cambia di più il risultato. Si trova in **Costo orario → Ore di stampa**, e sono
tre campi:

**Stampanti × Ore al giorno × Giorni al mese**

Metti **quello che succede davvero, non il massimo teorico**. Se hai tre
stampanti ma in media lavorano otto ore al giorno, sono otto. Non ventiquattro.

È allettante mettere un numero alto, perché più è alto, meno costa l'ora. Ma
quelle spese le paghi comunque, e quello che non ripartisci tra i pezzi lo paghi
tu a fine mese.

![La scheda Ore di stampa, con i tre campi e il risultato](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Quanto ti costa il laboratorio

Definite le ore, passa alle spese. In **Costo base** le aggiungi una alla volta;
BolloPrint le ordina per tipo e di ognuna ti chiede solo quello che serve:

| Tipo | Cosa ci metti |
|---|---|
| **Costo fisso** | Affitto, internet, commercialista, assicurazioni… l'importo al mese |
| **Stampante** | Quanto ti è costata e in quanti anni la ammortizzi |
| **Software** | L'abbonamento allo slicer, a BolloPrint, a quello che usi |
| **Stipendi** | Lo stipendio e quante persone |
| **Elettricità** | I kW che consuma una stampante e quanto ti fanno pagare il kWh |

Non serve che sia preciso al centesimo: vale di più un numero ragionevole oggi
che il numero perfetto l'anno prossimo.

:::warning ⚠️ Non inserire la stessa spesa due volte
Gli importi **al mese** descrivono **tutto il laboratorio**: l'affitto si mette
una volta sola. Quelli **per ora stampata** —come l'elettricità a consumo—
descrivono **una sola stampante**: lì metti il consumo di una macchina media,
non quello di tutto il capannone.
:::

In fondo trovi il conto già fatto, lo stesso dell'inizio:

> **spese del mese ÷ le tue ore di stampa = quanto ti costa un'ora «in pulito»**

Questo è il **costo base orario**: 0,72 € nell'esempio.

![Le spese del laboratorio in Costo base, raggruppate per tipo, e il conto che dà 0,72 € l’ora](/blog/media/2026-09-12-costes-reales/03b-coste-base.png)

## Quello che sai che succederà

Il costo base lascia fuori ciò che capita senza una fattura fissa: si rompono
ugelli, e **qualche pezzo viene male e va ristampato**.

Per questo c'è **Costo totale**, che aggiunge alcune percentuali al costo base:
manutenzione, tasso di fallimento e imprevisti.

Il tasso di fallimento è il più importante, e quello che più persone saltano. Se
su dieci pezzi uno finisce nel cestino, **i nove buoni stanno pagando quello
cattivo**. Se non lo includi qui, lo paghi tu.

Il risultato è il tuo **costo totale per ora**: 0,86 € nell'esempio. Questo è il
tuo numero vero, ed è quello che si applica a ogni pezzo.

:::info 💡 Il margine di profitto non va qui
Qui vanno solo i **costi**. Quanto vuoi guadagnare si decide dopo, nel prodotto,
perché è una decisione commerciale.
:::

![Le maggiorazioni di manutenzione, tasso di fallimento e imprevisti sul costo base, fino a 0,86 € l’ora](/blog/media/2026-09-12-costes-reales/03c-coste-total.png)

## Il materiale e gli extra

Resta la parte più semplice, in **Valori predefiniti**:

- **Il prezzo di ogni materiale**, al chilo. È **per tipo**, non per famiglia:
  il PLA e il TPU non costano uguale.
- **Le finiture**: quanto aggiungi se il pezzo è post-processato o dipinto.
- **I costi extra**: imballaggio, viteria, magneti, inserti, manodopera. Per
  ognuno scegli se si addebita **per unità** o **per piastra**.
- **I margini**: quello che vuoi di default, e da quale percentuale ti avvisiamo
  in rosso o in arancione.

:::info 💡 Se hai il materiale in inventario, comanda l'inventario
Questi prezzi sono di riferimento, per quando dietro non c'è niente. Se il pezzo
esce da una bobina registrata con il suo costo reale, usiamo quello.
:::

![Valori predefiniti: i margini con i loro avvisi di colore e il prezzo di ogni materiale al chilo](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## Ed ecco come arriva al tuo pezzo

I quattro passaggi precedenti finiscono in un solo numero: **quanto ti costa
un'ora di stampante**. Da lì, ogni pezzo è una somma:

> le sue **ore × il tuo costo orario**
> **+** il **materiale** che porta
> **+** la **finitura**, se è post-processato o dipinto
> **+** i **costi extra** che gli aggiungi

C'è un dettaglio che conviene capire, perché spiega perché conviene riempire il
piano: **il conto si fa per piastra, non per pezzo**. BolloPrint calcola quanto
costa la piastra intera e lo **ripartisce tra i pezzi che ne escono**. Per
questo, tra i costi extra, quelli che segni **per piastra** si addebitano una
volta sola —che tu stampi i pezzi uno alla volta o venti alla volta— e quelli
**per unità** si addebitano su ogni pezzo.

Inoltre, ogni pezzo **conserva il costo orario con cui è stato calcolato**. È
voluto: così il costo di quello che hai stampato l'anno scorso resta quello di
allora. Per questo esiste il pulsante **Ricalcola**, che trovi poco più sotto.

## Adesso hai il tuo numero

Per vedere il risultato, vai in **Costi → Riepilogo**. Il blocco **Esempio**
prende una piastra di prova e ti mostra il conto completo **con i tuoi valori**:
quanto è materiale, quanto stampa, quanto finitura e quanto costa il pezzo.

![Il blocco Esempio con il dettaglio completo di un pezzo](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Quando cambiano le tue spese

I tuoi numeri non saranno sempre gli stessi: aumenta la luce, compri un'altra
stampante o cambi locale. Quando li aggiorni, **i pezzi che avevi già non
cambiano da soli**. È voluto: ogni pezzo conserva il costo con cui è stato
calcolato, e non vorresti che si riscrivesse quello di tutto ciò che hai fatto
l'anno scorso.

Quando vuoi applicarlo a tutto, in **Riepilogo** hai un contatore dei pezzi
**da ricalcolare** e il pulsante **Ricalcola**. Decidi tu quando.

:::info 💡 Non tocca i tuoi prezzi di vendita
Ricalcolare aggiorna il **costo** e il prezzo *suggerito*. Quello che hai messo
tu a mano resta com'è. Quello che vedrai muoversi è l'indicatore del **margine**.
:::

## Mi compro un'altra stampante?

Con i tuoi costi configurati, puoi rispondere a questa domanda con i numeri. In
**Comparatore di farm** cambi le stampanti, le ore o i giorni e vedi cosa
succederebbe al tuo costo orario. Simula e basta: non cambia niente della tua
configurazione.

Quello che mostra meglio è che **la curva smette di scendere**. Passare da una
stampante a cinque divide il costo orario quasi per cinque. Passare da venti a
cento lo sposta appena, perché ci sono spese —come la luce— che si pagano a ogni
ora stampata e non si ripartiscono tra nessuno.

![Il comparatore di farm, con la curva del costo orario](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Configurarlo richiede quattro schermate e un po' di tempo in un pomeriggio. In
cambio, ogni pezzo che crei porterà con sé il suo costo reale, e saprai se stai
guadagnando senza fare il conto a mano.

:::info 💡 Ti aiutiamo con i tuoi numeri?
Se non sai da dove iniziare, scrivici dalla [pagina dei contatti](/contact) o
sul [nostro Discord](/help/soporte-por-discord). L'abbiamo già fatto parecchie
volte.
:::

Che i tuoi conti tornino sempre.

![Bollo, la mascotte di BolloPrint, con gli occhialini da officina, pensieroso tra operazioni scritte col gesso](/blog/media/2026-09-12-costes-reales/07-bollo.webp "60%")

## Documentazione correlata

- [Costi](/help/costes): il riferimento completo della sezione
- [Pezzi](/help/piezas): come si calcola il costo di ogni pezzo
- [Prodotti e Varianti](/help/productos-y-variantes): dal costo al prezzo di vendita
- [Inventario](/help/inventario): perché il materiale esca dal suo costo reale
