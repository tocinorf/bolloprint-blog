---
slug: connect-printers-local-network-agent
title: "Verbind je printers via je eigen netwerk: de lokale agent, stap voor stap"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper… Een kleine agent op een computer in je werkplaats, je hele vloot in BolloPrint en niets aan je router veranderen.
date: 2026-10-12
updated: 2026-10-16
tags: [handleidingen]
cover: 01-portada.webp
---

Je printers staan in de werkplaats, maar jij niet altijd. En om te weten of er
een nog print, of het goed is gegaan of dat er nog materiaal in zit, moet je
ervoor staan.

Daarvoor is er de **lokale agent**: een klein programma dat op een computer in je
werkplaats draait, via je eigen netwerk met je printers praat en BolloPrint
vertelt wat hij ziet.

- **Je verandert niets aan je router**: geen open poorten, geen vast IP-adres,
  geen firewall.
- **Hij is heel licht**: elke computer die toch al aanstaat, is genoeg.
- **Eén is genoeg voor je hele vloot**, hoe groot die ook is.
- **Hij werkt zichzelf bij**: als er een nieuwe versie uitkomt, installeert hij
  die zelf.

::animation{id="local-agent"}

## Waar je hem installeert

De agent draait op **elke computer in de werkplaats die je niet uitzet**: een
NAS, een mini-pc, een Raspberry Pi of de pc van de werkplaats. Hij moet alleen
**altijd aanstaan** en **Docker** hebben.

Het mooist is het als hij **op hetzelfde netwerk zit als de printers**, want dan
vindt hij ze zelf. Lukt dat niet, dan voeg je ze met de hand toe en werken ze
precies zo.

## Maak de agent aan in BolloPrint

Je begint in BolloPrint. Ga naar **Instellingen → Printers**. Je ziet drie
tabbladen: **Printers** (al je machines, hoe ze ook binnenkomen), **Lokale agent**
en **Bambu Cloud**. Open **Lokale agent** en klik op **Nieuwe agent**.

Geef hem een naam die je over zes maanden nog iets zegt: **noem hem naar waar hij
staat, niet naar wat hij is**. “Begane grond” of “Hal 2” zijn prima; “Agent 1”
niet. Klik daarna op **Agent aanmaken**.

![Het tabblad Lokale agent, met twee agents online en de knop Nieuwe agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-en.png)

## Kopieer het sjabloon

Bij het aanmaken laat BolloPrint je een **sjabloon** zien: een tekst waarin alles
van jou al **is ingevuld**, de sleutels van je agent en de juiste versie. Er hoeft
niets vervangen of ingevuld te worden.

Kies het formaat dat je gebruikt (**Docker Compose** is het gebruikelijke), klik op
**Kopiëren** en, als je het veilig hebt opgeslagen, op **Opslaan**.

![Het installatiesjabloon van de nieuwe agent, met de knop Kopiëren](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-en.png "75%")

:::warning 🔐 Kopieer het nu: de sleutels worden maar één keer getoond
We bewaren ze niet, dus we kunnen ze je niet nog een keer laten zien. Ben je het
sjabloon kwijt, geen probleem: open de agent met **Bewerken** (in zijn menu
**⋮**), ga naar het tabblad **Installatie** en klik op **Sleutels opnieuw
genereren**. Als hij nog nooit verbonden is geweest, wordt er niets onderbroken.
:::

## Plak het sjabloon op je computer

Dit doe je op je computer, niet in BolloPrint, en het hangt af van waar je hem
installeert:

- **Synology-NAS**: installeer **Container Manager** via het **Pakketcentrum**,
  ga naar **Project → Maken**, plak het sjabloon en maak het project aan. Zonder
  één commando te typen.
- **Windows of Mac**: installeer **Docker Desktop**, sla het sjabloon in een map
  op als `docker-compose.yml` en voer in die map
  `docker compose up -d` uit.
- **Linux**: installeer **Docker** met de pakketbeheerder van je distributie,
  sla het sjabloon op als `docker-compose.yml` en voer daar
  `docker compose up -d` uit.
