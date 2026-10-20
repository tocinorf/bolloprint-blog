---
slug: connect-printers-local-network-agent
title: "Připojte tiskárny přes vlastní síť: místní agent krok za krokem"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper… Malý agent na počítači v dílně, celá vaše flotila v BolloPrint a žádné zásahy do routeru.
date: 2026-10-12
updated: 2026-10-16
tags: [návody]
cover: 01-portada.webp
---

Vaše tiskárny jsou v dílně, ale vy ne vždycky. A chcete-li vědět, jestli některá
ještě tiskne, jestli tisk dopadl dobře nebo jestli jí zbývá materiál, musíte stát
přímo u ní.

Právě k tomu slouží **místní agent**: malý program, který běží na počítači ve
vaší dílně, komunikuje s tiskárnami přes vaši vlastní síť a předává BolloPrint
to, co vidí.

- **Na router nesaháte**: žádné otevřené porty, pevná IP ani firewall.
- **Je velmi nenáročný**: stačí mu jakýkoli počítač, který už stejně máte zapnutý.
- **Jeden stačí pro celou flotilu**, ať je jakkoli velká.
- **Aktualizuje se sám**: když vyjde nová verze, sám si ji nainstaluje.

::animation{id="local-agent"}

## Kam ho nainstalovat

Agent běží na **jakémkoli počítači v dílně, který nevypínáte**: na NAS, mini-PC,
Raspberry Pi nebo dílenském PC. Potřebuje jen, aby byl **stále zapnutý** a měl
**Docker**.

Ideální je, když je **ve stejné síti jako tiskárny**, protože pak je najde sám.
Pokud to nejde, přidáte je ručně a fungují stejně.

## Vytvořte agenta v BolloPrint

Začněte v BolloPrint. Přejděte do **Nastavení → Tiskárny**. Uvidíte tři karty:
**Tiskárny** (všechny vaše stroje, ať jsou připojené jakkoli), **Místní agent**
a **Bambu Cloud**. Otevřete **Místní agent** a klikněte na **Nový agent**.

Dejte mu název, který vám bude něco říkat i za půl roku: **pojmenujte ho podle
toho, kde stojí, ne podle toho, co je**. „Přízemí“ nebo „Hala 2“ poslouží,
„Agent 1“ ne. Potom klikněte na **Vytvořit agenta**.

![Karta Místní agent se dvěma agenty online a tlačítkem Nový agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-en.png)

## Zkopírujte šablonu

Po vytvoření vám BolloPrint ukáže **šablonu**: text, ve kterém je už **vyplněno**
všechno vaše, tedy klíče vašeho agenta a správná verze. Nic není potřeba
nahrazovat ani doplňovat.

Vyberte formát, který používáte (**Docker Compose** je nejběžnější), klikněte na
**Kopírovat** a jakmile ji budete mít v bezpečí, na **Uložit**.

![Šablona nasazení nového agenta s tlačítkem Kopírovat](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-en.png "75%")

:::warning 🔐 Zkopírujte ji hned: klíče se zobrazí jen jednou
Neukládáme je, takže vám je nemůžeme ukázat znovu. Pokud šablonu ztratíte, nic
se neděje: otevřete agenta přes **Upravit** (v jeho nabídce **⋮**), přejděte na
kartu **Nasazení** a klikněte na **Přegenerovat klíče**. Pokud se agent ještě
nikdy nepřipojil, nic se nepřeruší.
:::

## Vložte šablonu do svého počítače

Tohle už se dělá na vašem počítači, ne v BolloPrint, a postup závisí na tom, kam
agenta instalujete:

- **NAS Synology**: nainstalujte **Container Manager** z **Centra balíčků**,
  přejděte do **Projekt → Vytvořit**, vložte šablonu a projekt vytvořte. Bez
  psaní jediného příkazu.
- **Windows nebo Mac**: nainstalujte **Docker Desktop**, uložte šablonu do
  složky jako `docker-compose.yml` a z této složky spusťte
  `docker compose up -d`.
