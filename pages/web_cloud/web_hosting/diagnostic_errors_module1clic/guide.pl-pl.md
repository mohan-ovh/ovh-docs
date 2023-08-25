---
title: Rozwiąż najczęstsze błędy związane z modułami za pomocą 1 kliknięcia
excerpt: Zdiagnozuj najczęstsze przypadki błędów związanych z modułami za pomocą 1 kliknięcia
updated: 2023-08-21
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk "Zgłóś propozycję modyfikacji" na tej stronie.
>

## Wprowadzenie 

Utworzenie [modułu za pomocą 1 kliknięcia](/pages/web_cloud/web_hosting/cms_install_1_click_modules) w trybie prostym lub zaawansowanym może spowodować różne nieprawidłowości.

**Dowiedz się, jak zdiagnozować najczęstsze przypadki błędów związanych z modułami za pomocą 1 kliknięcia**

> [!warning]
>
> OVHcloud udostępnia różnorodne usługi, jednak to Ty odpowiadasz za ich konfigurację i zarządzanie nimi. Ponosisz więc odpowiedzialność za ich prawidłowe funkcjonowanie.
>
> Oddajemy w Twoje ręce niniejszy przewodnik, którego celem jest pomoc w wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy wyspecjalizowanego webmastera lub kontakt z producentem oprogramowania. Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji [Sprawdź również](#gofurther) ten przewodnik.
>

## Wymagania początkowe

- Posiadanie kompatybilnego [hostingu](https://www.ovhcloud.com/pl/web-hosting/).
- Dostęp do [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl).
- Korzystanie z funkcji [Module za 1 kliknięciem](/pages/web_cloud/web_hosting/cms_install_1_click_modules), aby utworzyć nową stronę.

## W praktyce

> [!primary]
>
> Wyszczególniamy tutaj najczęstsze błędy. Jeśli zauważysz inną anomalię, zapoznaj się z naszym [FAQ dotyczący hostingu www](https://www.ovhcloud.com/pl/web-hosting/).
>

### "Wystąpił błąd podczas pobierania informacji. (You need at least one free database)"

![1freeDB](images/1freeDB.png){.thumbnail}

Jeśli pojawi się ta wiadomość po uruchomieniu instalacji modułu, nie można utworzyć nowej bazy danych na Twoim hostingu.

#### Rozdział 1: zmień ofertę hostingu

> [!primary]
>
> Zapoznaj się z porównaniem naszych [ofert hostingu](https://www.ovhcloud.com/pl/web-hosting/).
>

W [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) kliknij `Web Cloud`{.action}, a następnie `Hosting`{.action}. Wybierz odpowiedni hosting i kliknij `Zmień ofertę` w sekcji `Abonament` - `Oferta`:

![upgrade_hosting](images/upgrade_hosting.png){.thumbnail}

Dzięki ofercie [Hosting Pro](https://www.ovhcloud.com/pl/web-hosting/professional-offer/) i [Hosting Performance](https://www.ovhcloud.com/pl/web-hosting/performance-offer/) możesz utworzyć do trzech modułów za pomocą 1 kliknięcia. Wraz z pakietem **Hosting Performance** będziesz mógł włączyć za darmo [Web Cloud Databases](https://www.ovhcloud.com/pl/web-hosting/options/start-sql/).

#### Rozdział 2: usuń niewykorzystaną bazę danych <a name="delete-database"></a>

> [!warning]
>
> Operacja usunięcia bazy danych jest ostateczna. Pociąga to również za sobą usunięcie kopii zapasowych odpowiedniej bazy danych. Jeśli nie masz pewności co do przeprowadzenia tych czynności, skontaktuj się z webmasterem lub jednym z naszych [partnerów](https://partner.ovhcloud.com/pl/directory/).
>

Aby usunąć bazę danych, w [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) kliknij pozycję `Web Cloud`{.action}, następnie `Hosting`{.action} i wreszcie `Bazy danych`{.action}. Usuń wybraną bazę danych:

![delete_a_database](images/delete_a_database.png){.thumbnail}

#### Rozdział 3: zamów nowe bazy danych

W [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) kliknij `Web Cloud`{.action}, a następnie `Hosting`{.action}. W `Bazach danych`{.action} kliknij `Operacje`{.action}:

![order_a_database](images/order_a_database.png){.thumbnail}

> [!primary]
>
> Zapoznaj się z porównaniem naszych [ofert baz danych](https://www.ovhcloud.com/pl/web-hosting/options/start-sql/)
>

#### Rozdział 4: zainstalować moduł na bazie danych

Aby zainstalować moduł na bazie danych, której już używasz, [użyj zaawansowanego](/pages/web_cloud/web_hosting/cms_install_1_click_modules#instalacja-w-trybie-zaawansowanym)trybu instalacji nowego **modułu za pomocą 1 kliknięcia**.

Aby odnaleźć dane do logowania do bazy danych, sprawdź nasz [przewodnik](/pages/web_cloud/web_hosting/cms_install_1_click_modules#konfiguracja-modulu).

### "Katalog instalacji nie jest pusty"

![folder_not_empty](images/folder_not_empty.png){.thumbnail}

Po utworzeniu modułu otrzymałeś e-mail z informacją, że katalog instalacyjny modułu nie jest pusty.

Wiadomość ta oznacza, że **Katalog główny** Twojej domeny zawiera jeden lub więcej plików lub katalogów.

Aby powiązać domenę z innym katalogiem, kliknij `Zmień domenę`{.action} w zakładce `MultiSite`{.action}, następnie podaj nazwę nowej **Katalogu głównego** (pusty katalog zostanie automatycznie utworzony na Twoim hostingu).

![modify_root_folder](images/modify_root_folder.png){.thumbnail}

Możesz również połączyć się z hostingiem przez [FTP](/pages/web_cloud/web_hosting/ftp_connection), a następnie usunąć lub przenieść zawartość folderu po jego zapisaniu.

### "Either no configuration (ovhConfig or runtime), or the current configuration is not valid (please, double check the module's requirement) (as a reminder, the global configuration is used for module)".

Wyświetli się komunikat, że plik ".ovhconfig" nie istnieje lub jest nieprawidłowy. Wystarczy, że zainstalujesz "moduł za 1 kliknięciem". Plik ten zawiera wersję PHP oraz środowisko wykonawcze zastosowane do Twojego hostingu.

Zaleca się korzystanie z najnowszej możliwej wersji PHP. **Przed** zmianą konfiguracji pliku ".ovhconfig", jeśli posiadasz inne strony WWW na Twoim hostingu, upewnij się, że są one kompatybilne z nową wersją PHP i/lub nowym środowiskiem wykonawczym, które zastosujesz na Twoim hostingu.

Aby sprawdzić tę konfigurację, zapoznaj się z naszymi przewodnikami:

- [Zmień konfigurację hostingu WWW](/pages/web_cloud/web_hosting/ovhconfig_modify_system_runtime)
- [Konfiguracja pliku .ovhconfig na hostingu](/pages/web_cloud/web_hosting/ovhconfig_configuration)

### "Wystąpił błąd podczas pobierania informacji (There is not enough space on your hosting (you need at least xxx MB))"

![not_enough_space](images/not_enough_space.png){.thumbnail}

Wiadomość ta wskazuje, że [przestrzeń dyskowa](/pages/web_cloud/web_hosting/ftp_connection) Twojego hostingu zawiera zbyt dużą ilość danych. Musisz więc usunąć lub przenieść domenę zanim będziesz mógł zainstalować nowy [moduł za 1 kliknięciem](/pages/web_cloud/web_hosting/cms_install_1_click_modules).

W tej sytuacji [zaloguj się przez FTP](/pages/web_cloud/web_hosting/ftp_connection) na Twoim hostingu [zapisz lokalnie](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide#transfer-plikow), a następnie usuń pliki, które nie są konieczne do działania Twojej strony WWW.

> [!primary]
>
> W przypadku pytań dotyczących danych do usunięcia, w celu zmniejszenia ilości danych na hostingu, skontaktuj się z naszą [społecznością użytkowników](https://community.ovh.com/en/) lub [partnerami OVHcloud](https://partner.ovhcloud.com/pl/directory/).<br>
> Nie będziemy w stanie udzielić wsparcia w tym zakresie.

### "Nie można połączyć się z bazą danych" <a name="delete-module"></a>

![wrong_id_database](images/wrong_id_database.png){.thumbnail}

Po uruchomieniu instalacji modułu w trybie zaawansowanym otrzymałeś wiadomość e-mail z informacją, że moduł nie może się łączyć z wskazaną bazą danych. 

Należy więc sprawdzić dane dostępowe do bazy danych. Aby je znaleźć, sprawdź nasz [przewodnik](/pages/web_cloud/web_hosting/cms_install_1_click_modules#konfiguracja-modulu).

Następnie usuń moduł w zakładce `Moduły za 1 kliknięciem`{.action}:

![delete_a_module](images/delete_a_module.png){.thumbnail}

Następnie uruchom ponownie instalację nowego modułu.

### "You have insufficient rights on this database."

![insufficient_rights](images/insufficient_rights.png){.thumbnail}

Baza danych nie może zostać zmieniona, ponieważ ilość danych w niej zawartych przekracza dozwolony limit. Wiadomość ta pojawia się podczas instalacji modułu w [tryb zaawansowany](/pages/web_cloud/web_hosting/cms_install_1_click_modules#instalacja-w-trybie-zaawansowanym).

W tej sytuacji zainstaluj moduł przechodząc przez [tryb "prosty"](/pages/web_cloud/web_hosting/cms_install_1_click_modules#prosta-instalacja-modulu) lub wybierz inną bazę danych podczas instalacji w trybie zaawansowanym. Jeśli potrzebujesz dodatkowej [oferty baz danych](https://www.ovh.pl/hosting/opcje-sql.xml).

Jeśli nie posiadasz innych baz danych i nie chcesz zamawiać dodatkowej oferty, [zaimportuj kopię bazy](/pages/web_cloud/web_hosting/sql_database_export#en-praktyka) a następnie usuń niepotrzebne dane.

> [!warning]
>
> **Usunięcie elementów z bazy danych może spowodować zablokowanie Twojej strony WWW.**
>
> W przypadku dodatkowych pytań skontaktuj się z naszym [społecznością użytkowników](https://community.ovh.com/en/) lub [partnerami OVHcloud](https://partner.ovhcloud.com/pl/directory/).<br>
> Nie będziemy w stanie udzielić wsparcia w tym zakresie.
>

### "Can't connect to database 'test' at 'xxxxxx-xxx.eu.clouddb.ovh.net'. The error is: Access denied for user 'xxxx'@'xxxxxxxx' (using password: YES)"

![cant_connect](images/cant_connect.png){.thumbnail}

Instalacja modułu za pomocą 1 kliknięcia w [tryb zaawansowany](/pages/web_cloud/web_hosting/cms_install_1_click_modules#prosta-instalacja-modulu) na bazie danych znajdującej się na [serwerze Web Cloud Databases](/pages/web_cloud/web_cloud_databases/starting_with_clouddb). Ten komunikat błędu został wysłany na e-mail. Oznacza to, że zarejestrowany użytkownik podczas instalacji nie posiada wystarczających uprawnień do bazy danych lub że wskazane identyfikatory są nieprawidłowe.

W tej sytuacji najpierw zmodyfikuj [prawa użytkownika](/pages/web_cloud/web_cloud_databases/create-db-and-user-on-db-server#zarzadzanie-prawami-uzytkownikow), aby posiadał on uprawnienia **Administrator** lub **Odczyt/zapis** na bazie danych.

Sprawdź również jego dane do logowania [bezpośrednio](/pages/web_cloud/web_cloud_databases/connecting-to-database-on-database-server#w-praktyce) do serwera baz danych i uruchom ponownie instalację modułu.

### "Can't connect to database 'xxxxxxxx' at 'xxxxxxxx.mysql.db'. The error is: Unknown MySQL server host 'xxxxxxxx.mysql.db'"

![cant_connect_server](images/cant_connect_server.png){.thumbnail}

Instalacja modułu za pomocą 1 kliknięcia w [tryb zaawansowany](/pages/web_cloud/web_hosting/cms_install_1_click_modules#prosta-instalacja-modulu) na bazie danych znajdującej się na [serwerze Web Cloud Databases](/pages/web_cloud/web_cloud_databases/starting_with_clouddb). Ten komunikat błędu został wysłany na e-mail. Oznacza to, że podana przez Ciebie nazwa serwera baz danych jest nieprawidłowa.

Kliknij na `Web cloud`{.action} [Panel klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl), a następnie na zakładkę `Bazy danych`{.action}.

Następnie kliknij wybraną ofertę: nazwa serwera, który ma być użyty, podana jest pod nagłówkiem `Nazwa hosta` w podczęści `SQL` danych do logowania.

### Twoja domena nie jest dostępna podczas tworzenia modułu

![domainenotproposed](images/domainenotproposed.png){.thumbnail}

Kliknij kartę `MultiSite`{.action}, po czym przeprowadź następujące kontrole:

|Scenariusz|Co należy zrobić?|
|---|---|
|Domena lub subdomena przypisana do strony, którą chcesz utworzyć nie wyświetla się w opcji `MultiSite`{.action}.|Dodaj swoją domenę zgodnie z [tymi wskazówkami](/pages/web_cloud/web_hosting/multisites_configure_multisite#etap-2-dodanie-domeny-lub-subdomeny).|
|Domena została usunięta z strony podpiętej w opcji MultiSite bez konieczności wykonywania przez Ciebie żadnych czynności.|Jeśli Twoja domena lub [Strefa DNS](/pages/web_cloud/domains/dns_zone_edit#zrozumienie-pojecia-dns) nie są zarządzane z poziomu konta OVHcloud, dodaj domenę do `MultiSite`{.action} zgodnie z [tym przewodnikiem](/pages/web_cloud/web_hosting/multisites_configure_multisite#etap-22-dodaj-domene-zewnetrzna).|

### Twój moduł wyświetla się na koncie www typu "xxxxx.cluster0xx.hosting.ovh.net"

![url-cluster](images/url-cluster.png){.thumbnail}

Po wykonaniu wszystkich niezbędnych kopii zapasowych [usuń moduł](#delete-module), następnie jego [bazę danych](#delete-database). Następnie uruchom ponownie instalację dla wybranej domeny.

### Twoja stara strona wciąż się wyświetla

Ta nieprawidłowość może mieć kilka przyczyn:

- Dokonałeś ostatnio zmiany strefy lub serwerów [DNS](/pages/web_cloud/domains/dns_zone_edit#zrozumienie-pojecia-dns) lub [transferu domeny](/pages/web_cloud/domains/transfer_incoming_generic_domain). Odczekaj, aż operacje te zostaną zakończone (48 godziny w przypadku zmiany serwerów DNS). Pamiętaj, aby zrestartować urządzenia (komputer, smartfon, box, etc.) i usunąć cache przeglądarki.

- Twoja domena jest zawsze powiązana z Twoim poprzednim hostingiem. W tym przypadku zmień [strefę DNS](/pages/web_cloud/domains/dns_zone_edit#modyfikacja-strefy-dns-domeny) lub [serwery DNS](/pages/web_cloud/domains/dns_server_general_information#zmien-serwery-dns) lub skontaktuj się z aktualnym dostawcą usług hostingowych.

### Hasło "Administrator" dostępu do "back-office" modułu za pomocą 1 kliknięcia nie działa <a name="adminpassword"></a>

W przypadku odrzucenia Twojego aktualnego hasła do interfejsu administracyjnego Twojego CMS, zapoznaj się z sekcją "Zmiana hasła do Twojego modułu" w dokumentacji dotyczącej [zarządzanie modułem za pomocą 1 kliknięcia](/pages/web_cloud/web_hosting/cms_manage_1_click_module#password-change).

## Sprawdź również <a name="gofurther"></a>

[Jak zdiagnozować białą stronę?](/pages/web_cloud/web_hosting/diagnostic_fix_500_internal_server_error)

Skontaktuj się z [partnerami OVHcloud](https://partner.ovhcloud.com/pl/directory/), jeśli chcesz wykonać specjalistyczne operacje (pozycjonowanie, rozwój, itp.)

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i korzystania z rozwiązań OVHcloud, sprawdź naszą [ofertę wsparcia](https://www.ovhcloud.com/pl/support-levels/).

Dołącz do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
