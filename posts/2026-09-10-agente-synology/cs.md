---
slug: install-bolloprint-agent-synology
title: Instalace agenta BolloPrint na NAS Synology
description: Pokud máte v dílně Synology, právě tam agent patří. Nativní balíček DSM, který nainstalujete z Centra balíčků a propojíte jedním kliknutím. Bez Dockeru, bez kopírování kódu a bez zásahů do routeru.
date: 2026-11-02
updated: 2026-11-02
tags: [návody]
draft: true
---

Pokud máte v dílně Synology, máte už i správné místo pro agenta BolloPrint. Běží
ve dne v noci, je ve stejné síti jako vaše tiskárny a už teď na něm běží vaše
ostatní drobné služby.

Agent se dodává jako **nativní balíček DSM**: nainstalujete ho jako kteroukoli
jinou aplikaci Synology a objeví se v hlavní nabídce DSM. Bez Dockeru, bez
Container Manageru, bez vkládání textu a bez kopírování kódu. Počítejte s deseti
minutami.

:::info
Tento článek se týká jen **instalace agenta na Synology**. Co je agent, které
značky podporuje a jak přidat jednotlivé tiskárny, najdete v
[návodu k místní síti](/blog/connect-printers-local-network-agent). Vraťte se k
němu, až budete tady hotovi.
:::

:::warning Balíček pro Synology je v betě
Funguje, ale některý krok se ještě může změnit. Pokud něco na vaší obrazovce
neodpovídá tomu, co tu čtete, dejte nám vědět.
:::

## Proč na NAS, a ne na notebooku

Protože agent je užitečný jen tehdy, když je vzhůru. Pokud běží na počítači,
který při odchodu vypínáte, o ty hodiny přijdete: co se tisklo, jak dlouho to
trvalo, jestli se tisk ve tři ráno nezastavil. NAS je zapnutý tak jako tak.

A zbytek dostanete navíc: je v síti tiskáren, díky čemuž je agent dokáže najít
sám, a je nenáročný: NAS dál dělá všechno ostatní jako dřív.

:::info 💡 Ne, na router sahat nebudete
Agent se k BolloPrint **připojuje směrem ven**, jako prohlížeč, když otevírá
webovou stránku. Nikdy nepřijímá spojení z internetu: žádné otevřené porty,
žádná pevná IP adresa, žádná pravidla firewallu. Funguje stejně za domácím
routerem jako na optice s CGNAT.
:::

## Co budete potřebovat předem

Zkontrolujte si to teď, ne v půlce:

- **DSM 7 nebo novější.** Najdete ho v **Ovládací panel → Informační centrum**.
  S DSM 6 to nepůjde.
- **Procesor vašeho NAS.** Na stejném místě, v **Informačním centru**. Intel
  nebo AMD znamená 64 bitů; u ARM zjistíte z technických údajů vašeho modelu na
  webu Synology, zda je 64bitový, nebo 32bitový. Budete to potřebovat, abyste
  stáhli správný soubor.
- **Účet správce DSM.** Jen správci mohou instalovat balíčky a otevřít stránku
  agenta.
- **Být v BolloPrint vlastníkem své dílny.** Při propojování agenta uvidíte jen
  dílny, jejichž jste vlastníkem.
- **NAS a tiskárny ve stejné síti.** V oddělených sítích (VLAN) agent funguje
  také, jen budete každou tiskárnu přidávat podle její IP adresy.

## 1. Stáhněte balíček

V BolloPrint přejděte do **Nastavení → Tiskárny → Místní agent → Nový agent** a
zvolte **Synology**.

Pro každý typ procesoru je tu jedno tlačítko ke stažení:
**Intel nebo AMD (64 bitů)**, **ARM (64 bitů)** a **ARM (32 bitů)**. Klikněte na
to svoje. Stáhne se soubor s příponou `.spk`, což je balíček DSM. Pokud si
nejste jistí, který to je, odkaz hned pod tlačítky vás zavede na web Synology,
kde si to u svého modelu ověříte.

![Nový agent → Synology v BolloPrint: tři tlačítka ke stažení, jedno pro každý typ procesoru, a pod nimi tři kroky instalace](/blog/media/2026-09-10-agente-synology/01-new-agent-synology.png)

Všimněte si, co na té obrazovce **není**: žádný kód, žádný klíč, nic k
vytvoření. Agent vznikne, až ho propojíte, v kroku 3.

## 2. Nainstalujte ho z Centra balíčků

