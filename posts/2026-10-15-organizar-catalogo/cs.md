---
slug: organize-your-3d-printing-catalog
title: "Od souborů STL k produktům ve vašem obchodě: jak uspořádat katalog 3D tisku"
description: Naučte se uspořádat soubory STL, spočítat náklady na díl a vytvářet varianty produktů pro svůj obchod s 3D tiskem bez komplikací.
date: 2026-10-18
tags: [návody]
cover: 01-portada.webp
---

Pokud 3D tisknete na prodej, tuhle scénu určitě znáte: desítky složek v počítači
se soubory jako `llavero_V2_FINAL_definitivo.stl` a nikdo si nepamatuje, kolik
filamentu ta verze spotřebovala ani jaký profil sliceru byl použit. A když přijde
objednávka z Etsy, odhadnete náklady od oka a doufáte, že neproděláte.

V dílně nebo farmě 3D tisku se technický a obchodní nepořádek prolínají, pokud je
neoddělíte. Proto je BolloPrint řeší zvlášť. V tomto průvodci vám vysvětlíme, jak
do sebe zapadají **Návrhy, Díly, Produkty a Varianty** a jak se od hromady
rozházených souborů dostat k uspořádanému katalogu.

::animation{id="how-it-works"}

## Oddělte technickou stránku od obchodní

Jednou z nejčastějších chyb při řízení dílny je brát soubor STL, jako by to byl
produkt, který prodáváte. V praxi lze tentýž 3D model tisknout z různých
materiálů, může mít více částí nebo se prodávat v sadách.

Proto BolloPrint uspořádá váš katalog do tří úrovní.

### Návrhy: technická knihovna

**Návrh** je schránka pro vaše zdrojové soubory: STL, OBJ nebo projekty 3MF,
spolu s fotkami modelu a vašimi interními poznámkami.

- **Berte Návrh jako plán nebo nápad.** Nemá časy ani gramy filamentu, protože
  tentýž STL lze tisknout v různých měřítkách nebo z různých materiálů.

![Návrh „Keyring BolloPrint“ se souborem STL, fotkou, interními poznámkami a dvěma díly: 5 cm a 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Díly: fyzický předmět

**Díl** vznikne, když Návrhu dáte konkrétní nastavení tisku: materiál a jeho
spotřebu (například černé PLA), rozměry a dobu tisku.

- **Jeden Návrh, několik Dílů.** Ze stejného STL můžete vytisknout figurku ve
  dvou velikostech, 5 cm a 10 cm: ten Návrh bude mít dva Díly, „Malá klíčenka“ a
  „Velká klíčenka“. Totéž platí pro různé barvy nebo materiály.
- **Soubor ze sliceru to spočítá za vás.** Když k Dílu nahrajete soubor ze
  sliceru (`.gcode`, `.gcode.3mf`, `.bgcode` nebo `.goo` pro pryskyřici),
  BolloPrint z něj načte hmotnost a dobu tisku a navrhne vám je. Když je
  použijete, spočítá, kolik vás stojí výroba přesně tohoto dílu. Údaje můžete
  také zadat nebo opravit ručně.

:::info 💡 Projektový 3MF sem nepatří
Aby slicer znal hmotnost a čas, musí podložku nejdřív naslicovat. Projektový
`.3mf` je neobsahuje: patří do Návrhu. K Dílu nahrajte `.gcode.3mf`, který
slicer vyexportuje.
:::

### Produkty a Varianty: co vidí a kupuje váš zákazník

**Produkt** je vaše výloha: to, co zveřejníte ve svém obchodě nebo na
marketplace jako Etsy. **Varianta** je konkrétní možnost, kterou si zákazník
vybere.

- **Varianta může mít jeden nebo více Dílů**, každý se svým množstvím.
- **Například:** váš Produkt je „Figurka Bolla“, našeho psa. Jedna Varianta může
  být „Zelená“, další „Oranžová“ a další sada „Zelená + Oranžová“ s oběma Díly
  uvnitř. Materiály, velikosti, povrchové úpravy nebo balení můžete kombinovat,
  jak chcete.

![Varianta Green+Orange se dvěma díly uvnitř, oranžovým a zeleným, a s nákladem, marží a cenou](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

:::info 💡 Sada může míchat Návrhy
Varianta může obsahovat Díly z různých Návrhů: například sada „Vítejte v
BolloPrint“ s klíčenkou a figurkou Bolla.
:::

- **Marže se spočítá sama.** Protože každá Varianta ví, z jakých Dílů se skládá,
  BolloPrint porovná vaši prodejní cenu se skutečným výrobním nákladem a ukáže
  vám marži. Když změníte cenu, marže se aktualizuje, a naopak.

![Varianta Green s jediným dílem: náklad 7,06 €, marže 70 % a cena 23,54 €](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## Spěcháte? Použijte Rychlé vytvoření

Pokud začínáte nebo máte k nahrání stovky modelů, nastavovat Návrhy, Díly a
Produkty jeden po druhém zabere čas.

K tomu slouží tlačítko **Rychlé vytvoření** v katalogu. Na jediné obrazovce
nahrajete 3D soubor, zadáte materiál, hmotnost, čas a cenu a BolloPrint najednou
vytvoří Návrh, Díl, Produkt i jeho Variantu. Výsledek je stejný jako při postupu
krok za krokem, takže potom můžete doladit, co chcete.

![Formulář Rychlého vytvoření: 3D soubor, fotky, materiál, hmotnost, čas, barvy, náklad a cena](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## Vaše štítky přejdou do produktu samy

Další drobnost, která vám ušetří práci: **štítky** Návrhu přejdou samy do jeho
Produktů.

Když Návrhu dáte štítek „Klíčenky“ nebo „Figurky“, při přidání jeho Dílů do
Varianty se tyto štítky přidají k Produktu. A pokud prodáváte na Etsy, při
publikování inzerátu je tam už najdete vyplněné jako *tagy*, které pomáhají, aby
vás zákazníci našli. Etsy jich povoluje až 13, každý nejvýš o 20 znacích, a před
publikováním je můžete upravit.

## Začněte s pořádkem v katalogu

Dobře uspořádaný katalog není jen otázka pořádku: je to způsob, jak vědět, kolik
vás stojí každý díl a kolik vyděláte na každé objednávce, a nechat dílnu růst bez
ztráty přehledu.

Pokud chcete podrobněji vidět, jak katalog nastavit nebo vytvořit pokročilé
varianty, podívejte se do
[dokumentace katalogu](/help/catalogo). A pokud vás zajímá, odkud se bere náklad
každého Dílu, píšeme o tom v článku
[Kolik doopravdy stojí vytištěný díl](/blog/calculate-your-3d-printing-costs).

Zjistěte, [jak mít výrobu ve své dílně pod kontrolou s BolloPrint](/features),
softwarem pro farmy 3D tisku.

Ať váš katalog roste stejně uspořádaný, jako začíná.

![Bollo, maskot BolloPrint, v dílenských brýlích vedle svého 3D modelu v drátěné síti](/blog/media/2026-10-15-organizar-catalogo/07-bollo.webp "60%")

## Související dokumentace

- [Katalog](/help/catalogo): úrovně katalogu v referenční příručce
- [Návrhy](/help/disenos): soubory, fotky a štítky
- [Díly](/help/piezas): materiál, soubor ze sliceru a náklad
- [Produkty a varianty](/help/productos-y-variantes): cena, marže a díly každé varianty
- [Rychlé vytvoření](/help/creacion-rapida): všechno najednou
- [Štítky](/help/etiquetas): jak se vytvářejí a spravují
