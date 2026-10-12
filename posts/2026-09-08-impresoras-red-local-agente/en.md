---
slug: connect-printers-local-network-agent
title: "Connect your printers over your own network: the local agent, step by step"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu… A small agent on a computer in your workshop, your whole fleet inside BolloPrint, and no need to touch the router.
date: 2026-10-12
tags: [tutorials]
cover: 01-portada.webp
---

Your printers are in the workshop, but you aren't always. And to know whether one
is still printing, whether it came out right or whether it has material left, you
have to be standing in front of it.

That's what the **local agent** is for: a small program that runs on a computer in
your workshop, talks to your printers over your own network and tells BolloPrint
what it sees.

- **You don't touch the router**: no open ports, no fixed IP, no firewall.
- **It's very lightweight**: any computer you already have switched on will do.
- **One is enough for the whole fleet**, whatever its size.

::animation{id="local-agent"}

## Where to install it

The agent lives on **any computer in the workshop that you don't switch off**: a
NAS, a mini-PC, a Raspberry Pi or the workshop PC. It only needs to be **always
on** and to have **Docker**.

Ideally it should be **on the same network as the printers**, because then it
finds them by itself. If that isn't possible, you add them by hand and they work
just the same.

## Create the agent in BolloPrint

Start in BolloPrint. Go to **Settings → Printers**, open the **Local agent** tab
and click **New agent**.

Give it a name that will still mean something to you in six months: **name it
after where it is, not what it is**. "Ground floor" or "Unit 2" work; "Agent 1"
doesn't.

![The Local agent tab, with the New agent button](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Copy the manifest

When you create it, BolloPrint shows you a **manifest**: a piece of text with
everything of yours **already filled in**, your agent's keys and the right
version. There's nothing to replace or fill out.

Choose the format you use (**Docker Compose** is the usual one) and click **Copy**.

![The deployment manifest, with the copy button](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Copy it now: it's only shown once
The keys don't expire, but we won't show them again. If you lose the manifest,
open the agent and use **Regenerate keys** to get a new one.
:::

## Paste the manifest on your computer

This part happens on your computer, not in BolloPrint, and depends on where you
install it:

- **Synology NAS**: install **Container Manager** from the **Package Center**, go
  to **Project → Create**, paste the manifest and create it. No commands to type.
- **Windows or Mac**: install **Docker Desktop**, save the manifest in a folder as
  `docker-compose.yml` and, from that folder, run
  `docker compose up -d`.
- **Linux**: install **Docker** with your distribution's package manager, save the
  manifest as `docker-compose.yml` and run
  `docker compose up -d` there.
- **Portainer**: paste the same manifest into a stack and deploy it.

:::info 💡 On Windows and Mac, printers aren't discovered on their own
There, Docker runs inside a virtual machine, which can't see the announcements
printers send out on your network. The agent works just the same, but you add the
printers yourself, as explained further down.
:::

## Check that it's online

Go back to BolloPrint: in less than a minute, the agent switches to **Online**.

![The agent with Online status](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

If it doesn't, it's almost always one of three causes: the manifest was **only
half pasted**, the computer has **no internet** or a **firewall** is blocking
outgoing traffic.

## Your printers show up on their own

From then on, the agent **looks for printers on your network** by itself every 15
minutes. The ones it finds appear in a list with their brand and model, and you
decide:

- **Add**: you register it and it starts reporting.
- **Ignore**: it isn't yours or you don't want it here.

![The printers found on the network, with the add and ignore buttons](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

If you've just switched a machine on and don't want to wait, click **Search now**.
Some brands ask for a **password** when you add the printer; we cover that further
down.

## If one doesn't show up, add it yourself

It's **normal** for a printer not to appear on its own in two cases:

- **It's on another network.** Printers' announcements don't cross from one
  network to another.
- **The agent runs on Windows or Mac.** Docker runs in a virtual machine there.

You don't lose anything because of it: you add it yourself and it works exactly
the same, with camera and controls if that machine has them. Click **Add by IP**
and enter the type of printer, its address on your network and, if it asks for
one, its password.

![The form for adding a printer by its IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Reserve its IP in the router
If the router changes a printer's address, we find it again on our own, but it'll
be down for a while. Reserving its address avoids that gap. It's a router setting,
not a BolloPrint one.
:::

## What each brand asks of you

This is where most questions come up. In short:

| Brand | What you have to do on the machine | Camera | Can you pause and cancel? |
|---|---|---|---|
| **Bambu Lab** | Turn on **LAN Mode** on its screen and use the **access code** it shows you | Yes | Yes, if you also turn on **Developer Mode** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Use the **password** the printer itself shows | Not yet | Yes |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Usually nothing: it normally connects without a password | Yes, if you have a webcam on your Klipper | Yes |
| **Elegoo resin** (Mars, Saturn, Jupiter) | Nothing, it doesn't ask for a password | On the models that have one | Yes |
| **Elegoo Centauri Carbon 2** | Only if you set a code on its screen | Yes | Not yet |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Turn on **LAN Only** and use the code on its screen | Yes | Not yet |

:::warning ⚠️ Bambu Lab: the access code changes
Every time you turn LAN Mode on or off, Bambu **generates a new code**. If a Bambu
that was working fine suddenly stops connecting, nine times out of ten this is
why: check the code on its screen again and update it in BolloPrint.
:::

:::info 💡 Can't find your model in the table?
Check [compatible printers](/help/impresoras-compatibles). If it runs **Klipper**
inside (any self-built or modified machine), it's supported even if the brand
doesn't appear on any list.
:::

## What you get with the local agent

With the agent up and running, you get:

- **Almost every brand**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron… The cloud doesn't offer this, as it only exists for Bambu Lab.
- **Camera**: live while you have the page open, a photo whenever you like and a
  final photo saved in the history of every print. It isn't video surveillance:
  nothing is recorded.
- **Controls**: pause, resume and cancel from BolloPrint, without walking over to
  the machine, on the ones that allow it (see the table above). On Bambu Lab, with
  the printer in **LAN Mode** and **Developer Mode**.
- **Resilience to internet outages**: if your line goes down, the agent **keeps
  reading the printers and stores what happens**. When the connection is back it
  sends everything, and you don't lose those hours of history.
- **Independence from the manufacturer**, and from their cloud staying up.

What no route allows is **sending jobs to print**: you still send the file from
your slicer.

## Frequently asked questions

The questions we get asked most.

### Do I have to open ports on the router?

No. No ports, no fixed IP, no firewall rules. It works behind a normal home
router.

### Do I need one agent per printer?

No. **A single one handles the whole fleet.** It only makes sense to have several
if you have two premises or two separate networks.

### What happens if I switch the computer off or a new version comes out?

When you switch it back on, the agent comes back by itself. It also updates
itself: when a new version comes out, it downloads it and restarts with it. You'll
only have to do something if we tell you on screen.

:::info 💡 Need help?
Write to us from the [contact page](/contact) or open a thread on
[our Discord](/help/soporte-por-discord). If you tell us which printers you have,
we'll tell you exactly what to do with each one.
:::

Enjoy having your whole fleet in view, wherever you are.

![Bollo, the BolloPrint mascot, with workshop goggles, in front of a farm of 3D printers at work](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp)

## Related documentation

- [Connecting printers](/help/conectar-impresoras): the two routes and which one suits you
- [The local agent](/help/el-agente-local): the full reference
- [Deploying the agent](/help/desplegar-el-agente): the technical detail, if you need it
- [Connection types](/help/tipos-de-conexion): what each printer family allows
- [Compatible printers](/help/impresoras-compatibles): look up your model here
