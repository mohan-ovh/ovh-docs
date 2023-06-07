---
title: Object Storage Swift - Konfiguracja automatycznego usuwania obiektów
excerpt: Konfiguracja automatycznego usuwania obiektów
slug: pcs/configure-automatic-object-deletion
section: OpenStack Swift Storage Class Specifics
legacy_guide_number: g1950
order: 070
updated: 2021-10-27
---

**Ostatnia aktualizacja z dnia 27/10/2021**

## Wprowadzenie

Aby uprościć zarządzanie usługą Object Storage, być może będziesz musiał zadecydować o długości życia niektórych plików.
Może to na przykład pozwolić Ci na zachowanie niektórych kopii zapasowych tylko przez określony czas.
Przewodnik ten wyjaśnia, jak usuwać pliki w sposób automatyczny po określonym czasie lub w określonym terminie.

## Wstępne wymagania

- [Przygotowanie środowiska do korzystania z API OpenStack](https://docs.ovh.com/pl/public-cloud/prepare_the_environment_for_using_the_openstack_api/)
- [Pobieranie zmiennych środowiskowych OpenStack](https://docs.ovh.com/pl/public-cloud/set-openstack-environment-variables/)

## W praktyce

Istnieją 2 sposoby usuwania plików:

- Po określonym czasie
- W określonym terminie

### Po określonym czasie

Aby to wykonać, należy skonfigurować header `X-Delete-After` dla obiektów:

```bash
root@server:~$ swift post --header "X-Delete-After: 3600" container test.txt
```

Plik test.txt zostanie usunięty po 1 godzinie.

### W określonym terminie

Najpierw trzeba poznać datę usunięcia w formacie epoch.
Można korzystać z [konwertera](http://www.epochconverter.com/){.external}, aby sprawdzić wartość do wpisania.

Następnie można wpisać tę datę w nagłówku (header) `X-Delete-At`:

```bash
root@server:~$ swift post --header "X-Delete-At: 1668877261000" container test.txt
```

Plik test.txt zostanie usunięty 19/11/2022 roku.

## Sprawdź również
 
Jeśli potrzebujesz szkolenia lub pomocy technicznej w celu wdrożenia naszych rozwiązań, skontaktuj się z przedstawicielem handlowym lub kliknij [ten link](https://www.ovhcloud.com/pl/professional-services/), aby uzyskać wycenę i poprosić o spersonalizowaną analizę projektu od naszych ekspertów z zespołu Professional Services.

Dołącz do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
