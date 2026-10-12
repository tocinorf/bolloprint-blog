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

Deine Drucker stehen in der Werkstatt. Du nicht immer. Und jedes Mal, wenn du
wissen willst, ob einer noch druckt, ob es gut geworden ist oder ob noch Material
drin ist, musst du davorstehen.

Dass sie in deinem Netzwerk sind, heißt nicht, dass du auch da sein musst. Dafür
gibt es den **lokalen Agenten**: ein kleines Programm, das auf einem Rechner in
deiner Werkstatt läuft, über dein eigenes Netzwerk mit deinen Druckern spricht und
BolloPrint laufend erzählt, was er sieht.

- **Du änderst nichts am Router.** Keine Ports öffnen, keine feste IP, keine Firewall.
- **Superleicht.** Jeder Rechner, der bei dir sowieso läuft, reicht ihm.
- **Einer für die ganze Flotte**, egal wie groß sie ist.

::animation{id="local-agent"}

## Wo er hinkommt

Auf **jeden Rechner in der Werkstatt, den du nicht ausschaltest**: ein NAS, ein
Mini-PC, ein Raspberry Pi, der Werkstatt-PC. Er braucht nur zwei Dinge: Er muss
**immer eingeschaltet** sein und **Docker** haben.

Noch besser, wenn er **im selben Netzwerk wie die Drucker** steht, denn dann findet
er sie von selbst. Wenn das nicht geht, fügst du sie von Hand hinzu, und sie
funktionieren genauso.

## Schritt 1 — Leg ihn in BolloPrint an

Geh zu **Einstellungen → Drucker**, öffne den Reiter **Lokaler Agent** und klick
auf **Neuer Agent**.

Gib ihm einen Namen, der dir auch in sechs Monaten noch etwas sagt. Ein Tipp:
**Benenn ihn danach, wo er steht, nicht danach, was er ist.** „Erdgeschoss“ oder
„Halle 2“ passen; „Agent 1“ nicht.

