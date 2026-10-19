---
slug: connect-printers-local-network-agent
title: "Podłącz drukarki przez własną sieć: agent lokalny krok po kroku"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper… Mały agent na komputerze w warsztacie, cała flota w BolloPrint i bez grzebania w routerze.
date: 2026-10-12
updated: 2026-10-16
tags: [poradniki]
cover: 01-portada.webp
---

Twoje drukarki są w warsztacie, ale ty nie zawsze. A żeby wiedzieć, czy któraś
nadal drukuje, czy wydruk się udał albo czy zostało jej jeszcze materiału, musisz
przy niej stać.

Do tego służy **agent lokalny**: mały program, który działa na komputerze w twoim
warsztacie, rozmawia z drukarkami przez twoją własną sieć i przekazuje BolloPrint
to, co widzi.

- **Nie ruszasz routera**: żadnych otwartych portów, stałego IP ani zapory.
- **Jest bardzo lekki**: wystarczy mu dowolny komputer, który i tak masz włączony.
- **Jeden wystarczy na całą flotę**, niezależnie od jej wielkości.
- **Aktualizuje się sam**: gdy wychodzi nowa wersja, sam ją instaluje.

::animation{id="local-agent"}

## Gdzie go zainstalować

Agent działa na **dowolnym komputerze w warsztacie, którego nie wyłączasz**: na
NAS-ie, mini-PC, Raspberry Pi albo zwykłym pececie. Potrzebuje tylko, żeby był
**zawsze włączony** i miał **Dockera**.

Najlepiej, żeby był **w tej samej sieci co drukarki**, bo wtedy sam je znajdzie.
Jeśli to niemożliwe, dodajesz je ręcznie i działają tak samo.

## Utwórz agenta w BolloPrint

Zacznij w BolloPrint. Przejdź do **Ustawienia → Drukarki**. Zobaczysz trzy
zakładki: **Drukarki** (wszystkie twoje maszyny, niezależnie od tego, którędy
przychodzą), **Agent lokalny** i **Bambu Cloud**. Otwórz **Agent lokalny** i kliknij
**Nowy agent**.

Nadaj mu nazwę, która za pół roku nadal będzie ci coś mówić: **nazwij go od
miejsca, w którym stoi, a nie od tego, czym jest**. „Parter” albo „Hala 2” są
dobre; „Agent 1” — nie. Potem kliknij **Utwórz agenta**.

![Zakładka Agent lokalny z dwoma agentami online i przyciskiem Nowy agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-en.png)

## Skopiuj szablon

Po utworzeniu agenta BolloPrint pokaże ci **szablon**: tekst, w którym jest już
**wpisane** wszystko, co twoje — klucze twojego agenta i właściwa wersja. Nie
trzeba niczego podmieniać ani uzupełniać.

Wybierz format, którego używasz (**Docker Compose** to ten najczęstszy), kliknij
**Kopiuj**, a gdy szablon będzie już bezpieczny, **Zapisz**.

![Szablon wdrożenia nowego agenta z przyciskiem Kopiuj](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-en.png "75%")

:::warning 🔐 Skopiuj go teraz: klucze są pokazywane tylko raz
Nie przechowujemy ich, więc nie możemy pokazać ci ich ponownie. Jeśli zgubisz
szablon, nic się nie stało: otwórz agenta przez **Edytuj** (w jego menu **⋮**),
przejdź do zakładki **Wdrożenie** i kliknij **Wygeneruj klucze ponownie**. Jeśli
agent jeszcze nigdy się nie połączył, nic nie zostanie przerwane.
:::

## Wklej szablon na swoim komputerze

To robisz już na swoim komputerze, nie w BolloPrint, a sposób zależy od tego,
gdzie instalujesz agenta:

- **NAS Synology**: zainstaluj **Container Manager** z **Centrum pakietów**,
  przejdź do **Projekt → Utwórz**, wklej szablon i utwórz projekt. Bez wpisywania
  żadnych poleceń.
- **Windows lub Mac**: zainstaluj **Docker Desktop**, zapisz szablon w folderze
  jako `docker-compose.yml` i z tego folderu uruchom
  `docker compose up -d`.
- **Linux**: zainstaluj **Dockera** menedżerem pakietów swojej dystrybucji,
  zapisz szablon jako `docker-compose.yml` i uruchom tam
  `docker compose up -d`.
