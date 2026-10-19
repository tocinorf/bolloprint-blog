---
slug: install-bolloprint-agent-synology
title: Instalacja agenta BolloPrint na Synology
description: Jeśli masz już w warsztacie NAS, nie szukaj dalej miejsca na agenta. Dwadzieścia minut w interfejsie DSM, bez wpisywania ani jednego polecenia i bez ruszania routera.
date: 2026-09-10
updated: 2026-09-10
tags: [poradniki]
draft: true
---

Jeśli masz w warsztacie Synology, masz już gdzie postawić agenta. Jest włączony
całą dobę, stoi w tej samej sieci co drukarki i od lat potrafi uruchamiać
kontenery. Trudno o lepsze miejsce.

I nie musisz nic wiedzieć o Dockerze: nie wpiszesz ani jednego polecenia.
Wszystko robi się w interfejsie DSM, wklejając tekst do okienka. Licz około
dwudziestu minut, z czego połowa to czekanie na pobieranie.

:::info
Ten tekst dotyczy wyłącznie **wdrożenia na Synology**. Czym jest agent, jakie
marki obsługuje i jak dodać każdą drukarkę, znajdziesz w
[poradniku o sieci lokalnej](/blog/connect-printers-local-network-agent) —
kiedy skończysz tutaj, przejdź tam.
:::

![Container Manager w DSM z działającym projektem agenta](/blog/media/2026-09-10-agente-synology/01-container-manager.png)

## Dlaczego na NAS-ie, a nie na laptopie

Bo agent przydaje się tylko wtedy, gdy nie śpi. Jeśli postawisz go na komputerze,
który wyłączasz, wychodząc z warsztatu, tych godzin nie zobaczysz: ani co się
drukowało, ani jak długo, ani czy drukarka stanęła o trzeciej w nocy. NAS i tak
jest cały czas włączony.

Reszta przychodzi gratis: stoi w sieci drukarek, dzięki czemu sam je znajduje,
a zużywa od 10 do 20 MB pamięci. Na NAS-ie nikt tego nawet nie zauważy.

:::info 💡 Nie, nie trzeba ruszać routera
Agent **łączy się na zewnątrz**, przez port 443, tak samo jak przy otwieraniu
strony internetowej. Nigdy nie przyjmuje połączeń z internetu. Nie trzeba więc
otwierać portów, ustawiać stałego IP ani walczyć z zaporą — i działa tak samo za
domowym routerem, jak na światłowodzie z CGNAT.
:::

## Co musisz mieć, zanim zaczniesz

Cztery rzeczy — lepiej sprawdzić je teraz niż w połowie:

- **NAS i drukarki w tej samej sieci.** Jeśli są w różnych VLAN-ach, agent
  działa tak samo, ale traci automatyczne wykrywanie: każdą drukarkę trzeba
  będzie dodać ręcznie po IP.
- **Wyjście NAS-a do internetu przez port 443.** Nic więcej.
- **DSM 7.2 lub nowszy.** Sprawdzisz to w **Panel sterowania → Aktualizacja
  i przywracanie** (*Control Panel → Update & Restore*). Z DSM 7.0 czy 7.1 ten
  poradnik ci nie pomoże: najpierw zaktualizuj DSM.
- **Kod połączenia agenta**, który dostajesz, tworząc agenta w BolloPrint
  w **Ustawienia → Drukarki → Agent lokalny**.

:::danger ⚠️ Uruchom go tylko na NAS-ie, nie testuj wcześniej gdzie indziej
**Pierwszy kontener, który wystartuje z tym kodem, przejmuje instalację.** Jeśli
więc odpalisz go na laptopie „na próbę”, a potem postawisz na Synology, NAS
zgłosi się jako nieznana instalacja i będzie czekał na twoją autoryzację.

To żadna tragedia — autoryzujesz go jednym kliknięciem — ale oszczędzisz sobie
chwili w stylu „no i czemu to nie działa?”.
:::

:::warning 🔐 Ten kod to hasło
Daje dostęp do danych połączenia drukarek w warsztacie. Nie wklejaj go na grupę
na WhatsAppie i nie zostawiaj go na zrzucie ekranu.
:::

## 1. Zainstaluj Container Manager

To aplikacja Synology do uruchamiania kontenerów. Instaluje się jak każda inna
i **w środku nie ma nic do konfigurowania**, więc ten krok idzie szybko.

Zaloguj się do DSM (`http://IP-NAS-A:5000`) jako administrator, otwórz
**Centrum pakietów** (*Package Center*), wyszukaj **Container Manager** i kliknij
instaluj. Minuta, dwie. Potem go otwórz i poczekaj, aż się uruchomi: gdy zakładka
**Przegląd** (*Overview*) pokaże dane zamiast komunikatu, gotowe.

