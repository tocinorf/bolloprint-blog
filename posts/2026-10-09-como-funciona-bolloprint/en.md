---
slug: how-bolloprint-works
title: "Design, Piece, Variant, Product: the map of BolloPrint in five minutes"
description: The four things behind every order, the question each one answers and why there are four rather than a single record. With a phone stand as the example, from start to finish.
date: 2026-10-09
updated: 2026-10-12
tags: [tutorials]
cover: 01-el-mapa.webp
draft: true
---

An order comes in: **two phone stands, in white**.

And before you lift a finger, BolloPrint already knows three things: **what it costs
you** to make them, **what you make** from selling them and **where the files are**
to print them.

How does it know? Because behind that order line there are four things you set up
just once: a **Design**, a **Piece**, a **Variant** and a **Product**. They're the
four words you'll see most in BolloPrint. Here we explain what each one is, why
there are four and not one, and how they end up in an order.

::animation{id="how-it-works"}

## Four questions, four things

The easiest way not to mix them up is to think about the question each one
answers:

| | Answers… | What it holds |
|---|---|---|
| **Design** | What is it? | The 3D files (STL, 3MF…), the photos and your notes. No cost and no price. |
| **Piece** | How do I make it? | The material, the colour, the finish, the weight and the time. **It has a cost.** |
| **Variant** | What do I sell it for? | The price and the margin. **It's what goes into an order.** |
| **Product** | How do I show it? | The name, the photos and the description. It groups the variants. |

If this table is all you take away, you've already got half the article.

## Let's build it: a phone stand

Let's set up the stand from the order, in the same order you'd do it yourself.

**1. The Design.** You upload the stand's STL and a couple of photos. That's the
Design: the model and nothing else. You haven't decided yet what you're going to
print it in, so it has no cost.

**2. The Pieces.** Now you decide how you make it. You want it in **black PLA** and
in **white PETG**: those are two Pieces of the same Design. Each one has its own
material, weight and print time, so each one has **its own cost**, and BolloPrint
works it out automatically.

![The detail of the stand's design, with its two pieces underneath: black PLA and white PETG](/blog/media/2026-10-09-como-funciona-bolloprint/02-diseno-y-piezas.png)

:::info 💡 A Piece always hangs off a Design
That's why there's no standalone list of Pieces: you find them inside the Design
they belong to.
:::

**3. The Variants.** Now you decide what you sell it for. You create the Variant
"Black PLA" at **€12.90** and the Variant "White PETG" at **€15.90**. Each one knows
which Piece it's made from, so it knows what it costs, and with the price it works
out **the margin** by itself.

**4. The Product.** Finally, what the customer sees: the Product "Adjustable phone
stand", with its name, its photos and its description. Inside it go the two
Variants, like the colour options in any online shop. It's what you publish, on
Etsy for example.

![The Adjustable phone stand product, with its two variants, each with its price and margin](/blog/media/2026-10-09-como-funciona-bolloprint/03-producto-y-variantes.png)

## Why four and not one record?

It's the question everyone asks, and the answer is simple: **each of the four
things changes for a different reason.**

- The **Design** changes when you fix the model.
- The **Piece**, when you switch material or your cost per hour goes up.
- The **Variant**, when you change the price.
- The **Product**, when you change the photos or the description.

If everything lived in a single record, fixing the STL would mean changing it in
every colour you sell. Kept separate, you fix it once, in the Design, and it applies
to everything that hangs off it.

If it helps to think of it this way: the Design is the recipe, the Piece is the
cooked dish and the Variant is what appears on the menu, with its price.

### The proof: a pack

Imagine you also sell a **cable organiser**, and you come up with a pack: the
black stand and the organiser together, for €19.90.

You don't have to set up anything new. You create an "Office pack" Variant with
**two Pieces inside**: the black stand one and the organiser one. BolloPrint adds
up what they both cost and, with the price, gives you the pack's margin.

![The Office pack variant, made of two pieces; and the black stand piece, used both by the standalone variant and by the pack](/blog/media/2026-10-09-como-funciona-bolloprint/04-variante-de-dos-piezas.webp)

Notice what's just happened: **the black stand Piece is now used by two
Variants**, the standalone one and the pack. If PLA goes up tomorrow, you change
that Piece just once, and BolloPrint tells you which Variants use it so you can
review their price. That's exactly why Piece and Variant are different things.

And it works just the same for selling several of the same thing: a "Pack x3" is a
Variant with the same Piece three times.

![The Pieces in this variant block, with the pack's two pieces](/blog/media/2026-10-09-como-funciona-bolloprint/05-piezas-de-la-variante.png)

## The order closes the circle

Let's go back to the order from the start.

When you create an order, what you add **is a Variant**: you search for "stand",
pick "White PETG", enter 2 units, and the price fills itself in.

And since that Variant knows which Pieces it's made of, the order line already
brings everything else with it:

- **what it costs and what it makes you**, because the Pieces have a cost and the
  Variant has a price;
- **the material, the colour and the weight**, which come from its Pieces;
- and **the files to print**: from the line, the **Designs** option takes you to the
  3D models for each Piece.

Once it's printed, you mark the line as **printed**, and the order carries on its
way through Production.

![An order with two lines, the white stand and the pack, and underneath the pieces that need printing to fulfil it](/blog/media/2026-10-09-como-funciona-bolloprint/06-del-pedido-a-la-impresora.webp)

That's what the four things save you: you don't note down the cost of every order,
you don't hunt for the STL in a folder and you don't recalculate the margin by hand.
You set it up once, and every order inherits it.

![The lines of an order, with the menu open on the Designs option](/blog/media/2026-10-09-como-funciona-bolloprint/07-lineas-del-pedido.png)

## All this every time? No

If it seems like a lot of work for a single stand, don't worry: that's what **Quick
create** is for. You give it the STL, the material, the colour and the price in a
single form, and BolloPrint creates the Design, the Piece, the Variant and the
Product in one go.

The best part is that the result is exactly the same as if you'd done it step by
step. So the day you want to add another colour or put together a pack, everything
is already in place.

![The Quick create form, with the file, the material, the colour and the price](/blog/media/2026-10-09-como-funciona-bolloprint/08-creacion-express.png)

:::info 💡 Any questions?
Write to us from the [contact page](/contact) or open a thread on
[our Discord](/help/soporte-por-discord). Tell us what you sell and we'll help you
set it up.
:::

## Related documentation

- [Catalogue](/help/catalogo) — the four levels, in the reference
- [Designs](/help/disenos) — files, photos and tags
- [Pieces](/help/piezas) — the material and how the cost is calculated
- [Products and Variants](/help/productos-y-variantes) — the price, the margin and the pieces in each variant
- [Orders](/help/pedidos) — from sale to delivery
- [Quick create](/help/creacion-express) — all four in one go
- [What a printed piece really costs you](/blog/calculate-your-3d-printing-costs) — where the cost of each Piece comes from