- **Portainer**: plak hetzelfde sjabloon in een stack en implementeer die.

:::info 💡 Op Windows en Mac worden printers niet vanzelf gevonden
Daar draait Docker in een virtuele machine, die de signalen niet ziet die de
printers op je netwerk uitsturen. De agent werkt net zo goed, maar de printers
voeg je zelf toe, zoals hieronder staat uitgelegd.
:::

## Kom je er niet uit, klik dan op “Installeren”

Zolang de agent nog nooit verbinding heeft gemaakt, staat er in zijn rij **Niet
geïnstalleerd**. Dat is geen fout: er is niets uitgevallen, hij moet alleen nog
geïnstalleerd worden.

In diezelfde rij staat de knop **Installeren**. Als je erop klikt, klappen de
stappen open die je net hebt gelezen, in het kort, met een link naar de
**Hulp**, een naar dit **Blogartikel** en een knop om het ons op **Discord** te
vragen. Heb je het sjabloon niet bewaard, dan brengt stap 3 je meteen naar het
maken van een nieuw sjabloon.

![Een niet-geïnstalleerde agent met het paneel Installeren open: de drie stappen, de hulp en Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-en.png)

## Controleer of hij online is

Ga terug naar BolloPrint: binnen een minuut springt de agent op **Online**, met
de naam van de computer waarop hij draait en de versie die hij heeft.

![De agent met de status Online](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-en.png)

Gebeurt dat niet, dan is het bijna altijd een van deze drie oorzaken: het
sjabloon is **maar half geplakt**, de computer **heeft geen internet** of een
**firewall** blokkeert het uitgaande verkeer. Wil je zien wat de agent zelf
meldt, open hem dan met **Bewerken**: het tabblad **Status** geeft alle details.

## Je printers verschijnen vanzelf

Vanaf dat moment **zoekt de agent elke 15 minuten zelf naar printers op je
netwerk**. Vindt hij er een, dan meldt hij dat boven de tabbladen en zie je hem
onderaan bij **Printers op het lokale netwerk**, met merk en model. Jij beslist:

- **Toevoegen**: je zet hem erbij en hij begint te rapporteren.
- **Negeren**: hij is niet van jou of je wilt hem hier niet.

![Een door de agent gevonden printer, met de knoppen Negeren en Toevoegen, en daarboven Nu zoeken en Toevoegen via IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-en.png)

Heb je net een machine aangezet en wil je niet wachten, klik dan op **Nu
zoeken**. Als een printer om een code gaat vragen, staat dat al in de rij
(“vraagt om de toegangscode”), zodat je hem bij de hand hebt.

## Verschijnt er een niet, voeg hem dan zelf toe

Dat een printer niet vanzelf verschijnt, is in twee gevallen **normaal**:

- **Hij zit op een ander netwerk.** De signalen van printers gaan niet van het
  ene netwerk naar het andere.
- **De agent draait op Windows of Mac.** Daar draait Docker in een virtuele
  machine.

Je verliest er niets door: je voegt hem zelf toe en hij werkt precies hetzelfde,
met camera en bediening als die machine dat heeft. Klik op **Toevoegen via IP**.
Het zijn drie stappen.

### 1. Kies het merk

Kies het merk van je printer: elk merk heeft zijn eigen kaart, en de merken met
een logo staan vooraan. Je hoeft niet te weten hoe je machine communiceert; daar
zorgen wij voor. Kies je **Elegoo**, dan vragen we **Welke Elegoo heb je?**,
want dat merk heeft meerdere families. **Klipper** en **Andere harsprinter
(ChituBox)** staan helemaal aan het eind, onder **Generiek**, voor een eigen bouw
of een merk dat niet in de lijst staat.

Twijfel je of je model werkt, dan staat onderaan **Twijfel je? Bekijk de lijst met
compatibele printers**; en staat je printer er niet bij, laat het ons dan weten op
Discord.

![De eerste stap van Printer toevoegen via IP: de merken die je kunt verbinden](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-en.png)

### 2. Vul de gegevens in

Alleen wat echt nodig is:

