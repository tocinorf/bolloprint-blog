---
slug: calculate-your-3d-printing-costs
title: "Was ein gedrucktes Teil wirklich kostet (und wie du es einfach berechnest)"
description: Das Teil mit 1,60 € Filament kostet dich 9,36 €. Wir zeigen dir, wie du die Ausgaben deiner Werkstatt auf deine Druckstunden verteilst, damit BolloPrint das automatisch auf jedes Teil anwendet.
date: 2026-10-15
tags: [anleitungen]
cover: 01-portada.webp
---

Ein Teil mit 6 Stunden Druckzeit und 80 Gramm PLA. Was kostet es dich?

Wenn du gedacht hast „80 Gramm bei 20 € pro Kilo, **1,60 €**“, hast du nur das
**Material** berechnet. In einer normalen Werkstatt ist das **nur ein kleiner
Teil** von dem, was dich das Teil wirklich kostet.

In einer Werkstatt mit drei Druckern, mit einem bemalten und verpackten Teil,
sieht die vollständige Rechnung so aus:

| | |
|---|---|
| Material | 1,60 € |
| 6 Druckerstunden | 5,16 € |
| Nachbearbeitung (bemalt) | 2,00 € |
| Zusatzkosten (Verpackung) | 0,60 € |
| **Echte Kosten des Teils** | **9,36 €** |

**Fast sechsmal so viel.** Der Unterschied ist kein Rundungsfehler: Das sind die
Miete, der Strom, der Verschleiß der Drucker, die Steuerberatung und die Teile,
die schiefgehen. Das alles bezahlst du; die Frage ist, ob du es auch berechnest.

Hier siehst du, wie du diese Ausgaben in die Kosten jedes Teils einbeziehst.
**Du richtest es einmal ein**, und danach wird es automatisch auf jedes Teil
angewendet, das du anlegst.

::animation{id="part-cost"}

## Woher die 5,16 € kommen

Die Idee ist einfach: Du addierst **alles, was dich die Werkstatt im Monat
kostet**, und teilst es durch **die Stunden, die du wirklich druckst**. So
erhältst du, was dich **eine Druckerstunde** kostet, und musst nur noch mit den
Stunden des Teils multiplizieren.

Mit den Zahlen aus dem Beispiel:

- **Stunden:** drei Drucker, zehn Stunden am Tag, fünfundzwanzig Tage im Monat →
  **750 Stunden**.
- **Ausgaben:** Für Miete, Steuerberatung, Software und die Abschreibung der
  Maschinen gehen rund **516 € im Monat** drauf. Verteilt: 0,69 € pro Stunde.
  Mit dem Strom liegen die **Basiskosten** bei **0,72 €**.
- **Zuschläge:** 5 % Wartung, 10 % Fehldruckquote und 5 % Puffer bringen sie auf
  **0,86 € pro Stunde**. Mal sechs Stunden: 5,16 €.

Genau diese Rechnung macht der Bereich **Kosten** in BolloPrint, unter
**Einstellungen → Kosten**. Sehen können ihn nur der **Inhaber** und die **Admins**.

