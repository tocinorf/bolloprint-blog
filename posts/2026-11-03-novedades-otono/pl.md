---
slug: whats-new-september-november-2026
title: "BolloPrint się zmienia! Nowości, które pomagają w Twoim warsztacie druku 3D"
description: "Wszystkie nowości w BolloPrint od 14 września do 3 listopada 2026: od agenta lokalnego bez kontenerów po faktury zgodne z prawem i zupełnie nowe Finanse."
date: 2026-11-03
tags: [nowości]
cover: 01-bollo.webp
---

Od połowy września opublikowaliśmy **41 aktualizacji** BolloPrint. Niektóre to duże
i ważne zmiany. Inne to drobne ulepszenia, dzięki którym Twoja codzienna praca jest
wygodniejsza. Oto najważniejsze.

![W siedem tygodni: ponad 400 odczuwalnych ulepszeń, ponad 250 zmian na ekranie, około 190 poprawionych błędów, 11 krajów z fakturami zgodnymi z prawem, 9 języków w aplikacji i 102 drukarki 15 marek](/blog/media/2026-11-03-novedades-otono/02-cifras-pl.webp)

## Zaczynamy od najciekawszego: tego, co zmienia sposób, w jaki pracujesz

### 1. Agent lokalny, teraz bez znajomości kontenerów

Wiemy, że Docker potrafi być skomplikowany. Dlatego teraz jest prościej. Zainstaluj
agenta na tym, co już masz: na swoim NAS-ie, komputerze w warsztacie albo w Home
Assistant.

![Logo Synology, QNAP, Windows, Home Assistant i TrueNAS](/blog/media/2026-11-03-novedades-otono/03-agentes.webp)

| Gdzie | Jak go zainstalować |
|---|---|
| **Synology i QNAP** | Pobierz pakiet dla swojego NAS-a i zainstaluj go ręcznie z jego centrum pakietów. |
| **Windows** | Instalator na komputer w warsztacie. |
| **Home Assistant** | Przycisk „Dodaj do Home Assistant” i gotowe. |
| **TrueNAS** | Wklejasz w jego aplikacjach konfigurację, którą Ci podajemy. |

Potem otwierasz jego stronę i klikasz **„Powiąż z BolloPrint”**: właściciel
warsztatu potwierdza to jednym kliknięciem, bez przepisywania kodów. Jak każdy
agent, aktualizuje się sam. Docker i Kubernetes działają dalej jak zawsze.

:::info
Znajdziesz go w **Ustawienia → Drukarki → Agent lokalny → „Nowy agent”**.
[Jak zainstalować agenta](/help/el-agente-local)
:::

---

### 2. Twoje drukarki, lepiej widoczne i dokładniej policzone

- **Kamera na żywo** i zdjęcie końcowe każdego wydruku w jego historii.
- **Każdy wydruk mówi wszystko**: ile trwał w porównaniu z szacunkiem, każda szpula z jej slotem AMS i nazwa modelu z MakerWorld z linkiem.
- **Rzeczywiste zużycie**: nieudany lub anulowany wydruk nie jest już liczony w całości, a wydruki z żywicy zapisują swoje mililitry.
- **Bambu Lab**, przez chmurę bez hasła (Twój e-mail i kod, a sesja odnawia się sama) i przez sieć lokalną z wstrzymywaniem, wznawianiem i anulowaniem z BolloPrint, przy włączonym trybie dewelopera.
- **Dodaj po IP** to teraz kreator dla każdej marki; nie musisz już wiedzieć, jakim „protokołem” mówi Twoja maszyna.
- **Agent lokalny aktualizuje się sam**, nigdy w trakcie wydruku, a każda marka drukarek ulepsza się osobno.
- Dołączają **Anycubic** (Kobra 3, S1, 4 i X) oraz **Creality** z fabrycznym firmware'em (K1, K2, Ender-3 V3 i Hi), w wersji beta.

[Zobacz zgodne drukarki](/help/impresoras-compatibles)

---

### 3. Inteligentna migracja

Przenieś klientów, projekty, części, produkty, zamówienia, wyceny i stany
magazynowe z folderów i arkuszy kalkulacyjnych na swoim komputerze. BolloPrint
czyta to, co przynosisz, i proponuje, jak to dopasować; Ty sprawdzasz wszystko,
zanim cokolwiek zostanie dodane, a jeśli się pomylisz, można to cofnąć.

