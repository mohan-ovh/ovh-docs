---
title: Enterprise File Storage - Volumes verwalten
excerpt: Erfahren Sie hier, wie Sie Ihre OVHcloud Enterprise File Storage Volumes mit der OVHcloud API erstellen und verwalten
updated: 2021-10-27
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie beim geringsten Zweifel die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button «Mitmachen» auf dieser Seite.
>

**Letzte Aktualisierung am 27.10.2021**

## Ziel

In diesem Tutorial geben wir einen Überblick über die Volume-Verwaltung von OVHcloud Enterprise File Storage über die OVHcloud API.

**Diese Anleitung erklärt, wie Sie bestehende Volumes auflisten, ein neues Volume erstellen oder ein bereits existierendes Volume löschen.**

## Voraussetzungen

- Sie verfügen über einen OVHcloud Enterprise File Storage
- Sie sind zur Verwendung der [OVHcloud API](https://api.ovh.com/) eingeloggt

## Das Wesentliche

Ein Volume ist ein persistentes, les- und beschreibbares Dateisystem, das eine Kapazität und ein Protokoll als Eigenschaften besitzt.

Es kann optional einen Namen und eine Beschreibung haben.

> [!warning]
>
> Standardmäßig ist der Zugang zu einem neu erstellten Volume beschränkt. Für den Zugriff muss eine ACL eingerichtet werden.
>

## In der praktischen Anwendung

Alle für diese Anleitung verwendeten API-Routen sind im Bereich `/storage` verfügbar: <https://api.ovh.com/console/#/storage>.

> [!primary]
>
> Bei der Verwendung der API sind alle mit einem Stern (\*) gekennzeichneten Felder Pflichtfelder.
>

### Volumes auflisten

Um die Volumes eines Dienstes aufzulisten, verwenden Sie den folgenden Pfad:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /storage/netapp/{serviceName}/share
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Service ID
>> >
>

Ersetzen Sie `serviceName` mit der ID Ihres Dienstes.

### Volume-Informationen abrufen

Um die Informationen eines Volumes abzurufen, verwenden Sie die folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /storage/netapp/{serviceName}/share/{shareId}
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Service ID
>> >
>> > **shareId** *
>> >
>> >> Volume ID
>

Ersetzen Sie `serviceName` mit der ID Ihres Dienstes und `shareId` mit der Volume-ID.

### Volume erstellen

Um ein neues Volume zu erstellen, verwenden Sie die folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {POST} /storage/netapp/{serviceName}/share
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Service ID
>> >
>

Ersetzen Sie `serviceName` mit der ID Ihres Dienstes.

Wählen Sie das NFS-Protokoll für Ihr neues Volume (`protocol`) sowie dessen Größe. Sie können auch die Eigenschaften Name und Beschreibung angeben (optional).

### Mountpunkte eines Volumes anzeigen

Um den Mountpfad eines Volumes einzusehen, verwenden Sie die folgende Route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /storage/netapp/{serviceName}/share/{shareId}/accessPath
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Service ID
>> >
>> > **shareId** *
>> >
>> >> Volume ID
>

Ersetzen Sie `serviceName` mit der ID Ihres Dienstes und `shareId` mit der Volume-ID.

Zurückgegebene Mountpfade können zum Mounten des Volume verwendet werden.

Je nach gewähltem Protokoll für das Volume muss der Mountbefehl verschieden sein.  

> [!primary]
>
> Die Anleitung für NFS finden Sie [hier](/pages/cloud/storage/file_storage/nas_nfs).
>
> Beachten Sie, dass der abgerufene Mountpfad IP_NAS/NFS_PATH in dieser Anleitung ersetzt.
>  

### Volume löschen

Um ein Volume zu löschen, verwenden Sie folgende Route:  

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {DELETE} /storage/netapp/{serviceName}/share/{shareId}
>> >
>>
>
> Parameter:
>
>> > **serviceName** *
>> >
>> >> Service ID
>> >
>> > **shareId** *
>> >
>> >> Volume ID
>

Ersetzen Sie `serviceName` mit der ID Ihres Dienstes und `shareId` mit der ID des zu löschenden Volumes.

## Weiterführende Informationen

[Erste Schritte mit der OVHcloud API](/pages/account/api/first-steps)

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
