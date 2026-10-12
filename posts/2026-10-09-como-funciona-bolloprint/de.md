---
slug: how-bolloprint-works
title: "Design, Teil, Variante, Produkt: BolloPrint in fünf Minuten erklärt"
description: Die vier Dinge hinter jeder Bestellung, welche Frage jedes davon beantwortet und warum es vier sind und nicht ein einziger Datensatz. Mit einem Handyhalter als Beispiel, von Anfang bis Ende.
date: 2026-10-09
updated: 2026-10-12
tags: [anleitungen]
cover: 01-el-mapa.webp
draft: true
---

Eine Bestellung kommt rein: **zwei Handyhalter, in Weiß**. Bevor du irgendetwas
tust, weiß BolloPrint schon, **was es dich kostet**, sie herzustellen, **was dir**
beim Verkauf **bleibt** und **wo die Dateien liegen**, um sie zu drucken.

Das weiß es, weil hinter dieser Bestellposition vier Dinge stehen, die du ein
einziges Mal vorbereitet hast: ein **Design**, ein **Teil**, eine **Variante** und
ein **Produkt**. Das sind die vier Wörter, die dir in BolloPrint am häufigsten
begegnen. Hier erfährst du, was jedes davon ist, warum es vier sind und nicht eins,
und wie sie in einer Bestellung landen.

::animation{id="how-it-works"}

## Vier Fragen, vier Dinge

Damit du sie nicht verwechselst, denk an die Frage, die jedes davon beantwortet:

| | Beantwortet … | Was es speichert |
|---|---|---|
| **Design** | Was ist es? | Die 3D-Dateien (STL, 3MF …), die Fotos und deine Notizen. Weder Kosten noch Preis. |
| **Teil** | Wie fertige ich es? | Material, Farbe, Nachbearbeitung, Gewicht und Zeit. **Hat Kosten.** |
| **Variante** | Wofür verkaufe ich es? | Den Preis und die Marge. **Das ist, was in eine Bestellung kommt.** |
| **Produkt** | Wie zeige ich es? | Name, Fotos und Beschreibung. Es fasst die Varianten zusammen. |

Wenn du dir nur diese Tabelle merkst, hast du schon die Hälfte des Artikels.

## Wir bauen es auf: ein Handyhalter

Wir bereiten den Halter aus der Bestellung vor, in der Reihenfolge, in der du es
auch tun würdest.

**1. Das Design.** Du lädst die STL des Halters und ein paar Fotos hoch. Das Design
ist genau das: das Modell und sonst nichts. Du hast noch nicht entschieden, womit
du es druckst, deshalb hat es keine Kosten.

**2. Die Teile.** Jetzt entscheidest du, wie du es fertigst: in **PLA schwarz** und
in **PETG weiß**. Das sind zwei Teile desselben Designs. Jedes hat sein Material,
sein Gewicht und seine Druckzeit, deshalb hat jedes **seine eigenen Kosten**, und
BolloPrint berechnet sie automatisch.

![Die Detailansicht des Halter-Designs, mit seinen zwei Teilen darunter: PLA schwarz und PETG weiß](/blog/media/2026-10-09-como-funciona-bolloprint/02-diseno-y-piezas.png)

:::info 💡 Ein Teil hängt immer an einem Design
Deshalb gibt es keine eigene Liste mit Teilen: Du findest sie im Design, zu dem
sie gehören.
:::

**3. Die Varianten.** Jetzt entscheidest du, wofür du es verkaufst. Du legst die
Variante „PLA schwarz“ für **12,90 €** an und die Variante „PETG weiß“ für
**15,90 €**. Jede weiß, aus welchem Teil sie besteht, und damit, was sie kostet;
mit dem Preis berechnet sie **die Marge** automatisch.

**4. Das Produkt.** Zum Schluss das, was der Kunde sieht: das Produkt
„Verstellbarer Handyhalter“, mit Name, Fotos und Beschreibung. Darin stecken die
beiden Varianten, wie die Farboptionen in jedem Onlineshop. Das ist es, was du zum
Beispiel auf Etsy veröffentlichst.

![Die Varianten des Halters als Tabs, die Variante in weißem PETG geöffnet: Kosten, Marge, Preis und das Teil, aus dem sie besteht](/blog/media/2026-10-09-como-funciona-bolloprint/03-producto-y-variantes.png)

## Warum vier und nicht ein Datensatz?

Weil sich **jedes der vier Dinge aus einem anderen Grund ändert**:

- Das **Design**, wenn du das Modell korrigierst.
- Das **Teil**, wenn du das Material wechselst oder deine Kosten pro Stunde steigen.
- Die **Variante**, wenn du den Preis änderst.
- Das **Produkt**, wenn du Fotos oder Beschreibung änderst.

Mit einem einzigen Datensatz müsstest du nach einer Korrektur der STL jede Farbe
anfassen, die du verkaufst. Getrennt korrigierst du sie einmal, im Design, und es
gilt für alles, was daran hängt.

