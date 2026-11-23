---
slug: how-your-inventory-keeps-itself-up-to-date
title: "Automatic stock: how your inventory adjusts itself as you sell"
description: You sell a figure or a spool of filament, or you head off to a maker event, and your inventory keeps itself up to date. Here's what BolloPrint does with your stock in each situation.
date: 2026-11-23
tags: [tutorials]
cover: 08-stock-del-pedido-en.png
---

Having your inventory up to date is great, but what really saves you work is
having it keep itself up to date. You sell a figure you'd already printed, you
take payment for a spool of filament at a market, you take two full boxes to an
event… and when you get back, you don't want to spend the afternoon counting
what's left.

In this guide we explain what BolloPrint does with your stock in each
situation.

## First, what your inventory holds

In **Inventory**, BolloPrint keeps two things apart:

- **The Stock**: the **pieces you've already printed** and stored, ready to
  assemble into a product or sell.
- **The material**: your spools of **Filament**, your bottles of **Resin** and
  your **Supplies** (boxes, magnets, inserts…). It's what you buy, although you
  can sell it too!

## You can sell your material too!

As well as your 3D products, you can add **filament, resin and supplies** to
your orders and quotes, and sell them from the point of sale. A customer buys a
spool from you? It comes out of your inventory like any other sale.

## What you sell comes out of the stock

When you save an order or accept a quote, BolloPrint checks your inventory to
see what you have and what you don't, and shows you what's coming out:

- The **materials** you sell: spools, bottles or supplies.
- The **pieces** of the 3D products you sell. If a product is made up of
  several pieces, they all come out of the Stock.

And you choose **Take from the stock** or **Don’t take from the stock**.

![When creating an order, what comes out of the stock: a spool of orange ABS and a keyring, each shown as a subtraction (you have, taken, left), a piece that has to be printed because there's none left, and the Take from the stock and Don’t take from the stock options](/blog/media/2026-11-23-como-se-mueve-el-inventario/08-stock-del-pedido-en.png "80%")

If there isn't enough, BolloPrint takes what there is (it never leaves the stock
negative) and tells you what's missing: a piece **has to be printed** and a
material **has to be bought**. Nothing is blocked. And if a line comes entirely
out of the Stock, it's marked as **printed**, because it no longer needs
printing.

Also:

- A **quote** doesn't touch the stock until you accept it.
- If you **cancel** an order, only what came out of the stock for it goes back.
- The stock **never changes the order's status**: marking it "Ready to
  dispatch" is up to you, because it may still need packing.

## Orders from Etsy and other marketplaces

An order that arrives by itself from your shop has no one to ask, so it comes
in as **stock to decide**. The first time you open it, BolloPrint asks you what
to do with the stock. And if the buyer cancels it on the marketplace, whatever
had been taken goes back by itself.

## At the point of sale

At the **Point of sale** there are no questions: taking the payment is the
decision. What you sell comes out of the stock and, if you void the sale, it
goes back. More in [Point of sale](/help/punto-de-venta).

## What you take to an event

If you're going to a market or a maker event, when you create an event in
**Events** you set out **what you take**: pieces from the Stock and material
from the inventory. When you save it, BolloPrint shows you what comes out of
the Stock and what has to be printed, just like with an order. What you take no
longer counts in your stock and is kept in the event's stock instead. Anything
you don't have in the Stock is treated as printed for the occasion.

- What you **sell at the event** with the point of sale is deducted from what
  you took, not from your inventory a second time.
- When you **close the event**, you record what comes back: whatever's left
  over **goes back to the stock**, and whatever doesn't come back (something
  broken, something given away) counts as an **event loss**, at its cost.
- Closing also tells you if **you sold products you hadn't taken**, for example
  a commission you'll deliver later.

![What you take in a closed event: for each piece, how many you took, how many you sold, how many came back and how many didn't](/blog/media/2026-11-23-como-se-mueve-el-inventario/09-que-te-llevas-en.png)

:::info 💡 Printed it specially for the event?
Choose **Leave the Stock alone**: what you take isn't removed from the
inventory, and whatever's left over is added when you close it.
:::

Step by step, in the Events help:
[What you take](/help/eventos#what-you-take) and
[Closing the event](/help/eventos#closing-the-event).

## Everything is recorded in the History

Every change to the inventory is recorded in **Inventory → History**: when,
what, why (an order, the point of sale, an event, a manual change), how much
and who did it. From the **⋯** menu on each row, **View history** shows you
just that material or that piece. More in the help for
[History](/help/inventario#history).

Purchases are recorded by hand, with the row's **+** or with "Add with a
photo". An expense in **Finance** doesn't change the inventory: that way the
same spool is never added twice.

## Start with your inventory up to date

All of this works best when what's in BolloPrint is what's on your shelves. If
you haven't added your spools and resins yet, do it with a few photos of the
labels: we explain how in
[Manage your inventory with your phone's camera](/blog/filament-inventory-from-a-photo).
From then on, your orders, your point of sale and your events keep it up to
date for you.

![Bollo, the BolloPrint mascot, wearing his workshop goggles, among boxes, spools of filament, bottles of resin and shelves of printed pieces](/blog/media/2026-11-23-como-se-mueve-el-inventario/11-bollo.jpg "60%")

## Related documentation

- [Inventory](/help/inventario): filament, resin, supplies and Stock
- [Material for sale](/help/material-a-la-venta): selling spools and supplies
- [Order details](/help/detalles-de-un-pedido): the lines and the stock
- [Marketplace orders](/help/pedidos-de-marketplaces): the orders that arrive by themselves
- [Point of sale](/help/punto-de-venta): selling in person
- [Events](/help/eventos): preparing, selling at and closing an event