- **Linux**: nainstalujte **Docker** pomocí správce balíčků své distribuce,
  uložte šablonu jako `docker-compose.yml` a ve stejné složce spusťte
  `docker compose up -d`.
- **Portainer**: vložte stejnou šablonu do stacku a nasaďte ho.

:::info 💡 Ve Windows a na Macu se tiskárny nenajdou samy
Docker tam běží uvnitř virtuálního stroje, který nevidí oznámení, jež tiskárny
posílají do vaší sítě. Agent funguje stejně, ale tiskárny přidáte ručně, jak je
popsáno níže.
:::

## Pokud si nevíte rady, klikněte na „Instalovat“

Dokud se agent ani jednou nepřipojí, je v jeho řádku stav **Nenainstalováno**.
Není to chyba: nic nespadlo, jen ho ještě zbývá nainstalovat.

Ve stejném řádku je tlačítko **Instalovat**. Po kliknutí se ve zkratce rozbalí
kroky popsané výše, s odkazem **Nápověda**, dalším odkazem **Článek na blogu**,
který vede na tento text, a tlačítkem, kterým se nás můžete zeptat na
**Discordu**. Pokud šablonu nemáte uloženou, krok 3 vás zavede rovnou
k vygenerování nové.

![Nenainstalovaný agent s otevřeným panelem Instalovat: tři kroky, nápověda a Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-en.png)

## Ověřte, že je online

Vraťte se do BolloPrint: za necelou minutu přejde agent do stavu **Online**
a ukáže název počítače, na kterém běží, a svou verzi.

![Agent ve stavu Online](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-en.png)

Pokud se to nestane, téměř vždy jde o jednu ze tří příčin: šablona byla **vložena
jen zčásti**, počítač **nemá internet** nebo odchozí provoz blokuje **firewall**.
Chcete-li vidět, co hlásí sám agent, otevřete ho přes **Upravit**: podrobnosti
najdete na kartě **Stav**.

## Tiskárny se objeví samy

Od té chvíle agent každých 15 minut sám **hledá tiskárny ve vaší síti**. Když
nějakou najde, upozorní vás nad kartami a tiskárnu uvidíte na konci části
**Tiskárny v místní síti**, i se značkou a modelem. Rozhodnutí je na vás:

- **Přidat**: tiskárnu zaregistrujete a začne hlásit svůj stav.
- **Ignorovat**: není vaše nebo ji tu nechcete.

![Tiskárna nalezená agentem s tlačítky Ignorovat a Přidat, nad ní Hledat nyní a Přidat podle IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-en.png)

Pokud právě zapínáte stroj a nechcete čekat, klikněte na **Hledat nyní**. Pokud
si tiskárna vyžádá kód, upozorní vás na to přímo její řádek („vyžádá si
přístupový kód“), ať máte kód po ruce.

## Když se některá neobjeví, přidejte ji ručně

To, že se tiskárna neobjeví sama, je **normální** ve dvou případech:

- **Je v jiné síti.** Oznámení tiskáren nepřecházejí z jedné sítě do druhé.
- **Agent běží ve Windows nebo na Macu.** Docker tam běží ve virtuálním
  stroji.

Nic tím neztrácíte: tiskárnu přidáte ručně a funguje úplně stejně, s kamerou
i ovládáním, pokud je daný stroj má. Klikněte na **Přidat podle IP**. Jsou to tři
kroky.

### 1. Vyberte značku

Vyberte značku své tiskárny: každá má svou dlaždici a ty s logem jsou první.
Nemusíte vědět, jak váš stroj komunikuje, o to se postaráme my. Pokud vyberete
**Elegoo**, zeptáme se **Jakou Elegoo máte?**, protože tato značka má několik
řad. **Klipper** a **Jiná pryskyřičná (ChituBox)** jsou na konci, v části
**Obecné**, pro vlastní stavbu nebo značku, která v seznamu není.

Pokud nevíte jistě, jestli se váš model hodí, dole najdete **Nevíte jistě?
Podívejte se na seznam kompatibilních tiskáren**. A pokud vaše tiskárna v seznamu
chybí, napište nám na Discord.