- **Portainer**: wklej ten sam szablon do stacka i go wdróż.

:::info 💡 W Windows i na Macu drukarki nie wykrywają się same
Tam Docker działa wewnątrz maszyny wirtualnej, która nie widzi komunikatów
wysyłanych przez drukarki w twojej sieci. Agent działa tak samo, ale drukarki
dodajesz ręcznie, jak opisujemy niżej.
:::

## Coś nie idzie? Kliknij „Zainstaluj”

Dopóki agent ani razu się nie połączył, w jego wierszu widnieje **Niezainstalowany**.
To nie błąd: nic nie padło, po prostu trzeba go jeszcze zainstalować.

W tym samym wierszu masz przycisk **Zainstaluj**. Po kliknięciu rozwijają się
w skrócie kroki opisane powyżej, z odnośnikiem **Pomoc**, drugim — **Artykuł na
blogu** — prowadzącym do tego tekstu, i przyciskiem, żeby zapytać nas na
**Discordzie**. Jeśli nie masz już szablonu, krok 3 zaprowadzi cię prosto do
wygenerowania nowego.

![Niezainstalowany agent z otwartym panelem Zainstaluj: trzy kroki, pomoc i Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-en.png)

## Sprawdź, czy jest online

Wróć do BolloPrint: w niecałą minutę agent przejdzie w stan **Online** i pokaże
nazwę komputera, na którym działa, oraz swoją wersję.

![Agent w stanie Online](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-en.png)

Jeśli tak się nie stanie, prawie zawsze winna jest jedna z trzech przyczyn:
szablon został **wklejony tylko częściowo**, komputer **nie ma internetu** albo
**zapora** blokuje ruch wychodzący. Jeśli chcesz zobaczyć, co mówi sam agent,
otwórz go przez **Edytuj**: szczegóły znajdziesz w zakładce **Stan**.

## Drukarki pojawiają się same

Od tej chwili agent sam **szuka drukarek w twojej sieci** co 15 minut. Gdy jakąś
znajdzie, da ci znać nad zakładkami, a samą drukarkę zobaczysz na dole sekcji
**Drukarki w sieci lokalnej**, z marką i modelem. Ty decydujesz:

- **Dodaj**: rejestrujesz ją i zaczyna raportować.
- **Ignoruj**: nie jest twoja albo nie chcesz jej tutaj.

![Drukarka wykryta przez agenta, z przyciskami Ignoruj i Dodaj, a nad nią Szukaj teraz i Dodaj po IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-en.png)

Jeśli właśnie włączasz maszynę i nie chcesz czekać, kliknij **Szukaj teraz**.
Jeśli drukarka poprosi o kod, jej wiersz uprzedzi cię o tym („poprosi o kod
dostępu”), żeby kod był już pod ręką.

## Jeśli któraś się nie pojawi, dodaj ją ręcznie

To, że drukarka nie pojawia się sama, jest **normalne** w dwóch przypadkach:

- **Jest w innej sieci.** Komunikaty drukarek nie przechodzą z jednej sieci do
  drugiej.
- **Agent działa w Windows lub na Macu.** Tam Docker działa w maszynie
  wirtualnej.

Nic przez to nie tracisz: dodajesz ją ręcznie i działa dokładnie tak samo,
z kamerą i sterowaniem, jeśli dana maszyna je ma. Kliknij **Dodaj po IP**. To
trzy kroki.

### 1. Wybierz markę

Wybierz markę swojej drukarki: każda ma swój kafelek, a te z logo są na początku.
Nie musisz wiedzieć, jak twoja maszyna się komunikuje — tym zajmujemy się my.
Jeśli wybierzesz **Elegoo**, zapytamy **Jaką masz drukarkę Elegoo?**, bo ta marka
ma kilka rodzin. **Klipper** i **Inna żywiczna (ChituBox)** są na końcu, w sekcji
**Ogólne**, na wypadek własnej konstrukcji albo marki, której nie ma na liście.

Jeśli nie masz pewności, czy twój model się nada, na dole jest **Nie masz
pewności? Zobacz listę kompatybilnych drukarek**; a jeśli twojej drukarki tam nie
ma, napisz nam o tym na Discordzie.

![Pierwszy krok dodawania drukarki po IP: marki, które można podłączyć](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-en.png)

