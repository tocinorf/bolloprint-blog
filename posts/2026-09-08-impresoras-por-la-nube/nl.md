---
slug: connect-bambu-lab-printers-cloud
title: "Verbind je Bambu Lab-printers in vijf minuten met BolloPrint"
description: Zonder iets te installeren en zonder wachtwoord. Je vult het e-mailadres van je Bambu Lab-account in, bevestigt een code en je printers verschijnen vanzelf, met wat ze aan het printen zijn en hun hele geschiedenis.
date: 2026-10-12
updated: 2026-10-16
tags: [handleidingen]
cover: 01-portada.webp
---

Heb je meerdere Bambu's aan het werk, dan ken je de routine vast: om te zien hoe
het gaat, loop je naar elke printer en kijk je op het scherm. Is de eerste klaar?
Heeft de tweede nog materiaal? Hoeveel uur heb je deze maand geprint?

Dat kun je allemaal op één scherm hebben, en **zonder iets te installeren**. Je
koppelt je Bambu Lab-account aan BolloPrint en je printers verschijnen vanzelf.
Het kost zo'n vijf minuten.

::animation{id="bambu-cloud"}

## Wat je van elke printer ziet

Live en zonder iets aan te raken:

- of hij aanstaat en verbonden is;
- wat hij aan het printen is, het **percentage** dat klaar is en hoelang het nog
  duurt;
- de temperatuur van de nozzle en van het bed;
- de geladen **materialen**, sleuf voor sleuf, als je een AMS hebt;
- de meldingen van de machine zelf.

En wat je aan het eind van de maand het meest merkt: **elke print wordt
vastgelegd**, met de duur, het materiaal en de kosten. Je hoeft niets bij te
houden.

![De kaart van een printer die aan het printen is, met de voortgang en de temperaturen](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora-en.png "42%")

## Wat je nodig hebt

Zorg dat je deze drie dingen bij de hand hebt voordat je begint:

- Toegang tot BolloPrint als **Eigenaar** of **Beheerder**. Met een andere rol
  zie je dit scherm niet.
- Het **e-mailadres** van je Bambu Lab-account. Het wachtwoord heb je niet nodig.
- Die **mailbox** open: Bambu stuurt je een code.

## Open het printerscherm

Alles gebeurt op één plek: **Instellingen → Printers**. Daar zie je drie
tabbladen:

