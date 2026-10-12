---
slug: calculate-your-3d-printing-costs
title: "What a printed piece really costs you (and how to work it out without losing your mind)"
description: That piece with €1.60 of filament actually costs you €9.36. We show you how to spread your workshop's expenses across your print hours, and how to get BolloPrint to apply it to every piece automatically.
date: 2026-09-12
updated: 2026-10-12
tags: [tutorials]
cover: 01-portada.webp
draft: true
---

A 6-hour piece using 80 grams of PLA. How much does it cost you?

If you thought "80 grams at €20 a kilo, **€1.60**", you've worked out what the
**material** costs. Which, in a normal workshop, is **a small part** of what that
piece really costs you.

The full sum, in a workshop with three printers and with the piece painted and
packaged, looks like this:

| | |
|---|---|
| Material | €1.60 |
| 6 hours of printer time | €5.16 |
| Finish (painted) | €2.00 |
| Extra costs (packaging) | €0.60 |
| **Real cost of the piece** | **€9.36** |

**Almost six times as much.** And the difference isn't a rounding error: it's the
rent, the electricity, the printers slowly wearing out, the accountant and the
pieces that come out wrong. You're paying for all of that. The question is whether
you're charging for it.

This is about fixing that. And the good news is that **you set it up once** and
from then on it's applied automatically to every piece you create.

::animation{id="part-cost"}

## Where that €5.16 comes from

From a simple idea: you take **everything the workshop costs you each month**,
divide it by **the hours you actually print**, and that tells you what **one hour of
printer time** costs you. Then you multiply by the piece's hours.

In the example above:

> Three printers, ten hours a day, twenty-five days a month → **750 hours**.
>
> Between rent, the accountant, software and the depreciation of the machines, about
> **€516 a month** goes out. Spread out: €0.69 an hour. Add electricity, and the
> **base cost** comes to **€0.72**.
>
> Plus 5% for maintenance, 10% for failure rate and 5% for contingency:
> **€0.86 an hour**. For six hours, €5.16.

That's exactly what BolloPrint's **Costs** section works out, in
**Settings → Costs**. Only the **Owner** and **Admins** can see it.

