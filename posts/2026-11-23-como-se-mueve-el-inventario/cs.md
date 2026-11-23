---
slug: how-your-inventory-keeps-itself-up-to-date
title: "Automatický sklad: takhle se váš sklad sám upravuje podle prodejů"
description: Prodáte figurku, cívku filamentu nebo vyrazíte na akci pro makery a váš sklad zůstane aktuální sám. Ukážeme vám, co BolloPrint s vaší zásobou v každé situaci dělá.
date: 2026-11-23
tags: [návody]
cover: 08-stock-del-pedido-en.png
---

Mít aktuální sklad je fajn, ale opravdu práci ušetří, až když se aktualizuje sám.
Prodáte figurku, kterou jste už měli vytištěnou, na trhu inkasujete za cívku
filamentu, na akci si vezmete dvě plné krabice… a po návratu nechcete strávit
odpoledne počítáním, co zbylo.

V tomto návodu vám ukážeme, co BolloPrint s vaší zásobou v každé situaci dělá.

## Nejdřív: co všechno je ve vašem skladu

Ve **Skladu materiálu** BolloPrint rozlišuje dvě věci:

- **Skladovou zásobu**: **už vytištěné díly**, které máte uložené a připravené
  k sestavení produktu nebo k prodeji.
- **Materiál**: vaše cívky **Filamentu**, lahve **Pryskyřice** a **Spotřební
  materiál** (krabice, magnety, závitové vložky…). To je to, co nakupujete,
  i když to můžete i prodávat!

## Svůj materiál můžete i prodávat!

Kromě svých 3D produktů můžete do objednávek a nabídek přidávat i **filament,
pryskyřici a spotřební materiál** a prodávat je v pokladně. Zákazník si od vás
koupí cívku? Odejde ze skladu jako každý jiný prodej.

## Co prodáte, odejde ze skladu

Když uložíte objednávku nebo přijmete nabídku, BolloPrint projde váš sklad, aby
zjistil, co máte a co ne, a ukáže vám, co odchází:

- **Materiály**, které prodáváte: cívky, lahve nebo spotřební materiál.
- **Díly** 3D produktů, které prodáváte. Když se produkt skládá z více dílů,
  odejdou ze skladové zásoby všechny.

A vy si vyberete **Odebrat ze skladu**, nebo **Neodebírat ze skladu**.

![Při vytváření objednávky, co odchází ze skladu: cívka oranžového ABS a klíčenka, každá jako odčítání (máte, odebere se, zbude), jeden díl, který je třeba vytisknout, protože už žádný nezbyl, a volby Odebrat ze skladu a Neodebírat ze skladu](/blog/media/2026-11-23-como-se-mueve-el-inventario/08-stock-del-pedido-en.png "80%")

Když nemáte dost, BolloPrint odebere, co je (nikdy nenechá sklad v mínusu),
a řekne vám, co chybí: díl **je potřeba vytisknout** a materiál **je potřeba
koupit**. Nic vás nezablokuje. A když položka odejde celá ze skladové zásoby,
označí se jako **vytištěná**, protože už ji tisknout nemusíte.

Dále:

- **Nabídka** se skladu nedotkne, dokud ji nepřijmete.
- Když objednávku **zrušíte**, vrátí se na sklad jen to, co z něj kvůli ní odešlo.
- Sklad **nikdy nemění stav objednávky**: o tom, kdy je „Připraveno k odeslání“,
  rozhodujete vy, protože ji možná ještě musíte zabalit.

## Objednávky z Etsy a dalších marketplaců

Objednávka, která přijde sama z vašeho obchodu, nemá koho se zeptat, a tak dorazí
se stavem **sklad čeká na rozhodnutí**. Když ji poprvé otevřete, BolloPrint se vás
zeptá, co se skladem udělat. A když ji kupující na marketplacu zruší, co se
odebralo, vrátí se samo.

## V pokladně

V **Pokladně** se nic neptá: zaplacení už je rozhodnutí. Co prodáte, odejde ze
skladu, a když prodej stornujete, vrátí se to. Víc v nápovědě
[Pokladna](/help/punto-de-venta).

## Co si berete na akci

Když jedete na trh nebo na akci pro makery, při vytváření akce v sekci **Akce**
určíte, **co si berete**: díly ze skladové zásoby a materiál ze skladu. Při
uložení vám BolloPrint ukáže, co odchází ze skladové zásoby a co je třeba
vytisknout, stejně jako u objednávky. To, co si berete, se přestane počítat do
vašeho skladu a zůstane uložené v zásobě akce. Co ve skladové zásobě nemáte,
se považuje za vytištěné speciálně pro tuto příležitost.

- Co **na akci prodáte** v pokladně, odečte se z toho, co jste si vzali, ne znovu
  z vašeho skladu.
- Při **uzavření akce** zadáte, co se vrací: co zbylo, **se vrátí na sklad**,
  a co se nevrací (něco rozbitého, něco darovaného), se počítá jako **ztráta
  akce**, v nákladové ceně.
- Uzavření vám také řekne, jestli **jste prodali produkty, které jste si
  nevzali**, třeba zakázku, kterou předáte později.

![Co si berete u uzavřené akce: u každého dílu kolik jste si vzali, kolik jste prodali, kolik se vrátilo a kolik ne](/blog/media/2026-11-23-como-se-mueve-el-inventario/09-que-te-llevas-en.png)

:::info 💡 Vytiskli jste to speciálně pro akci?
Zvolte **Nesahat na zásoby**: co si vezmete, se ze skladu neodebere, a co zbude,
se při uzavření přičte.
:::

Krok za krokem v nápovědě k akcím:
[Co si berete](/help/eventos#co-si-berete) a
[Uzavření akce](/help/eventos#uzavření-akce).

## Všechno se zapisuje do Historie

Každá změna skladu se zapíše do **Sklad materiálu → Historie**: kdy, co, proč
(objednávka, pokladna, akce, ruční změna), kolik a kdo ji provedl. V nabídce **⋯**
u každého řádku vám **Zobrazit historii** ukáže jen změny daného materiálu nebo
dílu. Víc v nápovědě k
[Historii](/help/inventario#historie).

Nákupy se zapisují ručně, tlačítkem **+** u řádku nebo přes „Přidat z fotky“.
Výdaj ve **Financích** sklad nemění: tak se stejná cívka nezapočítá dvakrát.

## Začněte s aktuálním skladem

Všechno tohle funguje nejlépe, když to, co je v BolloPrintu, odpovídá tomu, co
máte v regálech. Pokud jste ještě nezadali své cívky a pryskyřice, udělejte to
pár fotkami štítků: víc v článku
[Spravujte sklad fotoaparátem v mobilu](/blog/filament-inventory-from-a-photo).
Od té chvíle ho za vás udržují aktuální vaše objednávky, pokladna a akce.

![Bollo, maskot BolloPrintu, s dílenskými brýlemi, mezi krabicemi, cívkami filamentu, lahvemi pryskyřice a regály s vytištěnými díly](/blog/media/2026-11-23-como-se-mueve-el-inventario/11-bollo.jpg "60%")

## Související dokumentace

- [Sklad materiálu](/help/inventario): filament, pryskyřice, spotřební materiál a skladová zásoba
- [Materiál na prodej](/help/material-a-la-venta): prodej cívek a spotřebního materiálu
- [Detail objednávky](/help/detalles-de-un-pedido): položky a sklad
- [Objednávky z marketplaců](/help/pedidos-de-marketplaces): objednávky, které přicházejí samy
- [Pokladna](/help/punto-de-venta): prodej osobně
- [Akce](/help/eventos): příprava, prodej a uzavření akce