- **Welke agent verbindt hem?**, als je er meer dan één hebt. Je kunt alleen een
  agent kiezen die online is.
- **IP van de printer**. Die zie je op het scherm van de printer (Instellingen →
  Netwerk) of in je router.
- **De code van de printer**, als dat merk erom vraagt. Het veld heet zoals de
  fabrikant het noemt: bij een Bambu **LAN-toegangscode**.
- **Naam**, als je hem een eigen naam wilt geven. Dat is optioneel.

**Model en serienummer vul je niet in**: die vraagt de agent aan de printer. De
verplichte velden hebben een **rood sterretje** en worden rood gemarkeerd zolang
ze leeg zijn. Onderaan vertelt het vak **Let op** je wat je bij dat merk moet
voorbereiden voordat je verbindt.

![De tweede stap: de agent, het IP-adres, de verplichte LAN-toegangscode en het vak Let op](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-en.png)

### 3. Verbind

Klik op **Verbinden** en je ziet hoe het vordert: de agent krijgt het verzoek,
zoekt de printer op dat adres en maakt verbinding. Als het klaar is, zie je
**“Verbonden. Hij staat nu in je printerlijst.”**

![De derde stap: de printer verbonden en al in de lijst](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-en.png)

Gaat er iets mis, dan zeggen we je dat **in gewone woorden**: wat er aan de hand
is en wat je moet controleren (dat er niets reageert op dat IP-adres, dat de
printer de code weigert…). Met **Terug** pas je het gegeven aan en probeer je het
opnieuw. Het oorspronkelijke bericht van de printer zit ingeklapt onder
**Technische details tonen**: als je ons schrijft, kopieer dat dan voor ons, dan
zien we het sneller.

:::info 💡 Reserveer het IP-adres in je router
Als de router het adres van een printer verandert, zoeken we hem vanzelf
opnieuw, maar een tijdje is hij offline. Door het adres te reserveren voorkom je
dat gat. Dat is een instelling van je router, niet van BolloPrint.
:::

## Wat elk merk van je vraagt

Hier ontstaan de meeste vragen. Het is hetzelfde wat stap 2 je in het kort
laat zien:

| Merk | Wat je op de machine moet doen | Camera | Kun je pauzeren en annuleren? |
|---|---|---|---|
| **Bambu Lab** | De **LAN-modus** aanzetten op het scherm (Instellingen → Netwerk) en de **LAN-toegangscode** gebruiken die je daar ziet | Ja | Ja, als je ook de **Ontwikkelaarsmodus** aanzet |
| **Prusa** (bèta: MK4, MK3.5, MK3.9, MINI, XL, CORE One) | **PrusaLink** aanzetten en het **wachtwoord** gebruiken dat hij toont (niet dat van Prusa Connect) | Nee | Ja |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) en **andere harsprinters (ChituBox)** | Niets, ze vragen geen wachtwoord | Bij de modellen die er een hebben | Ja |
| **Elegoo Centauri Carbon 2** | Niets; alleen als je op het scherm een code hebt ingesteld, vul je die in | Ja | Nee |
| **Anycubic** (bèta: Kobra 3, Kobra S1, Kobra 4, Kobra X) | De **LAN-modus** aanzetten (Instellingen → Netwerk). Daarmee gebruikt de printer de cloud en de app van Anycubic niet meer | Nee | Nee |
| **FlashForge** (bèta: Adventurer 5M, 5M Pro, AD5X, Creator 5) | **LAN Only** aanzetten en de verificatiecode uit het netwerkmenu gebruiken | Ja | Nee |
| **Snapmaker** (U1) | Niets | Ja | Ja |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Meestal niets: alleen als je een API-sleutel in Moonraker hebt ingesteld | Ja, als je Klipper een webcam heeft | Ja |

:::warning ⚠️ Bambu Lab: de toegangscode verandert
Elke keer dat je de LAN-modus of de Ontwikkelaarsmodus aan- of uitzet, **maakt
Bambu een nieuwe code aan**. Als een Bambu die goed werkte opeens geen verbinding
meer maakt, is dat negen van de tien keer de reden: kijk opnieuw naar de code op
het scherm en werk hem bij in BolloPrint. En houd er rekening mee dat de
**Ontwikkelaarsmodus** de printer loskoppelt van Bambu Cloud: vanaf dat moment
zie je hem alleen nog via de agent.
:::

