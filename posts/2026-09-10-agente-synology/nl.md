---
slug: install-bolloprint-agent-synology
title: De BolloPrint-agent installeren op een Synology
description: Heb je al een NAS in de werkplaats, dan hoef je niet verder te zoeken naar een plek voor de agent. Twintig minuten via de interface van DSM, zonder één commando te typen en zonder aan je router te komen.
date: 2026-09-10
updated: 2026-09-10
tags: [handleidingen]
draft: true
---

Heb je een Synology in de werkplaats, dan heb je al een plek voor de agent. Hij
staat vierentwintig uur per dag aan, zit op hetzelfde netwerk als de printers en
kan al jaren containers draaien. Een betere plek vind je moeilijk.

En je hoeft niets van Docker te weten: je typt geen enkel commando. Alles gaat via
de interface van DSM, door een tekst in een vak te plakken. Reken op twintig
minuten, en de helft daarvan is wachten tot het downloaden klaar is.

:::info
Dit gaat alleen over de **installatie op een Synology**. Wat de agent is, welke
merken hij ondersteunt en hoe je elke printer toevoegt, staat in de
[handleiding voor het lokale netwerk](/blog/connect-printers-local-network-agent) —
ga daar verder als je hier klaar bent.
:::

![Container Manager in DSM met het project van de agent actief](/blog/media/2026-09-10-agente-synology/01-container-manager.png)

## Waarom op de NAS en niet op je laptop

Omdat de agent alleen iets doet als hij wakker is. Zet je hem op de computer die
je uitzet als je weggaat, dan zie je die uren niet: niet wat er geprint is, niet
hoelang het duurde en niet of een printer om drie uur 's nachts is gestopt. De NAS
staat toch al aan.

De rest krijg je er gratis bij: hij zit op het netwerk van de printers, waardoor
hij ze zelf kan vinden, en hij gebruikt tussen de 10 en 20 MB geheugen. Op een NAS
merkt niemand dat.

:::info 💡 Nee, je hoeft niet aan je router te komen
De agent **belt naar buiten**, via poort 443, net als wanneer je een webpagina
opent. Hij ontvangt nooit verbindingen vanaf internet. Dus geen poorten
openzetten, geen vast IP-adres en geen gedoe met de firewall — en het werkt net zo
goed achter een thuisrouter als achter een glasvezelverbinding met CGNAT.
:::

## Wat je nodig hebt voordat je begint

Vier dingen, en die kun je beter nu controleren dan halverwege:

- **De NAS en de printers zitten op hetzelfde netwerk.** Zitten ze in
  verschillende VLAN's, dan werkt de agent net zo goed, maar valt het
  automatisch zoeken weg: dan moet je elke printer met de hand via zijn IP-adres
  toevoegen.
- **De NAS kan via poort 443 het internet op.** Meer niet.
- **DSM 7.2 of hoger.** Dat zie je in **Configuratiescherm → Bijwerken en
  herstellen** (*Control Panel → Update & Restore*). Met 7.0 of 7.1 heb je hier
  niets aan: werk DSM eerst bij.
- **De verbindingscode van de agent**, die je krijgt door de agent aan te maken in
  BolloPrint via **Instellingen → Printers → Lokale agent**.

:::danger ⚠️ Start hem alleen op de NAS, probeer hem niet eerst ergens anders
**De eerste container die met die code start, neemt de installatie in bezit.**
Start je hem dus op je laptop “om te kijken of het werkt” en zet je hem daarna op
de Synology, dan meldt de NAS zich als een onbekende installatie en wacht hij tot
je hem goedkeurt.

Een drama is het niet — goedkeuren is één klik — maar zo bespaar je jezelf het
moment van “en waarom werkt het nu niet?”.
:::

:::warning 🔐 Die code is een wachtwoord
Hij geeft toegang tot de verbindingsgegevens van de printers in de werkplaats.
Plak hem niet in een WhatsApp-groep en laat hem niet op een screenshot staan.
:::

## 1. Container Manager installeren

Dat is de app van Synology die containers draait. Je installeert hem zoals elke
andere app en **binnenin valt er niets in te stellen**, dus deze stap gaat snel.

Log in op DSM (`http://IP-VAN-DE-NAS:5000`) met je beheerdersaccount, open het
**Pakketcentrum** (*Package Center*), zoek **Container Manager** en klik op
installeren. Een minuut of twee. Open hem daarna en wacht tot hij is opgestart:
zodra het tabblad **Overzicht** (*Overview*) gegevens laat zien in plaats van een
melding, is hij klaar.

