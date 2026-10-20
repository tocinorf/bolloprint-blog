---
slug: organize-your-3d-printing-catalog
title: "Van STL-bestanden naar producten in je winkel: zo organiseer je je 3D-printcatalogus"
description: Leer hoe je je STL-bestanden structureert, de kosten per onderdeel berekent en productvarianten maakt voor je 3D-printwinkel, zonder gedoe.
date: 2026-10-18
tags: [handleidingen]
cover: 01-portada.webp
---

Print je in 3D om te verkopen, dan ken je dit vast: tientallen mappen op je
computer met bestanden als `llavero_V2_FINAL_definitivo.stl`, zonder dat je nog
weet hoeveel filament die versie gebruikte of welk slicerprofiel je koos. En als
er een bestelling binnenkomt op Etsy, schat je je kosten op het oog en hoop je
dat je er geen geld op verliest.

In een 3D-printwerkplaats of printfarm raken de technische en de commerciële
chaos verstrikt als je ze niet scheidt. Daarom houdt BolloPrint ze uit elkaar.
In deze gids leggen we uit hoe **Ontwerpen, Onderdelen, Producten en Varianten**
in elkaar grijpen, zodat je van een stapel losse bestanden naar een overzichtelijke
catalogus gaat.

::animation{id="how-it-works"}

## Scheid het technische van het commerciële

Een van de meest gemaakte fouten bij het runnen van een werkplaats is een
STL-bestand behandelen alsof het het product is dat je verkoopt. In de praktijk
kan hetzelfde 3D-model in verschillende materialen worden geprint, uit meerdere
delen bestaan of in sets worden verkocht.

Daarom deelt BolloPrint je catalogus in drie niveaus in.

### Ontwerpen: de technische bibliotheek

Het **Ontwerp** is de plek voor je bronbestanden: de STL’s, OBJ’s of
3MF-projecten, samen met de foto’s van het model en je interne notities.

- **Zie het Ontwerp als de bouwtekening of het idee.** Er horen geen printtijden
  of grammen filament bij, want dezelfde STL kun je op verschillende schalen of in
  verschillende materialen printen.

