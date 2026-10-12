---
slug: connect-printers-local-network-agent
title: "Verbinde deine Drucker über dein eigenes Netzwerk: der lokale Agent, Schritt für Schritt"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu … Ein kleiner Agent auf einem Rechner in der Werkstatt, deine ganze Flotte in BolloPrint, und am Router änderst du nichts.
date: 2026-09-08
updated: 2026-10-12
tags: [anleitungen]
cover: 01-portada.webp
draft: true
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

::animation{id="local-agent"}

## Wo du ihn installierst

Der Agent läuft auf **jedem Rechner in der Werkstatt, den du nicht ausschaltest**:
einem NAS, einem Mini-PC, einem Raspberry Pi oder dem Werkstatt-PC. Er muss nur
**immer eingeschaltet** sein und **Docker** haben.

Ideal ist es, wenn er **im selben Netzwerk wie die Drucker** steht, denn dann
findet er sie von selbst. Wenn das nicht geht, fügst du sie von Hand hinzu, und sie
funktionieren genauso.

## Leg den Agenten in BolloPrint an

Du beginnst in BolloPrint. Geh zu **Einstellungen → Drucker**, öffne den Reiter
**Lokaler Agent** und klick auf **Neuer Agent**.

Gib ihm einen Namen, der dir auch in sechs Monaten noch etwas sagt: **Benenn ihn
danach, wo er steht, nicht danach, was er ist.** „Erdgeschoss“ oder „Halle 2“
passen; „Agent 1“ nicht.