![Het Pakketcentrum van DSM met Container Manager](/blog/media/2026-09-10-agente-synology/02-centro-paquetes.png)

Je ziet dat DSM zelf een gedeelde map met de naam `docker` aanmaakt. Dat is
normaal, laat die gewoon met rust.

:::warning ⚠️ Als je Container Manager niet ziet
Dan ondersteunt dat NAS-model geen containers. Daar is met software niets aan te
doen: zet de agent op een andere machine in hetzelfde netwerk — een mini-pc, een
Raspberry Pi, alles wat altijd aanstaat.
:::

## 2. Het project aanmaken

In Container Manager is een **project** eigenlijk een uitgeschreven recept: je
plakt een tekst en de NAS zorgt ervoor dat wat erin staat wordt gedownload en
gestart. Je hoeft geen mappen te maken of bestanden te kopiëren.

Ga naar **Project → Maken** (*Project → Create*).

![Container Manager, tabblad Project, knop Maken](/blog/media/2026-09-10-agente-synology/03-crear-proyecto.png)

Als naam `bolloprint-agent`, in kleine letters — DSM accepteert daar geen
hoofdletters of spaties. Klik voor het pad op **Pad instellen** (*Set Path*), ga
naar de map `docker`, maak daarin een map met de naam `bolloprint-agent` en
selecteer die.

:::info 💡 Daar komt alleen het recept, niet je gegevens
In die map wordt **alleen de tekst van de `docker-compose.yml`** opgeslagen. Wat
de agent moet onthouden, staat in een intern Docker-volume dat vanzelf wordt
aangemaakt en dat niet eens in File Station verschijnt. Zo is het beter: niets om
aan te komen en niets wat je per ongeluk kunt verwijderen.
:::

Kies bij **Bron** (*Source*) voor het aanmaken van een `docker-compose.yml`. Je
krijgt een leeg vak te zien, en daar komt het blok in.

:::danger ⚠️ Kopieer het blok van je eigen scherm, niet dat van hier
Je vindt het in BolloPrint, in **Instellingen → Printers → Lokale agent → Hoe
installeren**, tabblad **Docker Compose**, met de knop om te kopiëren. Daarin
staat de agentversie die op dat moment de juiste is; het blok hieronder is alleen
om je te laten zien hoe het eruitziet.

**En zet er vooral niet `latest` in.** Die tag bestaat niet in het register — we
hebben het vandaag gecontroleerd: het geeft een 404 — dus het project zou blijven
hangen op `manifest unknown` zonder ooit te starten. Dat is geen vergissing van
iemand: het is bewust zo, want een tag die meeschuift zou een update de agent
laten vervangen onder een vloot die draait, zonder dat de werkplaats daarover
beslist.
:::

```yaml
services:
  bolloprint-agent:
    image: ghcr.io/bolloprint/bolloprint-agent:0.4.8   # ← die op je scherm staat
    container_name: bolloprint_agent
    restart: unless-stopped
    network_mode: host
    mem_limit: 512m
    pids_limit: 512
    ulimits:
      nofile:
        soft: 65536
        hard: 65536
    environment:
      BP_AGENT_CODE: PLAK_HIER_JE_CODE
      # BP_STATUS_PORT: 9911
      # BP_LOG_LEVEL: debug
    volumes:
      - identity:/var/lib/bolloprint

volumes:
  identity:
    name: bolloprint_agent_identity
```

Vervang `PLAK_HIER_JE_CODE` door je eigen code, helemaal en zonder losse spaties
ervoor of erachter — het is de domste fout en de fout die het vaakst gebeurt.

![De editor van de docker-compose.yml in Container Manager](/blog/media/2026-09-10-agente-synology/04-compose.png)

Vier dingen in die tekst die je goed kunt weten:

- **Plak hem, typ hem niet over.** De spaties aan het begin van elke regel horen
  bij het formaat, en als er een tab tussen glipt, weigert DSM hem.
- **`network_mode: host`** zorgt ervoor dat de agent het netwerk van de NAS ziet
  en zelf printers vindt. Zonder dat moet alles met de hand.
- **Het volume `identity`** is het geheugen van de agent. Daardoor vraagt hij niet
  bij elke herstart om goedkeuring.
- **De regels met `#` staan expres uit.** Die zet je alleen aan als er iets
  gediagnosticeerd moet worden.

Als je verdergaat, biedt DSM aan een “webportal” te publiceren. Kies **Geen**
(*None*): de agent heeft geen pagina om te laten zien.

