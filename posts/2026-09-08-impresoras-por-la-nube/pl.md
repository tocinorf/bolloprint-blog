---
slug: connect-bambu-lab-printers-cloud
title: "Podłącz drukarki Bambu Lab do BolloPrint w pięć minut"
description: Bez instalowania czegokolwiek i bez hasła. Wpisujesz e-mail swojego konta Bambu Lab, potwierdzasz kod, a drukarki pojawiają się same — z tym, co właśnie drukują, i z całą swoją historią.
date: 2026-10-12
updated: 2026-10-16
tags: [poradniki]
cover: 01-portada.webp
---

Jeśli pracuje u ciebie kilka drukarek Bambu, pewnie znasz ten rytuał: żeby
sprawdzić, jak im idzie, podchodzisz do każdej i patrzysz na jej ekran. Czy
pierwsza już skończyła? Czy drugiej starczy materiału? Ile godzin wydruku masz
w tym miesiącu?

Wszystko to możesz mieć na jednym ekranie i **bez instalowania czegokolwiek**.
Łączysz swoje konto Bambu Lab z BolloPrint, a drukarki pojawiają się same. To
jakieś pięć minut.

::animation{id="bambu-cloud"}

## Co zobaczysz o każdej drukarce

Na bieżąco i bez dotykania czegokolwiek:

- czy jest włączona i połączona;
- co drukuje, ile **procent** już ma i ile jej jeszcze zostało;
- temperatury dyszy i stołu;
- załadowane **materiały**, gniazdo po gnieździe, jeśli masz AMS;
- komunikaty samej maszyny.

I to, co najbardziej czuć na koniec miesiąca: **każdy wydruk zostaje
zapisany**, z czasem trwania, materiałem i kosztem. Nie musisz niczego notować.

![Karta drukarki w trakcie druku, z postępem i temperaturami](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora-en.png "42%")

## Czego potrzebujesz

Zanim zaczniesz, przygotuj te trzy rzeczy:

- Dostęp do BolloPrint jako **Właściciel** albo **Admin**. Przy innej roli ten
  ekran się nie pojawia.
- **E-mail** swojego konta Bambu Lab. Hasło nie jest potrzebne.
- Otwartą skrzynkę tego **e-maila**: Bambu wyśle ci na nią kod.

## Otwórz ekran drukarek

Wszystko robisz w jednym miejscu: **Ustawienia → Drukarki**. Zobaczysz tam trzy
zakładki:

- **Drukarki**: lista wszystkich twoich maszyn, niezależnie od tego, którędy
  przychodzą.
