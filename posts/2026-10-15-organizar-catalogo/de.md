---
slug: organize-your-3d-printing-catalog
title: "Von STL-Dateien zu Produkten in deinem Shop: So organisierst du deinen 3D-Druck-Katalog"
description: So strukturierst du deine STL-Dateien, berechnest die Kosten pro Stück und legst Produktvarianten für deinen 3D-Druck-Shop an, ganz ohne Chaos.
date: 2026-10-18
tags: [anleitungen]
cover: 01-portada.webp
---

Wenn du 3D-Drucke verkaufst, kennst du diese Szene bestimmt: Dutzende Ordner auf
dem Rechner mit Dateien wie `llavero_V2_FINAL_definitivo.stl`, und du weißt nicht
mehr, wie viel Filament diese Version gebraucht hat oder welches Slicer-Profil du
benutzt hast. Und wenn auf Etsy eine Bestellung reinkommt, schätzt du deine Kosten
über den Daumen und hoffst, dass du kein Geld verlierst.

In einer Werkstatt oder einer 3D-Druckfarm vermischen sich das technische und das
kaufmännische Durcheinander, wenn du sie nicht trennst. Deshalb behandelt
BolloPrint beides getrennt. In dieser Anleitung erklären wir dir, wie **Designs,
Stücke, Produkte und Varianten** zusammenspielen, damit aus einem Haufen loser
Dateien ein geordneter Katalog wird.

::animation{id="how-it-works"}

## Trenne Technik und Verkauf

Einer der häufigsten Fehler bei der Verwaltung einer Werkstatt ist, eine STL-Datei
so zu behandeln, als wäre sie das Produkt, das du verkaufst. In der Praxis lässt
sich dasselbe 3D-Modell in verschiedenen Materialien drucken, aus mehreren Teilen
bestehen oder im Set verkaufen.

Deshalb gliedert BolloPrint deinen Katalog in drei Ebenen.

### Designs: die technische Bibliothek

Das **Design** ist der Container für deine Quelldateien: die STL-, OBJ- oder
3MF-Projekte, zusammen mit den Fotos des Modells und deinen internen Notizen.

- **Stell dir das Design als Bauplan oder Idee vor.** Es enthält weder Zeiten noch
  Gramm Filament, denn dieselbe STL lässt sich in verschiedenen Maßstäben oder mit
  verschiedenen Materialien drucken.

