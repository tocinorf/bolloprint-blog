---
slug: connect-bambu-lab-printers-cloud
title: "Verbinde deine Bambu-Lab-Drucker in fünf Minuten mit BolloPrint"
description: Ohne etwas zu installieren und ohne Passwort. Du gibst die E-Mail deines Bambu-Lab-Kontos ein, bestätigst einen Code, und deine Drucker erscheinen von selbst, mit dem, was sie gerade drucken, und ihrem ganzen Verlauf.
date: 2026-10-12
updated: 2026-10-14
tags: [anleitungen]
cover: 01-portada.webp
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

![Die Detailseite eines Druckers, der gerade druckt, mit Fortschritt und Temperaturen](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora-de.png "42%")

## Was du brauchst

Bevor du anfängst, halte diese drei Dinge bereit:

- Einen Zugang zu BolloPrint als **Inhaber** oder **Admin**. Mit einer anderen
  Rolle erscheint dieser Bildschirm nicht.
- Die **E-Mail-Adresse** deines Bambu-Lab-Kontos. Das Passwort brauchst du nicht.
- Dieses **E-Mail-Postfach** geöffnet: Bambu schickt dir einen Code.

## Öffne den Druckerbildschirm

Alles passiert an einer Stelle: **Einstellungen → Drucker**. Dort siehst du drei
Reiter:

- **Drucker**: die Liste all deiner Maschinen, egal über welchen Weg sie
  verbunden sind.
