---
slug: organize-your-3d-printing-catalog
title: "Od plików STL do produktów w twoim sklepie: jak uporządkować katalog druku 3D"
description: Dowiedz się, jak uporządkować pliki STL, liczyć koszt każdej części i tworzyć warianty produktów do swojego sklepu z drukiem 3D bez komplikacji.
date: 2026-10-18
tags: [poradniki]
cover: 01-portada.webp
---

Jeśli drukujesz w 3D na sprzedaż, na pewno znasz ten obrazek: dziesiątki
folderów na komputerze z plikami o nazwach w stylu `llavero_V2_FINAL_definitivo.stl`,
i ani śladu pamięci o tym, ile filamentu zużywała ta wersja ani jakiego profilu
slicera użyłeś. A gdy na Etsy wpada zamówienie, liczysz koszty na oko i masz
nadzieję, że nie stracisz.

W warsztacie czy na farmie druku 3D bałagan techniczny i handlowy mieszają się
ze sobą, jeśli ich nie rozdzielisz. Dlatego BolloPrint traktuje je osobno. W tym
przewodniku wyjaśniamy, jak łączą się ze sobą **Projekty, Części, Produkty i
Warianty**, żebyś przeszedł od sterty luźnych plików do uporządkowanego katalogu.

::animation{id="how-it-works"}

## Oddziel to, co techniczne, od tego, co handlowe

Jeden z najczęstszych błędów w prowadzeniu warsztatu to traktowanie pliku STL
tak, jakby był produktem, który sprzedajesz. W praktyce ten sam model 3D można
wydrukować z różnych materiałów, może składać się z kilku elementów albo być
sprzedawany w zestawach.

Dlatego BolloPrint układa twój katalog na trzech poziomach.

### Projekty: biblioteka techniczna

**Projekt** to pojemnik na twoje pliki źródłowe: STL, OBJ albo projekty 3MF,
razem ze zdjęciami modelu i twoimi notatkami wewnętrznymi.

- **Traktuj Projekt jak plan albo pomysł.** Nie ma w nim czasu druku ani gramów
  filamentu, bo ten sam STL można wydrukować w różnych skalach albo z różnych
  materiałów.