En dat is het. DSM downloadt de image en start de container, terwijl je een live
logboek ziet. Een paar minuten, afhankelijk van je verbinding. Blijft het project
na afloop gestopt, selecteer het dan en kies **Actie → Starten** (*Action →
Start*).

## 3. Controleren of hij werkt

Er zijn drie signalen, maar **het derde is het enige dat echt telt**. De eerste
twee zeggen alleen dat de container is gestart, niet dat hij met iemand praat.

**De container draait.** Onder **Container** (*Container*) moet
`bolloprint_agent` als **Actief** (*Running*) staan, met een paar tientallen MB
geheugengebruik.

![De lijst met containers met bolloprint_agent actief](/blog/media/2026-09-10-agente-synology/05-contenedor.png)

**Het logboek zegt wat het moet zeggen.** Dubbelklik op de container, tabblad
**Logboek** (*Log*), en in de eerste seconden zou je dit moeten zien:

```
INFO bolloprint-agent starting version=0.4.8
INFO installation fingerprint source=stored ...
INFO bootstrapped agent_id=... printers=0
INFO broker connected
```

Elke regel bevestigt iets anders, en daarom loont het om ze te bekijken:

| Regel | Wat hij je vertelt |
|---|---|
| `source=stored` | Het identiteitsvolume is gekoppeld en er kan in geschreven worden. Staat er iets anders, reken er dan op dat je de agent moet goedkeuren elke keer dat de container opnieuw wordt aangemaakt. |
| `bootstrapped` | De code is goed en BolloPrint heeft hem herkend. |
| `broker connected` | De vaste verbinding is open. Vanaf hier rapporteert de agent. |

![Het tabblad Logboek met de opstartregels](/blog/media/2026-09-10-agente-synology/06-registro.png)

**En de agent wordt groen in BolloPrint.** In **Instellingen → Printers → Lokale
agent** moet de kaart binnen zo'n dertig seconden op **Online** springen. Dat is
het echte signaal: het betekent dat de hele keten werkt.

![De kaart van de agent op Online in BolloPrint](/blog/media/2026-09-10-agente-synology/07-agente-online.png)

## Als iets niet lukt

| Wat je ziet | Wat het meestal is |
|---|---|
| `manifest unknown` bij het downloaden | Die versie van de image bestaat niet. Kopieer het blok opnieuw van je scherm — en kijk of je niet `latest` hebt ingevuld. |
| Hij start en stopt vanzelf | Kijk in het logboek. Bijna altijd is de code verkeerd geplakt, met een spatie ervoor of erachter. |
| `bootstrapped` verschijnt nooit | De NAS komt niet via poort 443 op internet, of een firewall houdt het uitgaande verkeer tegen. |
| Hij vraagt bij elke herstart om goedkeuring | Het identiteitsvolume ontbreekt. Controleer of je de hele sectie `volumes` hebt geplakt. |
| Hij verschijnt als installatie die op goedkeuring wacht | Die code is al op een andere machine gebruikt. Herken je het apparaat, keur het dan goed — maar let op: als je er een goedkeurt, verliest de vorige zijn toegang. |
| Hij vindt geen enkele printer | Zitten de NAS en de printers op hetzelfde netwerk? Zo niet, dan is dat te verwachten: voeg ze toe via IP en ze werken net zo goed. |

## Wat er nog overblijft

Met de agent op groen ben je halverwege. Nu moet je hem de printers nog geven: de
printers die vanzelf verschijnen, de printers die je via IP moet toevoegen en wat
elk merk vraagt, staat allemaal in de
[handleiding voor het lokale netwerk](/blog/connect-printers-local-network-agent).

Daarna kun je hem vergeten. De container komt na elke herstart van de NAS vanzelf
terug en heeft geen onderhoud nodig. Het enige wat je af en toe doet, is hem
bijwerken: als BolloPrint je laat weten dat er een nieuwe versie is, kopieer je
het blok opnieuw van het scherm en start je het project opnieuw.

## Verder lezen

- [De lokale agent](/help/el-agente-local) — installatie, identiteit, meerdere agents en diagnose
- [Printers op het lokale netwerk](/help/impresoras-por-red-local) — machines toevoegen
- [Verbindingstypen](/help/tipos-de-conexion) — wat elke printerfamilie mogelijk maakt
- [Compatibele printers](/help/impresoras-compatibles) — zoek hier je model
- [Printers verbinden](/help/conectar-impresoras) — de twee routes en welke bij je past
