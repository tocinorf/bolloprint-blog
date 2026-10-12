---
slug: connect-bambu-lab-printers-cloud
title: "Verbinde deine Bambu-Lab-Drucker in fünf Minuten mit BolloPrint"
description: Ohne etwas zu installieren. Du verbindest dein Bambu-Konto, und deine Maschinen erscheinen von selbst, mit dem, was sie gerade drucken, und ihrem ganzen Verlauf.
date: 2026-09-08
updated: 2026-10-12
tags: [anleitungen]
cover: 01-portada.webp
draft: true
---

Du hast drei Bambu im Einsatz, und um zu wissen, wie es läuft, stehst du auf und
schaust auf das Display von jedem einzelnen. Ist der erste schon fertig? Hat der
zweite noch Material? Wie viele Stunden hast du diesen Monat gedruckt?

Es gibt eine Möglichkeit, alles auf einem einzigen Bildschirm zu sehen, und **du
musst nichts installieren**. Du verbindest dein Bambu-Lab-Konto mit BolloPrint,
und deine Maschinen erscheinen von selbst. Fünf Minuten.

::animation{id="bambu-cloud"}

## Das bekommst du

Von jedem Drucker, live und ohne etwas anzufassen:

- ob er eingeschaltet und verbunden ist;
- was er gerade druckt, den **Fortschritt in Prozent** und die Restzeit;
- die Temperaturen von Düse und Bett;
- die geladenen **Materialien**, Fach für Fach, wenn du ein AMS hast;
- die Meldungen der Maschine selbst.

Und dazu das, was am Monatsende wirklich den Unterschied macht: **Jeder Druck
wird protokolliert**, mit Dauer, Material und Kosten. Ohne dass du etwas von Hand
aufschreibst.

![Die Detailseite eines Druckers, der gerade druckt, mit Fortschritt und Temperaturen](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png)

## Was du brauchst

- Einen Zugang zu BolloPrint als **Inhaber** oder **Admin**. Mit einer anderen
  Rolle siehst du diesen Bildschirm nicht.
- Dein **Bambu-Lab**-Konto, mit **E-Mail und Passwort**.
- Zugriff auf das **E-Mail-Postfach** dieses Kontos: Bambu schickt dir einen Code.

:::warning ⚠️ Wenn du dich bei Bambu mit Google, Apple oder Facebook anmeldest, klappt das hier nicht
BolloPrint braucht die **E-Mail und das Passwort** deines Bambu-Kontos. Wenn du
nie ein Passwort vergeben hast, weil du immer auf „Mit Google fortfahren“ klickst,
leg es zuerst auf der Website von Bambu Lab an und komm damit hierher zurück.
:::

## Schritt 1 — Öffne den Druckerbildschirm

Geh zu **Einstellungen → Drucker**. Dort siehst du drei Reiter:

- **Drucker** — die Liste all deiner Maschinen, egal über welchen Weg sie kommen.
- **Lokaler Agent** — zum Verbinden über dein Netzwerk. Dafür gibt es eine [eigene Anleitung](/blog/connect-printers-local-network-agent).
- **Bambu Cloud** — um den geht es heute.

Öffne **Bambu Cloud**.

