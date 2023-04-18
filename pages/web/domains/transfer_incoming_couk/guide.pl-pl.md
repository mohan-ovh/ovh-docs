---
title: 'Transfer domeny.uk do OVHcloud'
excerpt: 'W tym przewodniku znajdziesz różne informacje dotyczące transferu domeny .uk lub podobnej do OVHcloud'
updated: 2022-10-19
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk „Zaproponuj zmianę” na tej stronie.
>

**Ostatnia aktualizacja z dnia 20/10/2022**

## Wprowadzenie

Transfer domeny .uk (lub podobnej) wymaga zastosowania specjalnego podejścia.

> [!warning]
>
> OVHcloud udostępnia różnorodne usługi, jednak to Ty odpowiadasz za ich konfigurację i zarządzanie nimi. Ponosisz więc odpowiedzialność za ich prawidłowe funkcjonowanie.
>
> Oddajemy w Twoje ręce niniejszy przewodnik, którego celem jest pomoc w wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy wyspecjalizowanego webmastera lub kontakt z producentem oprogramowania. Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji [Sprawdź również](#gofurther) ten przewodnik.
>

**Dowiedz się, jak przenieść domenę .uk (lub podobną) na OVHcloud**

> [!warning]
>
> Jeśli nazwa domeny w trakcie modyfikacji jest aktualnie zarejestrowana w OVHcloud, transfer przychodzący domeny nie jest właściwą procedurą. Procedura ta dotyczy wyłącznie zmiany zarejestrowanej domeny (OVHcloud).
>
> Aby przenieść zarządzanie domeną na inne konto klienta OVHcloud, należy wykonać *zmianę kontaktów*. Procedura jest opisana w [tym przewodniku](/pages/account/customer/managing_contacts).
>
> Jeśli chcesz zmienić również **właściciela** domeny, musisz to zrobić **przed** zmianą kontaktów domeny. W tym celu postępuj zgodnie z instrukcjami zawartymi w przewodniku OVHcloud dotyczącym [zmiany właściciela domen](/pages/web/domains/trade_domain).
>

## Wymagania początkowe

- Twoja domena nie może być **odkupienia** ani usunięta.
- Domena nie może zostać zablokowana u Twojego operatora. 
- Dane kontaktowe właściciela muszą być aktualne w [bazie whois](https://www.nominet.uk/whois/){.external} domeny.
- Otrzymasz kod autoryzacyjny, który zostanie wysłany na adres e-mail właściciela.

> [!primary]
>
> Okres **odkupienia** wynosi maksymalnie 90 dni od dnia wygaśnięcia domeny. W przypadku transferu ten czas pozwala na przywrócenie domeny i odblokowanie możliwości jej transferu.

## Rozszerzenia

- .uk
- .co.uk
- .ac.uk
- .gov.uk
- .me.uk
- .net.uk
- .org.uk
- .plc.uk
- .sch.uk

## W praktyce

### Procedura transferu

#### Etap 1: Zmiana APR dla domeny

Aby móc przenieść domenę do OVHcloud, należy najpierw podać TAG OVHcloud u obecnego operatora. OVHcloud otrzymuje oznaczenie "OVH-FR". Lista TAGS poszczególnych operatorów jest dostępna na oficjalnej stronie internetowej [Nominet](https://registrars.nominet.uk/uk-namespace/registrar-agreement/list-of-registrars/){.external}.

> [!primary]
>
> Jeśli nie możesz wykonać modyfikacji Tag domeny za pomocą
> Twój obecny rejestr - możesz złożyć wniosek w Rejestrze
> Zmień nazwę użytkownika.
> Przekieruj się na stronę Registry: "Manage your domain - Change registrar".
> Uwaga, ta operacja jest płatna przez Nominet.
>

#### Etap 2: Uzyskanie kodu autoryzacji transferu

Po zmianie APR właściciel domeny po kilku minutach otrzyma e-mail z kodem autoryzacyjnym ("authcode"). Certyfikat, ważny przez 5 dni, pozwoli rozpocząć (bezpłatnie) zamawianie domeny w OVHcloud.

#### Etap 3: Bezpłatne zamówienie na transfer

Po uzyskaniu kodu autoryzacyjnego możesz wyszukać i rozpocząć transfer domeny na [stronę OVHcloud](https://www.ovhcloud.com/pl/). Zamówienie jest podobne do innych domen globalnych.

Twoja domena zostanie wyświetlona w [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) w ciągu kilku godzin.

### Przydatne informacje

#### Koszt transferu domeny z rozszerzeniem .uk (lub równorzędny)

Transfer jest bezpłatny.

#### Ważność kodeksu autoryzacji

Kod autoryzacji jest generowany automatycznie po zmianie GAR. Jeśli zamówienie nie zostanie zrealizowane w ciągu 5 dni, transfer zostanie anulowany.

#### Odnowienie domeny po transferze

Transfer jest darmowy. Data wygaśnięcia domeny po jego przeniesieniu będzie taka sama jak przed jego przeniesieniem. Aby odnowić usługę po jej przeniesieniu, przejdź na [stronę OVHcloud](https://www.ovh.co.uk/cgi-bin/order/renew.cgi).

## Sprawdź również <a name="gofurther"></a>

[Transfer domeny do OVHcloud](/pages/web/domains/transfer_incoming_generic_domain)

Dołącz do społeczności naszych użytkowników na stronie<https://community.ovh.com/en/>.