![Das Design „Keyring BolloPrint“ mit seiner STL-Datei, seinem Foto, seinen internen Notizen und seinen zwei Stücken: 5 cm und 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Stücke: das physische Objekt

Ein **Stück** entsteht, wenn du ein Design nimmst und ihm eine konkrete
Druckkonfiguration gibst: das Material und seinen Verbrauch (zum Beispiel
schwarzes PLA), die Maße und die Druckzeit.

- **Ein Design, mehrere Stücke.** Mit derselben STL kannst du eine Figur in zwei
  Größen drucken, 5 cm und 10 cm: Dieses Design hat dann zwei Stücke, „Kleiner
  Schlüsselanhänger“ und „Großer Schlüsselanhänger“. Dasselbe gilt für
  unterschiedliche Farben oder Materialien.
- **Deine geslicte Datei rechnet für dich.** Wenn du die Slicer-Datei (`.gcode`,
  `.gcode.3mf`, `.bgcode` oder `.goo` für Harz) in das Stück hochlädst, liest
  BolloPrint Gewicht und Druckzeit aus und schlägt sie dir vor. Wenn du sie
  übernimmst, berechnet es, was dich die Herstellung genau dieses Stücks kostet.
  Du kannst die Werte auch von Hand eintragen oder korrigieren.

:::info 💡 Ein 3MF-Projekt funktioniert hier nicht
Der Slicer muss die Platte gesliced haben, damit Gewicht und Zeit bekannt sind. Ein
`.3mf`-Projekt enthält sie nicht: Es gehört ins Design. Lade in das Stück die
`.gcode.3mf` hoch, die der Slicer exportiert.
:::

### Produkte und Varianten: was deine Kunden sehen und kaufen

Das **Produkt** ist dein Schaufenster: das, was du in deinem Shop oder auf einem
Marktplatz wie Etsy veröffentlichst. Die **Variante** ist die konkrete Option, die
der Kunde auswählt.

- **Eine Variante kann ein oder mehrere Stücke enthalten**, jedes mit seiner Menge.
- **Zum Beispiel:** Dein Produkt ist „Bollo-Figur“, unser Hund. Eine Variante kann
  „Grün“ sein, eine andere „Orange“ und eine weitere das Set „Grün + Orange“, mit
  beiden Stücken darin. Materialien, Größen, Oberflächen oder Mengen kannst du
  beliebig kombinieren.

![Die Variante Green+Orange mit ihren zwei Stücken, einem orangen und einem grünen, sowie ihren Kosten, ihrer Marge und ihrem Preis](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

:::info 💡 Ein Set kann Designs kombinieren
Eine Variante kann Stücke aus verschiedenen Designs enthalten: zum Beispiel ein
„Büro-Set“ mit dem Handyhalter und dem Kabelorganizer.
:::

- **Die Marge ergibt sich von selbst.** Weil jede Variante weiß, aus welchen
  Stücken sie besteht, vergleicht BolloPrint deinen Verkaufspreis mit den echten
  Produktionskosten und zeigt dir die Marge an. Änderst du den Preis, aktualisiert
  sich die Marge, und umgekehrt.

![Die Variante Green mit nur einem Stück: Kosten von 7,06 €, Marge von 70 % und Preis von 23,54 €](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## Keine Zeit? Nutze die Schnellerstellung

Wenn du gerade anfängst oder Hunderte Modelle hochladen musst, kostet es Zeit,
Designs, Stücke und Produkte einzeln einzurichten.

Dafür gibt es im Katalog den Button **Schnellerstellung**. Auf einem einzigen Bildschirm lädst du deine 3D-Datei hoch, gibst
Material, Gewicht, Zeit und Preis an, und BolloPrint legt Design, Stück, Produkt
und Variante in einem Schritt an. Das Ergebnis ist dasselbe, als würdest du es
Schritt für Schritt machen, du kannst also danach alles nach Belieben anpassen.

![Das Formular der Schnellerstellung: die 3D-Datei, die Fotos, das Material, das Gewicht, die Zeit, die Farben, die Kosten und der Preis](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## Deine Tags wandern von selbst ins Produkt

Noch ein Detail, das dir Arbeit spart: Die **Tags** (Schlagwörter) eines Designs
gehen automatisch auf seine Produkte über.

Wenn du ein Design mit „Schlüsselanhänger“ oder „Figuren“ taggst und dann seine
Stücke zu einer Variante hinzufügst, werden diese Tags dem Produkt hinzugefügt. Und
wenn du auf Etsy verkaufst, sind sie beim Veröffentlichen des Angebots schon als
*Tags* eingetragen, die dir helfen, gefunden zu werden. Etsy erlaubt bis zu 13 mit
jeweils höchstens 20 Zeichen, und du kannst sie vor dem Veröffentlichen noch
anpassen.

## Bring Ordnung in deinen Katalog

Ein gut organisierter Katalog ist nicht nur eine Frage der Ordnung: So weißt du,
was dich jedes Stück kostet, wie viel du an jeder Bestellung verdienst, und kannst
deine Werkstatt wachsen lassen, ohne den Überblick zu verlieren.

Wenn du genauer sehen willst, wie du deinen Katalog einrichtest oder komplexere
Varianten anlegst, wirf einen Blick in die
[Katalog-Dokumentation](/help/catalogo). Und wenn du dich fragst, woher die Kosten
jedes Stücks kommen, erklären wir das in
[was ein gedrucktes Teil wirklich kostet](/blog/calculate-your-3d-printing-costs).

Entdecke, [wie du die Produktion deiner Werkstatt mit BolloPrint steuerst](/features),
deiner Software für 3D-Druckfarmen.

Möge dein Katalog so geordnet wachsen, wie er beginnt.

![Bollo, das Maskottchen von BolloPrint, mit Werkstattbrille neben seinem 3D-Modell als Drahtgitter](/blog/media/2026-10-15-organizar-catalogo/07-bollo.webp "60%")

## Weiterführende Dokumentation

- [Katalog](/help/catalogo): die Ebenen des Katalogs, in der Referenz
- [Designs](/help/disenos): die Dateien, die Fotos und die Tags
- [Stücke](/help/piezas): das Material, die geslicte Datei und die Kosten
- [Produkte und Varianten](/help/productos-y-variantes): der Preis, die Marge und die Stücke jeder Variante
- [Schnellerstellung](/help/creacion-rapida): alles in einem Schritt
- [Tags](/help/etiquetas): wie du sie anlegst und verwaltest
