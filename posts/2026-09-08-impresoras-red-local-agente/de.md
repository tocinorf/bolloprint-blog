---
slug: connect-printers-local-network-agent
title: "Verbinde deine Drucker über dein eigenes Netzwerk: der lokale Agent, Schritt für Schritt"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper … Ein kleiner Agent auf einem Rechner in der Werkstatt, deine ganze Flotte in BolloPrint, und am Router änderst du nichts.
date: 2026-10-12
updated: 2026-10-16
tags: [anleitungen]
cover: 01-portada.webp
---

Deine Drucker stehen in der Werkstatt, du aber nicht immer. Und um zu wissen, ob
einer noch druckt, ob es gut geworden ist oder ob noch Material drin ist, musst du
davorstehen.

Dafür gibt es den **lokalen Agenten**: ein kleines Programm, das auf einem Rechner
in deiner Werkstatt läuft, über dein eigenes Netzwerk mit deinen Druckern spricht
und BolloPrint mitteilt, was er sieht.

- **Du änderst nichts am Router**: keine offenen Ports, keine feste IP, keine Firewall.
- **Er ist sehr leicht**: Jeder Rechner, der bei dir sowieso läuft, reicht ihm.
- **Einer genügt für die ganze Flotte**, egal wie groß sie ist.
- **Er aktualisiert sich selbst**: Kommt eine neue Version heraus, installiert er sie von allein.

::animation{id="local-agent"}

## Wo du ihn installierst

Der Agent läuft auf **jedem Rechner in der Werkstatt, den du nicht ausschaltest**:
einem NAS, einem Mini-PC, einem Raspberry Pi oder dem Werkstatt-PC. Er muss nur
**immer eingeschaltet** sein und **Docker** haben.

Ideal ist es, wenn er **im selben Netzwerk wie die Drucker** steht, denn dann
findet er sie von selbst. Wenn das nicht geht, fügst du sie von Hand hinzu, und sie
funktionieren genauso.

## Leg den Agenten in BolloPrint an

Du beginnst in BolloPrint. Geh zu **Einstellungen → Drucker**. Dort siehst du drei
Reiter: **Drucker** (alle deine Maschinen, egal wie sie verbunden sind), **Lokaler
Agent** und **Bambu Cloud**. Öffne **Lokaler Agent** und klick auf **Neuer Agent**.

Gib ihm einen Namen, der dir auch in sechs Monaten noch etwas sagt: **Benenn ihn
danach, wo er steht, nicht danach, was er ist.** „Erdgeschoss“ oder „Halle 2“
passen; „Agent 1“ nicht. Dann klick auf **Agent anlegen**.

![Der Reiter Lokaler Agent mit zwei Agenten online und dem Button Neuer Agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-de.png)

## Kopier das Manifest

Beim Anlegen zeigt dir BolloPrint ein **Manifest**: einen Text, in dem alles, was
zu dir gehört, **bereits eingetragen** ist, die Schlüssel deines Agenten und die
passende Version. Es gibt nichts zu ersetzen oder auszufüllen.

Wähl das Format, das du nutzt (**Docker Compose** ist der Normalfall), klick auf
**Kopieren** und, sobald du es sicher abgelegt hast, auf **Speichern**.

![Das Bereitstellungs-Manifest des neuen Agenten mit dem Button Kopieren](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-de.png "75%")

:::warning 🔐 Kopier es jetzt: Die Schlüssel werden nur einmal angezeigt
Wir speichern sie nicht, deshalb können wir sie dir nicht noch einmal zeigen. Wenn
du das Manifest verlierst, ist das kein Drama: Öffne den Agenten mit
**Bearbeiten** (in seinem **⋮**-Menü), geh zum Reiter **Bereitstellung** und klick
auf **Schlüssel neu erzeugen**. Hat er sich noch nie verbunden, wird nichts
unterbrochen.
:::

## Füg das Manifest auf deinem Rechner ein

Das passiert auf deinem Rechner, nicht in BolloPrint, und hängt davon ab, wo du
ihn installierst:

- **Synology-NAS**: Installier **Container Manager** aus dem **Paket-Zentrum**,
  geh zu **Projekt → Erstellen**, füg das Manifest ein und erstell das Projekt.
  Ohne einen einzigen Befehl.
- **Windows oder Mac**: Installier **Docker Desktop**, speicher das Manifest in
  einem Ordner als `docker-compose.yml` und führ in diesem Ordner
  `docker compose up -d` aus.