:::warning
To trzy kroki: **Przygotuj · Zrozum · Migruj**. Od planu Pro, w Chrome lub Edge na
komputerze. W planach Max i Business, jeśli wolisz, zrobimy to za Ciebie.
:::

---

### 4. Faktury zgodne z prawem prosto z zamówienia

Wystaw fakturę do zamówienia bez wychodzenia z BolloPrint: z jej numeracją,
podatkiem i Twoim logo. Przed wystawieniem widzisz fakturę **dokładnie tak, jak
wyjdzie**, a jeśli czegoś brakuje, mówimy Ci, czego i gdzie to poprawić.

- **Płatności**: oczekująca, przeterminowana lub opłacona, i plik ZIP ze
  wszystkimi Twoimi fakturami.
- **Sprzedaż bez VAT firmom z UE**, z adnotacją prawną i numerem sprawdzonym w
  VIES.
- **Niemiecka e-faktura, szwajcarski QR-bill** i faktury w innej walucie.

Już dostępne w 11 krajach: Austria, Cypr, Czechy, Holandia, Irlandia, Luksemburg,
Niemcy, Polska (przez KSeF), Szwajcaria, Szwecja i Wielka Brytania.

:::warning
**W Hiszpanii jeszcze nie**: pojawi się, gdy zintegrujemy VeriFactu, i damy Ci
znać.
:::

[Zobacz kraje z fakturowaniem](/help/paises-con-facturacion)

---

### 5. Bardziej profesjonalne wyceny

- PDF wyceny ma **formę faktury**: numer, datę, ważność i, w płatnych planach,
  Twoje własne logo.
- **Numeracja według roku** („2026-00001”) i bez luk, nawet jeśli jakąś usuniesz.
- **Rabat** w € lub %, który pojawia się jako kolejna pozycja.
- Karty klienta **Osoba prywatna lub Firma** i prostsze dane podatkowe.
- Automatyczne tworzenie **zamówienia po zaakceptowaniu** wyceny.

[Zobacz wyceny](/help/presupuestos)

---

### 6. Zupełnie nowe Finanse

Sześć kart, na których widzisz swoje przychody, wydatki, podatki i zysk w
wybranym okresie (miesięcznym, kwartalnym, rocznym…).

Wgrywaj wydatki z pomocą naszego agenta AI i archiwizuj faktury od dostawców, żeby
od razu widzieć, na co wydajesz pieniądze. Kontroluj podatki, które musisz zapłacić
w każdym okresie.

:::info
**Najlepsze:** wyeksportuj te dane dla swojego biura rachunkowego w pliku ZIP jednym kliknięciem.
:::

[Zobacz Finanse](/help/financiero)

---

### 7. „Powiadomienia”: problemy Twojego warsztatu w jednym miejscu

Drukarka zatrzymana z błędem, odłączony sklep Etsy, płatność, która nie przeszła,
prawie pełna przestrzeń dyskowa… Informujemy Cię tylko o tym, co naprawdę wymaga
działania, a każde powiadomienie zamyka się samo, gdy rozwiążesz problem.

Możesz wyciszyć powiadomienie na kilka dni albo na zawsze. Czerwone, czyli te,
które zatrzymują coś ważnego, pokazujemy na czerwono tylko temu, kto może je
naprawić; reszta zespołu widzi je z komunikatem „Daj znać właścicielowi
warsztatu”.

---

### 8. Eksportuj swój magazyn do Excela lub PDF

Teraz możesz pobrać listę tego, co masz w magazynie: stany, filamenty, żywice,
materiały eksploatacyjne…

| Format | Co otrzymujesz |
|---|---|
| **Excel** | Skoroszyt z podsumowaniem i jednym arkuszem na każdą sekcję, z filtrami, sumami i brakami na czerwono. |
| **PDF** | Jeden dokument na sekcję, z Twoim logo, zdjęciami Twoich części i kolorami każdej szpuli. |

We wszystkich planach i zawsze ze wszystkimi wierszami, nie tylko z tymi, które
masz na ekranie.

---

### 9. W Twoim języku i na Twój sposób

BolloPrint mówi już **🇵🇱 po polsku, 🇳🇱 po niderlandzku i 🇨🇿 po czesku**. Razem to
dziewięć języków.

