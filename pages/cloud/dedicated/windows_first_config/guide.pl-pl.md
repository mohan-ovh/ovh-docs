---
title: Skonfiguruj nową instalację Windows Server
excerpt: Dowiedz się, jak aktywować połączenie ze zdalnym pulpitem i odpowiedź ICMP
updated: 2023-02-14
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk “Zaproponuj zmianę” na tej stronie.
> 

**Ostatnia aktualizacja z dnia 14-02-2023**

## Wprowadzenie

Po ponownym zainstalowaniu systemu operacyjnego Windows Server na serwerze zdalny dostęp i odpowiedź ICMP (Internet Control Message Protocol) mogą być czasami wyłączone.

**Niniejszy przewodnik wyjaśnia, jak skonfigurować Windows, aby ponownie włączyć ICMP i zezwolić na połączenia przez protokół Remote Desktop Protocol.**

## Wymagania początkowe

- Dystrybucja Windows zainstalowana na [serwera dedykowanego OVHcloud](https://www.ovhcloud.com/pl/bare-metal/).
- Dostęp do [Panelu client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl).

## W praktyce

### Etap 1: dostęp do KVM

Aby uzyskać dostęp do konsoli KVM Twojego serwera, zapoznaj się z [przewodnikiem KVM](/pages/cloud/dedicated/using_ipmi_on_dedicated_servers#korzystanie-z-kvm-przez-przegladarke-internetowa-tylko-dla-najnowszych-serwerow).

### Etap 2: zakończenie instalacji systemu Windows

Po zakończeniu sesji KVM wyświetlają się monitory konfiguracji początkowej. Tutaj skonfiguruj **kraj/region**, **język systemu Windows** oraz **układ klawiatury**. Po przeprowadzeniu tej operacji kliknij `Next`{.action}.

![KVM](images/setup-03.png){.thumbnail}

W drugim oknie wpisz hasło do konta Administrator i je potwierdź, następnie kliknij `Finish`{.action}.

![KVM](images/setup-04.png){.thumbnail}

System Windows zastosuje Twoje ustawienia, a następnie wyświetli ekran logowania. Kliknij przycisk `Send CtrlAltDel`{.action} w prawym górnym rogu, aby się zalogować.

![KVM](images/setup-05.png){.thumbnail}

Wprowadź hasło, które utworzyłeś dla konta Administrator i kliknij strzałkę.

![KVM](images/setup-06.png){.thumbnail}

Konfiguracja początkowa została zakończona. Po zalogowaniu należy zmodyfikować niezbędne ustawienia zapory Windows.

### Etap 3: zmiana firewalla Windows

Otwórz `Narzędzia administracyjne`{.action} panelu konfiguracyjnego `System and Bezpieczeństwo`{.action} i kliknij dwukrotnie `Firewall Windows z zaawansowanym`{.action} bezpieczeństwem.

![Admin](images/windows4.png){.thumbnail}

W tej sekcji możesz włączyć odpowiednie reguły "ICMP" i "Remote Desktop" (zdalny pulpit). Kliknij prawym przyciskiem myszy regułę i wybierz `Zezwalaj na regułę`{.action} w menu kontekstowym.

![Aktywny](images/windows5.png){.thumbnail}

Twój serwer powinien odpowiadać na zapytania wykorzystujące te protokoły.

> [!primary]
> Aby zabezpieczyć system Windows za pomocą reguł firewalla, zapoznaj się z naszym przewodnikiem "[Konfiguracja firewalla w systemie Windows](/pages/cloud/dedicated/activate-port-firewall-soft-win)".
>

### Aktywacja logów startowych (boot log) Windows (opcjonalnie)

Aktywacja logów startowych (*boot log*) Windows może być przydatna przy diagnostyce błędów serwera.

Zaloguj się do serwera przez sesję "zdalny pulpit" lub [KVM](/pages/cloud/dedicated/using_ipmi_on_dedicated_servers#korzystanie-z-kvm-przez-przegladarke-internetowa-tylko-dla-najnowszych-serwerow). Otwórz menu Start systemu Windows i kliknij `Uruchom`{.action}.

![Bootlog](images/windowsboot1.png){.thumbnail}

Wprowadź "msconfig" i kliknij `OK`{.action}.

![Bootlog](images/windowsboot2.png){.thumbnail}

W nowym oknie zaznacz kratkę obok `Boot log`. Kliknij `OK`{.action}.

![Bootlog](images/windowsboot3.png){.thumbnail}

Po kolejnym uruchomieniu Twojego serwera logi będą zapisywane w pliku .txt. Droga do pliku to `C:\Windows\ntbtlog.txt`.

Aby uzyskać dostęp do zawartości tego pliku w trybie Rescue, postępuj zgodnie z instrukcjami zawartymi w [przewodniku dotyczącym trybu Rescue](/pages/cloud/dedicated/rescue_mode).

## Sprawdź również

[Konfiguracja firewalla w systemie Windows](/pages/cloud/dedicated/activate-port-firewall-soft-win)

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