![První krok přidání tiskárny podle IP: značky, které lze připojit](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-en.png)

### 2. Zadejte její údaje

Jen to nezbytné:

- **Který agent ji připojuje?**, pokud jich máte víc. Vybrat lze jen agenta,
  který je online.
- **IP tiskárny**. Najdete ji na displeji tiskárny (Nastavení → Síť) nebo
  v routeru.
- **Kód tiskárny**, pokud ho daná značka vyžaduje. Pole se jmenuje tak, jak ho
  nazývá výrobce: u Bambu **Přístupový kód LAN**.
- **Název**, pokud jí chcete dát vlastní. Je nepovinný.

**Model a sériové číslo nezadáváte**: agent se na ně zeptá tiskárny. Povinná pole
mají **červenou hvězdičku** a dokud jsou prázdná, jsou zvýrazněná červeně. Na
konci vám rámeček **Nezapomeňte** připomene, co je u dané značky potřeba připravit
před připojením.

![Druhý krok: agent, IP, povinný přístupový kód LAN a rámeček Nezapomeňte](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-en.png)

### 3. Připojte

Klikněte na **Připojit** a uvidíte, jak připojování postupuje: agent přijme
požadavek, hledá tiskárnu na dané adrese a připojí se k ní. Na konci uvidíte
**„Připojeno. Tiskárna je už ve vašem seznamu tiskáren.“**

![Třetí krok: tiskárna připojená a už v seznamu](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-en.png)

Pokud něco selže, řekneme vám to **srozumitelnými slovy**: co se děje a co
zkontrolovat (že na dané IP nic neodpovídá, že tiskárna odmítá kód…). Tlačítkem
**Zpět** údaj opravíte a zkusíte to znovu. Původní hlášení tiskárny je sbalené
pod **Zobrazit technické podrobnosti**: pokud nám budete psát, zkopírujte nám ho
a podíváme se na to rychleji.

:::info 💡 Rezervujte tiskárně IP v routeru
Pokud router tiskárně změní adresu, znovu ji automaticky najdeme, ale chvíli
bude nedostupná. Rezervace adresy tomuto výpadku zabrání. Je to nastavení
routeru, ne BolloPrint.
:::

## Co vyžaduje která značka

Tady vzniká nejvíc dotazů. Je to totéž, co připomíná krok 2, jen ve zkratce:

| Značka | Co je potřeba udělat na stroji | Kamera | Lze pozastavit a zrušit tisk? |
|---|---|---|---|
| **Bambu Lab** | Zapnout **režim LAN** na jejím displeji (Nastavení → Síť) a použít **přístupový kód LAN**, který tam zobrazí | Ano | Ano, pokud navíc zapnete **režim pro vývojáře** |
| **Prusa** (beta: MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Zapnout **PrusaLink** a použít zobrazené **heslo** (není to heslo k Prusa Connect) | Ne | Ano |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) a **jiné pryskyřičné (ChituBox)** | Nic, heslo nevyžadují | U modelů, které ji mají | Ano |
| **Elegoo Centauri Carbon 2** | Nic; jen pokud je na jejím displeji nastavený kód, zadejte ho | Ano | Ne |
| **Anycubic** (beta: Kobra 3, Kobra S1, Kobra 4, Kobra X) | Zapnout **režim LAN** (Nastavení → Síť). Se zapnutým režimem LAN přestane tiskárna používat cloud a aplikaci Anycubic | Ne | Ne |
| **FlashForge** (beta: Adventurer 5M, 5M Pro, AD5X, Creator 5) | Zapnout **LAN Only** a použít ověřovací kód ze síťové nabídky | Ano | Ne |
| **Snapmaker** (U1) | Nic | Ano | Ano |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Obvykle nic: jen pokud je v Moonrakeru nastavený klíč API | Ano, pokud má váš Klipper webkameru | Ano |