![The Costs section inside Settings](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## The hours you really print

This is the number most people get wrong, and the one that changes the result the
most. It's in **Hourly cost → Print hours**, and it's three fields:

**Printers × Hours / day × Days / month**

The only tip that matters: **don't put the theoretical maximum, put what really
happens**. If you have three printers but on average they work eight hours a day,
it's eight. Not twenty-four.

It's tempting to put the big number, because the higher it is, the cheaper the hour
comes out. But if you inflate the hours you're kidding yourself: you pay those
expenses anyway, and whatever you don't spread across your pieces comes out of your
own pocket at the end of the month.

![The Print hours tab, with the three fields and the result](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## What the workshop costs you

In **Base cost** you enter your expenses. BolloPrint sorts them by type and only
asks you for what it needs for each one:

| Type | What you enter |
|---|---|
| **Fixed cost** | Rent, internet, accountant, insurance… the monthly amount |
| **Printer** | What it cost you and over how many years you depreciate it |
| **Software** | The subscription to your slicer, to BolloPrint, to whatever you use |
| **Staff costs** | The salary and how many people |
| **Electricity** | The kW one printer uses and what you're charged per kWh |

It doesn't need to be accurate to the cent. A reasonable number today is worth far
more than the perfect number next year.

:::warning ⚠️ Don't enter the same expense twice
The **monthly** amounts describe **the whole workshop**: rent goes in just once.
The ones that go **per printed hour** — like electricity by usage — describe **a
single printer**: there, put what an average machine uses, not the whole unit.
:::

Right at the bottom you have the sum worked out, which is the one from the start:

> **monthly expenses ÷ your print hours = what one hour costs you "before extras"**

That's the **base cost per hour**. In the example above, €0.72.

![The workshop’s expenses in Base cost, grouped by type, and the sum that gives €0.72 an hour](/blog/media/2026-09-12-costes-reales/03b-coste-base.png)

## What you know is going to happen

The base cost leaves out things that do happen but don't come with a fixed bill:
nozzles break, and **some pieces come out wrong and have to be reprinted**.

That's what **Total cost** is for: a few percentages on top of the base cost.
Maintenance, failure rate and contingency.

The failure rate is the important one, and the one most people skip. If one in
every ten pieces ends up in the bin, **the nine good ones are paying for the bad
one**. If you don't put it in here, you pay for it yourself.

The result is your **total cost per hour** — €0.86 in the example. That's your real
number, and it's the one applied to every piece.

:::info 💡 Your profit margin doesn't go here
Only **costs** go here. How much you want to earn is decided later, on the product,
because it's a business decision.
:::

![The maintenance, failure-rate and contingency surcharges on the base cost, up to €0.86 an hour](/blog/media/2026-09-12-costes-reales/03c-coste-total.png)

## Material and extras

The easy part, in **Default values**:

- **The price of each material**, per kilo. It's **per type**, not per family: PLA
  and TPU don't cost the same.
- **Finishes**: how much you add on if it's post-processed or painted.
- **Extra costs**: packaging, fixings, magnets, inserts, labour. For each one you
  choose whether it's charged **per unit** or **per build plate**.
- **Margins**: your default one, and the percentage below which we warn you in red
  or in orange.

:::info 💡 If the material is in your inventory, the inventory wins
These prices are a reference, for when there's nothing behind them. If the piece
comes from a spool you've registered with its real cost, we use that one.
:::

![Default values: the margins with their colour warnings and the price of each material per kilo](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## And this is how it reaches your piece

The four steps end up in a single number: **what one hour of printer time costs
you**. From there, every piece is a sum:

> its **hours × your cost per hour**
> **+** the **material** it uses
> **+** the **finish**, if it's post-processed or painted
> **+** any **extra costs** you add to it

There's one detail worth understanding, because it explains why it pays to fill
the bed: **the sum is done per build plate, not per piece**. BolloPrint works out
what the whole plate costs and **splits it between the pieces that come off it**.
That's why, among the extra costs, the ones you mark **per build plate** are charged
just once — whether you print them one at a time or twenty at a time — while the
**per unit** ones are charged on every piece.

And every piece **keeps the cost per hour it was calculated with**. That isn't an
oversight: it's what makes the cost of what you printed last year stay what it was
back then, and it's the reason there's a **Recalculate** button, a little further down.

## Now you've got your number

In **Costs → Summary**, the **Example** block takes a sample plate and shows you the
whole sum **with your values**: how much is material, how much is printing, how
much is finish, and what the piece comes to.

![The Example block with the full breakdown of a piece](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## When your expenses change

Your electricity goes up, you buy another printer, you move premises. You change
the numbers and… **the pieces you already had don't change on their own**. That's
deliberate: every piece keeps the cost it was calculated with, and you wouldn't
want the cost of everything you made last year rewritten.

When you want to apply it to everything, in **Summary** you have a counter of
pieces **to recalculate** and a **Recalculate** button. You decide when.

:::info 💡 It doesn't touch your sale prices
Recalculating updates the **cost** and the *suggested* price. The one you set by
hand stays as it is. What you'll see move is the **margin** indicator.
:::

## Should I buy another printer?

That's **the** question, and now you can answer it with numbers. In **Cost
scenarios** you change the printers, the hours or the days and see what would
happen to your cost per hour. It doesn't change anything in your setup: it only
simulates.

There's one thing it shows really well: **the curve stops going down**. Going from
one printer to five divides the cost per hour by almost five. Going from twenty to
a hundred barely moves it, because there are expenses — like electricity — that you
pay for every printed hour and that don't get shared out at all.

![The Cost scenarios simulator, with the cost-per-hour curve](/blog/media/2026-09-12-costes-reales/05-comparador.png)

It's four screens and an afternoon of your time. In return, every piece you create
will come with its real cost already on it, and you'll know whether you're making
money without doing the sums by hand.

:::info 💡 Want a hand with your numbers?
If you don't know where to start, write to us from the [contact page](/contact)
or drop by [our Discord](/help/soporte-por-discord). We've done this a fair few
times already.
:::

## Related documentation

- [Costs](/help/costes) — the full reference for the section
- [Pieces](/help/piezas) — how the cost of each piece is calculated
- [Products and Variants](/help/productos-y-variantes) — from cost to sale price
- [Inventory](/help/inventario) — so the material comes from its real cost
