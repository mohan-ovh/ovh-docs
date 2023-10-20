---
title: HA-NAS - ACLs verwalten
excerpt: Erfahren Sie hier, wie Sie den Zugriff auf ein HA-NAS mit der OVHcloud API verwalten
updated: 2022-07-20
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel

OVHcloud HA-NAS Dienste ermöglichen Ihnen die Verwaltung zentral gespeicherter Dateien, die über ein Netzwerk zugänglich sind.

**Diese Anleitung erklärt, wie Sie die ACL einer HA-NAS Partition über die OVHcloud API verwalten.**

## Voraussetzungen

- Sie haben ein [OVHcloud HA-NAS](https://www.ovh.com/de/nas/) in Ihrem Kunden-Account.
- Sie haben sich anhand der [Anleitung zu den ersten Schritten mit der OVHcloud API](/pages/manage_and_operate/api/first-steps) mit der Verwendung der OVHcloud APIv6 vertraut gemacht.

## In der praktischen Anwendung

Alle API-Routen in dieser Anleitung sind im Bereich */dedicated/nasha* verfügbar: <https://api.ovh.com/console/#/dedicated/nasha>.

> [!primary]
>
> Bei der Verwendung der API sind alle mit einem Stern (\*) gekennzeichneten Felder Pflichtfelder.
>

### Informationen zu Ihrer Dienstleistung abrufen

Alle Ihre aktiven Dienste können über folgende Route abgerufen werden:

> [!api]
>
> @api {v1} /dedicated/nasha GET /dedicated/nasha
>

> [!warning]
>
> Der Zugriff ist gesperrt, solange er nicht über die ACL gewährt wird. Es können nur IP-Adressen hinzugefügt werden, die mit Ihren OVHcloud Diensten verbunden sind.
>

### ACL einer Partition abrufen

Um die IP-Adressen abzurufen, die aktuell auf die Partition zugreifen können, verwenden Sie folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {v1} /dedicated/nasha GET /dedicated/nasha/{serviceName}/partition/{partitionName}/access
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Der interne Name Ihres HA-NAS
>> >
>> > **partitionName** *
>> >
>> >> Partitionsname
>

### Abruf aller kompatiblen IP-Adressen

Sie können die IP-Adressen, für die der Zugang erlaubt werden kann, über folgende Aufrufe überprüfen:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {v1} /dedicated/nasha GET /dedicated/nasha/{serviceName}/partition/{partitionName}/authorizableIps
>> >
>> > @api {v1} /dedicated/nasha GET /dedicated/nasha/{serviceName}/partition/{partitionName}/authorizableBlocks
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Der interne Name Ihres HA-NAS
>> >
>> > **partitionName** *
>> >
>> >> Partitionsname
>

### Hinzufügen eines ACL Eintrags

Um einen neuen ACL Eintrag zu erstellen, über den Sie auf die Partition zugreifen können, verwenden Sie folgenden Aufruf:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {v1} /dedicated/nasha POST /dedicated/nasha/{serviceName}/partition/{partitionName}/access
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Der interne Name Ihres HA-NAS
>> >
>> > **partitionName** *
>> >
>> >> Partitionsname
>> >
>> > **ip** *
>> >
>> >> Die IP-Adresse oder der Bereich, für den der Zugang gewährt werden soll
>> >
>> > **type** *
>> >
>> >> Typ des ACL Zugangs für diesen Eintrag: *readonly* oder *readwrite*
>

> [!primary]
>
> Verwenden Sie die CIDR-Notation für IP-Bereiche, zum Beispiel: 192.0.2.0/24.
>

### Löschung eines ACL Eintrags

Um eine IP-Adresse oder einen Adressbereich aus der ACL zu löschen, verwenden Sie folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {v1} /dedicated/nasha DELETE /dedicated/nasha/{serviceName}/partition/{partitionName}/access/{ip}
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Der interne Name Ihres HA-NAS
>> >
>> > **partitionName** *
>> >
>> >> Partitionsname
>> >
>> > **ip** *
>> >
>> >> Die IP-Adresse oder der Bereich, dem der Zugriff verweigert werden soll
>

## Weiterführende Informationen

[NAS via NFS-Freigabe mounten](/pages/storage_and_backup/file_storage/ha_nas/nas_nfs)

[NAS auf Windows Server über CIFS mounten](/pages/storage_and_backup/file_storage/ha_nas/nas_cifs)

Wenn Sie Schulungen oder technische Unterstützung bei der Implementierung unserer Lösungen benötigen, wenden Sie sich an Ihren Vertriebsmitarbeiter oder klicken Sie auf [diesen Link](https://www.ovhcloud.com/de/professional-services/), um einen Kostenvoranschlag zu erhalten und eine persönliche Analyse Ihres Projekts durch unsere Experten des Professional Services Teams anzufordern.

Für den Austausch mit unserer Community gehen Sie auf <https://community.ovh.com/en/>.