### 2. Wpisz jej dane

Tylko to, co niezbędne:

- **Który agent ją łączy?** — jeśli masz więcej niż jednego. Możesz wybrać tylko
  taki, który jest online.
- **IP drukarki**. Znajdziesz je na ekranie drukarki (Ustawienia → Sieć) lub
  w routerze.
- **Kod drukarki**, jeśli dana marka go wymaga. Pole nazywa się tak, jak nazywa
  go producent: w Bambu to **Kod dostępu LAN**.
- **Nazwa**, jeśli chcesz nadać jej własną. To opcjonalne.

**Modelu i numeru seryjnego nie wpisujesz**: agent sam pyta o nie drukarkę. Pola
obowiązkowe mają **czerwoną gwiazdkę** i są zaznaczone na czerwono, dopóki są
puste. Na końcu ramka **Pamiętaj** podpowiada, co trzeba przygotować w drukarce
danej marki przed podłączeniem.

![Drugi krok: agent, IP, obowiązkowy kod dostępu LAN i ramka Pamiętaj](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-en.png)

### 3. Połącz

Kliknij **Połącz** i zobaczysz, jak to postępuje: agent otrzymuje żądanie, szuka
drukarki pod tym adresem i się z nią łączy. Na koniec zobaczysz **„Połączono.
Drukarka jest już na twojej liście.”**

![Trzeci krok: drukarka połączona i już na liście](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-en.png)

Jeśli coś pójdzie nie tak, powiemy ci to **zwykłymi słowami**: co się dzieje
i co sprawdzić (że pod tym IP nic nie odpowiada, że drukarka odrzuca kod…).
Przyciskiem **Wróć** poprawiasz dane i próbujesz jeszcze raz. Oryginalny komunikat
drukarki jest zwinięty pod **Pokaż szczegóły techniczne**: jeśli do nas piszesz,
skopiuj nam go, a szybciej sprawdzimy, o co chodzi.

:::info 💡 Zarezerwuj jej IP w routerze
Jeśli router zmieni drukarce adres, sami znajdziemy ją ponownie, ale przez chwilę
będzie niedostępna. Rezerwacja adresu eliminuje tę przerwę. To ustawienie
routera, nie BolloPrint.
:::

## Czego wymaga każda marka

Tu pojawia się najwięcej pytań. To samo, co przypomina krok 2, w skrócie:

| Marka | Co trzeba zrobić na maszynie | Kamera | Czy można wstrzymywać i anulować? |
|---|---|---|---|
| **Bambu Lab** | Włączyć **Tryb LAN** na jej ekranie (Ustawienia → Sieć) i użyć **kodu dostępu LAN**, który się tam pokaże | Tak | Tak, jeśli dodatkowo włączysz **Tryb dewelopera** |
| **Prusa** (beta: MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Włączyć **PrusaLink** i użyć wyświetlonego **hasła** (to nie jest hasło do Prusa Connect) | Nie | Tak |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) i **inne żywiczne (ChituBox)** | Nic, nie wymagają hasła | W modelach, które ją mają | Tak |
| **Elegoo Centauri Carbon 2** | Nic; tylko jeśli ustawiono w niej kod na ekranie, trzeba go wpisać | Tak | Nie |
| **Anycubic** (beta: Kobra 3, Kobra S1, Kobra 4, Kobra X) | Włączyć **Tryb LAN** (Ustawienia → Sieć). Po jego włączeniu drukarka przestaje korzystać z chmury i aplikacji Anycubic | Nie | Nie |
| **FlashForge** (beta: Adventurer 5M, 5M Pro, AD5X, Creator 5) | Włączyć **LAN Only** i użyć kodu weryfikacyjnego z menu sieci | Tak | Nie |
| **Snapmaker** (U1) | Nic | Tak | Tak |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Zwykle nic: tylko jeśli ustawiono klucz API w Moonraker | Tak, jeśli twój Klipper ma kamerę | Tak |

:::warning ⚠️ Bambu Lab: kod dostępu się zmienia
Za każdym razem, gdy włączasz lub wyłączasz Tryb LAN albo Tryb dewelopera, Bambu
**generuje nowy kod**. Jeśli Bambu, która działała bez zarzutu, nagle przestaje
się łączyć, w dziewięciu przypadkach na dziesięć właśnie dlatego: sprawdź jeszcze
raz kod na jej ekranie i zaktualizuj go w BolloPrint. Pamiętaj też, że **Tryb
dewelopera** odłącza ją od Bambu Cloud: od tej chwili zobaczysz ją tylko przez
agenta.
:::