![Centrum pakietów DSM z Container Managerem](/blog/media/2026-09-10-agente-synology/02-centro-paquetes.png)

Zauważysz, że DSM sam tworzy folder współdzielony o nazwie `docker`. To normalne,
zostaw go w spokoju.

:::warning ⚠️ Jeśli nie widzisz Container Managera
To znaczy, że ten model NAS-a nie obsługuje kontenerów. Programowo nic się nie da
zrobić: postaw agenta na innej maszynie w tej samej sieci — mini-PC, Raspberry Pi,
czymkolwiek, co jest zawsze włączone.
:::

## 2. Utwórz projekt

W Container Managerze **projekt** to w zasadzie spisany przepis: wklejasz tekst,
a NAS sam pobiera i uruchamia to, co w nim jest. Nie trzeba tworzyć folderów ani
kopiować plików.

Przejdź do **Projekt → Utwórz** (*Project → Create*).

![Container Manager, zakładka Projekt, przycisk Utwórz](/blog/media/2026-09-10-agente-synology/03-crear-proyecto.png)

Jako nazwę wpisz `bolloprint-agent`, małymi literami — DSM nie przyjmuje tam
wielkich liter ani spacji. Jako ścieżkę kliknij **Ustaw ścieżkę** (*Set Path*),
wejdź do folderu `docker`, utwórz w nim folder `bolloprint-agent` i go zaznacz.

:::info 💡 Trafia tam tylko przepis, nie twoje dane
W tym folderze zapisuje się **wyłącznie tekst pliku `docker-compose.yml`**. To, co
agent musi pamiętać, żyje w wewnętrznym wolumenie Dockera, który tworzy się sam
i nawet nie pojawia się w File Station. Tak jest lepiej: nie ma czego ruszać ani
czego przypadkiem usunąć.
:::

W polu **Źródło** (*Source*) wybierz utworzenie pliku `docker-compose.yml`.
Pojawi się puste okienko — tam wklejasz blok.

:::danger ⚠️ Skopiuj blok ze swojego ekranu, nie stąd
Masz go w BolloPrint, w **Ustawienia → Drukarki → Agent lokalny → Jak go
wdrożyć**, zakładka **Docker Compose**, z przyciskiem kopiowania. Ten ma wersję
agenta, która jest właściwa w danym momencie; ten poniżej jest tylko po to, żeby
było widać, jak to wygląda.

**I nawet nie myśl o wpisaniu `latest`.** Takiej etykiety nie ma w rejestrze —
sprawdziliśmy to dziś: zwraca 404 — więc projekt utknąłby na
`manifest unknown`, w ogóle nie startując. To nie jest niczyje przeoczenie, tylko
celowa decyzja: ruchoma etykieta pozwoliłaby aktualizacji podmienić agenta pod
działającą flotą, bez decyzji warsztatu.
:::

```yaml
services:
  bolloprint-agent:
    image: ghcr.io/bolloprint/bolloprint-agent:0.4.8   # ← ta, którą pokazuje twój ekran
    container_name: bolloprint_agent
    restart: unless-stopped
    network_mode: host
    mem_limit: 512m
    pids_limit: 512
    ulimits:
      nofile:
        soft: 65536
        hard: 65536
    environment:
      BP_AGENT_CODE: WKLEJ_TUTAJ_SWOJ_KOD
      # BP_STATUS_PORT: 9911
      # BP_LOG_LEVEL: debug
    volumes:
      - identity:/var/lib/bolloprint

volumes:
  identity:
    name: bolloprint_agent_identity
```

Zamień `WKLEJ_TUTAJ_SWOJ_KOD` na swój kod, w całości i bez przypadkowych spacji
na początku czy na końcu — to najgłupszy błąd i zdarza się najczęściej.

![Edytor pliku docker-compose.yml w Container Managerze](/blog/media/2026-09-10-agente-synology/04-compose.png)

Cztery rzeczy w tym tekście, o których warto wiedzieć:

- **Wklej go, nie przepisuj.** Spacje na początku każdej linii są częścią
  formatu, a jeśli wkradnie się tabulator, DSM go odrzuci.
- **`network_mode: host`** sprawia, że agent widzi sieć NAS-a i sam znajduje
  drukarki. Bez tego — wszystkie ręcznie.
- **Wolumen `identity`** to pamięć agenta. Dzięki niemu agent nie prosi o
  autoryzację przy każdym restarcie.
- **Linie z `#` są celowo wyłączone.** Włącza się je tylko wtedy, gdy trzeba coś
  zdiagnozować.

Gdy przejdziesz dalej, DSM zaproponuje opublikowanie „portalu WWW”. Wybierz
**Brak** (*None*): agent nie ma żadnej strony do pokazania.

