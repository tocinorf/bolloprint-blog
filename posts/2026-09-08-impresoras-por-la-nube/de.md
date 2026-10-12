---
slug: connect-bambu-lab-printers-cloud
title: "Verbinde deine Bambu-Lab-Drucker in fünf Minuten mit BolloPrint"
description: Ohne etwas zu installieren. Du verbindest dein Bambu-Lab-Konto, bestätigst einen Code, und deine Drucker erscheinen von selbst, mit dem, was sie gerade drucken, und ihrem ganzen Verlauf.
date: 2026-09-08
updated: 2026-10-12
tags: [anleitungen]
cover: 01-portada.webp
draft: true
---

Wenn bei dir mehrere Bambu laufen, kennst du wahrscheinlich die Routine: Um zu
sehen, wie es läuft, gehst du zu jedem Drucker und schaust auf sein Display. Ist
der erste fertig? Hat der zweite noch Material? Wie viele Stunden hast du diesen
Monat gedruckt?

All das kannst du auf einem einzigen Bildschirm sehen, und **ohne etwas zu
installieren**. Du verbindest dein Bambu-Lab-Konto mit BolloPrint, und deine
Drucker erscheinen von selbst. Das dauert etwa fünf Minuten.

::animation{id="bambu-cloud"}

## Was du von jedem Drucker siehst

In Echtzeit und ohne etwas anzufassen:

- ob er eingeschaltet und verbunden ist;
- was er gerade druckt, den **Fortschritt in Prozent** und die Restzeit;
- die Temperaturen von Düse und Bett;
- die geladenen **Materialien**, Fach für Fach, wenn du ein AMS hast;
- die Meldungen der Maschine selbst.

Und was du am Monatsende am deutlichsten merkst: **Jeder Druck wird
protokolliert**, mit Dauer, Material und Kosten. Du musst nichts aufschreiben.