:::info 💡 Nie ma twojego modelu w tabeli?
Sprawdź [kompatybilne drukarki](/help/impresoras-compatibles). Jeśli w środku
działa **Klipper** (każda maszyna własnej konstrukcji albo zmodyfikowana), jest
kompatybilna, nawet jeśli jej marki nie ma na żadnej liście.
:::

## Co zyskujesz dzięki agentowi lokalnemu

Z działającym agentem dostajesz:

- **Prawie wszystkie marki**: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge,
  Snapmaker i wszystko, co działa na Klipperze. Chmura tego nie oferuje, bo
  istnieje tylko dla Bambu Lab.
- **Kamerę**: podgląd na żywo, gdy masz otwartą stronę, zdjęcie, kiedy tylko
  chcesz, i zdjęcie końcowe zapisane w historii każdego wydruku. To nie monitoring:
  nic nie jest nagrywane.
- **Sterowanie**: wstrzymywanie, wznawianie i anulowanie z BolloPrint, bez
  chodzenia do maszyny, w tych, które na to pozwalają (patrz tabela wyżej).
  W Bambu Lab — gdy drukarka jest w **Trybie LAN** i **Trybie dewelopera**.
- **Odporność na awarie internetu**: jeśli padnie ci łącze, agent **nadal
  odczytuje drukarki i zapisuje, co się dzieje**. Gdy połączenie wróci, wysyła
  wszystko i nie tracisz tych godzin historii.
- **Niezależność od producenta** i od tego, czy jego chmura dalej działa.

Żadna droga nie pozwala natomiast **wysyłać zadań do druku**: plik nadal wysyłasz
ze swojego slicera.

## Najczęstsze pytania

Pytania, które dostajemy najczęściej.

### Czy muszę otwierać porty w routerze?

Nie. Ani portów, ani stałego IP, ani reguł zapory. Działa za zwykłym domowym
routerem.

### Czy potrzebny jest jeden agent na każdą drukarkę?

Nie. **Jeden obsługuje całą flotę.** Kilka ma sens tylko wtedy, gdy masz dwa
lokale albo dwie oddzielne sieci. Wtedy przy **Dodaj po IP** pojawi się pytanie,
który z nich łączy daną drukarkę.

### Co się stanie, jeśli wyłączę komputer albo wyjdzie nowa wersja?

Po włączeniu komputera agent wraca sam. Aktualizuje się też sam: gdy wychodzi
nowa wersja, pobiera ją i uruchamia się z nią ponownie, bez ruszania szablonu.
Coś zrobić trzeba tylko wtedy, gdy poprosimy o to na ekranie.

### Dlaczego nie mogę kliknąć „Dodaj po IP”?

Bo żaden z twoich agentów nie jest połączony — mówi o tym tekst pod przyciskiem.
Jeśli agent nie jest jeszcze zainstalowany, użyj **Zainstaluj** w jego wierszu;
jeśli już wcześniej działał, sprawdź, czy komputer jest włączony i ma internet.

:::info 💡 Potrzebujesz pomocy?
Napisz do nas przez [stronę kontaktową](/contact) albo otwórz wątek na
[naszym Discordzie](/help/soporte-por-discord). Jeśli powiesz nam, jakie masz
drukarki, podpowiemy dokładnie, co zrobić z każdą z nich.
:::

Ciesz się widokiem całej floty, gdziekolwiek jesteś.

![Bollo, maskotka BolloPrint, w warsztatowych goglach, przed farmą pracujących drukarek 3D](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Powiązana dokumentacja

- [Podłączanie drukarek](/help/conectar-impresoras): dwie drogi i która jest dla ciebie
- [Agent lokalny](/help/el-agente-local): pełny opis
- [Wdrażanie agenta](/help/desplegar-el-agente): szczegóły techniczne, jeśli ich potrzebujesz
- [Typy połączeń](/help/tipos-de-conexion): na co pozwala każda rodzina drukarek
- [Kompatybilne drukarki](/help/impresoras-compatibles): tu znajdziesz swój model