I tyle. DSM pobierze obraz i uruchomi kontener, pokazując ci log na żywo. Kilka
minut, zależnie od łącza. Jeśli po zakończeniu projekt pozostanie zatrzymany,
zaznacz go i wybierz **Akcja → Uruchom** (*Action → Start*).

## 3. Sprawdź, czy działa

Są trzy sygnały, ale **naprawdę liczy się trzeci**. Dwa pierwsze mówią tylko, że
kontener wystartował, a nie że z kimkolwiek rozmawia.

**Kontener działa.** W zakładce **Kontener** (*Container*) powinien być
`bolloprint_agent` ze stanem **Uruchomiony** (*Running*), zużywający kilkadziesiąt
MB.

![Lista kontenerów z działającym bolloprint_agent](/blog/media/2026-09-10-agente-synology/05-contenedor.png)

**Log mówi to, co powinien.** Kliknij dwukrotnie kontener, zakładka **Dziennik**
(*Log*), i w pierwszych sekundach powinno być widać to:

```
INFO bolloprint-agent starting version=0.4.8
INFO installation fingerprint source=stored ...
INFO bootstrapped agent_id=... printers=0
INFO broker connected
```

Każda linia potwierdza co innego, dlatego warto im się przyjrzeć:

| Linia | Co ci mówi |
|---|---|
| `source=stored` | Wolumen tożsamości jest zamontowany i da się do niego pisać. Jeśli jest tu coś innego, przygotuj się na autoryzowanie agenta przy każdym odtworzeniu kontenera. |
| `bootstrapped` | Kod jest poprawny i BolloPrint go rozpoznał. |
| `broker connected` | Stałe połączenie jest otwarte. Od tej chwili agent już raportuje. |

![Zakładka Dziennik z liniami startowymi](/blog/media/2026-09-10-agente-synology/06-registro.png)

**A agent w BolloPrint robi się zielony.** W **Ustawienia → Drukarki → Agent
lokalny** karta powinna przejść na **Online** w ciągu mniej więcej trzydziestu
sekund. To jest ten właściwy sygnał: oznacza, że cały obieg działa.

![Karta agenta w stanie Online w BolloPrint](/blog/media/2026-09-10-agente-synology/07-agente-online.png)

## Jeśli coś nie działa

| Co widzisz | Co to zwykle oznacza |
|---|---|
| `manifest unknown` przy pobieraniu | Ta wersja obrazu nie istnieje. Skopiuj jeszcze raz blok ze swojego ekranu — i sprawdź, czy nie ma tam `latest`. |
| Startuje i sam się zatrzymuje | Zajrzyj do logu. Prawie zawsze to źle wklejony kod, ze spacją przed nim albo po nim. |
| `bootstrapped` nigdy się nie pojawia | NAS nie wychodzi do internetu przez port 443 albo zapora zjada ruch wychodzący. |
| Prosi o autoryzację przy każdym restarcie | Brakuje wolumenu tożsamości. Sprawdź, czy wklejona jest cała sekcja `volumes`. |
| Pojawia się jako instalacja czekająca na autoryzację | Ten kod został już użyty na innej maszynie. Jeśli rozpoznajesz urządzenie, autoryzuj je — pamiętaj tylko, że po autoryzacji nowego poprzednie traci dostęp. |
| Nie znajduje żadnej drukarki | Czy NAS i drukarki są w tej samej sieci? Jeśli nie, to normalne: dodaj je po IP, a będą działać równie dobrze. |

## Co zostało

Z zielonym agentem masz połowę roboty za sobą. Zostaje dodać drukarki: te, które
pojawiają się same, te, które trzeba wpisać po IP, i to, czego wymaga każda marka
— wszystko jest w [poradniku o sieci lokalnej](/blog/connect-printers-local-network-agent).

Od tej chwili możesz o nim zapomnieć. Kontener sam wraca po każdym restarcie
NAS-a i nie wymaga konserwacji. Jedyne, co zrobisz od czasu do czasu, to
aktualizacja: gdy BolloPrint powiadomi cię o nowej wersji, kopiujesz ponownie
blok z ekranu i restartujesz projekt.

## Czytaj dalej

- [Agent lokalny](/help/el-agente-local) — instalacja, tożsamość, kilka agentów i diagnostyka
- [Drukarki w sieci lokalnej](/help/impresoras-por-red-local) — dodawanie maszyn
- [Typy połączeń](/help/tipos-de-conexion) — na co pozwala każda rodzina drukarek
- [Kompatybilne drukarki](/help/impresoras-compatibles) — tu znajdziesz swój model
- [Podłączanie drukarek](/help/conectar-impresoras) — dwie drogi i która jest dla ciebie