Daty i kwoty zapisujemy **tak jak w kraju Twojego warsztatu**, na ekranie, w PDF i
w e-mailach.

Jest też **nowy Start**, który zaczyna od tego, co pilne, z przyciskiem „Utwórz”
dla zamówienia, wyceny lub szybkiego tworzenia, i „Pierwsze kroki” z paskiem
postępu.

## A do tego, bo małe zmiany też robią różnicę

| Gdzie | Co się zmienia |
|---|---|
| **Ekrany** | Podczas ładowania widzisz kształt treści, nigdy fałszywą pustą listę; jeśli coś się nie uda, przycisk „Ponów”. Filtry są takie same na wszystkich listach, także na telefonie. |
| **Przesyłanie** | Każdy plik pokazuje postęp i wznawia się sam po zerwaniu połączenia. Pliki po slicingu mogą mieć do 5 GB. |
| **Koszty** | 29 rodzin filamentu i 9 rodzin żywicy z aktualnymi cenami za kilogram; marże z kolorowym paskiem i przykładem. |
| **Klienci** | Lista wyszukuje i sortuje po każdej kolumnie, a klient bez aliasu wyświetla się z pełnym imieniem i nazwiskiem. |
| **Etsy** | Import oferty jest do 8 razy szybszy, wchodzą zamówienia z dwiema wariacjami, a przed synchronizacją oferty widzisz wartość po wartości, co się zmieni. Ustawienia → Marketplace’y to teraz galeria, ze stroną dla każdego sklepu. |
| **Wysyłka** | Własni przewoźnicy i kanały sprzedaży dla Austrii, Niemiec, Wielkiej Brytanii, Polski, Czech i Holandii. |
| **Podręcznik i blog** | Podręcznik rośnie z 49 do 70 stron, we wszystkich dziewięciu językach, a na blogu jest sześć nowych artykułów: od agenta lokalnego po to, ile naprawdę kosztuje część. |
| **Na co dzień** | Aplikacja lepiej znosi szczyty ruchu, sama wraca po zerwaniu połączenia, tłumacz Chrome już jej nie psuje, a drukarka, której agent wyłączy się w trakcie, nie zostawia już wydruków-widm. |

## Gdzie jesteśmy

| Co | Gdzie i ile |
|---|---|
| 🧾 **Faktury zgodne z prawem w 11 krajach** | 🇦🇹 Austria · 🇨🇾 Cypr · 🇨🇿 Czechy · 🇳🇱 Holandia · 🇮🇪 Irlandia · 🇱🇺 Luksemburg · 🇩🇪 Niemcy · 🇵🇱 Polska · 🇨🇭 Szwajcaria · 🇸🇪 Szwecja · 🇬🇧 Wielka Brytania |
| 🌍 **Warsztat można założyć w 53 krajach Europy** | Z jego walutą, podatkami i przewoźnikami. Płatność w euro, funtach, złotych lub koronach czeskich. |
| 🖨️ **102 modele drukarek, do filamentu i żywicy** | Bambu Lab · Prusa · Elegoo · FlashForge · Anycubic · Creality · QIDI · Snapmaker · Voron · RatRig · Sovol · Artillery · Longer · Phrozen · Two Trees |
| ✅ **10 przetestowanych przez nas na prawdziwych maszynach** | Bambu Lab A1, A2L, P1P, P1S, P2S, X1 Carbon, X2D, H2C, H2D i H2S. |

## Czegoś Ci brakuje?

Napisz do nas na
[info@bolloprint.com](mailto:info@bolloprint.com) albo na naszym
[kanale Discord](/help/soporte-por-discord). Czytamy wszystko. Wiele z tego, co
tu widzisz, powstało dzięki wiadomościom takim jak Twoja.

Jeśli chcesz dowiedzieć się więcej o tym, jak to działa, wszystko znajdziesz w
[podręczniku](/help).

I nie zwalniamy: codziennie pracujemy nad tym, żeby BolloPrint było najlepszym
narzędziem dla Twojego warsztatu druku 3D.

![Bollo, maskotka BolloPrint, w okularach warsztatowych i z pasem na narzędzia, na planie](/blog/media/2026-11-03-novedades-otono/01-bollo.webp "60%")
