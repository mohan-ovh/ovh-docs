---
title: Skonfigurować NAS-HA na serwerze Windows poprzez CIFS
excerpt: Ten przewodnik pokazuje, jak zamontować NAS-HA w systemie Windows Server poprzez CIFS.
updated: 2021-11-22
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk "Zgłóś propozycję modyfikacji" na tej stronie.
>

## Wprowadzenie

Konfiguracja i zamontowanie przestrzeni dyskowej NAS-HA OVHcloud na serwerze Windows przy użyciu systemu CIFS.

## Wymagania początkowe

- Posiadanie [Serwer dedykowany](https://www.ovhcloud.com/pl/bare-metal/), **lub**  [VPS](https://www.ovhcloud.com/pl/vps/) **lub** [instancja Public Cloud](https://www.ovhcloud.com/pl/public-cloud/) z dystrybucją Windows.
- Posiadanie usługi [NAS-HA](https://www.ovh.pl/nas/)

### Ustawienia

- **Windows Server 2008**: Kliknij menu `Start`{.action} > `All the programs`{.action} > `Accessories`{.action} > `Command prompt`{.action}.
- **Windows Server 2012**: Kliknij ikonę `Windows PowerShell`{.action} u dołu ekranu na pasku zadań.
- **Windows Server 2016**: Kliknij menu `Start`{.action}, a następnie na ikonę `Windows PowerShell`{.action}.
- **Windows Server 2019**: Kliknij menu `Start`{.action}, a następnie na ikonę `Windows PowerShell`{.action}.

Teraz wprowadź następującą komendę:

```bash
net use z: \\CIFS_SERVER_IP\CIFS_PATH
```

### Przykłady

- Montowanie CIFS dla NAS-HA:

```bash
net use z: \\10.16.101.8\zpool-000206_PARTITION_NAME_1
```

> [!alert]
>
> Użytkownikiem SMB/CIFS jest `nobody`. Zmiana uprawnień tego użytkownika może spowodować konflikty z istniejącymi uprawnieniami systemu plików NFS 
> 

## Sprawdź również

[Najczęściej zadawane pytania dotyczące technologii NAS](/pages/storage_and_backup/file_storage/ha_nas/nas_faq)

Jeśli potrzebujesz szkolenia lub pomocy technicznej w celu wdrożenia naszych rozwiązań, skontaktuj się z przedstawicielem handlowym lub kliknij [ten link](https://www.ovhcloud.com/pl/professional-services/), aby uzyskać wycenę i poprosić o spersonalizowaną analizę projektu od naszych ekspertów z zespołu Professional Services.

Dołącz do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
