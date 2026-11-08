---
slug: install-bolloprint-agent-synology
title: Zainstaluj agenta BolloPrint na NAS-ie Synology
description: Jeśli w twoim warsztacie stoi Synology, to tam jest miejsce na agenta. Natywny pakiet DSM, instalowany z Centrum pakietów i powiązany jednym kliknięciem. Bez Dockera, bez kopiowania kodu i bez zmian w routerze.
date: 2026-11-02
updated: 2026-11-02
tags: [poradniki]
draft: true
---

Jeśli masz w warsztacie Synology, masz już właściwe miejsce na agenta
BolloPrint. Jest włączony dniem i nocą, stoi w tej samej sieci co twoje drukarki
i już teraz obsługuje resztę twoich małych usług.

Agent przychodzi jako **natywny pakiet DSM**: instalujesz go jak każdą inną
aplikację Synology i pojawia się w menu głównym DSM. Bez Dockera, bez Container
Managera, bez wklejania tekstu i bez kopiowania kodu. Zarezerwuj sobie dziesięć
minut.

:::info
Ten tekst dotyczy wyłącznie **instalacji agenta na Synology**. Czym jest agent,
jakie marki obsługuje i jak dodać każdą drukarkę, znajdziesz w
[poradniku o sieci lokalnej](/blog/connect-printers-local-network-agent). Wróć
do niego, gdy skończysz tutaj.
:::

:::warning Pakiet dla Synology jest w becie
Działa, ale któryś krok może się jeszcze zmienić. Jeśli coś na twoim ekranie nie
zgadza się z tym, co tu czytasz, daj nam znać.
:::

## Dlaczego na NAS-ie, a nie na twoim laptopie

Bo agent przydaje się tylko wtedy, gdy nie śpi. Jeśli działa na komputerze,
który wyłączasz, wychodząc z warsztatu, te godziny przepadają: co się wydrukowało,
ile to trwało, czy wydruk nie stanął o trzeciej w nocy. NAS i tak jest włączony.

Resztę dostaje gratis: jest w sieci drukarek, dzięki czemu agent sam je
znajduje, i jest lekki: NAS dalej robi wszystko inne tak jak wcześniej.

:::info 💡 Nie, nie ruszysz routera
Agent **sam łączy się** z BolloPrint, tak jak przeglądarka otwierająca stronę
internetową. Nigdy nie przyjmuje połączeń z internetu: żadnych otwartych portów,
stałego IP ani reguł zapory. Działa tak samo za domowym routerem, jak i na
światłowodzie z CGNAT.
:::

## Czego potrzebujesz na początek

Sprawdź to teraz, a nie w połowie:

- **DSM 7 lub nowszy.** Znajdziesz to w **Panel sterowania → Centrum
  informacji**. DSM 6 się nie nada.
- **Procesor twojego NAS-a.** W tym samym miejscu, w **Centrum informacji**.
  Intel lub AMD to 64 bity; przy ARM karta twojego modelu na stronie Synology
  mówi, czy jest 64-, czy 32-bitowy. Będzie ci to potrzebne, żeby wybrać
  właściwy plik do pobrania.
- **Konto administratora DSM.** Tylko administratorzy mogą instalować pakiety
  i otwierać stronę agenta.
- **Bycie właścicielem swojego warsztatu w BolloPrint.** Przy powiązywaniu
  agenta widzisz tylko warsztaty, których jesteś właścicielem.
- **NAS i drukarki w tej samej sieci.** W oddzielnych sieciach (VLAN-ach) agent
  też działa, ale każdą drukarkę dodasz po jej IP.

## 1. Pobierz pakiet

W BolloPrint przejdź do **Ustawienia → Drukarki → Agent lokalny → Nowy agent**
i wybierz **Synology**.

Jest tam jeden przycisk pobierania dla każdego typu procesora: **Intel lub AMD
(64-bit)**, **ARM (64-bit)** i **ARM (32-bit)**. Kliknij swój. Pobierzesz plik
z końcówką `.spk`, czyli pakiet DSM. Jeśli nie wiesz który, link tuż pod
przyciskami zaprowadzi cię na stronę Synology, gdzie sprawdzisz swój model.

![Nowy agent → Synology w BolloPrint: trzy przyciski pobierania, po jednym na typ procesora, a pod nimi trzy kroki instalacji](/blog/media/2026-09-10-agente-synology/01-new-agent-synology.png)

Zwróć uwagę, czego na tym ekranie **nie ma**: żadnego kodu, klucza ani niczego
do utworzenia. Agent powstaje w chwili, gdy go powiązujesz, w kroku 3.

