---
slug: whats-new-september-november-2026
title: "BolloPrint wird besser! Die Neuerungen, die dir in deiner 3D-Druck-Werkstatt helfen"
description: "Alles Neue in BolloPrint vom 14. September bis 3. November 2026: vom lokalen Agenten ohne Container bis zu rechtsgültigen Rechnungen und den ganz neuen Finanzen."
date: 2026-11-03
tags: [neuigkeiten]
cover: 01-bollo.webp
---

Seit Mitte September haben wir **41 Updates** von BolloPrint veröffentlicht.
Manche sind große, wichtige Änderungen. Andere sind kleine Verbesserungen, die
deinen Alltag angenehmer machen. Hier ist das Wichtigste.

![In sieben Wochen: mehr als 400 spürbare Verbesserungen, mehr als 250 Änderungen auf dem Bildschirm, rund 190 behobene Fehler, 11 Länder mit rechtsgültigen Rechnungen, 9 Sprachen in der App und 102 Drucker von 15 Marken](/blog/media/2026-11-03-novedades-otono/02-cifras-de.webp)

## Wir fangen mit dem Spannendsten an: was deine Arbeit verändert

### 1. Der lokale Agent, jetzt ganz ohne Container-Kenntnisse

Wir wissen, dass Docker kompliziert sein kann. Deshalb ist es jetzt einfacher.
Installiere den Agenten auf dem, was du schon hast: deinem NAS, dem Computer in
der Werkstatt oder deinem Home Assistant.

![Die Logos von Synology, QNAP, Windows, Home Assistant und TrueNAS](/blog/media/2026-11-03-novedades-otono/03-agentes.webp)

| Wo | So wird er installiert |
|---|---|
| **Synology und QNAP** | Lade das Paket für dein NAS herunter und installiere es manuell über dessen Paket-Zentrum. |
| **Windows** | Ein Installer für den Computer in der Werkstatt. |
| **Home Assistant** | Der Button „Zu Home Assistant hinzufügen“, und fertig. |
| **TrueNAS** | Füge die Konfiguration, die wir dir geben, in seine Apps ein. |

Danach öffnest du seine Seite und klickst auf **„Mit BolloPrint verknüpfen“**: Der
Inhaber der Werkstatt bestätigt es mit einem Klick, ohne Codes zu kopieren. Wie
alle Agenten aktualisiert er sich selbst. Docker und Kubernetes funktionieren
weiter wie immer.

:::info
Du findest ihn unter **Einstellungen → Drucker → Lokaler Agent → „Neuer Agent“**.
[So installierst du den Agenten](/help/el-agente-local)
:::

---

### 2. Deine Drucker, besser im Blick und genauer gezählt

- **Live-Kamera** und ein Abschlussfoto jedes Drucks in seinem Verlauf.
- **Jeder Druck erzählt alles**: wie lange er im Vergleich zur Schätzung gedauert hat, jede Spule mit ihrem AMS-Platz und der Name des MakerWorld-Modells mit Link.
- **Der echte Verbrauch**: Ein fehlgeschlagener oder abgebrochener Druck wird nicht mehr komplett gezählt, und Harzdrucke erfassen ihre Milliliter.
- **Bambu Lab**, über die Cloud ohne Passwort (deine E-Mail und ein Code, und die Sitzung erneuert sich selbst) und über das lokale Netzwerk mit Pausieren, Fortsetzen und Abbrechen aus BolloPrint, bei eingeschaltetem Entwicklermodus.
- **Per IP hinzufügen** ist jetzt ein Assistent pro Marke; du musst nicht mehr wissen, welches „Protokoll“ deine Maschine spricht.
- **Der lokale Agent aktualisiert sich selbst**, nie mitten in einem Druck, und jede Druckermarke wird für sich besser.
- **Anycubic** (Kobra 3, S1, 4 und X) und **Creality** mit Werks-Firmware (K1, K2, Ender-3 V3 und Hi) kommen dazu, in der Beta.

[Kompatible Drucker ansehen](/help/impresoras-compatibles)

---

### 3. Smart-Migration

Bring Kunden, Designs, Teile, Produkte, Bestellungen, Angebote und Bestand aus den
Ordnern und Tabellen auf deinem Computer mit. BolloPrint liest, was du mitbringst,
und schlägt vor, wie es passt; du prüfst es, bevor irgendetwas übernommen wird,
und wenn du dich vertust, lässt es sich rückgängig machen.

