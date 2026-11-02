---
slug: install-bolloprint-agent-synology
title: De BolloPrint-agent installeren op een Synology-NAS
description: Staat er een Synology in je werkplaats, dan hoort de agent daar. Een echt DSM-pakket, geïnstalleerd vanuit het Pakketcentrum en met één klik gekoppeld. Geen Docker, geen code om te kopiëren en niets aan je router veranderen.
date: 2026-11-02
updated: 2026-11-02
tags: [handleidingen]
draft: true
---

Heb je een Synology in de werkplaats, dan heb je al de juiste plek voor de
BolloPrint-agent. Hij staat dag en nacht aan, zit op hetzelfde netwerk als je
printers en draait nu al de rest van je kleine diensten.

De agent komt als **echt DSM-pakket**: je installeert hem zoals elke andere
Synology-app en hij verschijnt in het hoofdmenu van DSM. Geen Docker, geen
Container Manager, geen tekst om te plakken en geen code om te kopiëren. Reken
op tien minuten.

:::info
Dit artikel gaat alleen over **de agent installeren op een Synology**. Wat de
agent is, welke merken hij ondersteunt en hoe je elke printer toevoegt, lees je
in de [handleiding over het lokale netwerk](/blog/connect-printers-local-network-agent).
Ga daar verder als je hier klaar bent.
:::

:::warning Het pakket voor Synology is in bèta
Het werkt, maar er kan nog een stap of twee veranderen. Klopt iets op je scherm
niet met wat je hier leest, laat het ons dan weten.
:::

## Waarom op de NAS en niet op je laptop

Omdat de agent alleen iets oplevert zolang hij wakker is. Draait hij op de
computer die je uitzet als je weggaat, dan ben je die uren kwijt: wat er is
geprint, hoe lang het duurde, of een print om drie uur 's nachts is gestopt. De
NAS staat toch al aan.

De rest krijg je er gratis bij: hij zit op het netwerk van de printers, en
daardoor vindt de agent ze zelf. En hij is licht: de NAS blijft al het andere
doen zoals altijd.

:::info 💡 Nee, je hoeft niet aan je router te komen
De agent **belt naar buiten** naar BolloPrint, zoals een browser die een
webpagina opent. Hij neemt nooit verbindingen vanaf het internet aan: geen open
poorten, geen vast IP-adres, geen firewallregels. Het werkt net zo goed achter
een thuisrouter als op een glasvezellijn met CGNAT.
:::

## Wat je eerst nodig hebt

Controleer dit nu, en niet halverwege:

- **DSM 7 of hoger.** Dat zie je in **Configuratiescherm → Infocentrum**. Met
  DSM 6 werkt het niet.
- **De processor van je NAS.** Op dezelfde plek, in het **Infocentrum**. Intel of
  AMD is 64-bit; bij ARM staat op de pagina van je model op de website van
  Synology of het 64- of 32-bit is. Dat heb je nodig om de juiste download te
  kiezen.
- **Een beheerdersaccount in DSM.** Alleen beheerders kunnen pakketten
  installeren en de pagina van de agent openen.
- **Eigenaar zijn van je werkplaats in BolloPrint.** Bij het koppelen zie je
  alleen de werkplaatsen waarvan je eigenaar bent.
