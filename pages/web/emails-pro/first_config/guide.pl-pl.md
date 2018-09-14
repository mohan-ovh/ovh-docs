---
title: 'Konfiguracja konta E-mail Pro'
slug: pierwsza-konfiguracja-email-pro
excerpt: 'Dowiedz się, jak skonfigurować konto E-mail Pro'
section: 'Informacje ogólne'
---

**Ostatnia aktualizacja z dnia 28-08-2018**

## Wprowadzenie

Właśnie zakupiłeś usługę E-mail Pro. Umożliwia ona korzystanie z profesjonalnych kont e-mail w najlepszej cenie pozwalającej na prowadzenie bieżącej działalności lub rozpoczęcie nowej.

**Dowiedz się, jak przeprowadzić konfigurację usługi E-mail Pro.**

## Wymagania początkowe

- Wykupienie skrzynek [E-mail Pro](https://www.ovh.pl/emaile/email-pro/){.external}
- Otrzymanie wiadomości e-mail z potwierdzeniem, że usługa E-mail Pro została zainstalowana
- Zarejestrowana domena
- Dostęp do [Panelu klienta OVH](https://www.ovh.com/auth/?action=gotomanager){.external}

## W praktyce

### Etap 1: logowanie do usługi E-mail Pro

Po utworzeniu i udostępnieniu usługi E-mail Pro, można nią zarządzać poprzez [Panel klienta OVH](https://www.ovh.com/auth/?action=gotomanager){.external}.

Zaloguj się do `Panelu klienta`{.action}, kliknij E-mail Pro na pasku usług po lewej stronie, następnie wybierz odpowiednią usługę.

> [!primary]
>
> Nazwa usługi E-mail Pro w Panelu klienta zaczyna się od *emailpro-*, następnie zawiera część Twojego identyfikatora klienta i kończy się cyfrą (1 dla pierwszej zainstalowanej usługi E-mail Pro, 2 dla drugiej, etc.).
>

### Etap 2: dodanie domeny

Jeśli właśnie zamówiłeś usługę E-mail Pro, automatycznie wyświetli się okno, w którym zostaniesz poproszony o `Dodanie domeny`{.action}. Jeśli okno się nie wyświetla, przejdź do zakładki `Powiązane domeny`{.action}, następnie kliknij przycisk `Dodaj domenę`{.action}.

Masz do wyboru następujące czynności:

- **wybierz domenę z listy**: wyświetlają się jedynie domeny skonfigurowane w OVH i którymi zarządzasz w koncie klienta;
- **wpisz domenę, która nie jest zarządzana na Twoim koncie OVH**: aby usługa E-mail Pro działała poprawnie, musisz mieć możliwość modyfikacji konfiguracji domeny (jej strefy DNS).

Po wybraniu opcji kliknij `Dalej`{.action}.

![emailpro](images/first_config_email_pro_add_domain.png){.thumbnail}

Okno wyświetla teraz informacje dotyczące konfiguracji trybów.

- **Jeśli podałeś nazwę domeny nieobsługiwanej przez OVH**: zostanie domyślnie skonfigurowany tryb nieautorytatywny.
- **Jeśli wybrałeś z listy nazwę domeny obsługiwanej przez OVH**: wybierz jeden z trybów.

|Tryb|Opis|
|---|---|
|Autorytatywny|Odpowiedni, jeśli do obsługi poczty w Twojej domenie używasz jedynie usługi E-mail Pro. Nie pozwala na korzystanie z innego rozwiązania poczty elektronicznej w połączeniu z usługą E-mail Pro.|
|Nieautorytatywny|Odpowiedni, jeśli do obsługi Twojej domeny używasz kont E-mail Pro oraz jednocześnie innego rozwiązania poczty elektronicznej.| 

> [!primary]
>
> Wybór trybu nie jest ostateczny i możesz zmienić go później w Panelu klienta.
>

Kliknij przycisk `Dalej`{.action}, aby kontynuować proces dodawania domeny.

![emailpro](images/first_config_email_pro_add_domain_step2.png){.thumbnail}

**Jeśli wybrałeś z listy nazwę domeny obsługiwaną przez OVH**, jej konfiguracja może zostać przeprowadzona automatycznie. W celu przeprowadzenia automatycznej konfiguracji zaznacz odpowiednie pola i kliknij `Dalej`{.action}, aby kontynuować proces dodawania domeny.

**Jeśli podałeś nazwę domeny nieobsługiwanej przez OVH**, konfiguracja powinna zostać przeprowadzona na kolejnym etapie.

![emailpro](images/first_config_email_pro_add_domain_step3.png){.thumbnail}

Przed zakończeniem konfiguracji sprawdź wyświetlające się informacje, następnie kliknij przycisk `Zatwierdź`{.action}, aby zakończyć proces dodawania domeny.

### Etap 3: konfiguracja nazwy domeny

Po dodaniu nazwy domeny jako domeny powiązanej sprawdź jej ustawienia, korzystając z wyświetlającej się tabeli.

W kolumnie `Diagnostyka`{.action} możesz sprawdzić konfigurację pól MX nazwy domeny. Jeśli parametry powinny zostać zmodyfikowane, wyświetli się czerwony przycisk.

- **Jeśli podczas dodawania domeny wybrałeś automatyczną konfigurację**: wprowadzone ustawienia mogą wyświetlić się w Panelu klienta po kilku godzinach;
- **Jeśli wprowadziłeś nazwę domeny nieobsługiwanej przez OVH**: kliknij czerwony przycisk, aby wyświetlić listę modyfikacji do wprowadzania. Jeśli właśnie wprowadziłeś zmiany, mogą się one wyświetlić się w Panelu klienta po kilku godzinach.

![emailpro](images/first_config_email_pro_configure_domain.png){.thumbnail}

Możesz również dodać opcjonalnie pole SRV do konfiguracji Twojej domeny. Powinno ono umożliwić programowi pocztowemu lub urządzeniu, takiemu jak _smartphone_ czy tablet automatyczne pobranie elementów koniecznych do skonfigurowania Twojego konta E-mail Pro (serwery, porty i protokoły bezpieczeństwa).

Jeśli nie chcesz korzystać z tej możliwości, przejdź od razu do etapu nr 4. W przeciwnym razie dodaj pole SRV w interfejsie dostawcy zarządzającego konfiguracją DNS Twojej domeny. Jeśli jest nim OVH, postępuj zgodnie z instrukcjami podanymi w naszej dokumentacji [Edycja strefy DNS OVH](https://docs.ovh.com/pl/domains/hosting_www_jak_edytowac_strefe_dns/){.external}. Użyj poniższych elementów:

|Domena|Typ rekordu|Priorytet|Waga|Port|Adres docelowy|
|---|---|---|---|---|---|
|_autodiscover._tcp.*mypersonaldomain.ovh*_|SRV|0|0|443|autodiscover.mail.ovh.net.|

Pamiętaj, żeby zastąpić ogólną informację „mypersonaldomain.ovh” nazwą Twojej domeny.

### Etap 4: konfiguracja i korzystanie z kont E-mail Pro

Skonfiguruj konta e-mail w zakładce `Konta e-mail`{.action}. Konta, które zamówiłeś wyświetlają się w tabeli w postaci “*@configureme.me*”.

Aby przeprowadzić konfigurację kont, kliknij ikonę ołówka.

![emailpro](images/first_config_email_pro_configure_email_accounts.png){.thumbnail}

Teraz uzupełnij kolejne informacje, o które zostaniesz poproszony.

|Nazwa|Opis |
|---|---|
|Konto e-mail|Wprowadź nazwę, którą wybrałeś dla Twojego konta e-mail (np. Twoje imie.nazwisko) i wybierz z listy odpowiednią domenę.|
|Imię|Wprowadź imię.|
|Nazwisko|Wprowadź nazwisko.|
|Nazwa, która będzie się wyświetlać.|Wpisz nazwę nadawcy, która będzie się wyświetlać podczas wysyłki wiadomości e-mail przy użyciu tego konta.|
|Hasło i jego potwierdzenie|Wpisz hasło i je potwierdź.| 

Po wprowadzeniu informacji, kliknij przycisk `Dalej`{.action}, sprawdź dane, które się wyświetlają, następnie kliknij `Potwierdź`{.action}, aby rozpocząć konfigurację konta.

> [!primary]
>
> Wykonaj czynności tego etapu tyle razy, ile to konieczne, w zależności od liczby kont, które posiadasz. Możesz zamówić nowe konta, klikając przycisk `Zamówienie kont`{.action}.
>

![emailpro](images/first_config_email_pro_configure_email_accounts_step2.png){.thumbnail}

### Etap 5: korzystanie z kont e-mail

Po skonfigurowaniu Twoich kont możesz zacząć ich używać. W tym celu możesz użyć udostępnionej przez OVH aplikacji online (*webapp*). Aplikacja dostępna jest pod adresem <https://pro1.mail.ovh.net>. Zaloguj się, wprowadzając dane identyfikacyjne przypisane do Twojego konta e-mail utworzonego w OVH.

Jeśli chcesz skonfigurować Twoje konto e-mail w programie pocztowym lub na urządzeniu typu smartfon lub tablet, skorzystaj z naszej dokumentacji dostępnej tutaj: <https://docs.ovh.com/pl/emails-pro/>. Poniżej znajdziesz elementy potrzebne do konfiguracji Twojego konta E-mail Pro:

|Typ serwera|Nazwa serwera|Typ zabezpieczenia|Port|
|---|---|---|---|
|Serwer poczty przychodzącej|pro1.mail.ovh.net|SSL/TLS|993|
|Serwer poczty wychodzącej|pro1.mail.ovh.net|STARTTLS|587|

## Sprawdź również

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.