:::info 💡 Staat je model niet in de tabel?
Bekijk de [compatibele printers](/help/impresoras-compatibles). Draait er
**Klipper** op (elke zelfgebouwde of aangepaste machine), dan is hij compatibel,
ook al staat het merk in geen enkele lijst.
:::

## Wat de lokale agent je oplevert

Met de agent aan de slag krijg je:

- **Bijna alle merken**: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge,
  Snapmaker en alles waar Klipper op draait. De cloud biedt dat niet, want die
  bestaat alleen voor Bambu Lab.
- **Camera**: live zolang je de pagina open hebt, een foto wanneer je wilt en een
  eindfoto die in de geschiedenis van elke print wordt bewaard. Het is geen
  camerabewaking: er wordt niets opgenomen.
- **Bediening**: pauzeren, hervatten en annuleren vanuit BolloPrint, zonder naar
  de machine te lopen, bij de printers die het toestaan (zie de tabel hierboven).
  Bij Bambu Lab met de printer in **LAN-modus** en **Ontwikkelaarsmodus**.
- **Bestand tegen internetstoringen**: valt je verbinding weg, dan **blijft de
  agent de printers uitlezen en houdt hij bij wat er gebeurt**. Zodra de
  verbinding terug is, stuurt hij alles door en mis je die uren geschiedenis
  niet.
- **Onafhankelijkheid van de fabrikant** en van de vraag of zijn cloud blijft
  werken.

Wat via geen enkele route kan, is **printopdrachten versturen**: het bestand stuur
je nog steeds vanuit je slicer.

## Veelgestelde vragen

De vragen die we het vaakst krijgen.

### Moet ik poorten openzetten in mijn router?

Nee. Geen poorten, geen vast IP-adres en geen firewallregels. Het werkt achter een
gewone thuisrouter.

### Heb ik per printer een agent nodig?

Nee. **Eén agent regelt je hele vloot.** Meerdere agents zijn alleen zinvol als je
twee locaties of twee gescheiden netwerken hebt. In dat geval vraagt **Toevoegen
via IP** je welke agent de printer verbindt.

### Wat gebeurt er als ik de computer uitzet of als er een nieuwe versie uitkomt?

Als je hem weer aanzet, komt de agent vanzelf terug. Hij werkt zichzelf ook bij:
als er een nieuwe versie uitkomt, downloadt hij die en start hij ermee opnieuw,
zonder dat je aan het sjabloon hoeft te komen. Je hoeft alleen iets te doen als
we je dat op het scherm laten weten.

### Waarom kan ik niet op “Toevoegen via IP” klikken?

Omdat geen van je agents verbonden is, en dat staat ook onder de knop. Heb je hem
nog niet geïnstalleerd, gebruik dan **Installeren** in zijn rij; werkte hij al,
controleer dan of de computer aanstaat en internet heeft.

:::info 💡 Hulp nodig?
Schrijf ons via de [contactpagina](/contact) of open een draad op
[onze Discord](/help/soporte-por-discord). Als je ons vertelt welke printers je
hebt, zeggen we je precies wat je met elk ervan moet doen.
:::

Veel plezier met je hele vloot in beeld, waar je ook bent.

![Bollo, de mascotte van BolloPrint, met een werkplaatsbril, voor een 3D-printfarm aan het werk](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Gerelateerde documentatie

- [Printers verbinden](/help/conectar-impresoras): de twee routes en welke bij je past
- [De lokale agent](/help/el-agente-local): de volledige naslag
- [De agent installeren](/help/desplegar-el-agente): de technische details, als je ze nodig hebt
- [Verbindingstypen](/help/tipos-de-conexion): wat elke printerfamilie mogelijk maakt
- [Compatibele printers](/help/impresoras-compatibles): zoek hier je model
