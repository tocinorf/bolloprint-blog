---
slug: calculate-your-3d-printing-costs
title: "Wat een geprint onderdeel je echt kost (en hoe je dat zonder gedoe berekent)"
description: Dat onderdeel met € 1,60 aan filament kost je € 9,36. We laten je zien hoe je de kosten van je werkplaats over je printuren verdeelt, zodat BolloPrint ze vanzelf bij elk onderdeel optelt.
date: 2026-10-15
updated: 2026-10-16
tags: [handleidingen]
cover: 01-portada.webp
---

Een onderdeel van 6 uur en 80 gram PLA. Wat kost het je?

Als je dacht “80 gram à € 20 per kilo, **€ 1,60**”, dan heb je alleen het
**materiaal** berekend. In een gewone werkplaats is dat **maar een klein deel**
van wat het onderdeel je werkelijk kost.

In een werkplaats met drie printers, met het onderdeel geverfd en verpakt, ziet
de volledige berekening er zo uit:

| | |
|---|---|
| Materiaal | € 1,60 |
| 6 uur printer | € 5,16 |
| Afwerking (geverfd) | € 2,00 |
| Extra kosten (verpakking) | € 0,60 |
| **Werkelijke kosten van het onderdeel** | **€ 9,36** |

**Bijna zes keer zoveel.** Het verschil is geen afrondingsfout: het is de huur,
de stroom, de slijtage van de printers, de boekhouder en de onderdelen die
mislukken. Dat betaal je allemaal; de vraag is of je het ook doorberekent.

Hier zie je hoe je die kosten in de kosten van elk onderdeel verwerkt. **Je
stelt het één keer in** en daarna wordt het vanzelf toegepast op elk onderdeel
dat je aanmaakt.

::animation{id="part-cost"}

## Waar die € 5,16 vandaan komt

Het idee is simpel: je telt **alles op wat de werkplaats je per maand kost** en
deelt dat door **de uren dat je echt print**. Zo krijg je wat **één printeruur**
je kost, en hoef je dat alleen nog te vermenigvuldigen met de uren van het
onderdeel.

Met de getallen uit het voorbeeld:

- **Uren:** drie printers, tien uur per dag, vijfentwintig dagen per maand →
  **750 uur**.
- **Kosten:** huur, boekhouder, software en de afschrijving van de machines
  samen zijn zo’n **€ 516 per maand**. Verdeeld: € 0,69 per uur. Met de stroom
  erbij komen de **vaste kosten per uur** op **€ 0,72**.
- **Toeslagen:** 5% voor onderhoud, 10% faalpercentage en 5% voor onvoorziene
  kosten brengen het op **€ 0,86 per uur**. Voor zes uur: € 5,16.

Dat is precies de berekening die de sectie **Kosten** van BolloPrint maakt, in
**Instellingen → Kosten**. Alleen de **Eigenaar** en de **Beheerders** zien
die.