- **Lokaler Agent**: zum Verbinden über dein eigenes Netzwerk. Das erklären wir
  in einem [eigenen Artikel](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: der Reiter, den du jetzt brauchst.

Öffne **Bambu Cloud**.

![Der Bildschirm Einstellungen → Drucker mit seinen drei Reitern](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas-de.png)

## Gib die E-Mail deines Bambu-Kontos ein

Verwende die deines Bambu-Lab-Kontos (genau diese E-Mail, keine andere von dir)
und klick auf **Code senden**.

![Das Bambu-Cloud-Formular, mit eingetragener E-Mail-Adresse des Kontos und dem Button Code senden](/blog/media/2026-09-08-impresoras-por-la-nube/03-correo-de.png)

:::info 💡 Wir fragen nicht nach deinem Passwort
BolloPrint **sieht und speichert es nie**: Zum Verbinden reicht der Code, den
Bambu dir per E-Mail schickt.
:::

## Bestätige den Code aus der E-Mail

Bambu schickt dir einen **6-stelligen Code** von `noreply@bambulab.com` (die
E-Mail kommt auf Englisch). Wenn du ihn nicht siehst, **sieh im Spam-Ordner
nach**: Dort landet er häufig. Gib ihn auf demselben Bildschirm ein und klick auf **Überprüfen und verbinden**.

![Das Feld für den 6-stelligen Code und der Button Überprüfen und verbinden](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-de.png)

Drei Details ersparen dir einen zweiten Versuch:

- Der Code **läuft nach 10 Minuten ab**, und nur der zuletzt angeforderte gilt.
  Wenn er abgelaufen ist, klick auf **Code erneut senden**.
- Du kannst ihn **so einfügen, wie er ankommt**: Leerzeichen oder Bindestriche
  werden automatisch entfernt.
- Wenn du dich bei der E-Mail vertan hast, klick auf **E-Mail-Adresse ändern**.

Sobald er angenommen ist, siehst du **Konto verifiziert und verbunden**.

## Deine Drucker sind schon da

Du musst sie nicht einzeln anlegen: **Alle Drucker dieses Kontos erscheinen von
selbst** im Reiter **Drucker**, jeder mit seinem Namen und seiner Seriennummer.

![Die Druckerliste mit den gerade aufgetauchten Bambu-Maschinen](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas-de.png)

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
- **Die Sitzung bei Bambu hält 90 Tage, verlängert sich aber von selbst**:
  BolloPrint erneuert sie, bevor sie abläuft, und du musst dich nicht neu
  anmelden. Nur wenn Bambu sie von sich aus beendet, sagen wir dir auf dem
  Bildschirm Bescheid, und dann reicht ein neuer Code.

Und eins gilt für jede Verbindungsart: **BolloPrint schickt keine
Druckaufträge**. Die Datei schickst du weiterhin aus deinem Slicer; BolloPrint
liest aus, was die Maschine tut, und protokolliert es.

## Häufige Probleme

### Was, wenn du dich bei Bambu mit Google oder Apple anmeldest?

Gib die E-Mail dieses Google- oder Apple-Kontos ein: Der Code kommt genauso dort
an. Ein Passwort musst du nicht mehr anlegen.

### Warum heißt es, es gebe kein Konto mit dieser E-Mail?

Wenn **„Es gibt kein Bambu-Lab-Konto mit dieser E-Mail-Adresse.“** erscheint, ist
die E-Mail nicht die deines Bambu-Kontos: Bambu schickt den Code trotzdem, lehnt
ihn aber ab, wenn du ihn eingibst. Schau nach, mit welcher du dich in der
Bambu-App anmeldest, und klick auf **E-Mail-Adresse ändern**.

### Muss ich das Konto ab und zu neu verbinden?

Nein. Die Sitzung hält 90 Tage, und BolloPrint erneuert sie von selbst, bevor sie
abläuft. Wenn Bambu sie doch einmal von sich aus beendet, siehst du **„Sitzung
abgelaufen“** und einen Button **Erneut anmelden**: Du forderst einen neuen Code
an, und fertig, ohne etwas zu trennen.

### Was tun, wenn eine Zwei-Faktor-Authentifizierung verlangt wird?

Du musst sie in deinem Bambu-Konto deaktivieren, um es verbinden zu können.

### Was tun, wenn der Code nicht ankommt oder nicht angenommen wird?

Wenn er nicht ankommt, sieh im Spam-Ordner nach und klick auf **Code erneut
senden**. Wird er nicht angenommen, ist er höchstwahrscheinlich abgelaufen,
oder es ist nicht der zuletzt angeforderte: Fordere einen neuen an und füg ihn
vollständig ein.

## Wenn du mehr brauchst: der lokale Agent

Die Cloud zeigt dir alle Informationen, erlaubt dir aber nicht, die Drucker zu
steuern, und es gibt sie nur für Bambu Lab. Wenn du mehr brauchst, ist der
**lokale Agent** die Lösung: ein kleines Programm, das du auf einem Rechner in
deiner Werkstatt installierst und das über dein eigenes Netzwerk mit den Druckern
spricht. Einer reicht für die ganze Flotte, und er bietet dir:

- **fast alle Marken**: Prusa, Elegoo, Anycubic, FlashForge, Snapmaker und
  alles, was mit Klipper läuft (QIDI, Sovol, Voron …);
- **Kamera**, live und mit einem Abschlussfoto, das bei jedem Druck gespeichert
  wird;
- **Pausieren, Fortsetzen und Abbrechen** direkt aus BolloPrint, ohne zur
  Maschine zu gehen;
- **Robustheit bei Internetausfällen**: Er liest deine Drucker weiter aus und
  überträgt alles, sobald die Verbindung zurück ist.

:::info 💡 Um einem Bambu Befehle zu schicken
Der Drucker muss im **LAN-Modus** und im **Entwicklermodus** sein. Beides schaltest
du an seinem Display ein. Der Entwicklermodus trennt ihn von Bambu Cloud: Ab dann
siehst du ihn nur noch über den Agenten.
:::

Schritt für Schritt erklären wir das in
[deine Drucker über dein eigenes Netzwerk verbinden](/blog/connect-printers-local-network-agent).

Wenn du Fragen hast, schreib uns über die [Kontaktseite](/contact) oder in
[unserem Discord](/help/soporte-por-discord).

Viel Freude mit all deinen Druckern auf einem einzigen Bildschirm.

![Bollo, das Maskottchen von BolloPrint, mit Werkstattbrille, träumt von einem 3D-Drucker](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp "60%")

## Verwandte Dokumentation

- [Drucker verbinden](/help/conectar-impresoras): die zwei Wege und welcher zu dir passt
- [Drucker über die Cloud](/help/impresoras-por-la-nube): die vollständige Referenz zu diesem Bildschirm
- [Kompatible Drucker](/help/impresoras-compatibles): such hier dein Modell
- [Verbindungsarten](/help/tipos-de-conexion): was jede Druckerart ermöglicht