Otevřete v prohlížeči DSM a přejděte do **Centra balíčků**. Vpravo nahoře
klikněte na **Ruční instalace**, potom na **Procházet**, vyberte soubor `.spk`,
který jste právě stáhli, a klikněte na **Další**.

<!-- SCREENSHOT: 02-manual-install.png — DSM 7 (English UI) Package Center with the «Manual Install» dialog open and bolloprint-agent-…-x64.spk selected, Next button visible. -->

DSM vás upozorní, že balíček nevydává Synology. Pro pokračování to potvrďte.

Průvodce vám pak ukáže jediné nastavení: **port stránky agenta**, kde už je
vyplněno **8257**. Nechte ho tak, pokud vám DSM neoznámí, že je obsazený; v
takovém případě zadejte **8364**. Klikněte na **Další** a v souhrnu na
**Hotovo**.

<!-- SCREENSHOT: 03-install-wizard.png — DSM 7 (English UI) BolloPrint Agent install wizard: the page-port field with 8257 and the text «After installing, open BolloPrint Agent from the DSM main menu and press “Link with BolloPrint”…». -->

Zhruba za minutu se balíček zobrazí jako **Spuštěno** a v hlavní nabídce DSM se
objeví **BolloPrint Agent**.

:::info 💡 „Tento balíček není kompatibilní s vaším modelem“
To znamená, že jste stáhli balíček pro jiný procesor. Vraťte se do BolloPrint a
stáhněte ten druhý.
:::

## 3. Propojte ho se svou dílnou

Tento krok nahrazuje dřívější „zkopírujte tenhle kód a vložte ho tamhle“.

Otevřete **hlavní nabídku** DSM (ikona vlevo nahoře) a klikněte na
**BolloPrint Agent**. Na nové kartě se otevře vlastní stránka agenta: stojí na
ní, že agent zatím nepatří k žádné dílně, a zobrazuje krátký **kód**.

![Stránka agenta, zatím nepropojená, s kódem a tlačítkem Propojit s BolloPrint](/blog/media/2026-09-10-agente-synology/04-agent-page.png)

Klikněte na **Propojit s BolloPrint**. Otevře se BolloPrint (pokud je potřeba,
přihlaste se) a zeptá se, do které dílny agent patří. Potom vám ukáže
**zařízení** — název vašeho NAS a „Synology“ — a **kód**. Ověřte, že je to
**stejný kód**, jaký ukazovala stránka agenta, a klikněte na
**Přidat do dílny**.

<!-- SCREENSHOT: 05-confirm.png — BolloPrint (English UI) «Add an agent to <workshop>» confirmation: Device «<NAS name> · Synology», the same code as 04-agent-page, and the «Add to workshop» button. -->

Vrátíte se na stránku agenta, kde je teď uvedeno **Propojeno s** vaší dílnou.

:::warning 🔐 Potvrzujte jen to, na co jste právě sami klikli
Pokud vám někdy přijde odkaz k „přidání agenta“, o který jste nežádali, zavřete
ho. Agent se propojuje jen ze své vlastní stránky a na Synology tu stránku může
otevřít jen správce vašeho NAS.
:::

## 4. Ověřte, že funguje

V BolloPrint, v **Nastavení → Tiskárny → Místní agent**: agent tam je s názvem
vašeho NAS a logem Synology, ve stavu **Online**. Právě na tom záleží: celý
okruh funguje.

![Agent Synology ve stavu Online v Nastavení → Tiskárny → Místní agent a pod ním tiskárny nalezené v místní síti](/blog/media/2026-09-10-agente-synology/06-agent-online.png)

Zhruba do minuty začne hledat tiskárny ve vaší síti. Zobrazí se v sekci
**Tiskárny v místní síti** a odtud je přidáte; ty, které se neobjeví samy, přes
**Přidat podle IP**. Postup pro jednotlivé značky najdete v
[návodu k místní síti](/blog/connect-printers-local-network-agent).

## Aktualizace

**Skoro nikdy nemusíte nic dělat:** agent se aktualizuje sám. Když vyjde nová
verze, stáhne ji, ověří, že je od nás, a restartuje se s ní.

Jen pokud vám BolloPrint oznámí, že agenta je potřeba **aktualizovat ručně**,
uděláte to sami, a znamená to **nainstalovat nový balíček přes ten, který už
máte**: stáhněte ho znovu ze stejného místa v BolloPrint (**Místní agent → Nový
agent → Synology**) a pak v **Centrum balíčků → Ruční instalace** vyberte nový
soubor. DSM pozná, že už je nainstalovaný, a aktualizuje ho, aniž by se znovu
ptal na port. Agent zůstane propojený se stejnou dílnou, se stejnými tiskárnami a
celou jejich historií. Nic není potřeba znovu propojovat.

