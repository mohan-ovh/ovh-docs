---
title: Object Storage Swift - Optymalizacja wysyłki do Object Storage
legacy_guide_number: g1951
updated: 2021-10-27
---

**Ostatnia aktualizacja z dnia 27/10/2021**
  
## Wprowadzenie

Podczas wysyłania dużych plików na Object Storage (na przykład filmów czy obrazów dysków) można korzystać z klienta OpenStack Swift, w celu zoptymalizowania transferu poprzez segmentowanie tych plików.
Przewodnik ten wyjaśnia, jak zwiększyć prędkość wysyłki na Object Storage, dzięki tej funkcjonalności.

## Wstępne wymagania

- [Przygotowanie środowiska do korzystania z API OpenStack](/pages/platform/public-cloud/prepare_the_environment_for_using_the_openstack_api) za pomoca klienta python-swiftclient
- [Zmienne środowiskowe OpenStack](/pages/platform/public-cloud/loading_openstack_environment_variables)

## W praktyce

OpenStack Swift pozwala na przechowywanie plików bez ograniczenia rozmiaru dzieląc pliki na kilka segmentów.

Gdy klient Swift jest wykorzystywany do wysyłania plików, węzeł przestrzeni dyskowej jest określany przez proxy Swift poprzez wykorzystanie haszowania nazwy obiektu.
Możliwe, że segmenty będą przechowywane w różnych węzłach przestrzeni dyskowej, co pozwoli na zapisywanie danych z większą prędkością.

Można więc wysłać plik 10GB w 100 segmentach o rozmiarze 100MB:


```bash
root@server:~$ swift upload --segment-size 104857600 --segment-threads 100
container_name 10Gio.dat
```

|Argument|Opis|
|---|---|
|--segment-size|Rozmiar segmentów w bajtach|
|--segment-threads|Liczba segmentów|


Można zmierzyć prędkość wysyłki wykorzystując programy takie jak iftop.

## Sprawdź również
 
Dołącz do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