- **Linux**: Installier **Docker** mit dem Paketmanager deiner Distribution,
  speicher das Manifest als `docker-compose.yml` und führ dort
  `docker compose up -d` aus.
- **Portainer**: Füg dasselbe Manifest in einen Stack ein und stell ihn bereit.

:::info 💡 Auf Windows und Mac werden die Drucker nicht von selbst gefunden
Docker läuft dort in einer virtuellen Maschine, die die Meldungen nicht sieht, die
die Drucker in dein Netzwerk schicken. Der Agent funktioniert genauso, aber die
Drucker fügst du selbst hinzu, wie weiter unten erklärt.
:::

## Du hängst fest? Klick auf „Installieren“

Solange sich der Agent kein einziges Mal verbunden hat, steht in seiner Zeile
**Nicht installiert**. Das ist kein Fehler: Es ist nichts ausgefallen, er muss nur
noch installiert werden.

In derselben Zeile hast du den Button **Installieren**. Klickst du ihn an, klappen
die Schritte auf, die du gerade gelesen hast, in Kurzform, mit einem Link zur
**Hilfe**, einem zu diesem **Blogartikel** und einem Button, um uns auf **Discord**
zu fragen. Hast du das Manifest nicht aufbewahrt, bringt dich Schritt 3 direkt
dorthin, wo du ein neues erzeugst.

![Ein noch nicht installierter Agent mit aufgeklapptem Installieren-Bereich: die drei Schritte, die Hilfe und Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-de.png)

## Prüf, ob er online ist

Geh zurück zu BolloPrint: In weniger als einer Minute springt der Agent auf
**Online**, mit dem Namen des Rechners, auf dem er läuft, und seiner Version.

![Der Agent im Status Online](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-de.png)

Wenn nicht, liegt es fast immer an einer von drei Ursachen: Das Manifest wurde
**nur halb eingefügt**, der Rechner hat **kein Internet**, oder eine **Firewall**
blockiert den ausgehenden Verkehr. Wenn du sehen willst, was der Agent selbst
meldet, öffne ihn mit **Bearbeiten**: Der Reiter **Status** zeigt die Details.

## Deine Drucker erscheinen von selbst

Ab dann **sucht der Agent von allein alle 15 Minuten nach Druckern in deinem
Netzwerk**. Findet er einen, bekommst du über den Reitern einen Hinweis und siehst
ihn unten unter **Drucker im lokalen Netzwerk**, mit Marke und Modell. Du
entscheidest:

- **Hinzufügen**: Du nimmst ihn auf, und er beginnt zu melden.
- **Ignorieren**: Er gehört nicht dir, oder du willst ihn hier nicht haben.

![Ein vom Agenten gefundener Drucker mit den Buttons Ignorieren und Hinzufügen, darüber Jetzt suchen und Per IP hinzufügen](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-de.png)

Wenn du gerade eine Maschine eingeschaltet hast und nicht warten willst, klick auf
**Jetzt suchen**. Wird ein Drucker nach einem Code fragen, sagt dir das seine Zeile
schon vorher („fragt nach dem Zugangscode“), damit du ihn griffbereit hast.

## Wenn einer nicht auftaucht, füg ihn selbst hinzu

Dass ein Drucker nicht von selbst erscheint, ist in zwei Fällen **normal**:

- **Er ist in einem anderen Netzwerk.** Die Meldungen der Drucker gehen nicht von
  einem Netz ins andere.
- **Der Agent läuft auf Windows oder Mac.** Docker läuft dort in einer virtuellen
  Maschine.

Dir entgeht dadurch nichts: Du fügst ihn selbst hinzu, und er funktioniert
genauso, mit Kamera und Steuerung, wenn die Maschine das hat. Klick auf **Per IP
hinzufügen**. Das geht in drei Schritten.

### 1. Wähl die Marke

Wähl die Marke deines Druckers: Jede hat ihre eigene Karte, und die mit Logo
stehen vorn. Wie deine Maschine kommuniziert, musst du nicht wissen; darum
kümmern wir uns. Wählst du **Elegoo**, fragen wir **Welchen Elegoo hast du?**,
weil es mehrere Familien gibt. **Klipper** und **Anderer Resindrucker (ChituBox)**
stehen am Ende unter **Allgemein**, für einen Eigenbau oder eine Marke, die nicht
in der Liste steht.

Wenn du nicht sicher bist, ob dein Modell unterstützt wird, findest du unten
**Unsicher? Sieh dir die Liste der kompatiblen Drucker an**; und wenn dein Drucker
fehlt, sag es uns auf Discord.

