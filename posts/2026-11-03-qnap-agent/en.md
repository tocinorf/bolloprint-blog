---
slug: install-bolloprint-agent-qnap
title: "The BolloPrint agent on a QNAP: install it from App Center, no Docker needed"
description: If your workshop already has a QNAP, the agent can live there as just another app. Download one file from BolloPrint, install it in App Center, press one button to link it. Now in beta.
date: 2026-11-03
updated: 2026-11-03
tags: [tutorials]
draft: true
---

If there's a QNAP in your workshop, you already have the best place for the
agent. It's on around the clock, it sits on the same network as your printers,
and nobody turns it off at the end of the day.

Until now, putting the agent there meant Container Station and a Docker
template. Not anymore: the agent now comes as a **native QNAP app**. You
download one file from BolloPrint, install it in App Center like any other
app, and link it to your workshop with a single button. No commands, no
templates, no codes to copy, and nothing to change on the router.

Count on ten minutes, most of them waiting for App Center.

:::warning 🧪 It's a beta
We've tested it end to end on QTS 5.2 with an Intel processor. The packages
for ARM processors are published too, but we haven't seen them running on a
real QNAP yet. If you have one, tell us how it went — good or bad, it helps.
:::

:::info
This post is only about **installing the agent on a QNAP**. What the agent is,
which brands it supports and how to add each printer are in the
[local network tutorial](/blog/connect-printers-local-network-agent) — carry
on there when you finish here.
:::

## Why the NAS and not your laptop

Because the agent only helps while it's awake. If it runs on the computer you
switch off when you leave, those hours are lost: you won't see what printed,
how long it took, or whether a print stopped at three in the morning. The NAS
is on anyway.

The rest comes free: it's on the printers' network, which is what lets the
agent find them on its own, and it's light — it doesn't need a powerful
machine, and it sits next to everything else your NAS already runs.

:::info 💡 You won't need to touch the router
The agent **calls out**, the same way your browser does when you open a web
page. It never receives connections from the internet. No ports to open, no
fixed IP, no firewall rules.
:::

## What you need before you start

- **A QNAP with QTS 4.5 or later**, always on and on the same network as your
  printers. If they're on different networks (VLANs, a guest network), the
  agent still works, but you'll add the printers by IP instead of having them
  found for you.
- **A QTS administrator account.** You need it to install apps and to open the
  agent's page.
- **To be the owner of the workshop** in BolloPrint. Only the owner can add
  agents.
- **To know your QNAP's processor.** It's on your model's page on QNAP's
  website, or in QTS under **Control Panel → System → System Status**. Most
  models are Intel or AMD; some, like the TS-x33 or TS-x31P series, are ARM.

## Step 1: download the package from BolloPrint

The agent isn't in QNAP's store yet, so you get it from BolloPrint — and only
from BolloPrint.

1. Go to **Settings → Printers** and open the **Local agent** tab.
2. Press **New agent** and choose the **QNAP** card, under **With a package
   or an installer**.

![The «New local agent» window in BolloPrint: the QNAP card among the agents you install with a package or an installer](/blog/media/2026-11-03-qnap-agent/01-new-agent-qnap-card-en.png)

3. Pick the download that matches your processor: **Intel or AMD (64-bit)**,
   **ARM (64-bit)** or **ARM (32-bit)**. You get a file ending in `.qpkg`.

![The QNAP card in BolloPrint: three downloads by processor and the six install steps under «How to install it»](/blog/media/2026-11-03-qnap-agent/02-qnap-downloads-en.png)

If you're not sure which processor yours has, the card links to QNAP's website.
Under **How to install it** you'll find the same steps as in this post, in
short. Nothing is created in BolloPrint at this point: the agent will show up
in your list once you link it.

## Step 2: allow apps without QNAP's signature

QNAP signs the apps in its own store. Ours is waiting to be published there, so
for now it comes without that signature and QTS needs your permission to
install it.

1. Sign in to QTS with your administrator account and open **App Center**.
2. Open its settings (the ⚙ icon at the top right).
3. Turn on **Allow installation of applications without a valid digital
   signature** and save.

<!-- SCREENSHOT 03-app-center-settings-en.png: QTS (English), App Center → Settings, the «Allow installation of applications without a valid digital signature» option turned on. -->

If you'd rather not leave it on, you can turn it off again once the agent is
installed. You'll need it again for the next update.

## Step 3: install the package

1. In App Center, press **Install Manually** (the manual install button at the
   top right).
2. Choose the `.qpkg` file you downloaded and press **Install**.

<!-- SCREENSHOT 04-install-manually-en.png: QTS (English), App Center «Install Manually» dialog with BolloPrintAgent_<version>_x86_64.qpkg selected. -->

