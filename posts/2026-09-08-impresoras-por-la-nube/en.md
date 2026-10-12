---
slug: connect-bambu-lab-printers-cloud
title: "Connect your Bambu Lab printers to BolloPrint in five minutes"
description: Nothing to install. You connect your Bambu account and your machines show up on their own, with what they're printing and their whole history.
date: 2026-09-08
updated: 2026-10-12
tags: [tutorials]
cover: 01-portada.webp
draft: true
---

You've got three Bambus running and, to see how they're getting on, you get up
and look at each one's screen. Has the first one finished? Has the second still
got material? How many hours have you printed this month?

There's a way to see it all from a single screen, and **there's nothing to
install**. You connect your Bambu Lab account to BolloPrint and your machines show
up on their own. Five minutes.

::animation{id="bambu-cloud"}

## Here's what you'll get

For every printer, live and without touching a thing:

- whether it's switched on and connected;
- what it's printing, the **percentage** and how long it has left;
- the nozzle and bed temperatures;
- the **materials** loaded, tray by tray, if you have an AMS;
- the machine's own alerts.

And on top of that, the thing that really makes a difference at the end of the
month: **every print gets logged**, with its duration, its material and its cost.
Without writing anything down by hand.

![A printer's card while it's printing, with the progress and the temperatures](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## What you need

- To sign in to BolloPrint as an **Owner** or **Admin**. With any other role, this
  screen won't show up.
- Your **Bambu Lab** account, with its **email and password**.
- Access to that account's **email**: Bambu is going to send you a code.

:::warning ⚠️ If you sign in to Bambu with Google, Apple or Facebook, this won't work for you
BolloPrint needs your Bambu account's **email and password**. If you've never set
a password because you always click "Continue with Google", create one first on
the Bambu Lab website and come back here with it.
:::

## Step 1 — Open the printers screen

Go to **Settings → Printers**. You'll see three tabs:

- **Printers** — the list of all your machines, however they're connected.
- **Local agent** — for connecting over your network. That's [another tutorial](/blog/connect-printers-local-network-agent).
- **Bambu Cloud** — the one we're interested in today.

Open **Bambu Cloud**.

![The Settings → Printers screen with its three tabs](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Step 2 — Type in your Bambu email and password

The ones for your Bambu Lab account — that email, not another one of yours — and
click **Connect to Bambu Lab**.

![The Bambu Cloud form, with the account email typed in and the password still to go](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 Your password isn't stored
It stays **only in your browser**, and only until you've finished verifying.
:::

## Step 3 — Enter the code you get by email

Bambu sends you a **6-digit code** from `noreply@bambulab.com`. **Check your spam
too** — it ends up there more often than it should.

Type the six digits on the same screen and click **Verify and connect**.

![The 6-digit code field and the Verify and connect button](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Two details that will save you a second attempt: **the code expires in about 5
minutes** — if you take longer, click **Resend code** — and **paste it in whole,
just as it arrives**: if it comes with spaces or dashes, they get cleaned up on
their own.

Once it's accepted, you'll see **Account verified and connected**.

## Step 4 — There they are

You don't have to add the printers one by one. **Every machine on that account
shows up on its own** in the **Printers** tab, each with its name and serial
number.

![The printer list with the Bambu machines that have just appeared](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

At the top there's a counter like `3 / 6 active`: the printers your plan includes.
With the switch on each row you turn on and off whichever ones you like. One that's
switched off doesn't count towards the limit, but **stays on the list with its
whole history**.

And if you connect a whole fleet and there aren't enough places for all of them,
the extra ones come in **deactivated** instead of breaking your plan.

## What you WON'T be able to do this way

Better to know now than to spend half an hour hunting for the button:

- **It's read-only.** Through the cloud you can't pause, resume or cancel from
  BolloPrint: Bambu only accepts those commands over your local network, and with
  the printer in a special mode. We cover that at the end.
- **There's no camera.** It doesn't come through the cloud. What does come through
  is the job's slicer image, which is the preview, not what's actually happening
  inside.
- **It depends on the internet twice over:** yours and Bambu's. If either one goes
  down, the printer shows as disconnected even if it's printing perfectly.
- **The session expires every now and then** and you have to connect the account
  again. We'll let you know on screen.

And one that applies to every route: **BolloPrint doesn't send jobs to print**.
You still send the file from your slicer. What we do is read what the machine is
doing and log it.

## If you can't connect

| What you see | What it usually is |
|---|---|
| "Incorrect Bambu Lab account or password" and you're sure it's the right one | **This is the issue that wastes the most time.** If you've just created that password and have never used it, the account has its email verification pending and Bambu doesn't tell you. Sign in **once** on the Bambu website with those credentials, complete whatever it asks for, and come back. |
| "Incorrect Bambu Lab account or password" and you sign in to Bambu with Google or Apple | That route doesn't work here. Create a password on the Bambu website. |
| "There's no Bambu Lab account with that email" | The email isn't the one on the Bambu account. Check which one you sign in with on their app. |
| It mentions two-step verification | You need to turn it off in Bambu to be able to connect the account. |
| The code doesn't arrive | Check your spam and click **Resend code**. |
| It won't accept the code | It has probably expired. Ask for another one and paste it in whole. |

## Want more? Try the local agent

The cloud shows you everything, but it doesn't let you touch anything, and it only
exists for Bambu Lab. If you want more, what you need is the **local agent**: a
small program on a computer in your workshop that talks to the printers over your
own network. One is enough for the whole fleet, and it gives you:

- **almost every brand**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron…;
- **camera**, live while you're watching it, and with a final photo saved for every
  print;
- **pause, resume and cancel** from BolloPrint, without walking over to the
  machine;
- and it **copes with internet outages**: it keeps reading your printers and tells
  you everything once the connection is back.

:::info 💡 To send commands to a Bambu
The printer has to be in **LAN Mode** and in **Developer Mode**. Both are turned on
from its screen. Bear in mind: with LAN Mode, Bambu disconnects it from its cloud,
so from then on BolloPrint sees it through the agent. It's still **the same
printer**, with its name and its whole history, and it takes up **just one place**
in your plan.
:::

You'll find it step by step in the next tutorial:
[connecting your printers over your local network](/blog/connect-printers-local-network-agent).

:::info 💡 Any questions?
Write to us from the [contact page](/contact) or open a thread on
[our Discord](/help/soporte-por-discord).
:::

## Related documentation

- [Connecting printers](/help/conectar-impresoras) — the two routes and which one suits you
- [Cloud printers](/help/impresoras-por-la-nube) — the full reference for this screen
- [Compatible printers](/help/impresoras-compatibles) — look up your model here
- [Connection types](/help/tipos-de-conexion) — what each printer family allows