![Der erste Schritt von Drucker per IP hinzufügen: die Marken, die du verbinden kannst](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-de.png)

### 2. Gib seine Angaben ein

Nur das Nötigste:

- **Welcher Agent verbindet ihn?**, wenn du mehr als einen hast. Du kannst nur
  einen wählen, der online ist.
- **IP des Druckers**. Du findest sie auf dem Display des Druckers (Einstellungen
  → Netzwerk) oder in deinem Router.
- **Den Code des Druckers**, wenn diese Marke einen verlangt. Das Feld heißt so,
  wie der Hersteller ihn nennt: bei einem Bambu **LAN-Zugangscode**.
- **Name**, wenn du ihm einen eigenen geben willst. Das ist optional.

**Modell und Seriennummer tippst du nicht ein**: Die fragt der Agent beim Drucker
ab. Pflichtfelder haben ein **rotes Sternchen** und sind rot umrandet, solange sie
leer sind. Ganz unten sagt dir der Kasten **Denk daran**, was du bei dieser Marke
vor dem Verbinden vorbereiten musst.

![Der zweite Schritt: der Agent, die IP, der verpflichtende LAN-Zugangscode und der Kasten Denk daran](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-de.png)

### 3. Verbinde ihn

Klick auf **Verbinden**, und du siehst, wie es vorangeht: Der Agent bekommt die
Anfrage, sucht den Drucker unter dieser Adresse und verbindet sich. Am Ende steht
da **„Verbunden. Er steht jetzt in deiner Druckerliste.“**

![Der dritte Schritt: der Drucker ist verbunden und steht schon in der Liste](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-de.png)

Wenn etwas schiefgeht, sagen wir es dir **in klaren Worten**: was gerade passiert
und was du prüfen solltest (unter dieser IP antwortet nichts, der Drucker lehnt
den Code ab …). Mit **Zurück** korrigierst du die Angabe und versuchst es noch
einmal. Die Originalmeldung des Druckers liegt eingeklappt unter **Technische
Details anzeigen**: Wenn du uns schreibst, kopier uns die mit, dann finden wir die
Ursache schneller.

:::info 💡 Reservier ihm die IP im Router
Wenn der Router einem Drucker eine neue Adresse gibt, suchen wir ihn von selbst
wieder, aber er ist eine Weile weg. Wenn du ihm die Adresse reservierst, vermeidest
du diese Lücke. Das ist eine Einstellung im Router, nicht in BolloPrint.
:::

## Was jede Marke von dir will

Hier entstehen die meisten Fragen. Es ist dasselbe, woran dich Schritt 2 erinnert,
kurz zusammengefasst:

| Marke | Was du an der Maschine tun musst | Kamera | Kannst du pausieren und abbrechen? |
|---|---|---|---|
| **Bambu Lab** | Den **LAN-Modus** am Display einschalten (Einstellungen → Netzwerk) und den **LAN-Zugangscode** verwenden, den er dir anzeigt | Ja | Ja, wenn du zusätzlich den **Entwicklermodus** einschaltest |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | **PrusaLink** einschalten und das **Passwort** verwenden, das er anzeigt (nicht das von Prusa Connect) | Noch nicht | Ja |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) und **andere Resindrucker (ChituBox)** | Nichts, sie fragen nach keinem Passwort | Bei den Modellen, die eine haben | Ja |
| **Elegoo Centauri Carbon 2** | Nichts; nur wenn du am Display einen Code festgelegt hast, gib ihn ein | Ja | Noch nicht |
| **Anycubic** (Beta: Kobra 3, Kobra S1, Kobra 4, Kobra X) | Den **LAN-Modus** einschalten (Einstellungen → Netzwerk). Dann nutzt der Drucker die Cloud und die App von Anycubic nicht mehr | Noch nicht | Noch nicht |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | **LAN Only** einschalten und den Prüfcode aus seinem Netzwerkmenü verwenden | Ja | Noch nicht |
| **Snapmaker** (U1) | Nichts | Ja | Ja |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1 …) | Meist nichts: nur wenn du in Moonraker einen API-Schlüssel gesetzt hast | Ja, wenn dein Klipper eine Webcam hat | Ja |