- **Agent lokalny**: do łączenia ich przez twoją własną sieć. Opisujemy to
  w [innym artykule](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: ta, której potrzebujesz teraz.

Otwórz **Bambu Cloud**.

![Ekran Ustawienia → Drukarki z trzema zakładkami](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas-en.png)

## Wpisz e-mail swojego konta Bambu

Użyj adresu swojego konta Bambu Lab (właśnie tego, a nie innego swojego adresu)
i kliknij **Wyślij kod**.

![Formularz Bambu Cloud z wpisanym e-mailem konta i przyciskiem Wyślij kod](/blog/media/2026-09-08-impresoras-por-la-nube/03-correo-en.png)

:::info 💡 Nie prosimy o hasło
BolloPrint **nigdy go nie widzi ani nie przechowuje**: do połączenia wystarczy
kod, który Bambu wysyła na twój e-mail.
:::

## Potwierdź kod z e-maila

Bambu wyśle ci **6-cyfrowy kod** z adresu `noreply@bambulab.com` (wiadomość
przychodzi po angielsku). Jeśli jej nie widzisz, **sprawdź folder spamu**: często
tam trafia. Wpisz kod na tym samym ekranie i kliknij **Zweryfikuj i połącz**.

![Pole na 6-cyfrowy kod i przycisk Zweryfikuj i połącz](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-en.png)

Trzy szczegóły oszczędzą ci drugiego podejścia:

- Kod **wygasa po 10 minutach** i ważny jest tylko ostatni. Jeśli nie zdążysz,
  kliknij **Wyślij kod ponownie**.
- Możesz go **wkleić dokładnie tak, jak przyszedł**: spacje i myślniki zostaną
  usunięte automatycznie.
- Jeśli podano zły adres, kliknij **Zmień e-mail**.

Gdy kod zostanie przyjęty, zobaczysz **Konto zweryfikowane i połączone**.

## Twoje drukarki już są w środku

Nie trzeba dodawać ich po kolei: **wszystkie drukarki z tego konta pojawiają się
same** w zakładce **Drukarki**, każda ze swoją nazwą i numerem seryjnym.

![Lista drukarek z nowo dodanymi maszynami Bambu](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas-en.png)

U góry zobaczysz licznik w rodzaju `Aktywne: 3 / 6`: to drukarki, które obejmuje
twój plan. Przełącznikiem w każdym wierszu włączasz lub wyłączasz te, które
chcesz. Wyłączona drukarka nie liczy się do limitu, ale **zachowuje całą swoją
historię**. A jeśli podłączasz całą flotę i nie starcza miejsc dla wszystkich,
nadmiarowe wchodzą wyłączone, zamiast przekraczać limit twojego planu.

## Czego nie da się zrobić przez chmurę

Lepiej wiedzieć to od początku, żeby nie szukać opcji, których nie ma:

- **To tylko podgląd.** Przez chmurę nie można wstrzymywać, wznawiać ani anulować
  wydruków z BolloPrint: Bambu przyjmuje takie polecenia tylko przez twoją sieć
  lokalną i przy drukarce ustawionej w określonym trybie. Wrócimy do tego na
  końcu.
- **Nie ma kamery.** Widzisz za to obraz z podglądu zadania ze slicera, czyli
  wizualizację, a nie to, co dzieje się wewnątrz maszyny.
- **Zależy od dwóch połączeń z internetem** — twojego i Bambu. Jeśli zawiedzie
  którekolwiek, drukarka wyświetla się jako rozłączona, nawet jeśli normalnie
  drukuje.
- **Sesja z Bambu trwa 90 dni, ale odnawia się sama**: BolloPrint odnawia ją,
  zanim wygaśnie, i nie musisz logować się ponownie. Tylko jeśli Bambu zamknie ją
  z własnej inicjatywy, powiadomimy cię na ekranie — wtedy wystarczy poprosić
  o nowy kod.

I coś, co dotyczy każdego sposobu połączenia: **BolloPrint nie wysyła zadań do
druku**. Plik nadal wysyłasz ze swojego slicera; BolloPrint odczytuje, co robi
maszyna, i to zapisuje.

## Częste problemy

### A jeśli loguję się do Bambu przez Google albo Apple?

Wpisz adres tego konta Google lub Apple: kod przyjdzie tam tak samo. Nie trzeba
już tworzyć hasła.

### Dlaczego widzę komunikat, że nie ma konta z tym adresem?

Jeśli pojawia się **„Nie ma konta Bambu Lab z tym e-mailem”**, to nie jest adres
twojego konta Bambu: Bambu i tak wysyła kod, ale po jego wpisaniu go odrzuca.
Sprawdź, którym adresem logujesz się w ich aplikacji, i kliknij **Zmień e-mail**.

### Czy co jakiś czas trzeba ponownie łączyć konto?

Nie. Sesja trwa 90 dni, a BolloPrint sam ją odnawia, zanim wygaśnie. Jeśli Bambu
kiedyś zamknie ją z własnej inicjatywy, zobaczysz **„Sesja wygasła”** i przycisk
**Zaloguj się ponownie**: prosisz o nowy kod i gotowe, bez odłączania czegokolwiek.

### Co zrobić, jeśli kod nie przychodzi albo nie zostaje przyjęty?

Jeśli nie przychodzi, sprawdź folder spamu i kliknij **Wyślij kod ponownie**.
Jeśli nie zostaje przyjęty, najpewniej wygasł albo nie jest tym ostatnim, o który
proszono: poproś o kolejny i wklej go w całości.

## Jeśli potrzebujesz więcej: agent lokalny

Chmura pokazuje ci wszystkie informacje, ale nie pozwala działać na drukarkach
i istnieje tylko dla Bambu Lab. Jeśli potrzebujesz więcej, rozwiązaniem jest
**agent lokalny**: mały program, który instalujesz na komputerze w warsztacie
i który rozmawia z drukarkami przez twoją własną sieć. Jeden wystarczy na całą
flotę, a daje ci:

- **prawie wszystkie marki**: Prusa, Elegoo, Anycubic, FlashForge, Snapmaker
  i wszystkie z Klipperem (QIDI, Sovol, Voron…);
- **kamerę**, na żywo i ze zdjęciem końcowym zapisywanym przy każdym wydruku;
- **wstrzymywanie, wznawianie i anulowanie** z BolloPrint, bez chodzenia do
  maszyny;
- **odporność na awarie internetu**: dalej odczytuje twoje drukarki i wysyła
  wszystko, gdy połączenie wróci.

:::info 💡 Żeby wysyłać polecenia do Bambu
Drukarka musi być w **Trybie LAN** i w **Trybie dewelopera**. Oba włącza się na
jej ekranie, a drugi odłącza ją od Bambu Cloud: od tej chwili zobaczysz ją tylko
przez agenta.
:::

Wyjaśniamy to krok po kroku w artykule
[podłącz drukarki przez własną sieć](/blog/connect-printers-local-network-agent).

Jeśli masz jakiekolwiek pytania, napisz do nas przez [stronę kontaktową](/contact)
albo na [naszym Discordzie](/help/soporte-por-discord).

Ciesz się wszystkimi drukarkami na jednym ekranie.

![Bollo, maskotka BolloPrint, w warsztatowych goglach, marzący o drukarce 3D](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp "60%")

## Powiązana dokumentacja

- [Podłączanie drukarek](/help/conectar-impresoras): dwa sposoby i który jest dla ciebie
- [Drukarki przez chmurę](/help/impresoras-por-la-nube): pełny opis tego ekranu
- [Kompatybilne drukarki](/help/impresoras-compatibles): tu znajdziesz swój model
- [Typy połączeń](/help/tipos-de-conexion): na co pozwala każdy typ drukarki