- **Printers**: de lijst met al je machines, hoe ze ook binnenkomen.
- **Lokale agent**: om ze via je eigen netwerk te verbinden. Dat leggen we uit in
  [een ander artikel](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: het tabblad dat je nu nodig hebt.

Open **Bambu Cloud**.

![Het scherm Instellingen → Printers met de drie tabbladen](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas-en.png)

## Vul het e-mailadres van je Bambu-account in

Gebruik dat van je Bambu Lab-account (dat adres, geen ander adres van jou) en klik
op **Code verzenden**.

![Het formulier van Bambu Cloud, met het e-mailadres van het account ingevuld en de knop Code verzenden](/blog/media/2026-09-08-impresoras-por-la-nube/03-correo-en.png)

:::info 💡 We vragen je niet om je wachtwoord
BolloPrint **ziet het nooit en bewaart het niet**: om te verbinden is de code
genoeg die Bambu naar je e-mailadres stuurt.
:::

## Bevestig de code uit de e-mail

Bambu stuurt je een **code van 6 cijfers** vanaf `noreply@bambulab.com` (de
e-mail is in het Engels). Zie je hem niet, **kijk dan in je spammap**: daar komt
hij vaak terecht. Vul hem op hetzelfde scherm in en klik op **Verifiëren en
verbinden**.

![Het veld voor de code van 6 cijfers en de knop Verifiëren en verbinden](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-en.png)

Drie details besparen je een tweede poging:

- De code **verloopt na 10 minuten** en alleen de laatste is geldig. Ben je te
  laat, klik dan op **Code opnieuw verzenden**.
- Je kunt hem **plakken zoals hij binnenkomt**: spaties en streepjes worden
  vanzelf weggehaald.
- Heb je het verkeerde e-mailadres ingevuld, klik dan op **E-mailadres
  wijzigen**.

Als de code is geaccepteerd, zie je **Account geverifieerd en verbonden**.

## Je printers staan er al in

Je hoeft ze niet een voor een toe te voegen: **alle printers van dat account
verschijnen vanzelf** op het tabblad **Printers**, elk met zijn naam en
serienummer.

![De printerlijst met de zojuist verschenen Bambu-machines](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas-en.png)

Bovenaan zie je een teller als `3 / 6 actief`: dat zijn de printers die in je
abonnement zitten. Met de schakelaar in elke rij zet je de printers aan of uit
die je wilt. Een uitgeschakelde printer telt niet mee voor de limiet, maar
**houdt zijn hele geschiedenis**. En verbind je een hele vloot en is er niet voor
iedereen plaats, dan komen de printers die niet passen uitgeschakeld binnen, in
plaats van dat de limiet van je abonnement wordt overschreden.

## Wat je via de cloud niet kunt doen

Het is handig om dit vanaf het begin te weten, zodat je niet zoekt naar opties die
er niet zijn:

- **Het is alleen-lezen.** Via de cloud kun je vanuit BolloPrint niet pauzeren,
  hervatten of annuleren: Bambu accepteert die opdrachten alleen via je lokale
  netwerk en met de printer in een bepaalde modus. Dat zien we aan het eind.
- **Er is geen camera.** Je ziet wel de afbeelding van de slicer van de opdracht,
  maar dat is een voorbeeld, niet wat er in de machine gebeurt.
- **Het hangt af van twee internetverbindingen**, die van jou en die van Bambu.
  Valt een van beide uit, dan staat de printer als niet verbonden, ook al print
  hij gewoon door.
- **De sessie met Bambu duurt 90 dagen, maar wordt vanzelf verlengd**: BolloPrint
  verlengt hem voordat hij verloopt en je hoeft niet opnieuw in te loggen. Alleen
  als Bambu hem zelf afsluit, laten we het je op het scherm weten, en dan is het
  genoeg om een nieuwe code aan te vragen.

En iets wat voor elke manier van verbinden geldt: **BolloPrint verstuurt geen
printopdrachten**. Het bestand stuur je nog steeds vanuit je slicer; BolloPrint
leest wat de machine doet en legt het vast.

## Veelvoorkomende problemen

### En als ik bij Bambu inlog met Google of Apple?

Vul het e-mailadres van dat Google- of Apple-account in: de code komt daar net zo
goed aan. Je hoeft geen wachtwoord meer aan te maken.

### Waarom staat er dat er geen account met dat e-mailadres is?

Zie je **“Er is geen Bambu Lab-account met dat e-mailadres”**, dan is het niet het
adres van je Bambu-account: Bambu stuurt de code toch, maar als je hem invult,
wordt hij geweigerd. Kijk met welk adres je in de app van Bambu inlogt en klik op
**E-mailadres wijzigen**.

### Moet ik het account af en toe opnieuw koppelen?

Nee. De sessie duurt 90 dagen en BolloPrint verlengt hem vanzelf voordat hij
verloopt. Als Bambu hem ooit zelf afsluit, zie je **“Sessie verlopen”** en een
knop **Opnieuw inloggen**: je vraagt een nieuwe code aan en klaar, zonder iets te
ontkoppelen.

### Wat doe ik als de code niet aankomt of niet wordt geaccepteerd?

Komt hij niet aan, kijk dan in je spammap en klik op **Code opnieuw verzenden**.
Wordt hij niet geaccepteerd, dan is hij waarschijnlijk verlopen of is het niet de
laatste die je hebt aangevraagd: vraag een nieuwe aan en plak hem in zijn geheel.

## Wil je meer: de lokale agent

De cloud laat je alle informatie zien, maar je kunt niets met de printers doen,
en hij bestaat alleen voor Bambu Lab. Wil je meer, dan is de **lokale agent** de
oplossing: een klein programma dat je op een computer in je werkplaats installeert
en dat via je eigen netwerk met de printers praat. Eén is genoeg voor je hele
vloot, en je krijgt:

- **bijna alle merken**: Prusa, Elegoo, Anycubic, FlashForge, Snapmaker en alle
  printers met Klipper (QIDI, Sovol, Voron…);
- **camera**, live en met een eindfoto die bij elke print wordt bewaard;
- **pauzeren, hervatten en annuleren** vanuit BolloPrint, zonder naar de machine
  te lopen;
- **bestand tegen internetstoringen**: hij blijft je printers uitlezen en stuurt
  alles door zodra de verbinding terug is.

:::info 💡 Om opdrachten naar een Bambu te sturen
De printer moet in **LAN-modus** en in **Ontwikkelaarsmodus** staan. Beide zet je
aan op het scherm van de printer, en de tweede koppelt hem los van Bambu Cloud:
vanaf dat moment zie je hem alleen nog via de agent.
:::

We leggen het stap voor stap uit in
[verbind je printers via je eigen netwerk](/blog/connect-printers-local-network-agent).

Heb je een vraag, schrijf ons dan via de [contactpagina](/contact) of op
[onze Discord](/help/soporte-por-discord).

Veel plezier met al je printers op één scherm.

![Bollo, de mascotte van BolloPrint, met een werkplaatsbril, dromend van een 3D-printer](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp "60%")

## Gerelateerde documentatie

- [Printers verbinden](/help/conectar-impresoras): de twee manieren en welke bij je past
- [Printers via de cloud](/help/impresoras-por-la-nube): de volledige naslag van dit scherm
- [Compatibele printers](/help/impresoras-compatibles): zoek hier je model
- [Verbindingstypen](/help/tipos-de-conexion): wat elk type printer mogelijk maakt
