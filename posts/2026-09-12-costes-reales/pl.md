---
slug: calculate-your-3d-printing-costs
title: "Ile naprawdę kosztuje wydrukowana część (i jak to policzyć bez komplikacji)"
description: Ta część za 1,60 € filamentu kosztuje cię 9,36 €. Pokażemy ci, jak rozłożyć wydatki warsztatu na godziny druku, żeby BolloPrint sam doliczał je do każdej części.
date: 2026-10-15
updated: 2026-10-16
tags: [poradniki]
cover: 01-portada.webp
---

Część drukowana 6 godzin, 80 gramów PLA. Ile cię kosztuje?

Jeśli pomyślałeś „80 gramów po 20 € za kilogram, **1,60 €**”, policzyłeś tylko
**materiał**. W zwykłym warsztacie to **niewielka część** tego, ile ta część
naprawdę cię kosztuje.

W warsztacie z trzema drukarkami, przy części pomalowanej i zapakowanej, pełny
rachunek wygląda tak:

| | |
|---|---|
| Materiał | 1,60 € |
| 6 godzin pracy drukarki | 5,16 € |
| Wykończenie (malowanie) | 2,00 € |
| Koszty dodatkowe (opakowanie) | 0,60 € |
| **Rzeczywisty koszt części** | **9,36 €** |

**Prawie sześć razy więcej.** Ta różnica to nie zaokrąglenie: to czynsz, prąd,
zużycie drukarek, biuro rachunkowe i wydruki, które się nie udają. Za to
wszystko płacisz; pytanie tylko, czy doliczasz to do ceny.

Tutaj zobaczysz, jak przenieść te wydatki na koszt każdej części. **Ustawiasz to
raz**, a potem BolloPrint sam stosuje to do każdej części, którą utworzysz.

::animation{id="part-cost"}

## Skąd się bierze te 5,16 €

Pomysł jest prosty: sumujesz **wszystko, co warsztat kosztuje cię miesięcznie**,
i dzielisz to przez **godziny, w których naprawdę drukujesz**. Tak dostajesz
koszt **jednej godziny pracy drukarki** i zostaje tylko pomnożyć go przez
godziny danej części.

Na liczbach z przykładu:

- **Godziny:** trzy drukarki, dziesięć godzin dziennie, dwadzieścia pięć dni w
  miesiącu → **750 godzin**.
- **Wydatki:** czynsz, biuro rachunkowe, oprogramowanie i amortyzacja maszyn to
  razem około **516 € miesięcznie**. Po rozłożeniu: 0,69 € za godzinę. Z prądem
  **koszty stałe na godzinę** wynoszą **0,72 €**.
- **Narzuty:** 5% na konserwację, 10% na wydruki nieudane i 5% rezerwy
  podnoszą to do **0,86 € za godzinę**. Za sześć godzin: 5,16 €.

Dokładnie taki rachunek robi sekcja **Koszty** w BolloPrint, w
**Ustawienia → Koszty**. Widzą ją tylko **Właściciel** i osoby z rolą **Admin**.