![Projekt „Keyring BolloPrint” z plikiem STL, zdjęciem, notatkami wewnętrznymi i dwiema częściami: 5 cm i 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Części: fizyczny obiekt

**Część** to efekt wzięcia Projektu i nadania mu konkretnych ustawień druku:
materiału i jego zużycia (na przykład czarny PLA), wymiarów i czasu druku.

- **Jeden Projekt, kilka Części.** Z tego samego STL możesz wydrukować figurkę w
  dwóch rozmiarach, 5 cm i 10 cm: ten Projekt będzie miał dwie Części, „Mały
  brelok” i „Duży brelok”. To samo dotyczy różnych kolorów czy materiałów.
- **Twój plik ze slicera robi rachunki za ciebie.** Jeśli wgrasz do Części plik
  ze slicera (`.gcode`, `.gcode.3mf`, `.bgcode` albo `.goo` w przypadku żywicy),
  BolloPrint odczyta wagę i czas druku i ci je zaproponuje. Gdy je zastosujesz,
  obliczy, ile kosztuje cię wyprodukowanie dokładnie tej części. Dane możesz też
  wpisać albo poprawić ręcznie.

:::info 💡 Projekt 3MF się tu nie nada
Slicer musi pociąć płytę, żeby znać wagę i czas druku. Plik projektu `.3mf` ich
nie zawiera: jego miejsce jest w Projekcie. Do Części wgraj `.gcode.3mf`
wyeksportowany ze slicera.
:::

### Produkty i Warianty: to, co widzi i kupuje twój klient

**Produkt** to twoja witryna: to, co publikujesz w swoim sklepie albo na
marketplace takim jak Etsy. **Wariant** to konkretna opcja, którą wybiera klient.

- **Wariant może mieć jedną albo kilka Części**, każdą w swojej ilości.
- **Na przykład:** twój Produkt to „Figurka Bollo”, naszego psa. Jeden Wariant
  może być „Zielony”, drugi „Pomarańczowy”, a kolejny to zestaw „Zielony +
  Pomarańczowy” z obiema Częściami w środku. Materiały, rozmiary, wykończenia
  czy zestawy możesz łączyć, jak chcesz.

![Wariant Green+Orange z dwiema częściami w środku, pomarańczową i zieloną, oraz jego koszt, marża i cena](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

:::info 💡 Zestaw może łączyć różne Projekty
Wariant może zawierać Części z różnych Projektów: na przykład zestaw „Witaj w
BolloPrint” z brelokiem i figurką Bollo.
:::

- **Marża liczy się sama.** Ponieważ każdy Wariant wie, z jakich Części się
  składa, BolloPrint porównuje twoją cenę sprzedaży z rzeczywistym kosztem
  produkcji i pokazuje ci marżę. Jeśli zmienisz cenę, marża się zaktualizuje, i
  odwrotnie.

![Wariant Green z jedną częścią: koszt 7,06 €, marża 70% i cena 23,54 €](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## Spieszysz się? Użyj Szybkiego tworzenia

Jeśli dopiero zaczynasz albo masz do wgrania setki modeli, ustawianie Projektów,
Części i Produktów jeden po drugim zajmuje sporo czasu.

Do tego służy przycisk **Szybkie tworzenie** w katalogu. Na jednym ekranie
wgrywasz plik 3D, podajesz materiał, wagę, czas i cenę, a BolloPrint za jednym
razem tworzy Projekt, Część, Produkt i jego Wariant. Efekt jest taki sam, jak
gdybyś robił to krok po kroku, więc później możesz dopracować, co tylko chcesz.

![Formularz Szybkiego tworzenia: plik 3D, zdjęcia, materiał, waga, czas, kolory, koszt i cena](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## Twoje tagi same przechodzą do produktu

Kolejny szczegół, który oszczędza ci pracy: **tagi** Projektu same przechodzą do
jego Produktów.

Jeśli oznaczysz Projekt tagiem „Breloki” albo „Figurki”, to gdy dodasz jego
Części do Wariantu, te tagi zostaną dodane do Produktu. A jeśli sprzedajesz na
Etsy, przy publikowaniu oferty pojawią się już wpisane jako *tagi* Etsy, które
pomagają klientom cię znaleźć. Etsy przyjmuje ich do 13, każdy maksymalnie po 20
znaków, i przed publikacją możesz je poprawić.

## Zacznij porządkować swój katalog

Dobrze uporządkowany katalog to nie tylko kwestia porządku: to sposób, żeby
wiedzieć, ile kosztuje cię każda część, ile zarabiasz na każdym zamówieniu, i
rozwijać warsztat, nie tracąc nad nim kontroli.

Jeśli chcesz dokładniej zobaczyć, jak skonfigurować katalog albo tworzyć bardziej
zaawansowane warianty, zajrzyj do
[dokumentacji katalogu](/help/catalogo). A jeśli zastanawiasz się, skąd bierze
się koszt każdej Części, opisujemy to w artykule
[ile naprawdę kosztuje wydrukowana część](/blog/calculate-your-3d-printing-costs).

Zobacz, [jak kontrolować produkcję w swoim warsztacie z BolloPrint](/features),
oprogramowaniem dla farm druku 3D.

Niech twój katalog rośnie tak uporządkowany, jak zaczyna.

![Bollo, maskotka BolloPrint, w okularach warsztatowych, obok swojego modelu 3D w postaci siatki](/blog/media/2026-10-15-organizar-catalogo/07-bollo.webp "60%")

## Powiązana dokumentacja

- [Katalog](/help/catalogo): poziomy katalogu w pełnym opisie
- [Projekty](/help/disenos): pliki, zdjęcia i tagi
- [Części](/help/piezas): materiał, plik ze slicera i koszt
- [Produkty i Warianty](/help/productos-y-variantes): cena, marża i części każdego wariantu
- [Szybkie tworzenie](/help/creacion-rapida): wszystko za jednym razem
- [Tagi](/help/etiquetas): jak je tworzyć i nimi zarządzać
