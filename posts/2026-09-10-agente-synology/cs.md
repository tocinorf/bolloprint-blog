---
slug: install-bolloprint-agent-synology
title: Instalace agenta BolloPrint na Synology
description: Pokud už máte v dílně NAS, nemusíte dál hledat, kam agenta dát. Dvacet minut v rozhraní DSM, bez psaní jediného příkazu a bez zásahů do routeru.
date: 2026-09-10
updated: 2026-09-10
tags: [návody]
draft: true
---

Pokud máte v dílně Synology, máte už i místo pro agenta. Běží nepřetržitě, je ve
stejné síti jako tiskárny a kontejnery spouštět umí už roky. Těžko hledat lepší
místo.

A o Dockeru nemusíte vědět vůbec nic: nenapíšete ani jeden příkaz. Všechno se dělá
v rozhraní DSM, vložením textu do okénka. Počítejte asi s dvaceti minutami, z toho
polovina je čekání na stahování.

:::info
Tento text se týká jen **nasazení na Synology**. Co je agent, jaké značky
podporuje a jak přidat jednotlivé tiskárny, najdete v
[návodu k místní síti](/blog/connect-printers-local-network-agent) —
až tady skončíte, pokračujte tam.
:::

![Container Manager v DSM s běžícím projektem agenta](/blog/media/2026-09-10-agente-synology/01-container-manager.png)

## Proč na NAS, a ne na notebooku

Protože agent je k užitku, jen když je vzhůru. Pokud ho dáte na počítač, který při
odchodu vypínáte, tyto hodiny neuvidíte: ani co se tisklo, ani jak dlouho to
trvalo, ani jestli se tisk ve tři ráno zastavil. NAS je zapnutý tak jako tak.

Zbytek dostanete navíc: NAS je v síti tiskáren, a proto je agent dokáže najít sám,
a spotřebuje 10 až 20 MB paměti. Na NAS to nikdo ani nepozná.

:::info 💡 Ne, na router sahat nebudete
Agent se **připojuje ven**, přes port 443, stejně jako když otevíráte webovou
stránku. Nikdy nepřijímá připojení z internetu. Nemusíte tedy otevírat porty,
nastavovat pevnou IP ani bojovat s firewallem — a funguje stejně za domácím
routerem jako na optice s CGNAT.
:::

## Co potřebujete, než se do toho pustíte

Čtyři věci, které je lepší zkontrolovat teď než v polovině:

- **NAS a tiskárny ve stejné síti.** Pokud jsou v různých VLAN, agent funguje
  stejně, ale přijde o automatické vyhledávání: každou tiskárnu bude potřeba
  přidat ručně podle IP.
- **Přístup NAS do internetu přes port 443.** Nic víc.
- **DSM 7.2 nebo novější.** Zjistíte to v **Ovládací panel → Aktualizace
  a obnovení** (*Control Panel → Update & Restore*). S DSM 7.0 nebo 7.1 vám tento
  návod nepomůže: nejdřív DSM aktualizujte.
- **Kód připojení agenta**, který získáte vytvořením agenta v BolloPrint
  v **Nastavení → Tiskárny → Místní agent**.

:::danger ⚠️ Spusťte ho jen na NAS, nezkoušejte ho předtím jinde
**První kontejner, který se s tímto kódem spustí, si instalaci ponechá.** Pokud ho
tedy „na zkoušku“ spustíte na notebooku a potom ho nainstalujete na Synology, NAS
se ohlásí jako neznámá instalace a bude čekat na vaše schválení.

Žádná tragédie to není — schválí se jedním kliknutím —, ale ušetříte si chvíli
typu „a proč to teď nejde?“.
:::

:::warning 🔐 Tento kód je heslo
Dává přístup k údajům o připojení tiskáren v dílně. Nevkládejte ho do skupiny na
WhatsAppu a nenechávejte ho na snímku obrazovky.
:::

## 1. Nainstalujte Container Manager

Je to aplikace Synology, která spouští kontejnery. Instaluje se jako kterákoli
jiná a **uvnitř není co nastavovat**, takže tento krok je rychlý.

Přihlaste se do DSM (`http://IP-NAS:5000`) jako administrátor, otevřete **Centrum
balíčků** (*Package Center*), vyhledejte **Container Manager** a klikněte na
instalaci. Minuta nebo dvě. Pak ho otevřete a počkejte, až se spustí: jakmile
karta **Přehled** (*Overview*) místo upozornění ukáže data, je hotovo.