![Der Bereich Kosten in den Einstellungen](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## Die Stunden, die du wirklich druckst

Fang mit den Stunden an: Das ist die Zahl, die die meisten falsch berechnen, und
die, die das Ergebnis am stärksten verändert. Sie steht unter
**Stundenkosten → Druckstunden**, und es sind drei Felder:

**Drucker × Stunden pro Tag × Tage pro Monat**

Trag **das ein, was wirklich passiert, nicht das theoretische Maximum**. Wenn du
drei Drucker hast, die im Schnitt acht Stunden am Tag laufen, sind es acht. Nicht
vierundzwanzig.

Eine hohe Zahl ist verlockend, denn je höher sie ist, desto billiger wird die
Stunde. Aber diese Ausgaben bezahlst du trotzdem, und was du nicht auf die Teile
verteilst, trägst du am Monatsende selbst.

![Der Reiter Druckstunden mit den drei Feldern und dem Ergebnis](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Was dich die Werkstatt kostet

Wenn die Stunden stehen, geht es an die Ausgaben. Unter **Basiskosten** trägst du
sie nach und nach ein; BolloPrint sortiert sie nach Typ und fragt bei jedem nur
nach dem, was es braucht:

| Typ | Was du einträgst |
|---|---|
| **Allgemeine Fixkosten** | Miete, Internet, Steuerberatung, Versicherungen … der Betrag pro Monat |
| **Drucker** | Was er gekostet hat und über wie viele Jahre du ihn abschreibst |
| **Software** | Das Abo für den Slicer, für BolloPrint, für alles, was du nutzt |
| **Personalkosten** | Das Gehalt und wie viele Leute |
| **Strom** | Die kW, die ein Drucker verbraucht, und was du pro kWh zahlst |

Es muss nicht auf den Cent genau sein: Eine vernünftige Zahl heute ist mehr wert
als die perfekte Zahl im nächsten Jahr.

:::warning ⚠️ Trag dieselbe Ausgabe nicht zweimal ein
Die Beträge **pro Monat** beschreiben **die ganze Werkstatt**: Die Miete trägst du
nur einmal ein. Die Beträge **pro gedruckter Stunde** — wie der Strom nach
Verbrauch — beschreiben **einen einzelnen Drucker**: Trag dort den Verbrauch einer
durchschnittlichen Maschine ein, nicht den der ganzen Halle.
:::

Ganz unten steht die fertige Rechnung, dieselbe wie am Anfang:

> **Ausgaben im Monat ÷ deine Druckstunden = was dich eine Stunde „netto“ kostet**

Das sind die **Basiskosten pro Stunde**: 0,72 € im Beispiel.

![Die Ausgaben der Werkstatt unter Basiskosten, nach Art gruppiert, und die Rechnung, die 0,72 € pro Stunde ergibt](/blog/media/2026-09-12-costes-reales/03b-coste-base.png)

## Was sowieso passiert

Die Basiskosten lassen außen vor, was ohne feste Rechnung passiert: Düsen gehen
kaputt, und **manches Teil geht schief und muss neu gedruckt werden**.

Dafür gibt es die **Gesamtkosten**, die ein paar Prozentsätze auf die
Basiskosten aufschlagen: Wartung, Fehldruckquote und Puffer.

Die Fehldruckquote ist die wichtigste, und die, die die meisten auslassen. Wenn
von zehn Teilen eins im Müll landet, **bezahlen die neun guten für das
schlechte**. Trägst du sie hier nicht ein, zahlst du selbst.

Das Ergebnis sind deine **Gesamtkosten pro Stunde**: 0,86 € im Beispiel. Das ist
deine echte Zahl, und die wird auf jedes Teil angewendet.

:::info 💡 Die Gewinnmarge gehört nicht hierher
Hier stehen nur **Kosten**. Wie viel du verdienen willst, entscheidest du später,
im Produkt, denn das ist eine kaufmännische Entscheidung.
:::

![Die Zuschläge für Wartung, Fehlerquote und Puffer auf die Basiskosten, bis 0,86 € pro Stunde](/blog/media/2026-09-12-costes-reales/03c-coste-total.png)

## Material und Extras

Bleibt der einfachste Teil, unter **Standardwerte**:

- **Der Preis jedes Materials**, pro Kilo. Er gilt **je Art**, nicht je Familie:
  PLA und TPU kosten nicht dasselbe.
- **Die Nachbearbeitung**: wie viel du aufschlägst, wenn das Teil nachbearbeitet
  oder bemalt wird.
- **Die Zusatzkosten**: Verpackung, Schrauben, Magnete, Gewindeeinsätze,
  Arbeitszeit. Bei jedem wählst du, ob er **pro Einheit** oder **pro Druckplatte**
  berechnet wird.
- **Die Margen**: die, die du standardmäßig willst, und ab welchem Prozentsatz wir
  dich rot oder orange warnen.

:::info 💡 Wenn das Material im Materialbestand ist, gilt der Materialbestand
Diese Preise sind Richtwerte für den Fall, dass nichts dahintersteht. Wenn das
Teil von einer Rolle kommt, die mit ihren echten Kosten angelegt ist, verwenden wir
diese.
:::

![Standardwerte: die Margen mit ihren Farbwarnungen und der Preis jedes Materials pro Kilo](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## Und so landet es bei deinem Teil

Die vier Schritte davor enden in einer einzigen Zahl: **was dich eine
Druckerstunde kostet**. Ab da ist jedes Teil eine Summe:

> seine **Stunden × deine Kosten pro Stunde**
> **+** das **Material**, das darin steckt
> **+** die **Nachbearbeitung**, wenn es nachbearbeitet oder bemalt wird
> **+** die **Zusatzkosten**, die du hinzufügst

Ein Detail solltest du verstehen, weil es erklärt, warum es sich lohnt, das Bett
vollzumachen: **Gerechnet wird pro Druckplatte, nicht pro Teil.** BolloPrint
berechnet, was die ganze Druckplatte kostet, und **verteilt es auf die Teile, die
darauf entstehen**. Deshalb werden die Zusatzkosten, die du **pro Druckplatte**
markierst, nur einmal berechnet — egal ob du die Teile einzeln druckst oder
zwanzig auf einmal —, und die **pro Einheit** bei jedem Teil.

Außerdem **speichert jedes Teil die Kosten pro Stunde, mit denen es berechnet
wurde**. Das ist Absicht: So bleiben die Kosten von dem, was du letztes Jahr
gedruckt hast, die von damals. Deshalb gibt es auch den Button **Neu berechnen**,
den du weiter unten findest.

## Jetzt hast du deine Zahl

Um das Ergebnis zu sehen, geh zu **Kosten → Übersicht**. Der Block **Beispiel**
nimmt eine Muster-Druckplatte und zeigt dir die ganze Rechnung **mit deinen
Werten**: wie viel auf das Material entfällt, wie viel auf den Druck, wie viel auf
die Nachbearbeitung und was das Teil am Ende kostet.

![Der Block Beispiel mit der vollständigen Aufschlüsselung eines Teils](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Wenn sich deine Ausgaben ändern

Deine Zahlen bleiben nicht immer gleich: Der Strom wird teurer, du kaufst noch
einen Drucker oder ziehst um. Wenn du sie anpasst, **ändern sich die Teile, die du
schon hattest, nicht von selbst**. Das ist Absicht: Jedes Teil speichert die
Kosten, mit denen es berechnet wurde, und du willst nicht, dass die Kosten von
allem, was du letztes Jahr gemacht hast, überschrieben werden.

Wenn du es auf alles anwenden willst, hast du unter **Übersicht** einen Zähler für
Teile, die **neu zu berechnen** sind, und den Button **Neu berechnen**. Du
entscheidest, wann.

:::info 💡 Deine Verkaufspreise bleiben unangetastet
Neu berechnen aktualisiert die **Kosten** und den *vorgeschlagenen* Preis. Der
Preis, den du selbst gesetzt hast, bleibt. Was du dich bewegen siehst, ist die
**Margen**-Anzeige.
:::

## Soll ich mir noch einen Drucker kaufen?

Wenn deine Kosten eingerichtet sind, kannst du diese Frage mit Zahlen
beantworten. Unter **Kostenszenarien** veränderst du die Drucker, die Stunden oder
die Tage und siehst, was mit deinen Kosten pro Stunde passieren würde. Es wird nur
simuliert: An deiner Konfiguration ändert sich nichts.

Am besten zeigt es, dass **die Kurve irgendwann nicht mehr sinkt**. Von einem auf
fünf Drucker zu gehen, teilt die Kosten pro Stunde fast durch fünf. Von zwanzig
auf hundert zu gehen, bewegt sie kaum noch, weil es Ausgaben gibt — wie den
Strom —, die in jeder gedruckten Stunde anfallen und sich auf niemanden verteilen.

![Kostenszenarien mit der Kurve der Kosten pro Stunde](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Die Einrichtung sind vier Bildschirme und ein Teil eines Nachmittags. Dafür hat
jedes Teil, das du anlegst, seine echten Kosten eingetragen, und du weißt, ob du
Geld verdienst, ohne von Hand zu rechnen.

:::info 💡 Sollen wir dir bei deinen Zahlen helfen?
Wenn du nicht weißt, wo du anfangen sollst, schreib uns über die
[Kontaktseite](/contact) oder in [unserem Discord](/help/soporte-por-discord). Wir
haben das schon ein paar Mal gemacht.
:::

Mögen deine Zahlen immer aufgehen.

![Bollo, das Maskottchen von BolloPrint, mit Werkstattbrille, nachdenklich zwischen Rechnungen in Kreide](/blog/media/2026-09-12-costes-reales/07-bollo.webp "60%")

## Verwandte Dokumentation

- [Kosten](/help/costes): die vollständige Referenz zum Bereich
- [Teile](/help/piezas): wie die Kosten jedes Teils berechnet werden
- [Produkte und Varianten](/help/productos-y-variantes): von den Kosten zum Verkaufspreis
- [Materialbestand](/help/inventario): damit das Material mit seinen echten Kosten gerechnet wird
