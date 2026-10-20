---
slug: calculate-your-3d-printing-costs
title: "Kolik doopravdy stojí vytištěný díl (a jak to jednoduše spočítat)"
description: Díl za 1,60 € filamentu vás ve skutečnosti stojí 9,36 €. Ukážeme vám, jak rozpočítat výdaje dílny do hodin tisku, aby je BolloPrint sám uplatnil u každého dílu.
date: 2026-10-15
updated: 2026-10-16
tags: [návody]
cover: 01-portada.webp
---

Díl, který se tiskne 6 hodin a spotřebuje 80 gramů PLA. Kolik vás stojí?

Pokud vás napadlo „80 gramů po 20 € za kilo, **1,60 €**“, máte spočítaný jen
**materiál**. V běžné dílně je to jen **malá část** toho, kolik vás díl
doopravdy stojí.

V dílně se třemi tiskárnami, u natřeného a zabaleného dílu, vypadá celý výpočet
takto:

| | |
|---|---|
| Materiál | 1,60 € |
| 6 hodin tiskárny | 5,16 € |
| Povrchová úprava (natřeno) | 2,00 € |
| Další náklady (balení) | 0,60 € |
| **Skutečný náklad dílu** | **9,36 €** |

**Skoro šestkrát víc.** Ten rozdíl není zaokrouhlení: je to nájem, elektřina,
opotřebení tiskáren, účetní a díly, které se nepovedou. To všechno platíte;
otázkou je, jestli si to také účtujete.

Tady uvidíte, jak tyto výdaje promítnout do nákladu každého dílu. **Nastavuje se
to jednou** a pak se to samo uplatní u každého dílu, který vytvoříte.

::animation{id="part-cost"}

## Odkud se bere těch 5,16 €

Princip je jednoduchý: sečtete **všechno, co vás dílna stojí za měsíc**, a
vydělíte to **hodinami, kdy opravdu tisknete**. Tak zjistíte, kolik vás stojí
**jedna hodina tiskárny**, a zbývá ji jen vynásobit hodinami tisku dílu.

S čísly z příkladu:

- **Hodiny:** tři tiskárny, deset hodin denně, dvacet pět dní v měsíci →
  **750 hodin**.
- **Výdaje:** nájem, účetní, software a odpisy strojů dají dohromady zhruba
  **516 € měsíčně**. Po rozpočítání: 0,69 € za hodinu. S elektřinou vycházejí
  **fixní náklady za hodinu** na **0,72 €**.
- **Přirážky:** 5 % na údržbu, 10 % na chybovost a 5 % na nepředvídané výdaje to
  zvednou na **0,86 € za hodinu**. Za šest hodin 5,16 €.

Přesně tento výpočet dělá sekce **Náklady** v BolloPrint, v **Nastavení →
Náklady**. Vidí ji jen **Vlastník** a **Administrátoři**.