![Centrum balíčků DSM s aplikací Container Manager](/blog/media/2026-09-10-agente-synology/02-centro-paquetes.png)

Všimnete si, že DSM samo vytvoří sdílenou složku `docker`. To je normální,
nechte ji být.

:::warning ⚠️ Pokud se Container Manager nezobrazuje
Znamená to, že tento model NAS kontejnery nepodporuje. Softwarově se s tím nedá
nic dělat: nainstalujte agenta na jiný stroj ve stejné síti — mini-PC, Raspberry
Pi, cokoli, co je stále zapnuté.
:::

## 2. Vytvořte projekt

V Container Manageru je **projekt** v podstatě sepsaný recept: vložíte text a NAS
se postará o stažení a spuštění toho, co v něm je. Není potřeba vytvářet složky
ani kopírovat soubory.

Přejděte do **Projekt → Vytvořit** (*Project → Create*).

![Container Manager, karta Projekt, tlačítko Vytvořit](/blog/media/2026-09-10-agente-synology/03-crear-proyecto.png)

Jako název zadejte `bolloprint-agent`, malými písmeny — DSM tam velká písmena ani
mezery nepřijme. U cesty klikněte na **Nastavit cestu** (*Set Path*), otevřete
složku `docker`, vytvořte v ní složku `bolloprint-agent` a vyberte ji.

:::info 💡 Ukládá se tam jen recept, ne vaše data
V této složce je uložený **jen text souboru `docker-compose.yml`**. To, co si agent
potřebuje pamatovat, je v interním svazku Dockeru, který se vytvoří sám a který se
v File Station ani nezobrazuje. Tak je to lepší: není tam nic, na co sahat, ani nic,
co omylem smazat.
:::

V části **Zdroj** (*Source*) zvolte vytvoření souboru `docker-compose.yml`.
Zobrazí se prázdné okénko a do něj patří blok.

:::danger ⚠️ Zkopírujte blok ze své obrazovky, ne odsud
Najdete ho v BolloPrint, v **Nastavení → Tiskárny → Místní agent → Jak ho
nasadit**, na kartě **Docker Compose**, s tlačítkem pro kopírování. V tom je verze
agenta, která je v danou chvíli správná; ten níže je jen pro představu, jak to
vypadá.

**A v žádném případě nepište `latest`.** Tento štítek v registru neexistuje —
ověřili jsme to dnes: vrací 404 —, takže projekt by uvízl na `manifest unknown`
a vůbec by se nespustil. Nejde o ničí přehlédnutí, ale o záměr: pohyblivý štítek
by umožnil, aby aktualizace vyměnila agenta pod běžící flotilou, aniž by o tom
dílna rozhodla.
:::

```yaml
services:
  bolloprint-agent:
    image: ghcr.io/bolloprint/bolloprint-agent:0.4.8   # ← ta, kterou ukazuje vaše obrazovka
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
      BP_AGENT_CODE: SEM_VLOZTE_SVUJ_KOD
      # BP_STATUS_PORT: 9911
      # BP_LOG_LEVEL: debug
    volumes:
      - identity:/var/lib/bolloprint

volumes:
  identity:
    name: bolloprint_agent_identity
```

Nahraďte `SEM_VLOZTE_SVUJ_KOD` svým kódem, celým a bez zbloudilých mezer na
začátku nebo na konci — je to ta nejhloupější chyba a stává se nejčastěji.

![Editor souboru docker-compose.yml v Container Manageru](/blog/media/2026-09-10-agente-synology/04-compose.png)

Čtyři věci o tomto textu, které je dobré znát:

- **Vložte ho, nepřepisujte ho.** Mezery na začátku každého řádku jsou součástí
  formátu, a pokud se tam vloudí tabulátor, DSM ho odmítne.
- **`network_mode: host`** zajišťuje, že agent vidí síť NAS a najde tiskárny sám.
  Bez toho je budete přidávat všechny ručně.
- **Svazek `identity`** je paměť agenta. Díky němu po vás agent nechce schválení
  při každém restartu.
- **Řádky s `#` jsou záměrně vypnuté.** Zapínají se, jen když je potřeba něco
  diagnostikovat.

V dalším kroku vám DSM nabídne zveřejnění „webového portálu“. Zvolte **Žádný**
(*None*): agent nemá žádnou stránku, kterou by ukazoval.