3. QTS warns you that the app has no valid digital signature. That's expected:
   **accept it** and the installation carries on.

<!-- SCREENSHOT 05-signature-warning-en.png: QTS (English), the digital signature warning shown while installing the BolloPrint Agent package. -->

When it finishes, **BolloPrint Agent** appears among your apps.

<!-- SCREENSHOT 06-app-center-installed-en.png: QTS (English), App Center → My Apps with «BolloPrint Agent» installed and its «Open» button visible. -->

## Step 4: link it to your workshop

Press **Open**. QTS takes you to the agent's page. Only a QTS administrator who
is signed in can see it; anyone else is asked to sign in first.

The page says the agent doesn't belong to any workshop yet and shows a short
**code**.

![The agent's page on the QNAP: not linked yet, with its code and the «Link with BolloPrint» button](/blog/media/2026-11-03-qnap-agent/07-agent-page-en.png)

1. Press **Link with BolloPrint**. BolloPrint opens in your browser (sign in if
   you weren't already).
2. If you own more than one workshop, choose the one to add the agent to.
3. Check that the **code** BolloPrint shows is the same as the one on the
   agent's page, and press **Add to workshop**.

<!-- SCREENSHOT 08-add-to-workshop-en.png: BolloPrint (English UI), the «Add an agent to …» confirmation page with the device name, the code and the «Add to workshop» button. -->

4. You're taken back to the agent's page, which now says **Linked to** and your
   workshop's name.

:::warning 🔐 Only link what you've just installed
Only confirm in BolloPrint if you've just pressed **Link with BolloPrint** on
your own QNAP. If someone sends you a link to «link an agent», close it.
:::

## Step 5: check that it's online

Go back to **Settings → Printers → Local agent**. In under a minute the new
agent shows up **Online**, with the QNAP logo next to it.

<!-- SCREENSHOT 09-agent-online-en.png: BolloPrint (English UI), Settings → Printers → Local agent with the QNAP agent online and the QNAP logo on its row. -->

From here on it works like any other agent: the printers on your network show
up for you to add, or you add them by IP. The
[local network tutorial](/blog/connect-printers-local-network-agent) walks you
through each brand.

## Updating it later

Usually you don't do anything: **the agent updates itself**. When a new
version comes out, it downloads it, checks that it's ours and restarts with
it.

Only if BolloPrint tells you that your agent needs a **manual update** do you
install the new package over the old one: download it from the same QNAP card
in BolloPrint (for the same processor), check that the unsigned-apps option is
still on, and use **Install Manually** again. QTS replaces the program and
keeps its data, so the agent stays linked with its printers and their history.
There's nothing to link again.

## Moving it or removing it

- **Reinstalling it or moving it to another NAS** means linking a new agent.
  Install it on the new device, link it, and then delete the old one in
  BolloPrint from the **⋮** menu on its row. Your printers move to the new
  agent with their whole history as soon as you add them.
- **To remove it**, delete the agent in BolloPrint first, from the **⋮** menu
  on its row, then open **BolloPrint Agent** in App Center and press
  **Remove**. If you only delete it in BolloPrint, the agent stays installed
  without a workshop and its page goes back to offering **Link with
  BolloPrint**.

## If something doesn't work

- **QTS won't install the file**: check the unsigned-apps option. If it says
  the package isn't compatible, you downloaded the one for another processor.
- **«Open» asks you to sign in to QTS**: the page only opens for an
  administrator. Sign in as one and press **Open** again.
- **Linking says it couldn't reach BolloPrint**: the QNAP needs internet
  access. Check its connection and DNS under **Control Panel → Network**.
- **No printers are found**: if the QNAP and the printers are on different
  networks, add them by IP. If they're on the same network and still don't
  show up, add them by IP and tell us — it helps us finish the beta.

The full list is in the [QNAP agent guide](/help/agente-en-qnap).

:::info 💡 Need help?
Write to us from the [contact page](/contact) or open a thread on
[our Discord](/help/soporte-por-discord). Tell us your QNAP model and we'll
help you with the rest.
:::

Enjoy having your printers in view, with your QNAP as the bridge.

![Bollo, the BolloPrint mascot, next to the QNAP logo](/blog/media/2026-11-03-qnap-agent/10-bollo.webp "60%")

## Related documentation

- [The agent on a QNAP](/help/agente-en-qnap): the full guide, with updating and troubleshooting
- [The local agent](/help/el-agente-local): the full reference
- [Agent on Docker](/help/agente-en-docker): if you'd rather use Container Station (Docker)
- [Compatible printers](/help/impresoras-compatibles): look up your model here
