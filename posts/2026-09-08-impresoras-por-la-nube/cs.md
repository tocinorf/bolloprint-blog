---
slug: connect-bambu-lab-printers-cloud
title: "Připojte tiskárny Bambu Lab k BolloPrint za pět minut"
description: Bez instalace a bez hesla. Zadáte e-mail svého účtu Bambu Lab, potvrdíte kód a vaše tiskárny se objeví samy, i s tím, co právě tisknou, a s celou svou historií.
date: 2026-10-12
updated: 2026-10-16
tags: [návody]
cover: 01-portada.webp
---

Pokud vám pracuje několik tiskáren Bambu, nejspíš ten koloběh znáte: chcete-li
vědět, jak jsou na tom, musíte za každou dojít a podívat se na její displej.
Dotiskla už první? Má ta druhá ještě materiál? Kolik hodin tisku máte za tento měsíc?

To všechno můžete mít na jedné obrazovce a **bez instalace čehokoli**. Připojíte
svůj účet Bambu Lab k BolloPrint a vaše tiskárny se objeví samy. Zabere to asi
pět minut.

::animation{id="bambu-cloud"}

## Co uvidíte u každé tiskárny

V reálném čase a bez jakéhokoli zásahu z vaší strany:

- jestli je zapnutá a připojená;
- co tiskne, kolik **procent** má hotovo a kolik jí zbývá;
- teplotu trysky a podložky;
- zavedené **materiály**, slot po slotu, pokud máte AMS;
- upozornění samotného stroje.

A co nejvíc oceníte na konci měsíce: **každý tisk se zaznamená**, včetně doby
trvání, materiálu a nákladů. Nemusíte si nic zapisovat.

![Karta tiskárny během tisku s průběhem a teplotami](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora-en.png "42%")

## Co budete potřebovat

Než začnete, připravte si tyto tři věci:

- Přístup do BolloPrint s rolí **Vlastník** nebo **Administrátor**. S jinou rolí
  se tato obrazovka nezobrazí.
- **E-mail** svého účtu Bambu Lab. Heslo není potřeba.
- Tento **e-mail** otevřený: Bambu vám na něj pošle kód.

## Otevřete obrazovku tiskáren

Všechno se dělá na jednom místě: **Nastavení → Tiskárny**. Tam uvidíte tři karty:

