---
title: Możliwości techniczne
slug: mozliwosci-techniczne
excerpt: 'Poznaj możliwości i ograniczenia techniczne rozwiązań Hosted Private Cloud dostarczanych przez OVHcloud'
section: FAQ
order: 2
updated: 2021-08-18
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk „Zaproponuj zmianę” na tej stronie.
>

**Ostatnia aktualizacja z dnia 18/08/2021**

## Wprowadzenie

**Na stronie tej znajdziesz przegląd funkcji i ograniczeń technicznych usług Hosted Private Cloud OVHcloud.**

## Znane możliwości i ograniczenia

| Element | Opis | Wartość |
|:-----:|:-----:|:----------:|
| Maksymalna liczba Hosted Private Cloud na identyfikator klienta | Liczba vCenter lub pakietów na organizację | Brak limitu |
| Liczba powiązanych PCC | Połączenie vCenters (Enhanced Link Mode) | 0 (niedozwolony) |
| Minimalna liczba hostów na PCC (SLA) | Liczba hostów w vCenter do utrzymania regulaminu poziomu usługi | 2 |
| Minimalna liczba hostów na PCC (bez SLA) | Minimalna liczba hostów do wykorzystania z vCenter bez umowy na gwarantowany poziom usługi | 0 |
| Maksymalna liczba hostów na klaster | Hosty na klaster | 64 |
| Maksymalna liczba klastrów na vDC | Liczba klastrów w tym samym wirtualnym centrum danych | Brak limitu |
| Maksymalna liczba vDC z wykorzystaniem PCC | Liczba wirtualnych centrów danych (vDC), które klienci mogą dodać przez vCenter | 400 |
| Maksymalna liczba hosty z wykorzystaniem PCC | Limity hostów na vCenter | Zakres **Hostów**: 340 hosty, 70 zpoole<br>plaża **Hybrid**: 241 hosty, 120 zpoole<br>Zakres **BigDS**: 76 hosty, 205 zpoole |
| Maksymalna liczba wirtualnych maszyn przez SDDC | VM zarządzane przez ten sam vCenter | 25 000 |
| Maksymalna liczba wirtualnych maszyn na hosta | VM zainstalowane na tym samym fizycznym hoście | 1024 |
| Maksymalna liczba adresów IP przez PCC | Maksymalna liczba publicznych adresów IP, które mogą być przypisane i używane przez vCenter | 1 x /23 |
| vCPUs, RAM i dysk używane przez standardowe vCenter | Zasoby przeznaczone na vCenter (VCSA) | 4 wirtualnych procesorów, 16 GB pamięci RAM, 290 GB przestrzeni dyskowej |
| vCPUs, pamięci RAM i dysku używane przez NSX standard | Zasoby przeznaczone dla managera i sterownika NSX | 4 wirtualny procesor, 4 GB pamięci RAM, 60 GB przestrzeni dyskowej<br>4 wirtualny procesor, 2 GB pamięci RAM, 28 GB przestrzeni dyskowej |
| vCPUs, RAM i dysk używane przez vROPS | Zasoby przeznaczone na vROPS | 4 wirtualnych procesorów, 16 GB pamięci RAM |
| Maksymalna liczba edge nodes | Maksymalna liczba z urządzeń typu edge, które mają być wdrażane przez NSX | 2000 |
| Maksymalna liczba tuneli VPN IPSec | Maksymalna liczba tuneli VPN na edge | 512 compact edge<br>1600 large<br>4096 kwadrokopter<br>6000 extra large |
| Maksymalna liczba vRack na vDC | Maksymalna liczba prywatnych sieci przez Virtual Data Center (VDC) | 1 |
| Maksymalna liczba klientów VPN L2 | Liczba klientów VPN do połączenia | 5 |
| Maksymalna liczba upoważnionych adresów IP | Liczba adresów IP upoważnionych do łączenia się z Twoją infrastrukturą VMware | 2048 |

## Sprawdź również

Dołącz do społeczności naszych użytkowników na <https://community.ovh.com/en/>.