![Der Bildschirm Einstellungen → Drucker mit seinen drei Reitern](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Schritt 2 — Gib deine Bambu-E-Mail und dein Passwort ein

Die von deinem Bambu-Lab-Konto — genau diese E-Mail, keine andere von dir — und
klick auf **Mit Bambu Lab verbinden**.

![Das Bambu-Cloud-Formular mit ausgefüllter E-Mail und Passwort](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 Dein Passwort wird nicht gespeichert
Es bleibt **nur in deinem Browser**, und auch nur, bis du die Bestätigung
abgeschlossen hast.
:::

## Schritt 3 — Gib den Code aus der E-Mail ein

Bambu schickt dir einen **6-stelligen Code** von `noreply@bambulab.com`. **Sieh
auch im Spam nach**, da landet er öfter, als er sollte.

Gib die sechs Ziffern auf demselben Bildschirm ein und klick auf **Überprüfen und
verbinden**.

![Das Feld für den 6-stelligen Code und der Button Überprüfen und verbinden](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Zwei Details, die dir einen zweiten Versuch ersparen: **Der Code läuft nach etwa
5 Minuten ab** — wenn du länger brauchst, klick auf **Code erneut senden** — und
**füg ihn vollständig ein, so wie er kommt**: Leerzeichen oder Bindestriche werden
automatisch entfernt.

Sobald er angenommen ist, siehst du **Konto verifiziert und verbunden**.

## Schritt 4 — Da sind sie schon

Du musst die Drucker nicht einzeln anlegen. **Alle Maschinen dieses Kontos
erscheinen von selbst** im Reiter **Drucker**, jede mit ihrem Namen und ihrer
Seriennummer.

![Die Druckerliste mit den gerade aufgetauchten Bambu-Maschinen](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

Oben steht ein Zähler wie `3 / 6 aktiv`: die Drucker, die dein Plan umfasst.
Mit dem Schalter in jeder Zeile schaltest du die ein und aus, die du willst. Ein
ausgeschalteter Drucker zählt nicht für das Limit, **bleibt aber mit seinem ganzen
Verlauf in der Liste**.

Und wenn du eine ganze Flotte verbindest und nicht genug Plätze für alle hast,
kommen die übrigen **deaktiviert** herein, statt deinen Plan zu sprengen.

## Was du hier NICHT tun kannst

Besser, du weißt es jetzt, als eine halbe Stunde nach dem Button zu suchen:

- **Es gibt nur Lesezugriff.** Über die Cloud kannst du aus BolloPrint heraus
  nicht pausieren, fortsetzen oder abbrechen: Bambu nimmt diese Befehle nur über
  dein lokales Netzwerk an, und nur mit dem Drucker in einem besonderen Modus.
  Dazu kommen wir am Ende.
- **Es gibt keine Kamera.** Über die Cloud kommt sie nicht an. Was ankommt, ist
  das Slicer-Bild des Druckauftrags, also die Vorschau, nicht das, was gerade im
  Drucker passiert.
- **Es hängt doppelt vom Internet ab:** von deinem und dem von Bambu. Fällt eins
  davon aus, erscheint der Drucker als getrennt, auch wenn er einwandfrei druckt.
- **Die Sitzung läuft ab und zu ab**, und du musst das Konto neu verbinden. Wir
  sagen dir auf dem Bildschirm Bescheid.

Und eins gilt für alle Wege: **BolloPrint schickt keine Druckaufträge**. Die Datei
schickst du weiterhin aus deinem Slicer. Wir lesen aus, was die Maschine tut, und
protokollieren es.

## Wenn die Verbindung nicht klappt

| Was du siehst | Woran es meistens liegt |
|---|---|
| „Falsches Bambu-Lab-Konto oder falsches Passwort“, und du bist sicher, dass es stimmt | **Das ist der Fehler, der am meisten Zeit kostet.** Wenn du das Passwort gerade erst angelegt und noch nie benutzt hast, ist beim Konto die E-Mail-Bestätigung noch offen, und Bambu sagt dir das nicht. Melde dich **einmal** mit diesen Zugangsdaten auf der Bambu-Website an, erledige, was verlangt wird, und komm zurück. |
| „Falsches Bambu-Lab-Konto oder falsches Passwort“, und du meldest dich bei Bambu mit Google oder Apple an | Dieser Weg funktioniert hier nicht. Leg auf der Bambu-Website ein Passwort an. |
| „Es gibt kein Bambu-Lab-Konto mit dieser E-Mail-Adresse“ | Die E-Mail ist nicht die des Bambu-Kontos. Schau nach, mit welcher du dich in der Bambu-App anmeldest. |
| Es ist von Zwei-Faktor-Authentifizierung die Rede | Du musst sie bei Bambu deaktivieren, um das Konto verbinden zu können. |
| Der Code kommt nicht an | Sieh im Spam nach und klick auf **Code erneut senden**. |
| Der Code wird nicht angenommen | Er ist wahrscheinlich abgelaufen. Fordere einen neuen an und füg ihn vollständig ein. |

## Du willst mehr? Probier den lokalen Agenten

Die Cloud zeigt dir alles, lässt dich aber nichts anfassen, und es gibt sie nur
für Bambu Lab. Wenn du mehr willst, ist der **lokale Agent** das Richtige für
dich: ein kleines Programm auf einem Rechner in deiner Werkstatt, das über dein
eigenes Netzwerk mit den Druckern spricht. Einer reicht für die ganze Flotte, und
er bietet dir:

- **fast alle Marken**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron …;
- **Kamera**, live, während du zuschaust, und mit einem Abschlussfoto, das bei
  jedem Druck gespeichert wird;
- **Pausieren, Fortsetzen und Abbrechen** direkt aus BolloPrint, ohne zur
  Maschine zu laufen;
- und er **übersteht Internetausfälle**: Er liest deine Drucker weiter aus und
  erzählt dir alles, sobald das Netz zurück ist.

:::info 💡 Um einem Bambu Befehle zu schicken
Der Drucker muss im **LAN-Modus** und im **Entwicklermodus** sein. Beides schaltest
du an seinem Display ein. Achtung: Im LAN-Modus trennt Bambu ihn von seiner Cloud,
ab dann sieht BolloPrint ihn über den Agenten. Es bleibt **derselbe Drucker**, mit
seinem Namen und seinem ganzen Verlauf, und er belegt **nur einen Platz** in
deinem Plan.
:::

Schritt für Schritt findest du das in der nächsten Anleitung:
[deine Drucker über das lokale Netzwerk verbinden](/blog/connect-printers-local-network-agent).

:::info 💡 Noch Fragen?
Schreib uns über die [Kontaktseite](/contact) oder eröffne einen Thread in
[unserem Discord](/help/soporte-por-discord).
:::

## Verwandte Dokumentation

- [Drucker verbinden](/help/conectar-impresoras) — die zwei Wege und welcher zu dir passt
- [Drucker über die Cloud](/help/impresoras-por-la-nube) — die vollständige Referenz zu diesem Bildschirm
- [Kompatible Drucker](/help/impresoras-compatibles) — such hier dein Modell
- [Verbindungsarten](/help/tipos-de-conexion) — was jede Druckerfamilie kann
