---
title: HA-NAS - Snapshot-Verwaltung via API
excerpt: Erfahren Sie hier, wie Sie Snapshots auf Ihrem HA-NAS über die OVHcloud API verwalten
updated: 2022-07-20
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

**Letzte Aktualisierung am 20.07.2022**

## Ziel

OVHcloud HA-NAS Dienste ermöglichen Ihnen die Verwaltung zentral gespeicherter Dateien, die über ein Netzwerk zugänglich sind.

**Diese Anleitung erklärt, wie Sie die Snapshots einer HA-NAS-Partition über die OVHcloud API verwalten.**

## Voraussetzungen

- Sie haben ein [OVHcloud HA-NAS](https://www.ovh.com/de/nas/) in Ihrem Kunden-Account.
- Sie haben sich anhand der [Anleitung zu den ersten Schritten mit der OVHcloud API](/pages/account/api/first-steps) mit der Verwendung der OVHcloud APIv6 vertraut gemacht.

## In der praktischen Anwendung

> [!primary]
> Detaillierte technische Informationen zur Snapshot-Funktion finden Sie auf der [HA-NAS FAQ-Seite](/pages/cloud/storage/file_storage/nas_faq).
>


Alle API-Routen in dieser Anleitung sind im Bereich */dedicated/nasha* verfügbar: <https://api.ovh.com/console/#/dedicated/nasha>.

> [!primary]
>
> Bei der Verwendung der API sind alle mit einem Stern (\*) gekennzeichneten Felder Pflichtfelder.
>

### Informationen zu Ihrer Dienstleistung abrufen

Alle Ihre aktiven Dienste können über folgende Route abgerufen werden:

> [!api]
>
> @api {GET} /dedicated/nasha
>

Standardmäßig erfolgt stündlich eine Sicherung Ihrer Daten und wird auf Ihrem HA-NAS gespeichert. Sie können weitere Snapshot-Strategien aktivieren, die Snapshots bei vorgegebenen Frequenzen erstellen.

### Automatische Snapshot-Planung abrufen

Um den derzeit aktiven Snapshot-Zeitplan anzuzeigen, verwenden Sie die folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/snapshot
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

### Automatisches Snapshot-Intervall hinzufügen

Um zusätzliche automatische Snapshots mit einer ausgewählten Frequenz anzulegen, verwenden Sie die folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {POST} /dedicated/nasha/{serviceName}/partition/{partitionName}/snapshot
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
>> > **snapshotType** *
>> >
>> >> Eine Frequenz für den Snapshot: *day-1*, *day-2*, *day-3*, *day-7*, *hour-1*, oder *hour-6*
>

### Abruf der Informationen zu den automatischen Sicherungen

Um die Details eines automatischen Snapshots abzurufen, verwenden Sie die folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/snapshot/{snapshotType}
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
>> > **snapshotType** *
>> >
>> >> Die betroffene Snapshot-Frequenz: *day-1*, *day-2*, *day-3*, *day-7*, *hour-1*, oder *hour-6*
>

### Löschung eines automatischen Snapshot-Intervalls

Verwenden Sie die folgende Route, um eine automatische Snapshot-Frequenz zu löschen:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {DELETE} /dedicated/nasha/{serviceName}/partition/{partitionName}/snapshot/{snapshotType}
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
>> > **snapshotType** *
>> >
>> >> Die betroffene Snapshot-Frequenz: *day-1*, *day-2*, *day-3*, *day-7*, *hour-1*, oder *hour-6*
>

Über die folgenden Endpunkte können Sie auch Instant-Snapshots auf Ihrem HA-NAS verwenden.

### Liste der manuellen Snapshots

Verwenden Sie die folgende Route, um die manuell erstellten Snapshots abzurufen:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/customSnapshot
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

### Erstellung eines Instant-Snapshots

Um einen manuellen Snapshot hinzuzufügen, verwenden Sie folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {POST} /dedicated/nasha/{serviceName}/partition/{partitionName}/customSnapshot
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
>> > **expiration**
>> >
>> >> Ein optionales Ablaufdatum, zum Beispiel: 2022-06-24 (ISO 8601)
>> >
>> > **name** *
>> >
>> >> Name des Snapshots
>

### Abruf der Informationen eines personalisierten Snapshots

Um die Details eines personalisierten Snapshots anzuzeigen, verwenden Sie die folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/customSnapshot/{name}
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
>> > **name** *
>> >
>> >> Name des Snapshots
>

### Löschung eines manuellen Snapshots

Verwenden Sie die folgende Route, um einen individuellen Snapshot zu löschen:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {DELETE} /dedicated/nasha/{serviceName}/partition/{partitionName}/customSnapshot/{name}
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
>> > **name** *
>> >
>> >> Name des Snapshots
>

##### **Wiederherstellung von Snapshots**

Die API-Funktionen umfassen nicht die Wiederherstellung von Snapshots. Die Snapshots werden als "read-only" auf der Partition gespeichert.

Um von Ihrem Mountpunkt aus auf die Snapshots zuzugreifen, müssen Sie das Verzeichnis `.zfs/snapshot` Ihrer Partition öffnen.

Zum Beispiel: Auf einem Dienst mit der ID `zpool-123456` existiert eine Partition `partition1`, für die ein Snapshot namens `snap-snapshot01` erstellt wurde. Sie finden dann den Snapshot mit folgendem Befehl:

```bash
ls -al /zpool-123456/partition1/.zfs/snapshot/snap-snapshot01/
```

Um Ihren Snapshot wiederherzustellen, kopieren Sie diesen aus dem `.zfs`-Dateipfad  in ein neues Verzeichnis, in dem Sie den Snapshot wiederherstellen möchten. Sie können dazu ein Tool wie "rsync" verwenden, das Wiederherstellungen durchführen kann.

Zusätzliche Hilfe finden Sie unter "[Weiterführende Informationen](#gofurther)".


## Weiterführende Informationen

[NAS via NFS-Freigabe mounten](/pages/cloud/storage/file_storage/nas_nfs)

[NAS auf Windows Server über CIFS mounten](/pages/cloud/storage/file_storage/nas_cifs)

Wenn Sie Schulungen oder technische Unterstützung bei der Implementierung unserer Lösungen benötigen, wenden Sie sich an Ihren Vertriebsmitarbeiter oder klicken Sie auf [diesen Link](https://www.ovhcloud.com/de/professional-services/), um einen Kostenvoranschlag zu erhalten und eine persönliche Analyse Ihres Projekts durch unsere Experten des Professional Services Teams anzufordern.

Für den Austausch mit unserer Community gehen Sie auf <https://community.ovh.com/en/>.