:::warning ⚠️ Bambu Lab: Der Zugangscode ändert sich
Jedes Mal, wenn du den LAN-Modus oder den Entwicklermodus ein- oder ausschaltest,
**erzeugt Bambu einen neuen Code**. Wenn ein Bambu, der gut lief, plötzlich keine
Verbindung mehr bekommt, ist das in neun von zehn Fällen der Grund: Schau noch
einmal auf den Code am Display und aktualisier ihn in BolloPrint. Und denk daran:
Der **Entwicklermodus** trennt ihn von Bambu Cloud, ab dann siehst du ihn nur noch
über den Agenten.
:::

:::info 💡 Dein Modell steht nicht in der Tabelle?
Schau unter [kompatible Drucker](/help/impresoras-compatibles). Wenn darin
**Klipper** läuft (jede selbst gebaute oder umgebaute Maschine), wird er
unterstützt, auch wenn die Marke auf keiner Liste steht.
:::

## Was dir der lokale Agent bringt

Mit dem laufenden Agenten bekommst du:

- **Fast alle Marken**: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge,
  Snapmaker und alles, was mit Klipper läuft. Die Cloud bietet das nicht, denn es
  gibt sie nur für Bambu Lab.
- **Kamera**: live, solange du die Seite offen hast, ein Foto, wann du willst, und
  ein Abschlussfoto im Verlauf jedes Drucks. Das ist keine Videoüberwachung: Es
  wird nichts aufgezeichnet.
- **Steuerung**: Pausieren, Fortsetzen und Abbrechen direkt aus BolloPrint, ohne
  zur Maschine zu laufen, bei denen, die es zulassen (schau in die Tabelle oben).
  Bei Bambu Lab mit dem Drucker im **LAN-Modus** und im **Entwicklermodus**.
- **Robustheit bei Internetausfällen**: Wenn deine Leitung ausfällt,
  **liest der Agent die Drucker weiter aus und speichert, was passiert**. Sobald
  die Verbindung zurück ist, schickt er alles, und dir fehlen diese Stunden nicht
  im Verlauf.
- **Unabhängigkeit vom Hersteller** und davon, dass seine Cloud weiter
  funktioniert.

Was auf keinem Weg geht, ist **Druckaufträge senden**: Die Datei schickst du
weiterhin aus deinem Slicer.

## Häufige Fragen

Die Fragen, die wir am häufigsten hören.

### Muss ich Ports am Router öffnen?

Nein. Keine Ports, keine feste IP, keine Firewall-Regeln. Es funktioniert hinter
einem ganz normalen Heimrouter.

### Brauche ich einen Agenten pro Drucker?

Nein. **Einer allein schafft die ganze Flotte.** Mehrere lohnen sich nur, wenn du
zwei Standorte oder zwei getrennte Netzwerke hast. Dann fragt dich **Per IP
hinzufügen**, welcher den Drucker verbindet.

### Was passiert, wenn ich den Rechner ausschalte oder eine neue Version herauskommt?

Beim Einschalten ist der Agent von selbst wieder da. Er aktualisiert sich auch
selbst: Wenn eine neue Version herauskommt, lädt er sie herunter und startet damit
neu, ohne dass du das Manifest anfassen musst. Du musst nur etwas tun, wenn wir dir
auf dem Bildschirm Bescheid geben.

### Warum kann ich nicht auf „Per IP hinzufügen“ klicken?

Weil keiner deiner Agenten verbunden ist, und das steht auch unter dem Button.
Hast du ihn noch nicht installiert, nutz **Installieren** in seiner Zeile; lief er
schon, prüf, ob der Rechner eingeschaltet ist und Internet hat.

:::info 💡 Brauchst du Hilfe?
Schreib uns über die [Kontaktseite](/contact) oder eröffne einen Thread in
[unserem Discord](/help/soporte-por-discord). Wenn du uns sagst, welche Drucker du
hast, sagen wir dir genau, was du mit jedem tun musst.
:::

Viel Freude damit, deine ganze Flotte im Blick zu haben, wo immer du bist.

![Bollo, das Maskottchen von BolloPrint, mit Werkstattbrille vor einer Farm arbeitender 3D-Drucker](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Verwandte Dokumentation

- [Drucker verbinden](/help/conectar-impresoras): die zwei Wege und welcher zu dir passt
- [Der lokale Agent](/help/el-agente-local): die vollständige Referenz
- [Den Agenten ausrollen](/help/desplegar-el-agente): die technischen Details, falls du sie brauchst
- [Verbindungsarten](/help/tipos-de-conexion): was jede Druckerfamilie kann
- [Kompatible Drucker](/help/impresoras-compatibles): such hier dein Modell