![Het ontwerp “Keyring BolloPrint”, met zijn STL-bestand, zijn foto, zijn interne notities en zijn twee onderdelen: van 5 cm en van 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Onderdelen: het fysieke object

Een **Onderdeel** is wat je krijgt als je een Ontwerp een concrete
printconfiguratie geeft: het materiaal en het verbruik ervan (bijvoorbeeld zwart
PLA), de afmetingen en de printtijd.

- **Eén Ontwerp, meerdere Onderdelen.** Met dezelfde STL kun je een figuur in twee
  formaten printen, 5 cm en 10 cm: dat Ontwerp heeft dan twee Onderdelen, “Kleine
  sleutelhanger” en “Grote sleutelhanger”. Hetzelfde geldt voor andere kleuren of
  materialen.
- **Je slicerbestand doet het rekenwerk.** Upload je het bestand uit de slicer
  naar het Onderdeel (`.gcode`, `.gcode.3mf`, `.bgcode` of `.goo` voor hars), dan
  leest BolloPrint het gewicht en de printtijd uit en stelt ze aan je voor. Pas je
  ze toe, dan berekent het precies wat het maken van dat onderdeel je kost. Je kunt
  de gegevens ook met de hand invullen of corrigeren.

:::info 💡 Een 3MF-project werkt hier niet
De slicer moet de bouwplaat hebben gesliced om het gewicht en de tijd te kennen.
Een `.3mf`-project bevat die niet: dat hoort bij het Ontwerp. Upload naar het
Onderdeel de `.gcode.3mf` die de slicer exporteert.
:::

### Producten en Varianten: wat je klant ziet en koopt

Het **Product** is je etalage: wat je publiceert in je winkel of op een
marketplace zoals Etsy. De **Variant** is de concrete optie die de klant kiest.

- **Een Variant kan één of meer Onderdelen hebben**, elk met een eigen aantal.
- **Bijvoorbeeld:** je Product is “Bollo-figuur”, onze hond. Eén Variant kan
  “Groen” zijn, een andere “Oranje” en nog een andere de set “Groen + Oranje”,
  met beide Onderdelen erin. Je kunt materialen, formaten, afwerkingen of sets
  combineren zoals je wilt.

![De variant Green+Orange, met zijn twee onderdelen erin, een oranje en een groene, en zijn kosten, zijn marge en zijn prijs](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

:::info 💡 Een set kan Ontwerpen combineren
Een Variant kan Onderdelen van verschillende Ontwerpen bevatten: bijvoorbeeld een
set “Welkom bij BolloPrint” met de sleutelhanger en de Bollo-figuur.
:::

- **De marge rekent zichzelf uit.** Omdat elke Variant weet uit welke Onderdelen
  hij bestaat, vergelijkt BolloPrint je verkoopprijs met de werkelijke
  productiekosten en laat je de marge zien. Verander je de prijs, dan wordt de
  marge bijgewerkt, en andersom.

![De variant Green, met één onderdeel: kosten € 7,06, marge 70% en prijs € 23,54](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## Haast? Gebruik Snel aanmaken

Ben je net begonnen of heb je honderden modellen om te uploaden, dan kost het tijd
om Ontwerpen, Onderdelen en Producten een voor een in te stellen.

Daarvoor is de knop **Snel aanmaken** in de catalogus. Op één scherm upload je je
3D-bestand, vul je het materiaal, het gewicht, de tijd en de prijs in, en maakt
BolloPrint in één keer het Ontwerp, het Onderdeel, het Product en de Variant aan.
Het resultaat is hetzelfde als wanneer je het stap voor stap zou doen, dus daarna
kun je bijschaven wat je wilt.

![Het formulier Snel aanmaken: het 3D-bestand, de foto’s, het materiaal, het gewicht, de tijd, de kleuren, de kosten en de prijs](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## Je labels gaan vanzelf mee naar het product

Nog een detail dat je werk bespaart: de **labels** van een Ontwerp gaan vanzelf
mee naar zijn Producten.

Geef je een Ontwerp het label “Sleutelhangers” of “Figuren”, dan worden die
labels aan het Product toegevoegd zodra je de Onderdelen ervan aan een Variant
toevoegt. En verkoop je op Etsy, dan staan ze bij het publiceren van de
advertentie al ingevuld als *tags*, die helpen om je te vinden. Etsy staat er
maximaal 13 toe, van hoogstens 20 tekens, en je kunt ze vóór het publiceren nog
aanpassen.

## Begin met het ordenen van je catalogus

Een goed georganiseerde catalogus is niet alleen een kwestie van netheid: zo weet
je wat elk onderdeel je kost en hoeveel je aan elke bestelling verdient, en kun je
je werkplaats laten groeien zonder de controle te verliezen.

Wil je uitgebreider zien hoe je je catalogus instelt of geavanceerde varianten
maakt, kijk dan in de [documentatie van de catalogus](/help/catalogo). En vraag
je je af waar de kosten van elk Onderdeel vandaan komen, dan leggen we dat uit in
[wat een geprint onderdeel je echt kost](/blog/calculate-your-3d-printing-costs).

Ontdek [hoe je de productie van je werkplaats beheert met BolloPrint](/features),
je software voor 3D-printfarms.

Dat je catalogus net zo geordend mag groeien als hij begint.

![Bollo, de mascotte van BolloPrint, met een werkplaatsbril, naast zijn 3D-model als wireframe](/blog/media/2026-10-15-organizar-catalogo/07-bollo.webp "60%")

## Gerelateerde documentatie

- [Catalogus](/help/catalogo): de niveaus van de catalogus, in de naslag
- [Ontwerpen](/help/disenos): de bestanden, de foto’s en de labels
- [Onderdelen](/help/piezas): het materiaal, het slicerbestand en de kosten
- [Producten en varianten](/help/productos-y-variantes): de prijs, de marge en de onderdelen van elke variant
- [Snel aanmaken](/help/creacion-rapida): alles in één keer
- [Labels](/help/etiquetas): hoe je ze aanmaakt en beheert
