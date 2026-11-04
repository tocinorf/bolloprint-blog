---
slug: whats-new-september-november-2026
title: "BolloPrint se zlepšuje! Novinky, které vám pomohou ve vaší dílně 3D tisku"
description: "Všechny novinky v BolloPrint od 14. září do 3. listopadu 2026: od místního agenta bez kontejnerů po právně platné faktury a zcela nové Finance."
date: 2026-11-03
tags: [novinky]
cover: 01-bollo.webp
---

Od poloviny září jsme vydali **41 aktualizací** BolloPrint. Některé jsou velké a
důležité změny. Jiné jsou drobná vylepšení, díky kterým je vaše každodenní práce
pohodlnější. Tady je to nejdůležitější.

![Za sedm týdnů: více než 400 znatelných vylepšení, více než 250 změn na obrazovce, asi 190 opravených chyb, 11 zemí s právně platnými fakturami, 9 jazyků v aplikaci a 102 tiskáren od 15 značek](/blog/media/2026-11-03-novedades-otono/02-cifras-cs.webp)

## Začneme tím nejzajímavějším: co mění způsob, jakým pracujete

### 1. Místní agent, nyní bez znalosti kontejnerů

Víme, že Docker umí být složitý. Proto je to teď jednodušší. Nainstalujte agenta
na to, co už máte: na svůj NAS, počítač v dílně nebo svůj Home Assistant.

![Loga Synology, QNAP, Windows, Home Assistant a TrueNAS](/blog/media/2026-11-03-novedades-otono/03-agentes.webp)

| Kde | Jak ho nainstalovat |
|---|---|
| **Synology a QNAP** | Stáhněte balíček pro svůj NAS a nainstalujte ho ručně z jeho centra balíčků. |
| **Windows** | Instalátor pro počítač v dílně. |
| **Home Assistant** | Tlačítko „Přidat do Home Assistant“ a hotovo. |
| **TrueNAS** | Vložíte do jeho aplikací konfiguraci, kterou vám dáme. |

Pak otevřete jeho stránku a klikněte na **„Propojit s BolloPrint“**: vlastník
dílny to potvrdí jedním kliknutím, bez opisování kódů. Jako každý agent se
aktualizuje sám. Docker a Kubernetes fungují dál jako vždy.

:::info
Najdete ho v **Nastavení → Tiskárny → Místní agent → „Nový agent“**.
[Jak nainstalovat agenta](/help/el-agente-local)
:::

---

### 2. Vaše tiskárny, lépe vidět a přesněji spočítané

- **Živá kamera** a závěrečná fotka každého tisku v jeho historii.
- **Každý tisk řekne všechno**: jak dlouho trval oproti odhadu, každou cívku s jejím slotem v AMS a název modelu z MakerWorld s odkazem.
- **Skutečná spotřeba**: neúspěšný nebo zrušený tisk se už nepočítá celý a tisky z pryskyřice zaznamenávají své mililitry.
- **Bambu Lab**, přes cloud bez hesla (váš e-mail a kód, relace se obnovuje sama) a přes místní síť s pozastavením, obnovením a zrušením z BolloPrint, se zapnutým režimem pro vývojáře.
- **Přidat podle IP** je teď průvodce pro každou značku; už nemusíte vědět, jakým „protokolem“ vaše tiskárna mluví.
- **Místní agent se aktualizuje sám**, nikdy uprostřed tisku, a každá značka tiskáren se zlepšuje samostatně.
- Přibývají **Anycubic** (Kobra 3, S1, 4 a X) a **Creality** s továrním firmwarem (K1, K2, Ender-3 V3 a Hi), v betaverzi.

[Zobrazit kompatibilní tiskárny](/help/impresoras-compatibles)

---

### 3. Chytrá migrace

Přeneste zákazníky, návrhy, díly, produkty, objednávky, nabídky a sklad ze složek
a tabulek ve svém počítači. BolloPrint přečte, co přinesete, a navrhne, jak to
zařadit; vy vše zkontrolujete dřív, než cokoli vstoupí, a když se spletete, dá se
to vrátit zpět.

