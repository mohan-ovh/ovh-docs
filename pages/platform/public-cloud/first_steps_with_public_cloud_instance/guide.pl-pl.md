---
title: 'Zarządzanie instancjami Public Cloud'
excerpt: 'Dowiedz się, jak zarządzać instancjami Public Cloud w Panelu klienta OVHcloud'
updated: 2023-01-04
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk "Zgłóś propozycję modyfikacji" na tej stronie.
> 

**Ostatnia aktualizacja z dnia 04-01-2023**

## Wprowadzenie

Możesz zarządzać instancjami Public Cloud w [Panelu client](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl).

**Niniejszy przewodnik opisuje działania dostępne w Panelu klienta OVHcloud dla instancji Public Cloud.**

## Wymagania początkowe

- Projekt [Public Cloud](https://www.ovhcloud.com/pl/public-cloud/) na Twoim koncie OVHcloud
- Instancja [Public Cloud](/pages/platform/public-cloud/public-cloud-first-steps) w Twoim projekcie
- Dostęp do [Panelu client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl)

## W praktyce

Zaloguj się do [Panelu client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) i otwórz swój projekt `Public Cloud`{.action}. 

### Korzystanie z interfejsu zarządzania instancjami

Kliknij `Instances`{.action} w menu po lewej stronie. 

![public-cloud](images/compute.png){.thumbnail}

Strona ta zawiera listę wszystkich instancji Public Cloud i niektórych ich właściwości:

- ID instancji, wymagane dla niektórych połączeń API;
- lokalizacja centrum danych, czyli region instancji;
- model instancji;
- obraz, czyli system operacyjny zainstalowany na instancji;
- adres IPv4 instancji;
- dodatkowe wolumeny (dyski) aktualnie przypisane do instancji;
- status instancji, wskazujący, czy jest ona `włączona`.

### Opcje zarządzania na dashboardzie instancji

Na stronie z interfejsem zarządzania instancjami kliknij nazwę instancji.

Wybierz odpowiednią opcję w polu po lewej stronie "Zarządzanie".

![public-cloud](images/management.png){.thumbnail}

Działania te są również dostępne na stronie z interfejsem zarządzania instancjami, jeśli klikniesz przycisk `...`{.action} w tabeli.

#### Edycja konfiguracji instancji

Kliknij `Edytuj`{.action}.

Na nowej stronie, która się wyświetla pojawi zmieniona wersja opcji [tworzenia instancji](/pages/platform/public-cloud/public-cloud-first-steps), w której możesz zmienić następujące elementy:

- **Zmień nazwę**: możesz nadać instancji nazwę, aby ułatwić jej identyfikację.
- **Zmień obraz**: możesz wybrać inny system operacyjny dla instancji (pamiętaj, że reinstalacja instancji spowoduje usunięcie wszystkich zawartych w niej danych).
- **Zmień model**: możesz zmienić model instancji. Więcej informacji na temat opcji znajdziesz w [tym przewodniku](/pages/platform/public-cloud/public-cloud-first-steps#krok-3-tworzenie-instancji).
- **Zmień okres fakturowania**: możesz zmienić okres fakturowania instancji z godzinowego na miesięczny. Więcej informacji znajdziesz w [tym przewodniku](/pages/platform/public-cloud/changing_hourly_monthly_billing).

#### Utwórz kopię zapasową instancji

Kliknij `Utwórz kopię zapasową`{.action}.

Aby uzyskać więcej informacji, zapoznaj się z przewodnikiem "[Tworzenie kopii zapasowej instancji](/pages/platform/public-cloud/save_an_instance)". 

#### Utwórz automatyczny backup instancji

Kliknij `Utwórz automatyczną`{.action} kopię zapasową.

Aby uzyskać więcej informacji, zapoznaj się z przewodnikiem "[Tworzenie kopii zapasowej instancji](/pages/platform/public-cloud/save_an_instance#tworzenie-zautomatyzowanych-kopii-zapasowych-instancji)".

#### Zawieś instancję

Kliknij przycisk `Zatrzymaj`{.action}.

Działanie to spowoduje zawieszenie instancji. Więcej informacji znajdziesz w przewodniku "[Wstrzymanie lub uśpienie instancji](/pages/platform/public-cloud/suspend_or_pause_an_instance#zatrzymaj-suspend-instancje)".

Kliknij `Uruchom`{.action}, aby ponownie włączyć instancję.

#### Korzystanie z trybu Rescue

Kliknij `Zrestartuj w trybie Rescue`{.action}.

Uruchomi to tryb Rescue dla instancji. Aby uzyskać szczegółowe informacje, zapoznaj się z przewodnikiem [Przełączenie instancji w tryb rescue](/pages/platform/public-cloud/put_an_instance_in_rescue_mode).

#### Restart instancji 

> [!warning]
> Opcja uruchamiania bez wykonaj restart programowy (soft) nie jest aktualnie dostępna dla instancji Metal.
>

- Kliknij przycisk `Wykonaj restart programowy (soft)`{.action}, aby wykonać restart programowy.
- Kliknij `Wykonaj restart sprzętowy (hard)`{.action}, aby rozpocząć reboot na poziomie sprzętowym.

Potwierdź zlecenie restartu w oknie, które się wyświetli.

#### Zawieś (*shelve*) instancję

Kliknij `Zawieś`{.action}.

Wówczas instancja stanie się "*shelved*" wyświetlanym tutaj jako `Suspended`. Zapoznaj się z przewodnikiem "[Wstrzymanie lub uśpienie instancji](/pages/platform/public-cloud/suspend_or_pause_an_instance#zawies-shelve-instancje)", aby uzyskać więcej informacji na temat różnych stanów zawieszenia instancji.

Kliknij `Reaktywuj`{.action}, aby przywrócić stan `Włączony` instancji.

#### Reinstalacja instancji 

Kliknij `Reinstalacja`{.action}.

Operacja ta spowoduje ponowną instalację instancji za pomocą tego samego systemu operacyjnego, pod warunkiem, że obraz jest zawsze obsługiwany.

Pamiętaj, że reinstalacja **usuwa wszystkie dane** aktualnie przechowywane na Twojej instancji.

#### Usuwanie instancji

Kliknij `Usuń`{.action}.

Operacja ta spowoduje definitywne usunięcie instancji oraz wszystkich jej danych.

Potwierdź zlecenie usunięcia w oknie, które się wyświetli.

### Dostęp do konsoli VNC

Kliknij `Instances`{.action} w menu po lewej stronie. Na stronie z interfejsem zarządzania instancjami kliknij nazwę instancji w tabeli.

Następnie kliknij kartę `Konsola VNC`{.action}.

![public-cloud](images/vnc1.png){.thumbnail}

Konsola VNC zapewnia bezpośredni dostęp do Twojej instancji. Aby dostęp ten działał, najpierw skonfiguruj nazwę użytkownika i hasło dla instancji. 

Aby uzyskać więcej informacji, zapoznaj się z naszym przewodnikiem "[Tworzenie pierwszej instancji Public Cloud i łączenie się z nią](/pages/platform/public-cloud/public-cloud-first-steps#connect-to-instance)".

## Sprawdź również

[Tworzenie pierwszej instancji Public Cloud i łączenie się z nią](/pages/platform/public-cloud/public-cloud-first-steps)

[Prezentacja programu "Horyzont"](/pages/platform/public-cloud/introducing_horizon)

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.