- **De NAS en de printers op hetzelfde netwerk.** Op gescheiden netwerken
  (VLAN's) werkt de agent ook, maar dan voeg je elke printer toe via zijn IP.

## 1. Download het pakket

Ga in BolloPrint naar **Instellingen → Printers → Lokale agent → Nieuwe agent**
en kies **Synology**.

Er is een downloadknop per type processor: **Intel of AMD (64-bit)**,
**ARM (64-bit)** en **ARM (32-bit)**. Klik op de jouwe. Je krijgt een bestand
dat eindigt op `.spk`: dat is een DSM-pakket. Weet je niet welke, dan brengt de
link vlak onder de knoppen je naar de website van Synology om het voor je model
na te kijken.

![Nieuwe agent → Synology in BolloPrint: drie downloadknoppen, één per type processor, en daaronder de drie installatiestappen](/blog/media/2026-09-10-agente-synology/01-new-agent-synology.png)

Let op wat er **niet** op dat scherm staat: geen code, geen sleutel, niets om aan
te maken. De agent ontstaat pas als je hem koppelt, in stap 3.

## 2. Installeer het vanuit het Pakketcentrum

Open DSM in je browser en ga naar het **Pakketcentrum**. Klik rechtsboven op
**Handmatige installatie**, daarna op **Bladeren**, kies het `.spk`-bestand dat
je net hebt gedownload en klik op **Volgende**.

<!-- SCREENSHOT: 02-manual-install.png — DSM 7 (English UI) Package Center with the «Manual Install» dialog open and bolloprint-agent-…-x64.spk selected, Next button visible. -->

DSM waarschuwt je dat het pakket niet door Synology is gepubliceerd. Accepteer
dat om verder te gaan.

Daarna toont de wizard één enkele instelling: de **poort van de agentpagina**,
met **8257** al ingevuld. Laat die zo staan, tenzij DSM zegt dat hij al in
gebruik is; vul in dat geval **8364** in. Klik op **Volgende** en, in het
overzicht, op **Klaar**.

<!-- SCREENSHOT: 03-install-wizard.png — DSM 7 (English UI) BolloPrint Agent install wizard: the page-port field with 8257 and the text «After installing, open BolloPrint Agent from the DSM main menu and press “Link with BolloPrint”…». -->

Een minuut later staat het pakket op **Actief** en verschijnt **BolloPrint
Agent** in het hoofdmenu van DSM.

:::info 💡 ‘Dit pakket is niet compatibel met je model’
Dan heb je het pakket voor een andere processor gedownload. Ga terug naar
BolloPrint en download het andere.
:::

## 3. Koppel hem aan je werkplaats

Dit is de stap die het oude ‘kopieer deze code en plak hem daar’ vervangt.

Open het **hoofdmenu** van DSM (het pictogram linksboven) en klik op **BolloPrint
Agent**. Hij opent in een nieuw tabblad met de eigen pagina van de agent: daar
staat dat de agent nog bij geen enkele werkplaats hoort, met een korte **code**.

![De pagina van de agent, nog niet gekoppeld, met zijn code en de knop Koppelen met BolloPrint](/blog/media/2026-09-10-agente-synology/04-agent-page.png)

Klik op **Koppelen met BolloPrint**. BolloPrint gaat open (log in als dat nodig
is) en vraagt aan welke werkplaats je de agent toevoegt. Daarna toont het je het
**apparaat** — de naam van je NAS en ‘Synology’ — en de **code**. Controleer dat
het **dezelfde code** is als op de pagina van de agent en klik op **Toevoegen
aan werkplaats**.

<!-- SCREENSHOT: 05-confirm.png — BolloPrint (English UI) «Add an agent to <workshop>» confirmation: Device «<NAS name> · Synology», the same code as 04-agent-page, and the «Add to workshop» button. -->

Je komt terug op de pagina van de agent, waar nu **Gekoppeld aan** je werkplaats
staat.

:::warning 🔐 Bevestig alleen wat je zelf net hebt aangeklikt
Krijg je ooit een link om ‘een agent toe te voegen’ waar je niet om hebt
gevraagd, sluit hem dan. Een agent wordt alleen vanaf zijn eigen pagina
gekoppeld, en op een Synology kan alleen een beheerder van je NAS die pagina
openen.
:::

## 4. Controleer of het werkt

Ga in BolloPrint naar **Instellingen → Printers → Lokale agent**: daar staat de
agent met de naam van je NAS en het logo van Synology, **Online**. Dat is wat
telt: het hele circuit werkt.

![De Synology-agent Online in Instellingen → Printers → Lokale agent, met daaronder de printers die hij op het lokale netwerk heeft gevonden](/blog/media/2026-09-10-agente-synology/06-agent-online.png)

Binnen ongeveer een minuut begint hij printers op je netwerk te vinden. Ze
verschijnen bij **Printers op het lokale netwerk** en van daaruit voeg je ze
toe; de printers die niet vanzelf verschijnen, voeg je toe met **Toevoegen via
IP**. Hoe dat per merk gaat, staat allemaal in de
[handleiding over het lokale netwerk](/blog/connect-printers-local-network-agent).

## Bijwerken

**Je hoeft bijna nooit iets te doen:** de agent werkt zichzelf bij. Komt er een
nieuwe versie uit, dan downloadt hij die, controleert hij dat ze van ons is en
start hij ermee opnieuw op.

Alleen als BolloPrint je laat weten dat je de agent **met de hand moet
bijwerken**, doe je het zelf, en dan is het **het nieuwe pakket installeren over
het pakket dat je al hebt**: download het opnieuw vanaf dezelfde plek in
BolloPrint (**Lokale agent → Nieuwe agent → Synology**) en kies daarna in het
**Pakketcentrum → Handmatige installatie** het nieuwe bestand. DSM ziet dat het
al geïnstalleerd is en werkt het bij, zonder opnieuw naar de poort te vragen. De
agent blijft gekoppeld aan dezelfde werkplaats, met dezelfde printers en hun hele
geschiedenis. Je hoeft niets opnieuw te koppelen.

Zodra het pakket in de catalogus van het Pakketcentrum van Synology staat, laat
het Pakketcentrum je dat zelf weten en is bijwerken één klik.

:::warning Niet de-installeren om bij te werken
De-installeren wist de identiteit van de agent: wat je daarna installeert, is
een **nieuwe** agent die je opnieuw moet koppelen. Om bij te werken installeer je
altijd over het bestaande pakket heen.
:::

## Verhuizen of opnieuw beginnen

Een agent kun je niet ‘overzetten’, maar dat hoeft ook niet: wat verhuist, zijn
de printers, en die gaan mee met hun hele geschiedenis.

1. Installeer het pakket op de nieuwe NAS en koppel hem. Hij verschijnt als
   tweede agent.
2. Open elke printer met **Bewerken** in zijn menu **⋮** en zet hem over naar de
   nieuwe agent.
3. Heeft de oude agent geen printers meer, **verwijder** hem dan via het menu
   **⋮** van zijn regel.

Wil je de agent definitief weghalen: ga in DSM naar **Pakketcentrum → BolloPrint
Agent → Actie → Verwijderen** en **verwijder** daarna de agent via zijn menu
**⋮** in BolloPrint. Andersom werkt het ook: zodra je hem in BolloPrint
verwijdert, merkt de agent dat, vergeet hij zijn koppeling en biedt zijn pagina
weer **Koppelen met BolloPrint** aan. Hoe dan ook gaat er niets verloren: voeg je
later een van zijn printers opnieuw toe, dan komt die terug met zijn nummer en
zijn geschiedenis.

## Als er iets misgaat

| Wat je ziet | Wat het meestal is |
|---|---|
| De wizard zegt dat poort 8257 in gebruik is | Een andere toepassing op de NAS gebruikt hem. Vul 8364 in en ga verder. |
| ‘Niet compatibel met je model’ | Het pakket voor een andere processor. Download het juiste. |
| Bij het openen van BolloPrint Agent moet je inloggen op DSM | Open hem vanuit het hoofdmenu van DSM, ingelogd als beheerder. |
| Op de pagina staat dat de agent niet reageert | Het pakket staat stil of is nog aan het opstarten. Klik in het Pakketcentrum op **Actie → Uitvoeren** en wacht een paar seconden. |
| Je werkplaats staat niet in de lijst bij het koppelen | Je ziet alleen de werkplaatsen waarvan je **eigenaar** bent. Vraag de eigenaar om hem te koppelen. |
| ‘Dit koppelverzoek is ongeldig’, of het is verlopen | Ga terug naar de pagina van de agent en klik opnieuw op **Koppelen met BolloPrint**. |
| Na een herstart van de NAS duurt het even voordat hij terug is | Wacht een paar minuten: hij start op met DSM en blijft het proberen tot de NAS internet heeft. |
| Hij vindt geen printers | Zelfde netwerk? Zo niet, voeg ze dan toe via IP. Heb je er net een aangezet, klik dan op **Nu zoeken**. Staat de firewall van DSM aan, sta dan de poorten van BolloPrint Agent toe (hij staat in de lijst met toepassingen als je een regel aanmaakt). |

## Liever Docker?

Draait Container Manager al op je NAS en houd je alles liever in containers, dan
kan de agent ook als container draaien. De stappen staan in
[Agent in Docker](/help/agente-en-docker). Voor de meeste werkplaatsen
is het pakket eenvoudiger: het is een DSM-app zoals elke andere, en je koppelt
hem met één klik.

## Verder lezen

- [Agent op Synology](/help/agente-en-synology) — de volledige handleiding: installeren, bijwerken, verhuizen, de-installeren en problemen oplossen
- [De lokale agent](/help/el-agente-local) — wat hij doet, meerdere agents, diagnose
- [Printers via het lokale netwerk](/help/impresoras-por-red-local) — je machines toevoegen
- [Ondersteunde printers](/help/impresoras-compatibles) — zoek je model op