:::warning
Es sind drei Schritte: **Vorbereiten · Verstehen · Migrieren**. Ab dem Pro-Plan,
in Chrome oder Edge am Computer. Bei Max und Business übernehmen wir das auf Wunsch
für dich.
:::

---

### 4. Rechtsgültige Rechnungen direkt aus der Bestellung

Stelle die Rechnung zu einer Bestellung aus, ohne BolloPrint zu verlassen: mit
Nummerierung, Steuer und deinem Logo. Vor dem Ausstellen siehst du die Rechnung
**genau so, wie sie herauskommt**, und wenn etwas fehlt, sagen wir dir, was und wo
du es korrigierst.

- **Zahlungen**: offen, überfällig oder bezahlt, und ein ZIP mit allen deinen
  Rechnungen.
- **Umsatzsteuerfreie Verkäufe an Unternehmen in der EU**, mit dem gesetzlichen
  Hinweis und der in VIES geprüften Nummer.
- **Deutsche E-Rechnung, Schweizer QR-Rechnung** und Rechnungen in einer anderen
  Währung.

Schon verfügbar in 11 Ländern: Deutschland, Irland, Luxemburg, den Niederlanden,
Österreich, Polen (über KSeF), Schweden, der Schweiz, Tschechien, dem Vereinigten
Königreich und Zypern.

:::warning
**In Spanien noch nicht**: Das kommt, sobald wir VeriFactu integriert haben, und
wir sagen dir Bescheid.
:::

[Länder mit Rechnungsstellung ansehen](/help/paises-con-facturacion)

---

### 5. Professionellere Angebote

- Das Angebots-PDF hat **die Form einer Rechnung**: Nummer, Datum, Gültigkeit und
  in den bezahlten Plänen dein eigenes Logo.
- **Nummerierung pro Jahr** („2026-00001“) und ohne Lücken, auch wenn du eins
  löschst.
- **Rabatt** in € oder %, der als weitere Zeile erscheint.
- Kundenkarten als **Privatperson oder Unternehmen** und einfachere Steuerdaten.
- Beim Annehmen des Angebots wird **automatisch eine Bestellung** angelegt.

[Angebote ansehen](/help/presupuestos)

---

### 6. Komplett neue Finanzen

Sechs Tabs, in denen du deine Einnahmen, Ausgaben, Steuern und deinen Gewinn für
den gewünschten Zeitraum siehst (monatlich, quartalsweise, jährlich …).

Lade deine Ausgaben mit unserem KI-Agenten hoch und archiviere die Rechnungen
deiner Lieferanten, um auf einen Blick zu sehen, wofür du dein Geld ausgibst.
Behalte die Steuern im Blick, die du in jedem Zeitraum zahlen musst.

:::info
**Das Beste:** Exportiere diese Daten für deine Steuerberatung mit einem Klick als ZIP.
:::

[Finanzen ansehen](/help/financiero)

---

### 7. „Hinweise“: die Probleme deiner Werkstatt auf einen Blick

Ein Drucker, der mit einem Fehler steht, ein getrennter Etsy-Shop, eine Zahlung,
die nicht durchging, ein fast voller Speicher … Wir melden dir nur, was wirklich
etwas braucht, und jeder Hinweis schließt sich von selbst, sobald du es behebst.

Du kannst einen Hinweis ein paar Tage oder dauerhaft stummschalten. Die roten, die
etwas Wichtiges blockieren, zeigen wir nur demjenigen rot, der sie beheben kann;
der Rest des Teams sieht sie mit einem „Gib dem Inhaber der Werkstatt Bescheid“.

---

### 8. Exportiere deinen Materialbestand, als Excel oder PDF

Jetzt kannst du eine Liste von dem ziehen, was du auf Lager hast: Bestand,
Filamente, Harze, Verbrauchsmaterial …

| Format | Was du bekommst |
|---|---|
| **Excel** | Eine Arbeitsmappe mit einer Übersicht und einem Blatt pro Bereich, mit Filtern, Summen und allem, was nicht mehr vorrätig ist, in Rot. |
| **PDF** | Ein Dokument pro Bereich, mit deinem Logo, den Fotos deiner Teile und den Farben jeder Spule. |

In allen Plänen und immer mit allen Zeilen, nicht nur mit denen auf dem
Bildschirm.

---

### 9. In deiner Sprache und auf deine Art

BolloPrint spricht jetzt **🇵🇱 Polnisch, 🇳🇱 Niederländisch und 🇨🇿 Tschechisch**.
Damit sind es insgesamt neun Sprachen.

