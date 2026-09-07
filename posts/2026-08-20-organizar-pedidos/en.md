---
slug: order-management-3d-print-farm
title: How to organise orders in a 3D print farm
description: When you go from three printers to fifteen, the notebook stops working. Four decisions that prevent most of the mess.
date: 2026-08-20
updated: 2026-08-20
tags: [tutorials]
draft: false
---

Almost every workshop starts the same way: a notebook, a spreadsheet and a good
memory. It works until it doesn't — and it usually stops working all at once,
generally the month twice as many orders come in as the last one.

These are the four decisions that save the most headaches.

## 1. Separate the order from the part

This is the most common mix-up and the most expensive one. An **order** is what a
customer asked you for; a **part** is each thing you have to print to fulfil it.
An order might carry one part or forty, and some get reprinted.

If you track it all as a single list, the day a part comes out wrong you can't
tell which customer is affected without going through it by hand.

## 2. Let the status say everything

An order should be able to answer "why hasn't this shipped yet?" on its own.
Three or four well-chosen statuses are enough:

- **Pending** — accepted, not started
- **Queued** — assigned to a printer
- **Printing**
- **Ready** — finished, waiting to ship

The exact list matters less than this: **nobody should have to ask** where
something stands.

:::warning
Be careful inventing statuses for rare cases. Ten statuses don't give you more
control: they give you ten places an order can sit forgotten.
:::

## 3. Record the real cost, not the estimate

Filament, machine hours, the reprint you did because it lifted off the bed,
post-processing. If you only record the sale price you know what you invoiced but
not what you earned — and those are very different numbers when 15% of what you
print gets repeated.

## 4. Decide what happens when something fails

This isn't a software question: it's a workshop decision. Does it reprint
automatically? Does the customer get told? Who decides whether a defect is
acceptable?

Write it down even if there are two of you. The day someone else is standing at
the machine, that note is worth more than any tool.

---

Get those four right and the tool you use barely matters. Get them wrong and no
tool will save you.