![Sekce Náklady v Nastavení](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

Pokud teprve začínáte, úkol **Spočítejte, kolik vás stojí každý díl** v
**Prvních krocích** na **Úvodu** vás provede právě těmito obrazovkami, jednou po
druhé, a každou označí zeleně, jakmile ji uložíte.

## Hodiny, kdy opravdu tisknete

Začněte hodinami: je to číslo, které lidé nejčastěji spočítají špatně, a zároveň
to, které nejvíc mění výsledek. Najdete ho v **Hodinové náklady → Hodiny tisku**
a tvoří ho tři pole:

**Tiskárny × Hodiny / den × Dny / měsíc**

Zadejte **to, co se opravdu děje, ne teoretické maximum**. Pokud máte tři
tiskárny, ale v průměru pracují osm hodin denně, je to osm. Ne dvacet čtyři.

Svádí to zadat vysoké číslo, protože čím je vyšší, tím levněji vychází hodina.
Jenže výdaje zaplatíte stejně a to, co nerozpočítáte do dílů, zaplatíte na konci
měsíce ze svého.

![Karta Hodiny tisku se třemi poli a výsledkem](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Kolik vás stojí dílna

Když máte hodiny, je na řadě zapsat výdaje. Přidáváte je na kartě **Fixní
náklady**; BolloPrint je řadí podle typu a u každého po vás chce jen to, co
potřebuje:

| Typ | Co zadáte |
|---|---|
| **Fixní náklad** | Nájem, internet, účetní, pojištění… měsíční částku |
| **Tiskárna** | Kolik stála a za kolik let ji odepíšete |
| **Software** | Předplatné sliceru, BolloPrint a čehokoli dalšího, co používáte |
| **Mzdy** | Mzdu a počet lidí |
| **Elektřina** | Kolik kW tiskárna spotřebuje a kolik platíte za kWh |

Nemusí to sedět na cent: rozumné číslo dnes má větší cenu než dokonalé číslo za
rok.

:::warning ⚠️ Nezadávejte stejný výdaj dvakrát
Částky **za měsíc** popisují **celou dílnu**: nájem se zadává jen jednou. Ty,
které jsou **za vytištěnou hodinu** – jako elektřina podle spotřeby –, popisují
**jednu tiskárnu**: tam zadejte spotřebu průměrného stroje, ne celé haly.
:::

Úplně dole máte hotový výpočet, stejný jako na začátku:

> **měsíční výdaje ÷ vaše hodiny tisku = kolik vás stojí „čistá“ hodina**

To jsou vaše **fixní náklady za hodinu**: v příkladu 0,72 €.

![Výdaje dílny na kartě Fixní náklady, seskupené podle typu, a výpočet, který dává 0,72 € za hodinu](/blog/media/2026-09-12-costes-reales/03b-gastos-fijos.png)

## S čím se dá počítat dopředu

Fixní náklady nezahrnují to, co se děje bez pevné faktury: trysky se ničí a
**některý díl se nepovede a musí se tisknout znovu**.

K tomu slouží karta **Hodinové náklady**, která k fixním nákladům za hodinu
připočte několik procent: údržbu, chybovost a nepředvídané výdaje.

Chybovost je ta nejdůležitější a lidé ji nejčastěji vynechávají. Pokud z deseti
dílů jeden skončí v koši, **devět dobrých platí za ten špatný**. Pokud ji sem
nezahrnete, zaplatíte ho vy.

Výsledkem jsou vaše **hodinové náklady**: v příkladu 0,86 €. To je vaše skutečné
číslo a právě to se uplatní u každého dílu.

:::info 💡 Zisková marže sem nepatří
Sem patří jen **náklady**. Kolik chcete vydělat, se rozhoduje až potom, v
produktu, protože jde o obchodní rozhodnutí.
:::

![Přirážky na údržbu, chybovost a nepředvídané výdaje k fixním nákladům za hodinu, až na 0,86 € za hodinu](/blog/media/2026-09-12-costes-reales/03c-coste-por-hora.png)

## Materiál a další náklady

Zbývá nejjednodušší část, ve **Výchozích hodnotách**:

- **Cena každého materiálu** za kilogram. Je **podle typu**, ne podle skupiny:
  PLA a TPU nestojí stejně.
- **Povrchové úpravy**: kolik si přirazíte, pokud se díl opracovává nebo natírá.
- **Další náklady**: balení, spojovací materiál, magnety, inserty, práce. U
  každého zvolíte, jestli se účtuje **za kus**, nebo **za podložku**.
- **Marže**: ta, kterou chcete mít jako výchozí, a od kolika procent vás
  upozorníme červeně nebo oranžově.

:::info 💡 Pokud máte materiál ve skladu, rozhoduje sklad
Tyto ceny jsou orientační, pro případ, že za nimi nic není. Pokud se díl tiskne
z cívky zavedené ve skladu materiálu se skutečnou cenou, použijeme tu.
:::

![Výchozí hodnoty: marže s barevnými upozorněními a cena každého materiálu za kilogram](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## A takhle se to promítne do vašeho dílu

Předchozí čtyři kroky vedou k jedinému číslu: **kolik vás stojí jedna hodina
tiskárny**. Od té chvíle je každý díl součtem:

> jeho **hodiny × vaše hodinové náklady**
> **+** **materiál**, který spotřebuje
> **+** **povrchová úprava**, pokud se opracovává nebo natírá
> **+** **další náklady**, které k němu přidáte

Je dobré pochopit jeden detail, protože vysvětluje, proč se vyplatí zaplnit
celou podložku: **počítá se za podložku, ne za díl**. BolloPrint spočítá, kolik
stojí celá podložka, a **rozpočítá to mezi díly, které z ní vyjdou**. Proto se z
dalších nákladů ty, které označíte **za podložku**, účtují jen jednou – ať
tisknete díly po jednom, nebo po dvaceti – a ty **za kus** se účtují u každého
dílu.

Navíc si každý díl **ukládá hodinové náklady, se kterými byl spočítán**. Je to
záměr: náklad toho, co se tisklo loni, tak zůstává takový, jaký byl tehdy. Proto
existuje tlačítko **Přepočítat**, které uvidíte o kousek níž.

## Teď už máte své číslo

Výsledek uvidíte v **Náklady → Souhrn**. Blok **Příklad** vezme ukázkovou
podložku a ukáže vám celý výpočet **s vašimi hodnotami**: kolik dělá materiál,
kolik tisk, kolik povrchová úprava a kolik vychází díl.

![Blok Příklad s kompletním rozpisem nákladu dílu](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Když se změní vaše výdaje

Vaše čísla nebudou pořád stejná: zdraží elektřina, koupíte další tiskárnu nebo
se přestěhujete. Když je aktualizujete, **díly, které už máte, se samy
nezmění**. Je to záměr: každý díl si ukládá náklad, se kterým byl spočítán, a
jistě není žádoucí, aby se přepsal náklad všeho, co vzniklo loni.

Až to budete chtít uplatnit na všechno, v **Souhrnu** najdete počítadlo dílů
**K přepočtu** a tlačítko **Přepočítat**. Kdy, rozhodujete vy.

:::info 💡 Prodejní ceny to nemění
Přepočet aktualizuje **náklad** a *doporučenou* cenu. Cena zadaná ručně zůstane.
Pohne se ukazatel **marže**.
:::

## Mám si koupit další tiskárnu?

S nastavenými náklady můžete na tuto otázku odpovědět čísly. Ve **Scénářích
nákladů** měníte počet tiskáren, hodiny nebo dny a vidíte, co by se stalo s
vašimi hodinovými náklady. Je to jen simulace: ve vašem nastavení nic nemění.

Nejvíc ukáže to, že **křivka přestane klesat**. Přechod z jedné tiskárny na pět
sníží hodinové náklady skoro na pětinu. Přechod z dvaceti na sto s nimi skoro
nepohne, protože jsou výdaje – jako elektřina –, které se platí za každou
vytištěnou hodinu a nedají se na nikoho rozložit.

![Scénáře nákladů s křivkou hodinových nákladů](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Nastavení zabere čtyři obrazovky a chvilku jednoho odpoledne. Na oplátku bude mít
každý díl, který vytvoříte, svůj skutečný náklad a budete vědět, jestli
vyděláváte, bez ručního počítání.

:::info 💡 Pomůžeme vám s čísly?
Pokud nevíte, kde začít, napište nám přes [kontaktní stránku](/contact) nebo na
[našem Discordu](/help/soporte-por-discord). Už jsme to dělali mnohokrát.
:::

Ať vám čísla vždycky vycházejí.

![Bollo, maskot BolloPrint, v dílenských brýlích, zamyšlený mezi výpočty napsanými křídou](/blog/media/2026-09-12-costes-reales/07-bollo.webp "60%")

## Související dokumentace

- [Náklady](/help/costes): kompletní popis sekce
- [Díly](/help/piezas): jak se počítá náklad každého dílu
- [Produkty a varianty](/help/productos-y-variantes): od nákladu k prodejní ceně
- [Sklad materiálu](/help/inventario): aby se materiál počítal podle své skutečné ceny