![Sekcja Koszty w Ustawieniach](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

Jeśli dopiero zaczynasz, zadanie **Oblicz, ile kosztuje cię każda część** w
**Pierwszych krokach**, na ekranie **Start**, przeprowadzi cię przez te same
ekrany, jeden po drugim, i oznaczy każdy na zielono, gdy tylko go zapiszesz.

## Godziny, w których naprawdę drukujesz

Zacznij od godzin: to liczba, którą najwięcej osób liczy źle, i ta, która
najbardziej zmienia wynik. Znajdziesz ją w **Koszt godzinowy → Godziny druku** i
składa się z trzech pól:

**Drukarki × Godziny / dzień × Dni / miesiąc**

Wpisz **to, co dzieje się naprawdę, a nie teoretyczne maksimum**. Jeśli masz
trzy drukarki, ale średnio pracują osiem godzin dziennie, to wpisujesz osiem. Nie
dwadzieścia cztery.

Kusi, żeby wpisać dużą liczbę, bo im jest wyższa, tym tańsza wychodzi godzina.
Ale wydatki i tak płacisz, a to, czego nie rozłożysz na części, zapłacisz sam na
koniec miesiąca.

![Zakładka Godziny druku z trzema polami i wynikiem](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Ile kosztuje cię warsztat

Gdy masz już godziny, czas zapisać wydatki. Dodajesz je w zakładce **Koszty
stałe**; BolloPrint porządkuje je według typu i o każdy pyta tylko o to, czego
potrzebuje:

| Typ | Co wpisujesz |
|---|---|
| **Koszt stały** | Czynsz, internet, biuro rachunkowe, ubezpieczenia… kwota miesięczna |
| **Drukarka** | Ile cię kosztowała i przez ile lat ją amortyzujesz |
| **Oprogramowanie** | Subskrypcja slicera, BolloPrint i czegokolwiek, z czego korzystasz |
| **Wynagrodzenia** | Pensja i liczba osób |
| **Energia elektryczna** | Ile kW pobiera drukarka i ile płacisz za kWh |

Nie musi się zgadzać co do grosza: rozsądna liczba dziś jest warta więcej niż
idealna za rok.

:::warning ⚠️ Nie wpisuj tego samego wydatku dwa razy
Kwoty **miesięczne** opisują **cały warsztat**: czynsz wpisujesz tylko raz.
Kwoty **na godzinę druku** — jak prąd liczony według zużycia — opisują **jedną
drukarkę**: wpisz tam zużycie przeciętnej maszyny, a nie całej hali.
:::

Na samym dole masz gotowy rachunek, ten sam co na początku:

> **wydatki miesięczne ÷ twoje godziny druku = koszt jednej godziny „na czysto”**

To twoje **koszty stałe na godzinę**: w przykładzie 0,72 €.

![Wydatki warsztatu w zakładce Koszty stałe, pogrupowane według typu, i rachunek dający 0,72 € za godzinę](/blog/media/2026-09-12-costes-reales/03b-gastos-fijos.png)

## To, co i tak się wydarzy

Koszty stałe nie obejmują tego, co dzieje się bez stałej faktury: dysze się
psują, a **niektóre wydruki się nie udają i trzeba je powtórzyć**.

Do tego służy zakładka **Koszt godzinowy**, która dolicza do kosztów stałych na
godzinę kilka procentów: konserwację, nieudane wydruki i rezerwę na
nieprzewidziane wydatki.

Odsetek nieudanych wydruków jest najważniejszy i najczęściej pomijany. Jeśli z
dziesięciu części jedna ląduje w koszu, **dziewięć dobrych płaci za tę złą**.
Jeśli nie uwzględnisz go tutaj, zapłacisz za nią sam.

Wynik to twój **koszt godzinowy**: w przykładzie 0,86 €. To twoja prawdziwa
liczba i to ona jest doliczana do każdej części.

:::info 💡 Marża zysku nie należy do tego miejsca
Tutaj wpisujesz tylko **koszty**. Ile chcesz zarobić, decydujesz później, w
produkcie, bo to decyzja handlowa.
:::

![Narzuty na konserwację, nieudane wydruki i rezerwę na nieprzewidziane wydatki, doliczane do kosztów stałych na godzinę, aż do 0,86 € za godzinę](/blog/media/2026-09-12-costes-reales/03c-coste-por-hora.png)

## Materiał i dodatki

Zostaje najprostsza część, w **Wartościach domyślnych**:

- **Cena każdego materiału** za kilogram. Jest **według rodzaju**, a nie
  rodziny: PLA i TPU nie kosztują tyle samo.
- **Wykończenia**: ile doliczasz, jeśli część przechodzi obróbkę końcową albo
  jest malowana.
- **Koszty dodatkowe**: opakowanie, śruby i elementy złączne, magnesy, inserty,
  robocizna. Przy każdym wybierasz, czy naliczasz go **na sztukę**, czy **na
  płytę**.
- **Marże**: domyślna, której chcesz, oraz progi procentowe, od których
  ostrzegamy cię na czerwono lub na pomarańczowo.

:::info 💡 Jeśli masz materiał w magazynie, liczy się magazyn
Te ceny są orientacyjne, na wypadek gdy nic za nimi nie stoi. Jeśli część
powstaje ze szpuli dodanej do magazynu z jej rzeczywistym kosztem, używamy tego
kosztu.
:::

![Wartości domyślne: marże z kolorowymi ostrzeżeniami i cena każdego materiału za kilogram](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## I tak trafia to do twojej części

Cztery poprzednie kroki dają jedną liczbę: **koszt jednej godziny pracy
drukarki**. Od tej chwili każda część to suma:

> jej **godziny × twój koszt godzinowy**
> **+** **materiał**, który zużywa
> **+** **wykończenie**, jeśli przechodzi obróbkę końcową albo jest malowana
> **+** **koszty dodatkowe**, które do niej dodasz

Warto zrozumieć jeden szczegół, bo wyjaśnia, dlaczego opłaca się zapełniać
stół: **rachunek robi się na płytę, a nie na część**. BolloPrint liczy, ile
kosztuje cała płyta, i **rozkłada to na części, które z niej wychodzą**. Dlatego
z kosztów dodatkowych te oznaczone **na płytę** naliczane są tylko raz —
niezależnie od tego, czy drukujesz części po jednej, czy po dwadzieścia — a te
**na sztukę** naliczane są przy każdej części.

Poza tym każda część **zapamiętuje koszt godzinowy, z którym ją obliczono**. To
celowe: dzięki temu koszt tego, co wydrukowałeś w zeszłym roku, pozostaje taki,
jaki był wtedy. Dlatego istnieje przycisk **Przelicz**, który zobaczysz trochę
niżej.

## Teraz masz już swoją liczbę

Żeby zobaczyć wynik, przejdź do **Koszty → Podsumowanie**. Blok **Przykład**
bierze przykładową płytę i pokazuje cały rachunek **na twoich wartościach**: ile
to materiał, ile druk, ile wykończenie i ile kosztuje część.

![Blok Przykład z pełnym rozbiciem kosztu części](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Gdy zmienią się twoje wydatki

Twoje liczby nie zawsze będą takie same: prąd drożeje, kupujesz kolejną drukarkę
albo zmieniasz lokal. Gdy je zaktualizujesz, **części, które już masz, nie
zmienią się same**. To celowe: każda część zapamiętuje koszt, z jakim ją
obliczono, a raczej nie chciałbyś, żeby nadpisał się koszt wszystkiego, co
zrobiłeś w zeszłym roku.

Kiedy zechcesz zastosować zmiany do wszystkiego, w **Podsumowaniu** masz licznik
części **do przeliczenia** i przycisk **Przelicz**. Ty decydujesz kiedy.

:::info 💡 Nie rusza twoich cen sprzedaży
Przeliczenie aktualizuje **koszt** i cenę *sugerowaną*. Cena, którą ustawiłeś
ręcznie, zostaje. Zmieniać się będzie wskaźnik **marży**.
:::

## Kupić kolejną drukarkę?

Mając skonfigurowane koszty, możesz odpowiedzieć na to pytanie liczbami. W
**Scenariuszach kosztów** zmieniasz liczbę drukarek, godziny albo dni i widzisz,
co stałoby się z twoim kosztem godzinowym. To tylko symulacja: niczego nie
zmienia w twoich ustawieniach.

Najwięcej pokazuje to, że **krzywa przestaje spadać**. Przejście z jednej
drukarki na pięć dzieli koszt godzinowy prawie przez pięć. Przejście z
dwudziestu na sto prawie go nie rusza, bo są wydatki — jak prąd — które płacisz
za każdą godzinę druku i których nie da się na nikogo rozłożyć.

![Scenariusze kosztów z krzywą kosztu godzinowego](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Konfiguracja to cztery ekrany i chwila jednego popołudnia. W zamian każda
część, którą utworzysz, będzie miała swój rzeczywisty koszt, a ty będziesz
wiedzieć, czy zarabiasz, bez liczenia na piechotę.

:::info 💡 Pomóc ci z liczbami?
Jeśli nie wiesz, od czego zacząć, napisz do nas przez [stronę kontaktową](/contact)
albo na [naszym Discordzie](/help/soporte-por-discord). Robiliśmy to już
niejeden raz.
:::

Niech twoje liczby zawsze się zgadzają.

![Bollo, maskotka BolloPrint, w okularach warsztatowych, zamyślony wśród obliczeń zapisanych kredą](/blog/media/2026-09-12-costes-reales/07-bollo.webp "60%")

## Powiązana dokumentacja

- [Koszty](/help/costes): pełny opis sekcji
- [Części](/help/piezas): jak obliczany jest koszt każdej części
- [Produkty i Warianty](/help/productos-y-variantes): od kosztu do ceny sprzedaży
- [Magazyn materiałów](/help/inventario): żeby materiał był liczony po jego rzeczywistym koszcie