![Der Reiter Lokaler Agent mit dem Button Neuer Agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Schritt 2 — Kopier die Vorlage

Beim Anlegen zeigt dir BolloPrint eine **Vorlage**: einen Text, in dem schon alles
steht, was zu dir gehört — die Schlüssel deines Agenten und die passende
Version —, **bereits eingetragen**. Es gibt nichts zu ersetzen oder auszufüllen.

Wähl das Format, das du nutzt (**Docker Compose** ist der Normalfall), und klick
auf **Kopieren**.

![Die Bereitstellungsvorlage mit dem Button zum Kopieren](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Kopier sie jetzt: Sie wird nur einmal angezeigt
Die Schlüssel laufen nicht ab, aber wir zeigen sie dir nicht noch einmal. Wenn du
die Vorlage verlierst, ist das nicht schlimm: Du öffnest den Agenten und erzeugst
mit **Schlüssel neu erzeugen** eine neue.
:::

## Schritt 3 — Füg sie dort ein, wo er laufen soll

Das passiert jetzt auf deinem Rechner, nicht in BolloPrint. Es hängt davon ab, wo
du ihn hinstellst:

**Auf einem Synology-NAS.** Installier **Container Manager** aus dem
**Paket-Zentrum**. Geh zu **Projekt → Erstellen**, füg die Vorlage ein und klick
auf Erstellen. Ohne einen einzigen Befehl.

**Auf Windows oder Mac.** Installier **Docker Desktop**, speicher die Vorlage in
einem Ordner als `docker-compose.yml` und starte ihn aus diesem Ordner mit
`docker compose up -d`.

**Auf Linux.** Installier **Docker** mit dem Paketmanager deiner Distribution,
speicher die Vorlage als `docker-compose.yml` und führ in diesem Ordner
`docker compose up -d` aus.

Du nutzt **Portainer**? Füg dieselbe Vorlage in einen Stack ein und stell sie bereit.

:::info 💡 Auf Windows und Mac werden die Drucker nicht von selbst gefunden
Docker läuft dort in einer virtuellen Maschine, die die Meldungen nicht sieht, die
die Drucker in dein Netzwerk schicken. Der Agent funktioniert genauso, aber die
Drucker fügst du selbst hinzu, wie in Schritt 6.
:::

## Schritt 4 — Prüf, ob er online ist

Geh zurück zu BolloPrint. In weniger als einer Minute springt der Agent auf
**Online**.

![Der Agent im Status Online](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Wenn er nicht auftaucht, liegt es fast immer an einem von drei Dingen: Die Vorlage
wurde **nur halb eingefügt**, der Rechner hat **kein Internet**, oder eine
**Firewall** blockiert den ausgehenden Verkehr.

## Schritt 5 — Deine Drucker erscheinen von selbst

Der Agent **sucht von allein alle 15 Minuten nach Druckern in deinem Netzwerk**.
Die, die er findet, erscheinen in einer Liste mit Marke und Modell, und du
entscheidest:

- **Hinzufügen** — du nimmst ihn auf, und er beginnt zu melden.
- **Ignorieren** — er gehört nicht dir, oder du willst ihn hier nicht haben.

![Die im Netzwerk gefundenen Drucker mit den Buttons zum Hinzufügen und Ignorieren](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Wenn du gerade eine Maschine eingeschaltet hast und nicht warten willst, gibt es
den Button **Jetzt suchen**.

Manche fragen beim Hinzufügen nach einem **Passwort**. Das hängt von der Marke ab,
und dazu kommen wir gleich.

## Schritt 6 — Wenn einer nicht auftaucht, fügst du ihn selbst hinzu

Dass ein Drucker nicht von selbst erscheint, ist in zwei Fällen **normal**:

- **Er ist in einem anderen Netzwerk.** Die Meldungen der Drucker gehen nicht von
  einem Netz ins andere, deshalb werden sie nicht von selbst gefunden.
- **Der Agent läuft auf Windows oder Mac.** Docker läuft dort in einer virtuellen
  Maschine, und auch dann werden sie nicht von selbst gefunden.

**Dir entgeht dadurch nichts.** Du fügst ihn selbst hinzu, und er funktioniert
genauso, mit Kamera und Steuerung, wenn die Maschine das hat. Du klickst auf **Per
IP hinzufügen** und gibst die Art des Druckers ein, seine Adresse in deinem
Netzwerk und, falls er eins verlangt, sein Passwort.

![Das Formular zum Hinzufügen eines Druckers über seine IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png)

:::info 💡 Reservier ihm die IP im Router
Wenn der Router einem Drucker eine neue Adresse gibt, suchen wir ihn von selbst
wieder, aber er ist eine Weile weg. Wenn du ihm die Adresse reservierst, vermeidest
du diese Lücke. Das ist eine Einstellung im Router, nicht in BolloPrint.
:::

## Was jede Marke von dir will

Hier bleiben die meisten hängen. Kurz zusammengefasst:

| Marke | Was du an der Maschine tun musst | Kamera | Kannst du pausieren und abbrechen? |
|---|---|---|---|
| **Bambu Lab** | Den **LAN-Modus** am Display einschalten und den **Zugangscode** verwenden, den er dir anzeigt | Ja | Ja, wenn du zusätzlich den **Entwicklermodus** einschaltest |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Das **Passwort** verwenden, das der Drucker selbst anzeigt | Noch nicht | Ja |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1 …) | Meist nichts: Er verbindet sich in der Regel ohne Passwort | Ja, wenn dein Klipper eine Webcam hat | Ja |
| **Elegoo-Harzdrucker** (Mars, Saturn, Jupiter) | Nichts, er fragt nach keinem Passwort | Bei den Modellen, die eine haben | Ja |
| **Elegoo Centauri Carbon 2** | Nur, wenn du am Display einen Code festgelegt hast | Ja | Noch nicht |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | **LAN Only** einschalten und den Code vom Display verwenden | Ja | Noch nicht |

:::warning ⚠️ Bambu Lab: Der Zugangscode ÄNDERT sich
Jedes Mal, wenn du den LAN-Modus ein- oder ausschaltest, **erzeugt Bambu einen
neuen Code**. Wenn ein Bambu, der gut lief, plötzlich keine Verbindung mehr
bekommt, ist es in neun von zehn Fällen genau das: Schau noch einmal auf den Code
am Display und aktualisier ihn in BolloPrint.
:::

:::info 💡 Dein Modell steht nicht in der Tabelle?
Schau unter [kompatible Drucker](/help/impresoras-compatibles). Und wenn darin
**Klipper** läuft — jede selbst gebaute oder umgebaute Maschine —, ist er dabei,
auch wenn die Marke auf keiner Liste steht.
:::

## Wenn du Bambu schon über die Cloud hattest, leg sie nicht doppelt an

Wenn der Agent in deinem Netzwerk eine Maschine findet, die **du schon über die
Cloud verbunden hattest**, erkennt BolloPrint das und sagt es dir: *„Das ist
‚P1S-02‘, den du schon über Bambu Cloud hast“*. Der Button heißt **Auch per LAN
verbinden**.

Klick darauf, und du hast ihn nicht zweimal:

- Es bleibt **ein einziger Drucker**, mit seiner Nummer, seinem Namen und seinem
  ganzen Verlauf.
- Er belegt **nur einen Platz** in deinem Plan.
- Und er bekommt die **Kamera** dazu, die du über die Cloud nicht hattest.

![Der Hinweis, dass dieser Drucker schon in Bambu Cloud ist, mit dem Button Auch per LAN verbinden](/blog/media/2026-09-08-impresoras-red-local-agente/07-tambien-por-lan.png)

:::warning ⚠️ Der LAN-Modus trennt die Bambu-Cloud
Sobald du ihn einschaltest, spricht der Drucker nicht mehr mit der Cloud von Bambu
Lab. Ab dann sieht BolloPrint ihn über den Agenten.
:::

## Was du konkret davon hast

- **Fast alle Marken.** Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron … Das bietet dir die Cloud nicht, die es nur für Bambu Lab gibt.
- **Kamera.** Live zuschauen, solange du die Seite offen hast, ein Foto machen,
  wann du willst, und ein Abschlussfoto im Verlauf jedes Drucks. Das ist keine
  Videoüberwachung: Es wird nichts aufgezeichnet.
- **Steuerung.** Pausieren, Fortsetzen und Abbrechen direkt aus BolloPrint, ohne
  zur Maschine zu laufen, bei denen, die es zulassen (schau in die Tabelle oben).
  Bei Bambu Lab mit dem Drucker im **LAN-Modus** und im **Entwicklermodus**.
- **Übersteht Internetausfälle.** Wenn deine Leitung ausfällt, **liest der Agent
  die Drucker weiter aus und speichert, was passiert**. Sobald das Netz zurück ist,
  schickt er alles. Diese Stunden fehlen dir nicht im Verlauf.
- **Du bist nicht vom Hersteller abhängig** und auch nicht davon, dass seine Cloud
  weiter funktioniert.

Was auf keinem Weg geht: **Druckaufträge senden**. Die Datei schickst du weiterhin
aus deinem Slicer.

## Fragen, die wir oft hören

**Muss ich Ports am Router öffnen?** Nein. Keine Ports, keine feste IP, keine
Firewall-Regeln. Es funktioniert hinter einem ganz normalen Heimrouter.

**Brauche ich einen Agenten pro Drucker?** Nein. **Einer allein schafft die ganze
Flotte.** Mehrere lohnen sich nur, wenn du zwei Standorte oder zwei getrennte
Netzwerke hast.

**Und wenn ich den Rechner ausschalte oder eine neue Version herauskommt?** Beim
Einschalten ist der Agent von selbst wieder da. Und er aktualisiert sich selbst:
Wenn eine neue Version herauskommt, lädt er sie herunter und startet damit neu.
Nur wenn wir dir auf dem Bildschirm Bescheid geben, musst du selbst etwas tun.

:::info 💡 Hängst du irgendwo fest?
Schreib uns über die [Kontaktseite](/contact) oder eröffne einen Thread in
[unserem Discord](/help/soporte-por-discord). Wenn du uns sagst, welche Drucker du
hast, sagen wir dir genau, was du mit jedem tun musst.
:::

## Verwandte Dokumentation

- [Drucker verbinden](/help/conectar-impresoras) — die zwei Wege und welcher zu dir passt
- [Der lokale Agent](/help/el-agente-local) — die vollständige Referenz
- [Den Agenten ausrollen](/help/desplegar-el-agente) — die technischen Details, falls du sie brauchst
- [Verbindungsarten](/help/tipos-de-conexion) — was jede Druckerfamilie kann
- [Kompatible Drucker](/help/impresoras-compatibles) — such hier dein Modell
