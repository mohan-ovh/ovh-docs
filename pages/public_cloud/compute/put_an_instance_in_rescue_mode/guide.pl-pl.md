---
title: 'Przełączenie instancji w tryb rescue'
excerpt: 'Ten przewodnik zawiera informacje o przełączaniu instancji w tryb ratunkowy (rescue)'
legacy_guide_number: g2029
updated: 2023-01-04
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk "Zgłóś propozycję modyfikacji" na tej stronie.
> 

**Ostatnia aktualizacja z dnia 04-01-2023**

## Wprowadzenie

Jeśli instancja została niewłaściwie skonfigurowana lub utracono klucz SSH, instancja może być niedostępna.

W takiej sytuacji można ponownie skonfigurować instancję lub odzyskać dane przy użyciu trybu ratunkowego (rescue). 

**Ten przewodnik zawiera informacje o przełączaniu instancji w tryb ratunkowy (rescue)**

## Wymagania początkowe

* [Instancja Public Cloud](https://www.ovhcloud.com/pl/public-cloud/){.external} utworzona na koncie OVHcloud
* dostęp do [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl){.external}
* dostęp administracyjny (uprawnienia użytkownika root) do instancji za pośrednictwem protokołu SSH

## W praktyce> 

[!alert]
>
> Do tej pory tryb Rescue dla instancji Metal nie jest dostępny w panelu klienta OVHcloud. Aby uzyskać więcej informacji, zapoznaj się z naszym przewodnikiem dotyczącym [trybu Rescue dla instancji Metal](/pages/public_cloud/compute/rescue_mode_metal_instance).


### Aktywacja trybu ratunkowego

Najpierw zaloguj się do [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl){.external} i kliknij menu `Public Cloud`{.action}.

Następnie wybierz projekt Public Cloud z menu bocznego po lewej stronie ekranu i przejdź do pozycji Instancje.

Kliknij ikonę z trzema kropkami (po prawej stronie instancji) i wybierz `Restartuj w trybie ratunkowym`{.action}.

![control panel](images/rescue2022.png){.thumbnail}

Zostanie wyświetlone okno dialogowe “Restart w trybie ratunkowym”. Kliknij listę rozwijaną, aby wybrać dystrybucję systemu Linux do użycia w trybie ratunkowym, a następnie kliknij przycisk `Uruchom ponownie`{.action}.

![control panel](images/rescue2.png){.thumbnail}

Po ponownym uruchomieniu instancji w trybie Rescue wyświetli się okno informacyjne zawierające dostępne metody dostępu. Twoje **hasło do trybu Rescue** tymczasowego będzie wyświetlane tylko w konsoli VNC. Kliknij Twoją instancję w tabeli, następnie przejdź do zakładki `Konsola VNC`{.action}, aby pobrać instancję.

![control panel](images/rescuedata.png){.thumbnail}


### Dostęp do danych

Po aktywacji trybu ratunkowego dane instancji będą widoczne jako dodatkowy dysk. Aby go zamontować, wykonaj następujące kroki.

Po pierwsze nawiąż połączenie SSH z instancją. Po nawiązaniu połączenia sprawdź dostępne dyski przy użyciu tego polecenia:

```
root@instance:/home/admin# lsblk

NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
vda 253:0 0 1G 0 disk
└─vda1 253:1 0 1023M 0 part /
vdb 253:16 0 10G 0 disk
└─vdb1 253:17 0 10G 0 part
```

Następnie zamontuj partycję:

```
root@instance:/home/admin# mount /dev/vdb1 /mnt
```

Dane będą dostępne w folderze /mnt.

### Dezaktywacja trybu ratunkowego

Po wykonaniu wszystkich zadań można zdezaktywować tryb ratunkowy przez zrestartowanie instancji w trybie normalnym. Aby to zrobić, kliknij strzałkę menu rozwijanego instancji i wybierz pozycję `Wyjdź z trybu ratunkowego`{.action}.

![control panel](images/rescueexit2022.png){.thumbnail}

> [!warning]
> Jeśli przycisk `Wyjdź z trybu ratunkowego`{.action} nie pojawi się po wykonaniu instancji w trybie rescue, zalecamy odświeżenie karty.
>

### Aktywacja trybu ratunkowego przy użyciu interfejsu API OpenStack

Tryb ratunkowy można aktywować także za pośrednictwem interfejsu API OpenStack przy użyciu następującego polecenia:

```
# root@server:~# nova rescue INSTANCE_ID
```

Aby wyjść z trybu ratunkowego, użyj następującego polecenia:

```
# root@server:~# nova unrescue INSTANCE_ID
```

## Sprawdź również

Dołącz do naszej społeczności użytkowników: <https://community.ovh.com/en/>.