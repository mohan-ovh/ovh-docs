---
title: NAS-HA - Zarządzanie ACL przez API
excerpt: Dowiedz się, jak zarządzać dostępami do NAS HA za pomocą API OVHcloud
updated: 2022-07-20
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk "Zgłóś propozycję modyfikacji" na tej stronie.
> 

**Ostatnia aktualizacja z dnia 20-07-2022**

## Wprowadzenie

Usługa NAS-HA OVHcloud pozwala na zarządzanie przestrzenią dyskową plików dostępną z poziomu sieci.

**Niniejszy przewodnik wyjaśnia, jak zarządzać ACL partycji NAS-HA za pomocą interfejsu API OVHcloud.**

## Wymagania początkowe

- Usługa [NAS-HA OVHcloud](https://www.ovh.pl/nas/)
- Zapoznaj się z naszym przewodnikiem Pierwsze kroki z [API OVHcloud](/pages/manage_and_operate/api/first-steps), aby zapoznać się z APIv6 OVHcloud

## W praktyce

Wszystkie drogi API w tym przewodniku są dostępne w sekcji */dedicated/nasha*: <https://api.ovh.com/console/#/dedicated/nasha>.

> [!primary]
>
> Podczas korzystania z API wszystkie pola oznaczone gwiazdką (\*) są obowiązkowe.
>

### Pobranie informacji o usłudze

Wszystkie Twoje aktywne usługi można odzyskać przy użyciu następującej drogi:

> [!api]
>
> @api {GET} /dedicated/nasha
>

> [!warning]
>
> Dostęp nie jest domyślnie udzielany, chyba że jest udzielany za pośrednictwem ACL. Można dodać wyłącznie adresy IP przypisane do Twoich usług OVHcloud.
>

### Pobierz ACL partycji

Aby pobrać adresy IP, które mogą mieć dostęp do partycji, użyj następującej drogi:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/access
>> >
>>
>
> Ustawienia:
>
>> > **serviceName** *
>> >
>> >> Nazwa wewnętrzna usługi NAS-HA
>> >
>> > **partitionName** *
>> >
>> >> Nazwa partycji
>

### Pobranie wszystkich kwalifikujących się adresów IP

Możesz sprawdzić adresy IP kwalifikujące się do dostępu za pomocą następujących wywołań API:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/authorizableIps
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/authorizableBlocks
>> >
>>
>
> Ustawienia:
>
>> > **serviceName** *
>> >
>> >> Wewnętrzna nazwa usługi NAS-HA
>> >
>> > **partitionName** *
>> >
>> >> Nazwa partycji
>

### Dodanie wpisu ACL

Aby utworzyć nowy wpis ACL umożliwiający logowanie do partycji, użyj następującej drogi:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {POST} /dedicated/nasha/{serviceName}/partition/{partitionName}/access
>> >
>>
>
> Ustawienia:
>
>> > **serviceName** *
>> >
>> >> Nazwa wewnętrzna usługi NAS-HA
>> >
>> > **partitionName** *
>> >
>> >> Nazwa partycji
>> >
>> > **ip** *
>> >
>> >> Adres IP lub zakres, w jakim należy udzielić dostępu
>> >
>> > **type** *
>> >
>> >> Typ dostępu ACL dla tego wpisu: *readonly* lub *readwrite*
>

> [!primary]
>
> Użyj ratingu CIDR dla pul IP, na przykład: 192.0.2.0/24.
>

### Usunięcie wpisu ACL

Aby usunąć adres IP lub zakres adresów ACL, użyj następującej drogi:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {DELETE} /dedicated/nasha/{serviceName}/partition/{partitionName}/access/{ip}
>> >
>>
>
> Ustawienia:
>
>> > **serviceName** *
>> >
>> >> Nazwa wewnętrzna usługi NAS-HA
>> >
>> > **partitionName** *
>> >
>> >> Nazwa partycji
>> >
>> > **ip** *
>> >
>> >> Adres IP lub zakres, który ma zostać odrzucony
>

## Sprawdź również

[Montowanie przestrzeni dyskowej NAS przy użyciu protokołu NFS](/pages/storage_and_backup/file_storage/ha_nas/nas_nfs)

[Skonfigurować NAS na serwerze Windows poprzez CIFS](/pages/storage_and_backup/file_storage/ha_nas/nas_cifs)

Jeśli potrzebujesz szkolenia lub pomocy technicznej w celu wdrożenia naszych rozwiązań, skontaktuj się z przedstawicielem handlowym lub kliknij [ten link](https://www.ovhcloud.com/pl/professional-services/), aby uzyskać wycenę i poprosić o spersonalizowaną analizę projektu od naszych ekspertów z zespołu Professional Services.

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.