- **Tiskárny**: seznam všech vašich strojů, ať jsou připojené jakkoli.
- **Místní agent**: pro připojení přes vaši vlastní síť. Vysvětlujeme ho
  v [jiném článku](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: ta, kterou teď potřebujete.

Otevřete **Bambu Cloud**.

![Obrazovka Nastavení → Tiskárny se třemi kartami](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas-en.png)

## Zadejte e-mail svého účtu Bambu

Použijte e-mail svého účtu Bambu Lab (právě ten, ne jinou svou adresu)
a klikněte na **Poslat kód**.

![Formulář Bambu Cloud s vyplněným e-mailem účtu a tlačítkem Poslat kód](/blog/media/2026-09-08-impresoras-por-la-nube/03-correo-en.png)

:::info 💡 Heslo po vás nechceme
BolloPrint ho **nikdy nevidí ani neukládá**: k připojení stačí kód, který vám
Bambu pošle e-mailem.
:::

## Potvrďte kód z e-mailu

Bambu vám pošle **šestimístný kód** z adresy `noreply@bambulab.com` (e-mail
přijde v angličtině). Pokud ho nevidíte, **podívejte se do složky se spamem**:
často skončí tam. Zadejte ho na stejné obrazovce a klikněte na **Ověřit
a připojit**.

![Pole pro šestimístný kód a tlačítko Ověřit a připojit](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-en.png)

Tři drobnosti, díky kterým to nebudete muset zkoušet dvakrát:

- Kód **vyprší po 10 minutách** a platí jen ten poslední. Pokud to nestihnete,
  klikněte na **Znovu poslat kód**.
- Můžete ho **vložit přesně tak, jak přišel**: mezery a pomlčky se odstraní samy.
- Pokud jde o špatný e-mail, klikněte na **Změnit e-mail**.

Když kód projde, uvidíte **Účet ověřen a připojen**.

## Vaše tiskárny už jsou uvnitř

Není potřeba je přidávat jednu po druhé: **všechny tiskárny z daného účtu se
objeví samy** na kartě **Tiskárny**, každá se svým názvem a sériovým číslem.

![Seznam tiskáren s právě objevenými stroji Bambu](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas-en.png)

Nahoře uvidíte počítadlo jako `Aktivní: 3 / 6`: to jsou tiskárny, které zahrnuje
váš tarif. Přepínačem v každém řádku aktivujete nebo deaktivujete ty, které
chcete. Deaktivovaná tiskárna se do limitu nepočítá, ale **zachová si celou svou
historii**. A pokud připojíte celou flotilu a místa pro všechny nejsou, ty, které
se nevejdou, se přidají deaktivované, místo aby překročily limit vašeho tarifu.

## Co přes cloud udělat nejde

Je dobré to vědět hned od začátku, ať nehledáte možnosti, které neexistují:

- **Je to jen pro čtení.** Přes cloud nelze z BolloPrint tisk pozastavit, obnovit
  ani zrušit: Bambu tyto příkazy přijímá jen přes vaši místní síť a s tiskárnou
  v určitém režimu. Podíváme se na to na konci.
- **Kamera není k dispozici.** Vidíte ale náhled tiskové úlohy ze sliceru, což je
  náhled, ne to, co se děje uvnitř stroje.
- **Závisí na dvou připojeních k internetu**, na vašem a na tom Bambu. Pokud
  selže kterékoli z nich, tiskárna se zobrazí jako odpojená, i když normálně
  tiskne.
- **Přihlášení k Bambu platí 90 dní, ale obnovuje se samo**: BolloPrint ho
  obnoví dřív, než vyprší, a nemusíte se přihlašovat znovu. Jen pokud ho Bambu
  ukončí ze své strany, upozorníme vás na obrazovce a stačí si vyžádat nový kód.

A ještě něco, co platí pro jakýkoli způsob připojení: **BolloPrint neposílá
úlohy k tisku**. Soubor dál posíláte ze svého sliceru; BolloPrint čte, co stroj
dělá, a zaznamenává to.

## Časté problémy

### Co když se do Bambu přihlašuji přes Google nebo Apple?

Zadejte e-mail daného účtu Google nebo Apple: kód na něj přijde stejně. Heslo už
vytvářet nemusíte.

### Proč se píše, že s tímto e-mailem neexistuje žádný účet?

Pokud se zobrazí **„S tímto e-mailem neexistuje žádný účet Bambu Lab“**, nejde
o e-mail vašeho účtu Bambu: Bambu kód pošle i tak, ale po jeho zadání ho odmítne.
Zkontrolujte, kterým e-mailem se přihlašujete do jejich aplikace, a klikněte na
**Změnit e-mail**.

### Musím účet čas od času připojovat znovu?

Ne. Přihlášení platí 90 dní a BolloPrint ho obnoví samo dřív, než vyprší. Pokud
ho Bambu někdy ukončí ze své strany, uvidíte **„Přihlášení vypršelo“** a tlačítko **Znovu
se přihlásit**: vyžádáte si nový kód a je hotovo, bez odpojování čehokoli.

### Co dělat, když kód nepřijde nebo ho systém nepřijme?

Pokud nepřijde, podívejte se do složky se spamem a klikněte na **Znovu poslat
kód**. Pokud ho systém nepřijme, nejspíš vypršel nebo nejde o poslední vyžádaný
kód: vyžádejte si nový a vložte ho celý.

## Pokud potřebujete víc: místní agent

Cloud vám ukáže všechny informace, ale neumožňuje tiskárny ovládat a existuje
jen pro Bambu Lab. Pokud potřebujete víc, řešením je **místní agent**: malý
program, který nainstalujete na počítač ve své dílně a který s tiskárnami
komunikuje přes vaši vlastní síť. Jeden stačí pro celou flotilu a nabízí:

- **téměř všechny značky**: Prusa, Elegoo, Anycubic, FlashForge, Snapmaker a
  všechny, na kterých běží Klipper (QIDI, Sovol, Voron…);
- **kameru**, živě a se závěrečným snímkem uloženým u každého tisku;
- **pozastavení, obnovení a zrušení tisku** z BolloPrint, bez chození ke stroji;
- **odolnost vůči výpadkům internetu**: dál čte stav vašich tiskáren a všechno
  odešle, jakmile se připojení obnoví.

:::info 💡 Jak posílat příkazy tiskárně Bambu
Tiskárna musí být v **režimu LAN** a v **režimu pro vývojáře**. Oba se zapínají
na jejím displeji a ten druhý ji odpojí od Bambu Cloud: od té chvíle ji uvidíte
už jen přes agenta.
:::

Postup krok za krokem popisujeme v článku
[připojte tiskárny přes vlastní síť](/blog/connect-printers-local-network-agent).

S jakýmkoli dotazem nám napište přes [kontaktní stránku](/contact) nebo na
[náš Discord](/help/soporte-por-discord).

Užijte si všechny své tiskárny na jedné obrazovce.

![Bollo, maskot BolloPrint, v dílenských brýlích sní o 3D tiskárně](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp "60%")

## Související dokumentace

- [Připojení tiskáren](/help/conectar-impresoras): dva způsoby připojení a který se vám hodí
- [Tiskárny přes cloud](/help/impresoras-por-la-nube): kompletní referenční popis této obrazovky
- [Kompatibilní tiskárny](/help/impresoras-compatibles): tady najdete svůj model
- [Typy připojení](/help/tipos-de-conexion): co umožňuje který typ tiskárny