:::warning
Jsou to tři kroky: **Připravit · Porozumět · Migrovat**. Od tarifu Pro, v Chromu
nebo Edgi na počítači. V tarifech Max a Business to za vás můžeme udělat my.
:::

---

### 4. Právně platné faktury přímo z objednávky

Vystavte fakturu k objednávce, aniž byste opustili BolloPrint: s číselnou řadou,
daní a vaším logem. Před vystavením vidíte fakturu **přesně tak, jak vyjde**, a
pokud něco chybí, řekneme vám co a kde to opravit.

- **Platby**: čekající, po splatnosti nebo zaplacená, a ZIP se všemi vašimi
  fakturami.
- **Prodej bez DPH firmám z EU**, s právní doložkou a číslem ověřeným ve VIES.
- **Německá e-faktura, švýcarský QR-bill** a faktury v jiné měně.

Už dostupné v 11 zemích: Česko, Irsko, Kypr, Lucembursko, Německo, Nizozemsko,
Polsko (přes KSeF), Rakousko, Spojené království, Švédsko a Švýcarsko.

:::warning
**Ve Španělsku zatím ne**: přijde, až integrujeme VeriFactu, a dáme vám vědět.
:::

[Zobrazit země s fakturací](/help/paises-con-facturacion)

---

### 5. Profesionálnější nabídky

- PDF nabídky má **podobu faktury**: číslo, datum, platnost a v placených
  tarifech vaše vlastní logo.
- **Číslování podle roku** („2026-00001“) a bez mezer, i když některou smažete.
- **Sleva** v € nebo v %, která se zobrazí jako další řádek.
- Karty zákazníka **Fyzická osoba nebo Firma** a jednodušší daňové údaje.
- Automatické vytvoření **objednávky po přijetí** nabídky.

[Zobrazit nabídky](/help/presupuestos)

---

### 6. Zcela nové Finance

Šest karet, kde vidíte své příjmy, výdaje, daně a zisk za libovolné období
(měsíční, čtvrtletní, roční…).

Nahrávejte výdaje s naším agentem s AI a archivujte faktury svých dodavatelů,
abyste na první pohled viděli, za co utrácíte peníze. Mějte přehled o daních,
které musíte v každém období zaplatit.

:::info
**To nejlepší:** exportujte tato data pro svou účetní do ZIPu jedním kliknutím.
:::

[Zobrazit Finance](/help/financiero)

---

### 7. „Upozornění“: problémy vaší dílny na první pohled

Tiskárna zastavená s chybou, odpojený obchod na Etsy, platba, která neprošla,
téměř plné úložiště… Upozorníme vás jen na to, co opravdu něco vyžaduje, a každé
upozornění se samo zavře, jakmile problém vyřešíte.

Upozornění můžete ztlumit na pár dní nebo navždy. Červená, ta, která zastavují
něco důležitého, ukazujeme červeně jen tomu, kdo je může vyřešit; zbytek týmu je
vidí s „Dejte vědět vlastníkovi dílny“.

---

### 8. Exportujte svůj sklad do Excelu nebo PDF

Teď si můžete vytáhnout seznam toho, co máte na skladě: zásoby, filamenty,
pryskyřice, spotřební materiál…

| Formát | Co dostanete |
|---|---|
| **Excel** | Sešit se souhrnem a jedním listem pro každou sekci, s filtry, součty a tím, co došlo, červeně. |
| **PDF** | Jeden dokument pro každou sekci, s vaším logem, fotkami vašich dílů a barvami každé cívky. |

Ve všech tarifech a vždy se všemi řádky, nejen s těmi, které máte na obrazovce.

---

### 9. Ve vašem jazyce a po vašem

BolloPrint už mluví **🇵🇱 polsky, 🇳🇱 nizozemsky a 🇨🇿 česky**. Celkem je to tedy
devět jazyků.

