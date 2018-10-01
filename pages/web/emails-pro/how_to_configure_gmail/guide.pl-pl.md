---
title: 'Konfiguracja konta E-mail Pro w interfejsie online programu pocztowego Gmail'
slug: konfiguracja-gmail
excerpt: 'Dowiedz się, jak skonfigurować konto E-mail Pro w interfejsie online programu pocztowego Gmail'
section: 'Konfiguracja programu pocztowego'
order: 6
---

**Ostatnia aktualizacja dnia 2018-08-03**

## Wprowadzenie

Konta E-mail Pro mogą być skonfigurowane w jednym z kompatybilnych programów pocztowych i interfejsów online. Dzięki temu możesz wysyłać i odbierać wiadomości, korzystając z wybranej przez Ciebie aplikacji lub interfejsu online.

**Dowiedz się, jak skonfigurować konto E-mail Pro w interfejsie online programu pocztowego Gmail.**

> [!warning]
>
> OVH udostępnia różnorodne usługi, jednak ich konfiguracja, zarządzanie oraz utrzymanie należy do Ciebie.  Jesteś tym samym odpowiedzialny za ich prawidłowe funkcjonowanie.
> 
> Oddajemy w Twojej ręce niniejszy przewodnik, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku  trudności zalecamy skorzystanie z pomocy wyspecjalizowanego webmastera lub kontakt z producentem interfejsu. Niestety firma OVH nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji „Sprawdź również”.
> 

## Wymagania początkowe

- Wykupienie usługi [E-mail Pro](https://www.ovh.pl/emaile/email-pro/){.external}
- Dane do logowania do konta E-mail Pro, które chcesz skonfigurować
- Dane do konta Gmail, w którym chcesz skonfigurować konto E-mail Pro OVH

> [!primary]
>
> Niniejszy przewodnik został przygotowany w oparciu o nowy interfejs Gmail. Nawet jeśli elementy graficzne nieznacznie różnią się od Twojej wersji, instrukcje postępowania pozostają takie same.
>

## W praktyce

### Etap 1: dodaj konto E-mail Pro OVH do interfejsu Gmail

Przed rozpoczęciem operacji przejdź do interfejsu online programu Gmail, korzystając z Twojej przeglądarki internetowej. Wprowadź Twoje dane identyfikacyjne przypisane do konta Gmail, a następnie zaloguj się.

Po zalogowaniu do interfejsu kliknij ikonę koła zębatego, a następnie `Ustawienia`{.action}. Na stronie, która się wyświetli kliknij zakładkę `Konta i import`{.action}. 

![emailpro](images/configuration-gmail-web-step1.png){.thumbnail}

Obok pozycji `Sprawdź inne konta programu pocztowego`, kliknij `Dodaj konto programu pocztowego`{.action}. W oknie, które się wyświetla wprowadź konto E-mail Pro OVH, następnie kliknij `Dalej`{.action}. Wybierz `Importuj e-maile z innego konta (POP3)`{.action}, następnie ponownie kliknij `Dalej`{.action}.

![emailpro](images/configuration-gmail-web-step2.png){.thumbnail}

Teraz podaj parametry serwera POP (serwer poczty przychodzącej) dla Twojego konta E-mail Pro OVH:

|Informacja|Opis | 
|---|---| 
|Nazwa użytkownika|Wpisz **pełny** adres e-mail.|  
|Hasło|Wpisz hasło przypisane do tego konta e-mail.|
|Serwer POP|Wpisz serwer „pro1.mail.ovh.net”.|
|Port|Wybierz port „995”.|

Opcje, które możesz zaznaczyć:

- **„Zachowaj kopię wiadomości na serwerze”**: zalecamy zaznaczenie tej kratki, jeśli chcesz zachowywać na serwerach OVH kopie wiadomości przychodzących na Twoje konto E-mail Pro;

- **„Kiedy pobierasz Twoje e-maile, zawsze używaj bezpiecznego połączenia (SSL)”**: upewnij się, że zaznaczyłeś tę kratkę, aby połączenie z Twoim kontem E-mail Pro OVH mogło zostać zrealizowane;

- **„Dodaj etykietę do wiadomości przychodzących„**: wybór tej opcji pozwala dodać etykietę do e-maili, które będą importowane z Twojego konta E-mail Pro OVH do Twojego konta Gmail;

- **„Archiwizuj wiadomości przychodzące (tak, aby nie przechodziły przez skrzynkę odbiorczą)”**: wybór tej opcji sprawi, że wiadomości zaimportowane z Twojego konta OVH nie będą się wyświetlały w skrzynce odbiorczej Gmail.

Po uzupełnieniu informacji kliknij przycisk `Dodaj konto`{.action}. Jeśli wpisane informacje są poprawne, logowanie zakończy się sukcesem. 

![emailpro](images/configuration-gmail-web-step3.png){.thumbnail}

Jeśli chcesz również wysyłać e-maile z Twojego konta E-mail Pro OVH przy użyciu interfejsu online programu Gmail, zaznacz kratkę `Tak, chciałbym wysyłać e-maile z konta`{.action}, a następnie kliknij `Dalej`{.action}. 

Następnie wprowadź nazwę nadawcy, która ma się wyświetlać w przypadku wysyłki z konta e-mail, zaznacz kratkę `Traktuj jako alias`{.action}, następnie kliknij przycisk `Następny etap`{.action}.

![emailpro](images/configuration-gmail-web-step4.png){.thumbnail}

Teraz podaj parametry serwera SMTP (serwer poczty wychodzącej) dla Twojego konta e-mail OVH:

|Informacja|Opis | 
|---|---| 
|Serwer SMTP|Wpisz serwer „pro1.mail.ovh.net”.|
|Port|Wybierz port „587”.|
|Nazwa użytkownika|Wpisz **pełny** adres e-mail.|  
|Hasło|Wpisz hasło przypisane do tego konta e-mail.|

Po uzupełnieniu informacji zaznacz kratkę obok `Bezpieczne połączenie TLS`{.action}, następnie kliknij przycisk `Dodaj konto`{.action}. Jeśli wpisane informacje są poprawne, logowanie zakończy się sukcesem. 

![emailpro](images/configuration-gmail-web-step5.png){.thumbnail}

Teraz zatwierdź dodane konto, wprowadzając kod wysłany na Twój adres E-mail Pro OVH.  Aby pobrać kod, zaloguj się jak zwykle do konta OVH, korzystając z interfejsu online dostępnego tutaj: <https://pro1.mail.ovh.net>. 

Po zatwierdzeniu dodanego konta, konto E-mail Pro OVH pojawi się w zakładce `Konta i import`{.action}, którą otworzyłeś na początku operacji.

### Etap 2: korzystanie z konta E-mail Pro przy użyciu interfejsu programu Gmail

Po zakończeniu konfiguracji konto E-mail Pro jest gotowe do użytku. Możesz teraz wysyłać i odbierać wiadomości na konto, używając interfejsu Gmail.

Aby wysłać wiadomość z konta E-mail Pro OVH za pośrednictwem interfejsu online Gmail, po napisaniu wiadomości wybierz konto e-mail OVH. Odpowiednie konto należy zaznaczyć obok pola `Od`{.action} w oknie wiadomości e-mail.

![emailpro](images/configuration-gmail-web-step6.png){.thumbnail}

Pamiętaj, że w celu uzyskania dostępu do Twojego konta E-mail Pro OVH, możesz również użyć interfejsu OVH online dostępnego pod adresem <https://pro1.mail.ovh.net>. Zaloguj się, używając Twoich danych identyfikacyjnych.

## Sprawdź również

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en>.