![De sectie Kosten in Instellingen](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

Ben je net begonnen? Dan leidt de taak **Bereken wat elk onderdeel je kost** in
**Eerste stappen**, op **Start**, je door precies deze schermen, het ene na het
andere, en kleurt elk scherm groen zodra je het opslaat.

## De uren dat je echt print

Begin met de uren: dat is het getal dat de meeste mensen verkeerd inschatten en
dat de uitkomst het sterkst verandert. Je vindt het in **Kosten per uur →
Printuren**, en het zijn drie velden:

**Printers × Uren / dag × Dagen / maand**

Vul in **wat er echt gebeurt, niet het theoretische maximum**. Heb je drie
printers, maar draaien ze gemiddeld acht uur per dag, dan is het acht. Geen
vierentwintig.

Het is verleidelijk om een hoog getal in te vullen, want hoe hoger het is, hoe
goedkoper het uur uitvalt. Maar de kosten betaal je toch, en wat je niet over
je onderdelen verdeelt, betaal je aan het eind van de maand zelf.

![Het tabblad Printuren, met de drie velden en de uitkomst](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Wat de werkplaats je kost

Staan de uren erin, dan is het tijd om je kosten in te voeren. Op het tabblad
**Vaste kosten** voeg je ze een voor een toe; BolloPrint sorteert ze per type
en vraagt van elke post alleen wat nodig is:

| Type | Wat je invult |
|---|---|
| **Vaste kosten** | Huur, internet, boekhouder, verzekeringen… het bedrag per maand |
| **Printer** | Wat hij je kostte en in hoeveel jaar je hem afschrijft |
| **Software** | Het abonnement op je slicer, op BolloPrint, op wat je ook gebruikt |
| **Personeelskosten** | Het salaris en hoeveel mensen |
| **Elektriciteit** | Hoeveel kW één printer verbruikt en wat je per kWh betaalt |

Het hoeft niet tot op de cent te kloppen: een redelijk getal vandaag is meer
waard dan het perfecte getal volgend jaar.

:::warning ⚠️ Voer dezelfde kosten niet twee keer in
De bedragen **per maand** gaan over **de hele werkplaats**: de huur zet je er
maar één keer in. De bedragen **per geprint uur** — zoals stroom naar verbruik —
gaan over **één printer**: vul daar het verbruik van een gemiddelde machine in,
niet dat van de hele werkruimte.
:::

Helemaal onderaan staat de berekening al klaar, dezelfde als aan het begin:

> **kosten per maand ÷ je printuren = wat één uur je “kaal” kost**

Dat zijn je **vaste kosten per uur**: € 0,72 in het voorbeeld.

![De kosten van de werkplaats op het tabblad Vaste kosten, gegroepeerd per type, en de berekening die op € 0,72 per uur uitkomt](/blog/media/2026-09-12-costes-reales/03b-gastos-fijos.png)

## Wat je weet dat er gaat gebeuren

De vaste kosten laten buiten wat er gebeurt zonder vaste rekening: nozzles gaan
kapot, en **soms mislukt een onderdeel en moet het opnieuw**.

Daarvoor is het tabblad **Kosten per uur**: dat telt een paar percentages op bij
de vaste kosten per uur: onderhoud, faalpercentage en onvoorziene kosten.

Het faalpercentage is het belangrijkst, en het wordt het vaakst overgeslagen.
Gaat van elke tien onderdelen er één de prullenbak in, dan **betalen de negen
goede voor het mislukte**. Neem je het hier niet mee, dan betaal je het zelf.

De uitkomst zijn je **kosten per uur**: € 0,86 in het voorbeeld. Dat is je
echte getal, en dat wordt op elk onderdeel toegepast.

:::info 💡 De winstmarge hoort hier niet
Hier gaan alleen **kosten** in. Hoeveel je wilt verdienen, bepaal je later, bij
het product, want dat is een commerciële beslissing.
:::

![De toeslagen voor onderhoud, faalpercentage en onvoorziene kosten op de vaste kosten per uur, tot € 0,86 per uur](/blog/media/2026-09-12-costes-reales/03c-coste-por-hora.png)

## Het materiaal en de extra’s

Blijft het eenvoudigste deel over, in **Standaardwaarden**:

- **De prijs van elk materiaal**, per kilo. Die is **per type**, niet per
  familie: PLA en TPU kosten niet hetzelfde.
- **De afwerkingen**: hoeveel je erbij rekent als het onderdeel nabewerkt of
  geverfd wordt.
- **De extra kosten**: verpakking, bevestigingsmateriaal, magneten, inserts,
  arbeid. Per post kies je of die **per stuk** of **per bouwplaat** wordt
  berekend.
- **De marges**: je standaardmarge, en vanaf welk percentage we je in rood of
  oranje waarschuwen.

:::info 💡 Staat het materiaal in je materiaalvoorraad, dan telt de voorraad
Deze prijzen zijn een richtwaarde, voor als er niets achter zit. Komt het
onderdeel van een spoel die je met de echte kosten hebt ingevoerd, dan gebruiken
we die.
:::

![Standaardwaarden: de marges met hun kleurwaarschuwingen en de prijs per kilo van elk materiaal](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## En zo komt het bij je onderdeel

De vier stappen hiervoor komen uit op één getal: **wat één printeruur je kost**.
Vanaf daar is elk onderdeel een optelsom:

> de **uren × je kosten per uur**
> **+** het **materiaal** dat erin gaat
> **+** de **afwerking**, als het nabewerkt of geverfd wordt
> **+** de **extra kosten** die je eraan toevoegt

Eén detail is goed om te begrijpen, want het verklaart waarom het loont om het
printbed vol te zetten: **er wordt per bouwplaat gerekend, niet per onderdeel**.
BolloPrint berekent wat de hele bouwplaat kost en **verdeelt dat over de
onderdelen die ervan af komen**. Daarom worden de extra kosten die je **per
bouwplaat** markeert maar één keer berekend — of je de onderdelen nu een voor
een print of met twintig tegelijk — en die **per stuk** bij elk onderdeel.

Bovendien **bewaart elk onderdeel de kosten per uur waarmee het is berekend**.
Dat is met opzet: zo blijven de kosten van wat je vorig jaar printte wat ze
toen waren. Daarom is er de knop **Herberekenen**, die je verderop tegenkomt.

## Nu heb je je getal

Om de uitkomst te zien, ga je naar **Kosten → Overzicht**. Het blok **Voorbeeld
met jouw kosten** neemt een voorbeeldbouwplaat en laat je de hele berekening
zien **met jouw waarden**: hoeveel materiaal is, hoeveel printen, hoeveel
afwerking en wat het onderdeel uiteindelijk kost.

![Het blok Voorbeeld met de volledige uitsplitsing van een onderdeel](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Als je kosten veranderen

Je getallen blijven niet altijd hetzelfde: de stroom wordt duurder, je koopt een
extra printer of je verhuist. Werk je ze bij, dan **veranderen de onderdelen die
je al had niet vanzelf**. Dat is met opzet: elk onderdeel bewaart de kosten
waarmee het is berekend, en je wilt niet dat de kosten van alles wat je vorig
jaar maakte worden overschreven.

Wil je het op alles toepassen, dan vind je in **Overzicht** een teller met
onderdelen **Te herberekenen** en de knop **Herberekenen**. Jij bepaalt wanneer.

:::info 💡 Je verkoopprijzen blijven onaangeroerd
Herberekenen werkt de **kosten** en de *voorgestelde* prijs bij. De prijs die je
zelf hebt ingevuld, blijft staan. Wat je wel ziet bewegen, is de
**marge**-indicator.
:::

## Koop ik er een printer bij?

Met je kosten ingesteld kun je die vraag met getallen beantwoorden. In
**Kostenscenario's** verander je het aantal printers, de uren of de dagen en zie
je wat er met je kosten per uur zou gebeuren. Het is alleen een simulatie: er
verandert niets aan je instellingen.

Wat het het best laat zien, is dat **de curve ophoudt met dalen**. Van één naar
vijf printers deelt de kosten per uur bijna door vijf. Van twintig naar honderd
verandert ze nauwelijks, want sommige kosten — zoals stroom — betaal je voor elk
geprint uur en worden over niemand verdeeld.

![De kostenscenario’s, met de curve van de kosten per uur](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Het instellen kost vier schermen en een deel van een middag. In ruil daarvoor
heeft elk onderdeel dat je aanmaakt zijn echte kosten, en weet je of je geld
verdient zonder het met de hand uit te rekenen.

:::info 💡 Zullen we je helpen met je getallen?
Weet je niet waar je moet beginnen, stuur ons dan een bericht via de
[contactpagina](/contact) of op [onze Discord](/help/soporte-por-discord). We
hebben dit al heel wat keren gedaan.
:::

Dat je getallen altijd mogen kloppen.

![Bollo, de mascotte van BolloPrint, met een werkplaatsbril, peinzend tussen met krijt geschreven sommen](/blog/media/2026-09-12-costes-reales/07-bollo.webp "60%")

## Gerelateerde documentatie

- [Kosten](/help/costes): de volledige naslag van de sectie
- [Onderdelen](/help/piezas): hoe de kosten van elk onderdeel worden berekend
- [Producten en varianten](/help/productos-y-variantes): van kosten naar verkoopprijs
- [Materiaalvoorraad](/help/inventario): zodat het materiaal tegen de echte kosten wordt gerekend
