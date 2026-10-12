---
slug: calculate-your-3d-printing-costs
title: "Was ein gedrucktes Teil wirklich kostet (und wie du es berechnest, ohne verrückt zu werden)"
description: Das Teil mit 1,60 € Filament kostet dich 9,36 €. Wir zeigen dir, wie du die Ausgaben deiner Werkstatt auf deine Druckstunden verteilst und BolloPrint das automatisch auf jedes Teil anwendet.
date: 2026-09-12
updated: 2026-10-12
tags: [anleitungen]
cover: 01-portada.webp
draft: true
---

Ein Teil mit 6 Stunden Druckzeit und 80 Gramm PLA. Was kostet es dich?

Wenn du gedacht hast „80 Gramm bei 20 € pro Kilo, **1,60 €**“, dann hast du
ausgerechnet, was das **Material** kostet. Und das ist in einer normalen Werkstatt
**nur ein kleiner Teil** von dem, was dich dieses Teil wirklich kostet.

Die vollständige Rechnung, in einer Werkstatt mit drei Druckern und mit einem
bemalten und verpackten Teil, sieht so aus:

| | |
|---|---|
| Material | 1,60 € |
| 6 Druckerstunden | 5,16 € |
| Nachbearbeitung (bemalt) | 2,00 € |
| Zusatzkosten (Verpackung) | 0,60 € |
| **Echte Kosten des Teils** | **9,36 €** |

**Fast sechsmal so viel.** Und der Unterschied ist kein Rundungsfehler: Das sind
die Miete, der Strom, die Drucker, die sich abnutzen, die Steuerberatung und die
Teile, die schiefgehen. Das alles bezahlst du. Die Frage ist, ob du es auch
berechnest.

Darum geht es hier. Und die gute Nachricht: **Du richtest es einmal ein**, und
danach wird es automatisch auf jedes Teil angewendet, das du anlegst.

::animation{id="part-cost"}

## Woher die 5,16 € kommen

Aus einer einfachen Idee: Du nimmst **alles, was dich die Werkstatt im Monat
kostet**, teilst es durch **die Stunden, die du wirklich druckst**, und weißt so,
was dich **eine Druckerstunde** kostet. Dann multiplizierst du mit den Stunden des
Teils.

Im Beispiel oben:

> Drei Drucker, zehn Stunden am Tag, fünfundzwanzig Tage im Monat → **750 Stunden**.
>
> Für Miete, Steuerberatung, Software und die Abschreibung der Maschinen gehen
> rund **516 € im Monat** drauf. Verteilt: 0,69 € pro Stunde. Mit dem Strom liegen
> die **Basiskosten** bei **0,72 €**.
>
> Dazu 5 % Wartung, 10 % Fehldruckquote und 5 % Puffer:
> **0,86 € pro Stunde**. Mal sechs Stunden: 5,16 €.

Genau das berechnet der Bereich **Kosten** in BolloPrint, unter
**Einstellungen → Kosten**. Sehen können ihn nur der **Inhaber** und die **Admins**.