Datum und Beträge werden **so geschrieben wie im Land deiner Werkstatt**, auf dem
Bildschirm, im PDF und in den E-Mails.

Und es gibt einen **neuen Start**, der mit dem Dringenden beginnt, mit „Neu
erstellen“ für eine Bestellung, ein Angebot oder eine Schnellerstellung, und
„Erste Schritte“ mit Fortschrittsbalken.

## Und außerdem, denn auch kleine Änderungen merkt man

| Wo | Was sich ändert |
|---|---|
| **Bildschirme** | Während etwas lädt, siehst du seine Form, nie eine falsche leere Liste; schlägt es fehl, ein „Erneut versuchen“. Die Filter sind in allen Listen gleich, auch auf dem Handy. |
| **Uploads** | Jede Datei zeigt ihren Fortschritt und wird nach einem Netzabbruch automatisch fortgesetzt. Geslicte Dateien dürfen bis zu 5 GB groß sein. |
| **Kosten** | 29 Filament- und 9 Harzfamilien mit aktualisierten Kilopreisen; die Margen mit einem farbigen Balken und einem Beispiel. |
| **Kunden** | Die Liste sucht und sortiert nach jeder Spalte, und ein Kunde ohne Alias wird mit vollem Namen angezeigt. |
| **Etsy** | Ein Etsy-Angebot zu importieren geht bis zu 8-mal schneller, Bestellungen mit zwei Variationen kommen an, und bevor du ein Etsy-Angebot synchronisierst, siehst du Wert für Wert, was sich ändert. Einstellungen → Marktplätze ist jetzt eine Galerie, mit einer Seite pro Shop. |
| **Versand** | Eigene Versanddienstleister und Verkaufskanäle für Österreich, Deutschland, das Vereinigte Königreich, Polen, Tschechien und die Niederlande. |
| **Handbuch und Blog** | Das Handbuch wächst von 49 auf 70 Seiten, in allen neun Sprachen, und im Blog gibt es sechs neue Artikel: vom lokalen Agenten bis dazu, was ein Teil wirklich kostet. |
| **Im Alltag** | Die App verkraftet Spitzen besser, kommt nach einem Netzabbruch von selbst zurück, der Chrome-Übersetzer macht sie nicht mehr kaputt, und ein Drucker, dessen Agent sich mitten im Druck abschaltet, hinterlässt keine Geisterdrucke mehr. |

## Wo wir stehen

| Was | Wo und wie viel |
|---|---|
| 🧾 **Rechtsgültige Rechnungen in 11 Ländern** | 🇩🇪 Deutschland · 🇮🇪 Irland · 🇱🇺 Luxemburg · 🇳🇱 Niederlande · 🇦🇹 Österreich · 🇵🇱 Polen · 🇸🇪 Schweden · 🇨🇭 Schweiz · 🇨🇿 Tschechien · 🇬🇧 Vereinigtes Königreich · 🇨🇾 Zypern |
| 🌍 **Eine Werkstatt lässt sich aus 53 Ländern Europas eröffnen** | Mit ihrer Währung, ihren Steuern und ihren Versanddienstleistern. Bezahlt wird in Euro, Pfund, Złoty oder tschechischen Kronen. |
| 🖨️ **102 Druckermodelle, für Filament und Harz** | Bambu Lab · Prusa · Elegoo · FlashForge · Anycubic · Creality · QIDI · Snapmaker · Voron · RatRig · Sovol · Artillery · Longer · Phrozen · Two Trees |
| ✅ **10 von uns an echten Maschinen getestet** | Bambu Lab A1, A2L, P1P, P1S, P2S, X1 Carbon, X2D, H2C, H2D und H2S. |

## Fehlt dir etwas?

Erzähl es uns unter
[info@bolloprint.com](mailto:info@bolloprint.com) oder in unserem
[Discord-Kanal](/help/soporte-por-discord). Wir lesen alles. Vieles von dem, was
du hier siehst, ist aus Nachrichten wie deiner entstanden.

Wenn du genauer wissen willst, wie es funktioniert, steht alles im
[Handbuch](/help).

Und wir hören nicht auf: Wir arbeiten jeden Tag weiter daran, BolloPrint zum
besten Werkzeug für deine 3D-Druck-Werkstatt zu machen.

![Bollo, das Maskottchen von BolloPrint, mit Werkstattbrille und Werkzeuggürtel, auf einem Bauplan](/blog/media/2026-11-03-novedades-otono/01-bollo.webp "60%")