:::warning ⚠️ Bambu Lab: přístupový kód se mění
Pokaždé, když zapnete nebo vypnete režim LAN nebo režim pro vývojáře, Bambu
**vygeneruje nový kód**. Pokud se Bambu, která dosud fungovala bez problémů,
najednou přestane připojovat, v devíti případech z deseti je to právě kvůli
tomu: znovu se podívejte na kód na jejím displeji a aktualizujte ho v BolloPrint.
A počítejte s tím, že **režim pro vývojáře** ji odpojí od Bambu Cloud: od té chvíle
ji uvidíte už jen přes agenta.
:::

:::info 💡 Váš model v tabulce chybí?
Podívejte se na [kompatibilní tiskárny](/help/impresoras-compatibles). Pokud
v tiskárně běží **Klipper** (jakýkoli stroj vlastní stavby nebo upravený), je
kompatibilní, i když její značka není v žádném seznamu.
:::

## Co vám místní agent přinese

S běžícím agentem získáte:

- **Téměř všechny značky**: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge,
  Snapmaker a vše, na čem běží Klipper. Cloud to nenabízí, protože existuje jen
  pro Bambu Lab.
- **Kameru**: živě, dokud máte stránku otevřenou, snímek, kdykoli chcete,
  a závěrečný snímek uložený v historii každého tisku. Není to kamerový dohled:
  nic se nenahrává.
- **Ovládání**: pozastavení, obnovení a zrušení tisku z BolloPrint, bez chození
  ke stroji, u tiskáren, které to umožňují (viz tabulka výše). U Bambu Lab
  s tiskárnou v **režimu LAN** a v **režimu pro vývojáře**.
- **Odolnost vůči výpadkům internetu**: když vám vypadne připojení, agent **dál
  čte stav tiskáren a ukládá, co se děje**. Jakmile se připojení obnoví, všechno
  odešle a o ty hodiny historie nepřijdete.
- **Nezávislost na výrobci** a na tom, jestli jeho cloud dál funguje.

Žádná cesta ale neumožňuje **posílat úlohy k tisku**: soubor dál posíláte ze
svého sliceru.

## Časté dotazy

Na tohle se nás ptáte nejčastěji.

### Musím otevírat porty v routeru?

Ne. Ani porty, ani pevnou IP, ani pravidla firewallu. Funguje za běžným domácím
routerem.

### Je potřeba jeden agent na každou tiskárnu?

Ne. **Jeden zvládne celou flotilu.** Víc agentů má smysl jen tehdy, když máte dvě
provozovny nebo dvě oddělené sítě. V tom případě se vás při **Přidat podle IP**
zeptá, který z nich tiskárnu připojuje.

### Co když vypnu počítač nebo vyjde nová verze?

Po zapnutí počítače se agent vrátí sám. Aktualizuje se také sám: když vyjde nová
verze, stáhne ji a restartuje se s ní a na šablonu přitom není potřeba sahat.
Něco udělat budete muset, jen pokud vás na to upozorníme na obrazovce.

### Proč nemohu kliknout na „Přidat podle IP“?

Protože žádný z vašich agentů není připojený a pod tlačítkem se to také píše.
Pokud agenta ještě nemáte nainstalovaného, použijte **Instalovat** v jeho řádku.
Pokud už fungoval, zkontrolujte, že je počítač zapnutý a má internet.

:::info 💡 Potřebujete pomoc?
Napište nám přes [kontaktní stránku](/contact) nebo založte vlákno na
[našem Discordu](/help/soporte-por-discord). Když nám řeknete, jaké tiskárny
máte, poradíme vám přesně, co s každou z nich udělat.
:::

Užijte si přehled o celé flotile, ať jste kdekoli.

![Bollo, maskot BolloPrint, v dílenských brýlích před farmou pracujících 3D tiskáren](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Související dokumentace

- [Připojení tiskáren](/help/conectar-impresoras): dvě cesty a která se vám hodí
- [Místní agent](/help/el-agente-local): kompletní referenční popis
- [Nasazení agenta](/help/desplegar-el-agente): technické podrobnosti, pokud je potřebujete
- [Typy připojení](/help/tipos-de-conexion): co umožňuje která rodina tiskáren
- [Kompatibilní tiskárny](/help/impresoras-compatibles): tady najdete svůj model