![Die Detailseite eines Druckers, der gerade druckt, mit Fortschritt und Temperaturen](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## Was du brauchst

Bevor du anfängst, halte diese drei Dinge bereit:

- Einen Zugang zu BolloPrint als **Inhaber** oder **Admin**. Mit einer anderen
  Rolle erscheint dieser Bildschirm nicht.
- **E-Mail und Passwort** deines Bambu-Lab-Kontos.
- Das geöffnete **E-Mail-Postfach** dieses Kontos: Bambu schickt dir einen Code.

:::warning ⚠️ Wenn du dich bei Bambu mit Google, Apple oder Facebook anmeldest
BolloPrint braucht **E-Mail und Passwort** des Kontos. Wenn du nie ein Passwort
vergeben hast, weil du immer „Mit Google fortfahren“ verwendest, leg zuerst eins
auf der Website von Bambu Lab an und komm dann zurück.
:::

## Öffne den Druckerbildschirm

Alles passiert an einer Stelle: **Einstellungen → Drucker**. Dort siehst du drei
Reiter:

- **Drucker**: die Liste all deiner Maschinen, egal über welchen Weg sie
  verbunden sind.
- **Lokaler Agent**: zum Verbinden über dein eigenes Netzwerk. Das erklären wir
  in einem [eigenen Artikel](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: der Reiter, den du jetzt brauchst.

Öffne **Bambu Cloud**.

![Der Bildschirm Einstellungen → Drucker mit seinen drei Reitern](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Gib E-Mail und Passwort von Bambu ein

Verwende die Zugangsdaten deines Bambu-Lab-Kontos (genau diese E-Mail, keine
andere von dir) und klick auf **Mit Bambu Lab verbinden**.

![Das Bambu-Cloud-Formular, mit eingetragener E-Mail-Adresse; das Passwort fehlt noch](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 Dein Passwort wird nicht gespeichert
Es bleibt **nur in deinem Browser**, und auch nur, bis du die Bestätigung
abgeschlossen hast.
:::

## Bestätige den Code aus der E-Mail

Bambu schickt dir einen **6-stelligen Code** von `noreply@bambulab.com`. Wenn du
ihn nicht siehst, **sieh im Spam-Ordner nach**: Dort landet er häufig. Gib ihn
auf demselben Bildschirm ein und klick auf **Überprüfen und verbinden**.

![Das Feld für den 6-stelligen Code und der Button Überprüfen und verbinden](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Zwei Details ersparen dir einen zweiten Versuch:

- Der Code **läuft nach etwa 5 Minuten ab**. Wenn er abgelaufen ist, klick auf
  **Code erneut senden**.
- Du kannst ihn **so einfügen, wie er ankommt**: Leerzeichen oder Bindestriche
  werden automatisch entfernt.

Sobald er angenommen ist, siehst du **Konto verifiziert und verbunden**.

## Deine Drucker sind schon da

Du musst sie nicht einzeln anlegen: **Alle Drucker dieses Kontos erscheinen von
selbst** im Reiter **Drucker**, jeder mit seinem Namen und seiner Seriennummer.

![Die Druckerliste mit den gerade aufgetauchten Bambu-Maschinen](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

Oben siehst du einen Zähler wie `3 / 6 aktiv`: Das sind die Drucker, die dein
Plan umfasst. Mit dem Schalter in jeder Zeile aktivierst oder deaktivierst du die
Drucker, die du möchtest. Ein deaktivierter Drucker zählt nicht für das Limit,
**behält aber seinen ganzen Verlauf**. Und wenn du eine ganze Flotte verbindest
und nicht genug Plätze für alle hast, kommen die übrigen deaktiviert herein,
statt das Limit deines Plans zu überschreiten.

## Was über die Cloud nicht möglich ist

Das solltest du von Anfang an wissen, damit du nicht nach Optionen suchst, die es
nicht gibt:

- **Es gibt nur Lesezugriff.** Über die Cloud kannst du aus BolloPrint heraus
  nicht pausieren, fortsetzen oder abbrechen: Bambu nimmt diese Befehle nur über
  dein lokales Netzwerk an, und nur mit dem Drucker in einem bestimmten Modus.
  Dazu kommen wir am Ende.
- **Es gibt keine Kamera.** Du siehst aber das Slicer-Bild des Druckauftrags,
  also eine Vorschau, nicht das, was in der Maschine passiert.
- **Es hängt von zwei Internetverbindungen ab**, deiner und der von Bambu. Fällt
  eine davon aus, erscheint der Drucker als getrennt, auch wenn er ganz normal
  druckt.
- **Die Sitzung läuft ab und zu ab**, und du musst das Konto neu verbinden. Wir
  sagen dir auf dem Bildschirm Bescheid.

Und eins gilt für jede Verbindungsart: **BolloPrint schickt keine
Druckaufträge**. Die Datei schickst du weiterhin aus deinem Slicer; BolloPrint
liest aus, was die Maschine tut, und protokolliert es.

## Häufige Probleme

### Warum meldet Bambu ein falsches Passwort, obwohl es stimmt?

Das ist das häufigste Problem. **„Falsches Bambu-Lab-Konto oder falsches
Passwort“** erscheint fast immer bei einem gerade erst angelegten Passwort, das
noch nie benutzt wurde: Beim Konto ist die E-Mail-Bestätigung noch offen, und
Bambu weist nicht darauf hin. Melde dich **einmal** mit dieser E-Mail und diesem
Passwort auf der Bambu-Website an, erledige, was verlangt wird, und versuch es
dann erneut.

### Was, wenn du dich bei Bambu mit Google oder Apple anmeldest?

Auf diesem Weg geht es nicht. Leg auf der Website von Bambu Lab ein Passwort an
und verwende die E-Mail mit diesem Passwort.

### Warum heißt es, es gebe kein Konto mit dieser E-Mail?

Wenn **„Es gibt kein Bambu-Lab-Konto mit dieser E-Mail-Adresse“** erscheint, ist
die E-Mail nicht die deines Bambu-Kontos. Schau nach, mit welcher du dich in der
Bambu-App anmeldest.

### Was tun, wenn eine Zwei-Faktor-Authentifizierung verlangt wird?

Du musst sie in deinem Bambu-Konto deaktivieren, um es verbinden zu können.

### Was tun, wenn der Code nicht ankommt oder nicht angenommen wird?

Wenn er nicht ankommt, sieh im Spam-Ordner nach und klick auf **Code erneut
senden**. Wird er nicht angenommen, ist er höchstwahrscheinlich abgelaufen:
Fordere einen neuen an und füg ihn vollständig ein.

## Wenn du mehr brauchst: der lokale Agent

Die Cloud zeigt dir alle Informationen, erlaubt dir aber nicht, die Drucker zu
steuern, und es gibt sie nur für Bambu Lab. Wenn du mehr brauchst, ist der
**lokale Agent** die Lösung: ein kleines Programm, das du auf einem Rechner in
deiner Werkstatt installierst und das über dein eigenes Netzwerk mit den Druckern
spricht. Einer reicht für die ganze Flotte, und er bietet dir:

- **fast alle Marken**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron …;
- **Kamera**, live und mit einem Abschlussfoto, das bei jedem Druck gespeichert
  wird;
- **Pausieren, Fortsetzen und Abbrechen** direkt aus BolloPrint, ohne zur
  Maschine zu gehen;
- **Robustheit bei Internetausfällen**: Er liest deine Drucker weiter aus und
  überträgt alles, sobald die Verbindung zurück ist.

:::info 💡 Um einem Bambu Befehle zu schicken
Der Drucker muss im **LAN-Modus** und im **Entwicklermodus** sein. Beides schaltest
du an seinem Display ein.
:::

Schritt für Schritt erklären wir das in
[deine Drucker über dein eigenes Netzwerk verbinden](/blog/connect-printers-local-network-agent).

Wenn du Fragen hast, schreib uns über die [Kontaktseite](/contact) oder in
[unserem Discord](/help/soporte-por-discord).

## Verwandte Dokumentation

- [Drucker verbinden](/help/conectar-impresoras): die zwei Wege und welcher zu dir passt
- [Drucker über die Cloud](/help/impresoras-por-la-nube): die vollständige Referenz zu diesem Bildschirm
- [Kompatible Drucker](/help/impresoras-compatibles): such hier dein Modell
- [Verbindungsarten](/help/tipos-de-conexion): was jede Druckerart ermöglicht