Jakmile bude balíček v katalogu Centra balíčků Synology, Centrum balíčků vás na
novou verzi upozorní samo a aktualizace bude otázkou jednoho kliknutí.

:::warning Kvůli aktualizaci neodinstalovávejte
Odinstalace smaže identitu agenta: co nainstalujete potom, je **nový** agent,
kterého musíte znovu propojit. Při aktualizaci instalujte vždy přes stávající
balíček.
:::

## Přesun nebo začátek od nuly

Agenta „převést“ nelze, ale ani to není potřeba: přesouvají se tiskárny, a to s
celou svou historií.

1. Nainstalujte balíček na nový NAS a propojte ho. Zobrazí se jako druhý agent.
2. Otevřete každou tiskárnu přes **Upravit** v její nabídce **⋮** a přepněte ji
   na nového agenta.
3. Jakmile starému agentovi nezůstane žádná tiskárna, **smažte** ho z nabídky
   **⋮** na jeho řádku.

Pokud chcete agenta odebrat úplně: v DSM zvolte **Centrum balíčků → BolloPrint
Agent → Akce → Odinstalovat** a pak agenta v BolloPrint **smažte** z jeho
nabídky **⋮**. Funguje to i obráceně: jakmile ho v BolloPrint smažete, agent to
pozná, zapomene své propojení a jeho stránka znovu nabídne **Propojit s
BolloPrint**. V žádném případě se nic neztratí: pokud později některou z jeho
tiskáren znovu přidáte, vrátí se se svým číslem a svou historií.

## Když něco nefunguje

| Co vidíte | Co to obvykle znamená |
|---|---|
| Průvodce hlásí, že port 8257 je obsazený | Používá ho jiná aplikace na NAS. Zadejte 8364 a pokračujte. |
| „Není kompatibilní s vaším modelem“ | Balíček pro jiný procesor. Stáhněte ten správný. |
| Při otevření BolloPrint Agent se zobrazí výzva k přihlášení do DSM | Otevřete ho z hlavní nabídky DSM, přihlášeni jako správce. |
| Stránka hlásí, že agent neodpovídá | Balíček je zastavený nebo se ještě spouští. V Centru balíčků zvolte **Akce → Spustit** a počkejte několik sekund. |
| Při propojování se vaše dílna v seznamu nezobrazí | Vidíte jen dílny, jejichž jste **vlastníkem**. Požádejte vlastníka, aby agenta propojil. |
| „Tento požadavek na propojení není platný“ nebo vypršel | Vraťte se na stránku agenta a znovu klikněte na **Propojit s BolloPrint**. |
| Po restartu NAS chvíli trvá, než se agent vrátí | Dejte mu pár minut: spouští se spolu s DSM a zkouší to znovu, dokud NAS nemá internet. |
| Nenajde žádnou tiskárnu | Jsou ve stejné síti? Pokud ne, přidejte je podle IP. Pokud jste nějakou právě zapnuli, klikněte na **Hledat nyní**. Pokud máte zapnutou bránu firewall v DSM, povolte porty BolloPrint Agent (najdete ho v seznamu aplikací při vytváření pravidla). |

## Raději Docker?

Pokud na vašem NAS už běží Container Manager a chcete mít všechno v
kontejnerech, agent běží i jako kontejner. Postup najdete v článku
[Agent v Dockeru](/help/agente-en-docker). Pro většinu dílen je ale balíček
jednodušší: je to aplikace DSM jako každá jiná a propojí se jedním kliknutím.

Ať se vám líbí mít tiskárny stále na očích, se Synology jako prostředníkem.

![Bollo, maskot BolloPrint, vedle loga Synology](/blog/media/2026-09-10-agente-synology/10-bollo.webp "60%")

## Další čtení

- [Agent na Synology](/help/agente-en-synology) — kompletní průvodce: instalace, aktualizace, přesun, odinstalace a řešení potíží
- [Místní agent](/help/el-agente-local) — co dělá, více agentů, diagnostika
- [Tiskárny v místní síti](/help/impresoras-por-red-local) — přidání vašich strojů
- [Kompatibilní tiskárny](/help/impresoras-compatibles) — vyhledejte svůj model