## 2. Zainstaluj go z Centrum pakietów

Otwórz DSM w przeglądarce i przejdź do **Centrum pakietów**. W prawym górnym
rogu kliknij **Instalacja ręczna**, potem **Przeglądaj**, wybierz pobrany przed
chwilą plik `.spk` i kliknij **Dalej**.

<!-- SCREENSHOT: 02-manual-install.png — DSM 7 (English UI) Package Center with the «Manual Install» dialog open and bolloprint-agent-…-x64.spk selected, Next button visible. -->

DSM ostrzeże cię, że pakiet nie jest publikowany przez Synology. Zaakceptuj,
żeby przejść dalej.

Kreator pokaże wtedy jedno jedyne ustawienie: **port strony agenta**, z wpisanym
już **8257**. Zostaw go tak, chyba że DSM powie, że jest zajęty; wtedy wpisz
**8364**. Kliknij **Dalej**, a w podsumowaniu **Gotowe**.

<!-- SCREENSHOT: 03-install-wizard.png — DSM 7 (English UI) BolloPrint Agent install wizard: the page-port field with 8257 and the text «After installing, open BolloPrint Agent from the DSM main menu and press “Link with BolloPrint”…». -->

Po minucie pakiet pokazuje się jako **Uruchomiony**, a **BolloPrint Agent**
pojawia się w menu głównym DSM.

:::info 💡 „Ten pakiet nie jest zgodny z twoim modelem”
To znaczy, że pobrałeś pakiet dla innego procesora. Wróć do BolloPrint i pobierz
ten drugi.
:::

## 3. Powiąż go ze swoim warsztatem

To krok, który zastępuje dawne „skopiuj ten kod i wklej go tam”.

Otwórz **menu główne** DSM (ikona w lewym górnym rogu) i kliknij **BolloPrint
Agent**. Otworzy się w nowej karcie z własną stroną agenta: przeczytasz na niej,
że agent nie należy jeszcze do żadnego warsztatu, i zobaczysz krótki **kod**.

![Strona agenta, jeszcze niepowiązanego, z jego kodem i przyciskiem Powiąż z BolloPrint](/blog/media/2026-09-10-agente-synology/04-agent-page.png)

Kliknij **Powiąż z BolloPrint**. Otworzy się BolloPrint (zaloguj się, jeśli
trzeba) i zapyta, do którego warsztatu trafia agent. Potem pokaże ci
**urządzenie** — nazwę twojego NAS-a i „Synology” — oraz **kod**. Sprawdź, czy to
**ten sam kod**, który pokazała strona agenta, i kliknij **Dodaj do warsztatu**.

<!-- SCREENSHOT: 05-confirm.png — BolloPrint (English UI) «Add an agent to <workshop>» confirmation: Device «<NAS name> · Synology», the same code as 04-agent-page, and the «Add to workshop» button. -->

Wrócisz na stronę agenta, która teraz pokazuje **Powiązany z** i twój warsztat.

:::warning 🔐 Potwierdzaj tylko to, co sam przed chwilą kliknąłeś
Jeśli kiedykolwiek dostaniesz link do „dodania agenta”, o który nie prosiłeś,
zamknij go. Agenta powiązuje się tylko z jego własnej strony, a na Synology tę
stronę może otworzyć tylko administrator twojego NAS-a.
:::

## 4. Sprawdź, czy działa

W BolloPrint, w **Ustawienia → Drukarki → Agent lokalny**, agent jest już na
liście z nazwą twojego NAS-a i logo Synology, w stanie **Online**. To jest ten
sygnał, który się liczy: cały obieg działa.

![Agent Synology w stanie Online w Ustawienia → Drukarki → Agent lokalny, a pod nim drukarki znalezione w sieci lokalnej](/blog/media/2026-09-10-agente-synology/06-agent-online.png)

Mniej więcej po minucie zaczyna znajdować drukarki w twojej sieci. Pojawiają się
w **Drukarki w sieci lokalnej** i stamtąd je dodajesz; te, które nie pojawią się
same, dodasz przez **Dodaj po IP**. Jak to zrobić dla każdej marki, znajdziesz
w [poradniku o sieci lokalnej](/blog/connect-printers-local-network-agent).

## Aktualizacja

**Prawie nigdy nie musisz nic robić:** agent aktualizuje się sam. Gdy wychodzi
nowa wersja, pobiera ją, sprawdza, czy pochodzi od nas, i uruchamia się z nią
ponownie.