![Der Bereich Kosten in den Einstellungen](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## Schritt 1 — Die Stunden, die du wirklich druckst

Das ist die Zahl, die die meisten falsch berechnen, und die, die das Ergebnis am
stärksten verändert. Sie steht unter **Stundenkosten → Druckstunden**, und es sind
drei Felder:

**Drucker × Stunden pro Tag × Tage pro Monat**

Der einzige Rat, der zählt: **Trag nicht das theoretische Maximum ein, sondern das,
was wirklich passiert.** Wenn du drei Drucker hast, die im Schnitt acht Stunden am
Tag laufen, sind es acht. Nicht vierundzwanzig.

Die große Zahl ist verlockend, denn je höher sie ist, desto billiger wird die
Stunde. Aber wenn du die Stunden aufbläst, belügst du dich selbst: Diese Ausgaben
bezahlst du trotzdem, und was du nicht auf die Teile verteilst, trägst du am
Monatsende selbst.

![Der Reiter Druckstunden mit den drei Feldern und dem Ergebnis](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Schritt 2 — Was dich die Werkstatt kostet

Unter **Basiskosten** trägst du nach und nach deine Ausgaben ein. BolloPrint
sortiert sie nach Typ und fragt bei jedem nur nach dem, was es braucht:

| Typ | Was du einträgst |
|---|---|
| **Allgemeine Fixkosten** | Miete, Internet, Steuerberatung, Versicherungen … der Betrag pro Monat |
| **Drucker** | Was er gekostet hat und über wie viele Jahre du ihn abschreibst |
| **Software** | Das Abo für den Slicer, für BolloPrint, für alles, was du nutzt |
| **Personalkosten** | Das Gehalt und wie viele Leute |
| **Strom** | Die kW, die ein Drucker verbraucht, und was du pro kWh zahlst |

Es muss nicht auf den Cent genau sein. Eine vernünftige Zahl heute ist viel mehr
wert als die perfekte Zahl im nächsten Jahr.

:::warning ⚠️ Trag dieselbe Ausgabe nicht zweimal ein
Die Beträge **pro Monat** beschreiben **die ganze Werkstatt**: Die Miete trägst du
nur einmal ein. Die Beträge **pro gedruckter Stunde** — wie der Strom nach
Verbrauch — beschreiben **einen einzelnen Drucker**: Trag dort den Verbrauch einer
durchschnittlichen Maschine ein, nicht den der ganzen Halle.
:::

Ganz unten steht die fertige Rechnung, die vom Anfang:

> **Ausgaben im Monat ÷ deine Druckstunden = was dich eine Stunde „netto“ kostet**

Das sind die **Basiskosten pro Stunde**. Im Beispiel oben 0,72 €.

## Schritt 3 — Was sowieso passiert

Die Basiskosten lassen Dinge außen vor, die passieren, aber keine feste Rechnung
haben: Düsen gehen kaputt, und **manches Teil geht schief und muss neu gedruckt
werden**.

Dafür gibt es die **Gesamtkosten**: ein paar Prozentsätze auf die Basiskosten.
Wartung, Fehldruckquote und Puffer.

Die Fehldruckquote ist die wichtigste, und die, die die meisten auslassen. Wenn von
zehn Teilen eins im Müll landet, **bezahlen die neun guten für das schlechte**.
Trägst du sie hier nicht ein, zahlst du selbst.

Das Ergebnis sind deine **Gesamtkosten pro Stunde** — 0,86 € im Beispiel. Das ist
deine echte Zahl, und die wird auf jedes Teil angewendet.

:::info 💡 Die Gewinnmarge gehört nicht hierher
Hier stehen nur **Kosten**. Wie viel du verdienen willst, entscheidest du später,
im Produkt, denn das ist eine kaufmännische Entscheidung.
:::

## Schritt 4 — Material und Extras

Der einfache Teil, unter **Standardwerte**:

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

## Und so landet es bei deinem Teil

Die vier Schritte enden in einer einzigen Zahl: **was dich eine Druckerstunde
kostet**. Ab da ist jedes Teil eine Summe:

> seine **Stunden × deine Kosten pro Stunde**
> **+** das **Material**, das darin steckt
> **+** die **Nachbearbeitung**, wenn es nachbearbeitet oder bemalt wird
> **+** die **Zusatzkosten**, die du hinzufügst

Ein Detail solltest du verstehen, weil es erklärt, warum es sich lohnt, das Bett
vollzumachen: **Gerechnet wird pro Druckplatte, nicht pro Teil.** BolloPrint
berechnet, was die ganze Druckplatte kostet, und **verteilt es auf die Teile, die
darauf entstehen**. Deshalb werden die Zusatzkosten, die du **pro Druckplatte**
markierst, nur einmal berechnet — egal ob du einzeln druckst oder zwanzig auf
einmal —, während die **pro Einheit** bei jedem Teil berechnet werden.

Und jedes Teil **speichert die Kosten pro Stunde, mit denen es berechnet wurde**.
Das ist kein Versehen: Genau das sorgt dafür, dass die Kosten von dem, was du
letztes Jahr gedruckt hast, die von damals bleiben, und es ist der Grund, warum es
den Button **Neu berechnen** gibt, den du weiter unten findest.

## Jetzt hast du deine Zahl

Unter **Kosten → Übersicht** nimmt der Block **Beispiel** eine Muster-Druckplatte
und zeigt dir die ganze Rechnung **mit deinen Werten**: wie viel auf das Material
entfällt, wie viel auf den Druck, wie viel auf die Nachbearbeitung und was das
Teil am Ende kostet.

![Der Block Beispiel mit der vollständigen Aufschlüsselung eines Teils](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Wenn sich deine Ausgaben ändern

Der Strom wird teurer, du kaufst noch einen Drucker, du ziehst um. Du änderst die
Zahlen und … **die Teile, die du schon hattest, ändern sich nicht von selbst**. Das
ist Absicht: Jedes Teil speichert die Kosten, mit denen es berechnet wurde, und du
willst nicht, dass die Kosten von allem, was du letztes Jahr gemacht hast,
überschrieben werden.

Wenn du es auf alles anwenden willst, hast du unter **Übersicht** einen Zähler für
Teile, die **neu zu berechnen** sind, und einen Button **Neu berechnen**. Du
entscheidest, wann.

:::info 💡 Deine Verkaufspreise bleiben unangetastet
Neu berechnen aktualisiert die **Kosten** und den *vorgeschlagenen* Preis. Der
Preis, den du selbst gesetzt hast, bleibt. Was du dich bewegen siehst, ist die
**Margen**-Anzeige.
:::

## Soll ich mir noch einen Drucker kaufen?

Das ist **die** Frage, und jetzt kannst du sie mit Zahlen beantworten. Unter
**Kostenszenarien** veränderst du die Drucker, die Stunden oder die Tage und
siehst, was mit deinen Kosten pro Stunde passieren würde. An deiner Konfiguration
ändert sich nichts: Es wird nur simuliert.

Eins zeigt das sehr gut: **Die Kurve sinkt irgendwann nicht mehr.** Von einem auf
fünf Drucker zu gehen, teilt die Kosten pro Stunde fast durch fünf. Von zwanzig auf
hundert zu gehen, bewegt sie kaum noch, weil es Ausgaben gibt — wie den Strom —,
die in jeder gedruckten Stunde anfallen und sich auf niemanden verteilen.

![Kostenszenarien mit der Kurve der Kosten pro Stunde](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Es sind vier Bildschirme und ein Nachmittag. Dafür hat jedes Teil, das du anlegst,
seine echten Kosten eingetragen, und du weißt, ob du Geld verdienst, ohne von Hand
zu rechnen.

:::info 💡 Sollen wir dir bei deinen Zahlen helfen?
Wenn du nicht weißt, wo du anfangen sollst, schreib uns über die
[Kontaktseite](/contact) oder schau in [unserem Discord](/help/soporte-por-discord)
vorbei. Wir haben das schon ein paar Mal gemacht.
:::

## Verwandte Dokumentation

- [Kosten](/help/costes) — die vollständige Referenz zum Bereich
- [Teile](/help/piezas) — wie die Kosten jedes Teils berechnet werden
- [Produkte und Varianten](/help/productos-y-variantes) — von den Kosten zum Verkaufspreis
- [Materialbestand](/help/inventario) — damit das Material mit seinen echten Kosten gerechnet wird