Data a částky se píšou **tak, jak je to zvykem v zemi vaší dílny**, na obrazovce,
v PDF i v e-mailech.

A je tu **nový Úvod**, který začíná tím, co je naléhavé, s „Vytvořit“ pro
objednávku, nabídku nebo rychlé vytvoření a s „Prvními kroky“ s ukazatelem
postupu.

## A navíc, protože i malé změny jsou znát

| Kde | Co se mění |
|---|---|
| **Obrazovky** | Během načítání vidíte tvar obsahu, nikdy falešný prázdný seznam; když se něco nepovede, „Zkusit znovu“. Filtry jsou stejné ve všech seznamech, i na mobilu. |
| **Nahrávání** | Každý soubor ukazuje svůj postup a po výpadku sítě pokračuje sám. Soubory ze sliceru mohou mít až 5 GB. |
| **Náklady** | 29 rodin filamentů a 9 rodin pryskyřic s aktualizovanými cenami za kilogram; marže s barevným pruhem a příkladem. |
| **Zákazníci** | Seznam vyhledává a řadí podle libovolného sloupce a zákazník bez přezdívky se zobrazuje celým jménem. |
| **Etsy** | Import inzerátu je až 8× rychlejší, přicházejí objednávky se dvěma variantami a před synchronizací inzerátu vidíte hodnotu po hodnotě, co se změní. Nastavení → Tržiště je teď galerie se stránkou pro každý obchod. |
| **Doprava** | Vlastní dopravci a prodejní kanály pro Rakousko, Německo, Spojené království, Polsko, Česko a Nizozemsko. |
| **Příručka a blog** | Příručka roste ze 49 na 70 stran, ve všech devíti jazycích, a na blogu je šest nových článků: od místního agenta po to, kolik díl doopravdy stojí. |
| **Každý den** | Aplikace lépe zvládá špičky, sama se vrátí po výpadku sítě, překladač Chromu ji už nerozbije a tiskárna, jejíž agent se uprostřed vypne, už nenechává tiskové „duchy“. |

## Kde jsme

| Co | Kde a kolik |
|---|---|
| 🧾 **Právně platné faktury v 11 zemích** | 🇨🇿 Česko · 🇮🇪 Irsko · 🇨🇾 Kypr · 🇱🇺 Lucembursko · 🇩🇪 Německo · 🇳🇱 Nizozemsko · 🇵🇱 Polsko · 🇦🇹 Rakousko · 🇬🇧 Spojené království · 🇸🇪 Švédsko · 🇨🇭 Švýcarsko |
| 🌍 **Dílnu lze založit z 53 zemí Evropy** | S vlastní měnou, daněmi a dopravci. Platí se v eurech, librách, zlotých nebo českých korunách. |
| 🖨️ **102 modelů tiskáren, pro filament i pryskyřici** | Bambu Lab · Prusa · Elegoo · FlashForge · Anycubic · Creality · QIDI · Snapmaker · Voron · RatRig · Sovol · Artillery · Longer · Phrozen · Two Trees |
| ✅ **10 jsme sami vyzkoušeli na skutečných strojích** | Bambu Lab A1, A2L, P1P, P1S, P2S, X1 Carbon, X2D, H2C, H2D a H2S. |

## Chybí vám něco?

Napište nám na
[info@bolloprint.com](mailto:info@bolloprint.com) nebo na našem
[kanálu na Discordu](/help/soporte-por-discord). Čteme všechno. Mnoho z toho, co
tu vidíte, vzniklo ze zpráv, jako je ta vaše.

Pokud chcete vědět víc o tom, jak to funguje, všechno najdete v
[příručce](/help).

A nezastavujeme se: každý den dál pracujeme na tom, aby BolloPrint byl nejlepším
nástrojem pro vaši dílnu 3D tisku.

![Bollo, maskot BolloPrint, s dílenskými brýlemi a opaskem na nářadí, na výkresu](/blog/media/2026-11-03-novedades-otono/01-bollo.webp "60%")