Tylko jeśli BolloPrint poinformuje cię, że agent wymaga **ręcznej aktualizacji**,
robisz to sam, a polega to na **zainstalowaniu nowego pakietu na ten, który już
masz**: pobierz go ponownie z tego samego miejsca w BolloPrint (**Agent lokalny →
Nowy agent → Synology**), a potem **Centrum pakietów → Instalacja ręczna** z
nowym plikiem. DSM widzi, że pakiet jest już zainstalowany, i go aktualizuje, nie
pytając ponownie o port. Agent pozostaje powiązany z tym samym warsztatem, z tymi
samymi drukarkami i całą ich historią. Nie trzeba niczego powiązywać od nowa.

Gdy pakiet trafi do katalogu Centrum pakietów Synology, Centrum pakietów samo
cię powiadomi, a aktualizacja będzie kwestią jednego kliknięcia.

:::warning Nie odinstalowuj, żeby zaktualizować
Odinstalowanie usuwa tożsamość agenta: to, co zainstalujesz potem, będzie
**nowym** agentem, którego trzeba powiązać od nowa. Żeby zaktualizować, zawsze
instaluj na istniejący.
:::

## Przeniesienie albo start od nowa

Agenta nie da się „przenieść”, ale nie ma takiej potrzeby: przenoszą się
drukarki, i to z całą swoją historią.

1. Zainstaluj pakiet na nowym NAS-ie i go powiąż. Pojawi się jako drugi agent.
2. Otwórz każdą drukarkę przez **Edytuj** w jej menu **⋮** i przełącz ją na
   nowego agenta.
3. Gdy stary agent nie będzie miał już drukarek, **Usuń** go z menu **⋮** w jego
   wierszu.

Żeby usunąć agenta na dobre: w DSM **Centrum pakietów → BolloPrint Agent →
Akcja → Odinstaluj**, a potem **Usuń** agenta z jego menu **⋮** w BolloPrint.
W odwrotnej kolejności też to zadziała: gdy usuniesz go w BolloPrint, agent to
zauważy, zapomni swoje powiązanie, a jego strona znów zaproponuje **Powiąż z
BolloPrint**. Tak czy inaczej nic nie przepada: jeśli później ponownie dodasz
którąś z jego drukarek, wróci ona ze swoim numerem i swoją historią.

## Gdy coś nie działa

| Co widzisz | Co to zwykle jest |
|---|---|
| Kreator mówi, że port 8257 jest zajęty | Używa go inna aplikacja na NAS-ie. Wpisz 8364 i kontynuuj. |
| „Nie jest zgodny z twoim modelem” | Pakiet dla innego procesora. Pobierz właściwy. |
| Otwarcie BolloPrint Agent prosi o zalogowanie do DSM | Otwórz go z menu głównego DSM, zalogowany jako administrator. |
| Strona mówi, że agent nie odpowiada | Pakiet jest zatrzymany albo jeszcze się uruchamia. W Centrum pakietów kliknij **Akcja → Uruchom** i daj mu kilka sekund. |
| Przy powiązywaniu nie ma twojego warsztatu na liście | Widzisz tylko warsztaty, których jesteś **właścicielem**. Poproś właściciela, żeby go powiązał. |
| „To żądanie powiązania jest nieprawidłowe” albo wygasło | Wróć na stronę agenta i ponownie kliknij **Powiąż z BolloPrint**. |
| Po restarcie NAS-a długo nie wraca | Daj mu kilka minut: uruchamia się razem z DSM i ponawia próby, dopóki NAS nie ma internetu. |
| Nie znajduje żadnej drukarki | Ta sama sieć? Jeśli nie, dodaj je po IP. Jeśli któraś została właśnie włączona, kliknij **Szukaj teraz**. Jeśli zapora DSM jest włączona, zezwól na porty BolloPrint Agent (jest na liście aplikacji przy tworzeniu reguły). |

## Wolisz Dockera?

Jeśli na twoim NAS-ie działa już Container Manager i wolisz trzymać wszystko
w kontenerach, agent działa też jako kontener. Kroki znajdziesz w
[Agent w Dockerze](/help/agente-en-docker). W większości warsztatów pakiet
jest prostszy: to aplikacja DSM jak każda inna, powiązana jednym kliknięciem.

## Powiązana dokumentacja

- [Agent na Synology](/help/agente-en-synology) — pełny przewodnik: instalacja, aktualizacja, przeniesienie, odinstalowanie i rozwiązywanie problemów
- [Agent lokalny](/help/el-agente-local) — co robi, kilka agentów, diagnostyka
- [Drukarki w sieci lokalnej](/help/impresoras-por-red-local) — dodawanie twoich maszyn
- [Obsługiwane drukarki](/help/impresoras-compatibles) — sprawdź swój model
