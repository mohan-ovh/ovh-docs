---
title: HA-NAS auf Windows Server über CIFS mounten
excerpt: Erfahren Sie hier, wie Sie Ihr HA-NAS unter Windows Server über CIFS mounten können
updated: 2021-11-22
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

**Letzte Aktualisierung am 08.12.2021**

## Ziel

Konfigurieren und mounten Sie einen OVHcloud HA-NAS-Speicherraum auf Ihrem Windows Server mit CIFS.

## Voraussetzungen

- Sie haben einen [Dedicated Server](https://www.ovhcloud.com/de/bare-metal/) **oder** einen [VPS](https://www.ovhcloud.com/de/vps/) **oder** eine [Public Cloud Instanz](https://www.ovhcloud.com/de/public-cloud/) mit einer Windows-Distribution in Ihrem Kunden-Account.
- Sie verfügen über eine [HA-NAS Lösung](https://www.ovh.de/nas/).

### Einstellungen

- **Windows Server 2008**: Klicken Sie auf `Start`{.action}, `All the programs`{.action}, `Accessories`{.action}, `Command prompt`{.action}.
- **Windows Server 2012**: Klicken Sie auf das `Windows PowerShell`{.action} Icon am unteren Bildschirmrand in der Taskleiste.
- **Windows Server 2016**: Klicken Sie auf `Start`{.action} und dann auf das `Windows PowerShell`{.action} Icon.
- **Windows Server 2019**: Klicken Sie auf `Start`{.action} und dann auf das `Windows PowerShell`{.action} Icon.

Führen Sie dann den folgenden Befehl aus:

```powershell
net use z: \\CIFS_SERVER_IP\CIFS_PATH
```

### Beispiele

- CIFS Mount für HA-NAS:

```powershell
net use z: \\10.16.101.8\zpool-000206_PARTITION_NAME_1
```

> [!alert]
>
> Der SMB/CIFS Benutzer ist `nobody`. Das Ändern von Berechtigungen mit diesem Benutzer kann Konflikte mit bestehenden NFS-Berechtigungen verursachen.
>

## Weiterführende Informationen

[Häufig gestellte Fragen zu NAS](/pages/cloud/storage/file_storage/nas_faq)

Wenn Sie Schulungen oder technische Unterstützung bei der Implementierung unserer Lösungen benötigen, wenden Sie sich an Ihren Vertriebsmitarbeiter oder klicken Sie auf [diesen Link](https://www.ovhcloud.com/de/professional-services/), um einen Kostenvoranschlag zu erhalten und eine persönliche Analyse Ihres Projekts durch unsere Experten des Professional Services Teams anzufordern.

Für den Austausch mit unserer Community gehen Sie auf <https://community.ovh.com/en/>.