![Der Reiter Lokaler Agent mit dem Button Neuer Agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Kopier die Vorlage

Beim Anlegen zeigt dir BolloPrint eine **Vorlage**: einen Text, in dem alles, was
zu dir gehört, **bereits eingetragen** ist, die Schlüssel deines Agenten und die
passende Version. Es gibt nichts zu ersetzen oder auszufüllen.

Wähl das Format, das du nutzt (**Docker Compose** ist der Normalfall), und klick
auf **Kopieren**.

![Die Bereitstellungsvorlage mit dem Button zum Kopieren](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Kopier sie jetzt: Sie wird nur einmal angezeigt
Die Schlüssel laufen nicht ab, aber wir zeigen sie dir nicht noch einmal. Wenn du
die Vorlage verlierst, öffne den Agenten und erzeug mit **Schlüssel neu erzeugen**
eine neue.
:::

## Füg die Vorlage auf deinem Rechner ein

Das passiert auf deinem Rechner, nicht in BolloPrint, und hängt davon ab, wo du
ihn installierst:

- **Synology-NAS**: Installier **Container Manager** aus dem **Paket-Zentrum**,
  geh zu **Projekt → Erstellen**, füg die Vorlage ein und erstell das Projekt.
  Ohne einen einzigen Befehl.
- **Windows oder Mac**: Installier **Docker Desktop**, speicher die Vorlage in
  einem Ordner als `docker-compose.yml` und führ in diesem Ordner
  `docker compose up -d` aus.
- **Linux**: Installier **Docker** mit dem Paketmanager deiner Distribution,
  speicher die Vorlage als `docker-compose.yml` und führ dort
  `docker compose up -d` aus.
- **Portainer**: Füg dieselbe Vorlage in einen Stack ein und stell ihn bereit.

:::info 💡 Auf Windows und Mac werden die Drucker nicht von selbst gefunden
Docker läuft dort in einer virtuellen Maschine, die die Meldungen nicht sieht, die
die Drucker in dein Netzwerk schicken. Der Agent funktioniert genauso, aber die
Drucker fügst du selbst hinzu, wie weiter unten erklärt.
:::

## Prüf, ob er online ist

Geh zurück zu BolloPrint: In weniger als einer Minute springt der Agent auf
**Online**.

![Der Agent im Status Online](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Wenn nicht, liegt es fast immer an einer von drei Ursachen: Die Vorlage wurde
**nur halb eingefügt**, der Rechner hat **kein Internet**, oder eine **Firewall**
blockiert den ausgehenden Verkehr.

## Deine Drucker erscheinen von selbst

Ab dann **sucht der Agent von allein alle 15 Minuten nach Druckern in deinem
Netzwerk**. Die, die er findet, erscheinen in einer Liste mit Marke und Modell,
und du entscheidest:

- **Hinzufügen**: Du nimmst ihn auf, und er beginnt zu melden.
- **Ignorieren**: Er gehört nicht dir, oder du willst ihn hier nicht haben.

![Die im Netzwerk gefundenen Drucker mit den Buttons zum Hinzufügen und Ignorieren](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Wenn du gerade eine Maschine eingeschaltet hast und nicht warten willst, klick auf
**Jetzt suchen**. Manche Marken fragen beim Hinzufügen nach einem **Passwort**;
dazu weiter unten mehr.

## Wenn einer nicht auftaucht, füg ihn selbst hinzu

Dass ein Drucker nicht von selbst erscheint, ist in zwei Fällen **normal**:

- **Er ist in einem anderen Netzwerk.** Die Meldungen der Drucker gehen nicht von
  einem Netz ins andere.
- **Der Agent läuft auf Windows oder Mac.** Docker läuft dort in einer virtuellen
  Maschine.

Dir entgeht dadurch nichts: Du fügst ihn selbst hinzu, und er funktioniert
genauso, mit Kamera und Steuerung, wenn die Maschine das hat. Klick auf **Per IP
hinzufügen** und gib die Art des Druckers ein, seine Adresse in deinem Netzwerk
und, falls er eins verlangt, sein Passwort.

![Das Formular zum Hinzufügen eines Druckers über seine IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Reservier ihm die IP im Router
Wenn der Router einem Drucker eine neue Adresse gibt, suchen wir ihn von selbst
wieder, aber er ist eine Weile weg. Wenn du ihm die Adresse reservierst, vermeidest
du diese Lücke. Das ist eine Einstellung im Router, nicht in BolloPrint.
:::

## Was jede Marke von dir will

Hier entstehen die meisten Fragen. Kurz zusammengefasst:

| Marke | Was du an der Maschine tun musst | Kamera | Kannst du pausieren und abbrechen? |
|---|---|---|---|
| **Bambu Lab** | Den **LAN-Modus** am Display einschalten und den **Zugangscode** verwenden, den er dir anzeigt | Ja | Ja, wenn du zusätzlich den **Entwicklermodus** einschaltest |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Das **Passwort** verwenden, das der Drucker selbst anzeigt | Noch nicht | Ja |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1 …) | Meist nichts: Er verbindet sich in der Regel ohne Passwort | Ja, wenn dein Klipper eine Webcam hat | Ja |
| **Elegoo-Harzdrucker** (Mars, Saturn, Jupiter) | Nichts, er fragt nach keinem Passwort | Bei den Modellen, die eine haben | Ja |
| **Elegoo Centauri Carbon 2** | Nur, wenn du am Display einen Code festgelegt hast | Ja | Noch nicht |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | **LAN Only** einschalten und den Code vom Display verwenden | Ja | Noch nicht |

:::warning ⚠️ Bambu Lab: Der Zugangscode ändert sich
Jedes Mal, wenn du den LAN-Modus ein- oder ausschaltest, **erzeugt Bambu einen
neuen Code**. Wenn ein Bambu, der gut lief, plötzlich keine Verbindung mehr
bekommt, ist das in neun von zehn Fällen der Grund: Schau noch einmal auf den Code
am Display und aktualisier ihn in BolloPrint.
:::

:::info 💡 Dein Modell steht nicht in der Tabelle?
Schau unter [kompatible Drucker](/help/impresoras-compatibles). Wenn darin
**Klipper** läuft (jede selbst gebaute oder umgebaute Maschine), wird er
unterstützt, auch wenn die Marke auf keiner Liste steht.
:::

## Was dir der lokale Agent bringt

Mit dem laufenden Agenten bekommst du:

- **Fast alle Marken**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron … Die Cloud bietet das nicht, denn es gibt sie nur für Bambu Lab.
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
zwei Standorte oder zwei getrennte Netzwerke hast.

### Was passiert, wenn ich den Rechner ausschalte oder eine neue Version herauskommt?

Beim Einschalten ist der Agent von selbst wieder da. Er aktualisiert sich auch
selbst: Wenn eine neue Version herauskommt, lädt er sie herunter und startet damit
neu. Du musst nur etwas tun, wenn wir dir auf dem Bildschirm Bescheid geben.

:::info 💡 Brauchst du Hilfe?
Schreib uns über die [Kontaktseite](/contact) oder eröffne einen Thread in
[unserem Discord](/help/soporte-por-discord). Wenn du uns sagst, welche Drucker du
hast, sagen wir dir genau, was du mit jedem tun musst.
:::

## Verwandte Dokumentation

- [Drucker verbinden](/help/conectar-impresoras): die zwei Wege und welcher zu dir passt
- [Der lokale Agent](/help/el-agente-local): die vollständige Referenz
- [Den Agenten ausrollen](/help/desplegar-el-agente): die technischen Details, falls du sie brauchst
- [Verbindungsarten](/help/tipos-de-conexion): was jede Druckerfamilie kann
- [Kompatible Drucker](/help/impresoras-compatibles): such hier dein Modell