A je to. DSM stáhne obraz a spustí kontejner, přičemž vám ukazuje protokol
v reálném čase. Pár minut podle vašeho připojení. Pokud projekt po dokončení
zůstane zastavený, vyberte ho a zvolte **Akce → Spustit** (*Action → Start*).

## 3. Ověřte, že běží

Signály jsou tři, ale **opravdu se počítá ten třetí**. První dva vám říkají jen to,
že se kontejner spustil, ne že s někým komunikuje.

**Kontejner běží.** V části **Kontejner** (*Container*) by měl být
`bolloprint_agent` ve stavu **Spuštěno** (*Running*) a spotřebovávat několik
desítek MB.

![Seznam kontejnerů se spuštěným bolloprint_agent](/blog/media/2026-09-10-agente-synology/05-contenedor.png)

**Protokol říká, co má.** Dvakrát klikněte na kontejner, otevřete kartu
**Protokol** (*Log*) a během prvních sekund by se mělo zobrazit tohle:

```
INFO bolloprint-agent starting version=0.4.8
INFO installation fingerprint source=stored ...
INFO bootstrapped agent_id=... printers=0
INFO broker connected
```

Každý řádek potvrzuje něco jiného, a proto stojí za to se na ně podívat:

| Řádek | Co vám říká |
|---|---|
| `source=stored` | Svazek identity je připojený a lze do něj zapisovat. Pokud je tu něco jiného, připravte se, že agenta budete schvalovat při každém novém vytvoření kontejneru. |
| `bootstrapped` | Kód je v pořádku a BolloPrint ho rozpoznal. |
| `broker connected` | Trvalé spojení je otevřené. Od této chvíle agent už hlásí stav. |

![Karta Protokol se spouštěcími řádky](/blog/media/2026-09-10-agente-synology/06-registro.png)

**A agent v BolloPrint zezelená.** V **Nastavení → Tiskárny → Místní agent** by
měla karta asi do třiceti sekund přejít do stavu **Online**. To je ten
rozhodující signál: znamená, že funguje celý řetězec.

![Karta agenta ve stavu Online v BolloPrint](/blog/media/2026-09-10-agente-synology/07-agente-online.png)

## Když něco nejde

| Co vidíte | Co to obvykle znamená |
|---|---|
| `manifest unknown` při stahování | Tato verze obrazu neexistuje. Zkopírujte znovu blok ze své obrazovky — a zkontrolujte, že v něm není `latest`. |
| Spustí se a sám se zastaví | Podívejte se do protokolu. Téměř vždy jde o špatně vložený kód se zbloudilou mezerou před ním nebo za ním. |
| `bootstrapped` se nikdy neobjeví | NAS se nedostane do internetu přes port 443, nebo odchozí provoz pohlcuje firewall. |
| Při každém restartu chce schválení | Chybí svazek identity. Zkontrolujte, že je vložená celá sekce `volumes`. |
| Zobrazuje se jako instalace čekající na schválení | Tento kód už byl použitý na jiném stroji. Pokud zařízení znáte, schvalte ho — jen počítejte s tím, že schválením nového přijde to předchozí o přístup. |
| Nenajde žádnou tiskárnu | Jsou NAS a tiskárny ve stejné síti? Pokud ne, je to očekávané: přidejte je podle IP a fungují stejně dobře. |

## Co zbývá

Se zeleným agentem máte půlku práce za sebou. Zbývá mu předat tiskárny: ty, které
se objeví samy, ty, které je potřeba zadat podle IP, a to, co vyžaduje každá
značka — to vše je v [návodu k místní síti](/blog/connect-printers-local-network-agent).

Od té chvíle na něj můžete zapomenout. Kontejner se sám vrátí po každém restartu
NAS a nevyžaduje údržbu. Jediné, co občas uděláte, je aktualizace: když vás
BolloPrint upozorní na novou verzi, znovu zkopírujete blok z obrazovky a projekt
restartujete.

## Další čtení

- [Místní agent](/help/el-agente-local) — instalace, identita, více agentů a diagnostika
- [Tiskárny v místní síti](/help/impresoras-por-red-local) — přidání strojů
- [Typy připojení](/help/tipos-de-conexion) — co umožňuje která rodina tiskáren
- [Kompatibilní tiskárny](/help/impresoras-compatibles) — tady najdete svůj model
- [Připojení tiskáren](/help/conectar-impresoras) — dvě cesty a která se vám hodí