Anders gesagt: Das Design ist das Rezept, das Teil ist das fertig gekochte Gericht,
und die Variante ist das, was mit Preis auf der Speisekarte steht.

### Der Beweis: ein Set

Stell dir vor, du verkaufst auch einen **Kabelorganizer**, und dir kommt die Idee
für ein Set: der schwarze Halter und der Organizer zusammen für 19,90 €.

Du musst nichts Neues vorbereiten. Du legst eine Variante „Büro-Set“ mit **zwei
Teilen darin** an: dem des schwarzen Halters und dem des Organizers. BolloPrint
addiert, was beide kosten, und gibt dir mit dem Preis die Marge des Sets.

![Die Variante Büro-Set, bestehend aus zwei Teilen; und das Teil des schwarzen Halters, das gleichzeitig von der Einzelvariante und vom Set genutzt wird](/blog/media/2026-10-09-como-funciona-bolloprint/04-variante-de-dos-piezas.webp)

Jetzt **wird das Teil des schwarzen Halters von zwei Varianten genutzt**: der
einzelnen und dem Set. Wenn morgen PLA teurer wird, änderst du dieses Teil ein
einziges Mal, und BolloPrint zeigt dir, welche Varianten es nutzen, damit du ihren
Preis prüfen kannst. Deshalb sind Teil und Variante zwei verschiedene Dinge.

Dasselbe gilt, wenn du mehrere Stück vom selben Artikel verkaufst: Ein „3er-Set“ ist
eine Variante mit dreimal demselben Teil.

![Der Block Teile, aus denen die Variante besteht, mit den zwei Teilen des Sets](/blog/media/2026-10-09-como-funciona-bolloprint/05-piezas-de-la-variante.png)

## Die Bestellung schließt den Kreis

Zurück zur Bestellung vom Anfang. Wenn du eine Bestellung anlegst, fügst du **eine
Variante** hinzu: Du suchst nach „Halter“, wählst „PETG weiß“, gibst 2 Stück ein,
und der Preis wird automatisch ausgefüllt.

Weil diese Variante weiß, aus welchen Teilen sie besteht, bringt die
Bestellposition schon alles andere mit:

- **was sie kostet und was dir bleibt**, weil die Teile Kosten haben und die
  Variante einen Preis;
- **Material, Farbe und Gewicht**, die aus ihren Teilen kommen;
- **die Dateien zum Drucken**: In der Position bringt dich die Option **Designs**
  zu den 3D-Modellen jedes Teils.

Wenn alles gedruckt ist, markierst du die Position als **gedruckt**, und die
Bestellung geht ihren Weg weiter durch die Produktion.

![Eine Bestellung mit zwei Positionen, dem weißen Halter und dem Set, und daneben die Teile, die gedruckt werden müssen, um sie auszuliefern](/blog/media/2026-10-09-como-funciona-bolloprint/06-del-pedido-a-la-impresora.webp)

Das ersparen dir die vier Dinge: Du schreibst nicht bei jeder Bestellung die Kosten
auf, suchst die STL nicht in irgendeinem Ordner und rechnest die Marge nicht von
Hand nach. Du hast es einmal vorbereitet, und jede Bestellung übernimmt es.

![Die Positionen einer Bestellung, mit geöffnetem Menü bei der Option Designs](/blog/media/2026-10-09-como-funciona-bolloprint/07-lineas-del-pedido.png)

## Das alles jedes Mal? Nein

Für einen einzigen Halter kann das nach viel Arbeit aussehen, und genau dafür gibt
es die **Schnellerstellung**. Du gibst ihr die STL, das Material, die Farbe und den
Preis in einem einzigen Formular, und BolloPrint legt auf einen Schlag Design, Teil,
Variante und Produkt an.

Das Ergebnis ist genau dasselbe, als hättest du es Schritt für Schritt gemacht. Wenn
du eines Tages eine weitere Farbe hinzufügen oder ein Set zusammenstellen willst,
ist schon alles an seinem Platz.

![Das Formular der Schnellerstellung mit Datei, Material, Farbe und Preis](/blog/media/2026-10-09-como-funciona-bolloprint/08-creacion-express.png)

:::info 💡 Noch Fragen?
Schreib uns über die [Kontaktseite](/contact) oder eröffne einen Thread in
[unserem Discord](/help/soporte-por-discord). Wenn du uns erzählst, was du
verkaufst, helfen wir dir, es aufzusetzen.
:::

## Verwandte Dokumentation

- [Katalog](/help/catalogo): die vier Ebenen, in der Referenz
- [Designs](/help/disenos): die Dateien, die Fotos und die Tags
- [Teile](/help/piezas): das Material und wie die Kosten berechnet werden
- [Produkte und Varianten](/help/productos-y-variantes): der Preis, die Marge und die Teile jeder Variante
- [Bestellungen](/help/pedidos): vom Verkauf bis zur Lieferung
- [Schnellerstellung](/help/creacion-express): alle vier auf einmal
- [Was ein gedrucktes Teil wirklich kostet](/blog/calculate-your-3d-printing-costs) — woher die Kosten jedes Teils kommen
