---
title: 'Erste Schritte mit einem Kimsufi, So You Start oder Rise Dedicated Server'
excerpt: 'Erfahren Sie hier, wie Sie Ihren neuen Kimsufi, So You Start oder Rise Dedicated Server verwalten'
updated: 2023-02-28
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel

Ein dedizierter Server ist ein physischer Server in einem unserer Rechenzentren. Im Gegensatz zum Webhosting (auch "Shared Hosting" genannt), bei dem die technische Verwaltung von OVHcloud geleistet wird, sind Sie für die Verwaltung Ihres Servers allein verantwortlich.

**Diese Anleitung erläutert einige Grundlagen zur Erstverwendung eines Kimsufi, So You Start oder Rise Dedicated Server.**

## Voraussetzungen

- Sie verfügen über einen [Dedicated Server](https://www.ovhcloud.com/de/bare-metal/) der Reihe Kimsufi, So You Start oder Rise in Ihrem Kunden-Account.
- Sie haben administrativen Zugriff (Root) auf Ihren Server über SSH oder RDP (optional). 
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de).

## In der praktischen Anwendung

Wenn Ihr Dedicated Server während des Bestellprozesses zum ersten Mal konfiguriert wird, können Sie das zu installierende Betriebssystem auswählen.

### Ihren Dedicated Server installieren oder reinstallieren

Sie können Ihren Server in wenigen Schritten in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) reinstallieren und ein anderes Betriebssystem auswählen. Klicken Sie im Tab `Allgemeine Informationen`{.action} auf `...`{.action} neben `System (OS)` und danach auf `Installieren`{.action}.

![Button Reinstallieren](images/reinstalling-your-server-00.png){.thumbnail}

Wählen Sie im Popup-Fenster eine der Installationsoptionen aus:

- `Installation mit einem OVHcloud Template`{.action}: Sie können das Betriebssystem auswählen und die Konfiguration Ihres Servers anpassen.
- `Installation mit einem Ihrer Templates`{.action}: Um eine personalisierte Vorlage verwenden zu können, müssen Sie zuvor mindestens eine Serverkonfiguration gespeichert haben. Aktivieren Sie dazu in Schritt 4 des Installationsprozesses die Option "Diese Installation speichern".
- `Installation auf Basis eines personalisierten Images`{.action}: Mit dieser Option können Sie ein externes Image auf dem Server installieren. Weitere Informationen zu dieser Option finden Sie in der Anleitung ["Bring Your Own Image verwenden"](/pages/bare_metal_cloud/dedicated_servers/bring-your-own-image)".

> [!primary]
>
> Einige proprietäre Betriebssysteme und Plattformen wie Plesk oder Windows benötigen Lizenzen, die zusätzliche Kosten verursachen. Sie können Lizenzen [bei OVHcloud](https://www.ovhcloud.com/de/bare-metal/os/) oder einem externen Reseller beziehen. Danach müssen Sie Ihre Lizenz im Betriebssystem selbst oder über Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) hinzufügen.
>
> Sie können alle Ihre Lizenzen im Bereich `Bare Metal Cloud`{.action} unter `Lizenzen`{.action} verwalten. In diesem Abschnitt können Sie auch über den Button `Aktionen`{.action} Lizenzen bestellen oder bestehende Lizenzen hinzufügen.
>

Klicken Sie auf `Weiter`{.action}, um fortzufahren.

![Template-Auswahl](images/reinstalling-your-server-02.png){.thumbnail}

Nachdem Sie `Installation mit einem OVHcloud Template`{.action} ausgewählt haben, können Sie das gewünschte Betriebssystem in den Menüs auswählen.

![Operationelle Auswahl](images/reinstalling-your-server-03.png){.thumbnail}

Wenn Sie das Partitionsschema Ihres Betriebssystems ändern müssen, setzen Sie einen Haken in dem Feld "Konfiguration der Partitionen anpassen", bevor Sie auf `Weiter`{.action} klicken.

![Konfiguration der Partitionen anpassen](images/SSH_02.png){.thumbnail}

Klicken Sie nach Abschluss der Anpassungen auf `Weiter`{.action}, um zur Zusammenfassung zu gelangen.

#### Hinzufügen eines SSH-Schlüssels (optional)

Wenn Sie ein GNU/Linux-Betriebssystem installieren, können Sie Ihren SSH-Schlüssel im letzten Schritt des Installationsprozesses hinzufügen.

![Partitionskonfiguration personalisieren](images/SSH_03.png){.thumbnail}

Wenn ein SSH-Schlüssel bereits hinterlegt ist, erscheint er unten im Drop-down-Menü unter "SSH-Schlüssel". Falls nicht, fügen Sie zuerst einen im Bereich "Meine Dienstleistungen" hinzu.

Öffnen Sie hierzu die Seitenleiste, indem Sie oben rechts auf Ihren Namen klicken und nutzen Sie dann den Shortcut `Produkte und Dienstleistungen`{.action}.

![Partitionskonfiguration personalisieren](images/SSH_keys_panel_2022.png){.thumbnail}

Gehen Sie in "Meine Dienste" auf den Tab `SSH-Schlüssel`{.action} und klicken Sie auf `SSH-Schlüssel hinzufügen`{.action}.

![Partitionskonfiguration personalisieren](images/SSH_14.png){.thumbnail}

Da es sich um die Einrichtung eines Dedicated Servers handelt, wählen Sie im Drop-down-Menü "Dedicated" aus (ebenso gültig für einen VPS).

Geben Sie im neuen Fenster eine ID (Name Ihrer Wahl) und den Schlüssel selbst (vom Typ RSA, ECDSA oder Ed25519) in die entsprechenden Felder ein.

![Partitionskonfiguration personalisieren](images/SSH_12.png){.thumbnail}

Weitere Informationen zur Erstellung von SSH-Schlüsseln finden Sie in unserer [Anleitung](/pages/bare_metal_cloud/dedicated_servers/creating-ssh-keys-dedicated).

> [!warning]
>OVHcloud stellt Ihnen Dienste zur Verfügung, für deren Konfiguration und Verwaltung Sie verantwortlich sind. Sie sind also verantwortlich für das ordnungsgemäße Funktionieren dieser Systeme.
>
>Diese Anleitung hilft Ihnen bei der Bewältigung allgemeiner Aufgaben. Dennoch empfehlen wir Ihnen, einen [spezialisierten Dienstleister](https://partner.ovhcloud.com/de/directory/) zu kontaktieren, falls Sie Schwierigkeiten oder Zweifel hinsichtlich der Administration, Nutzung oder Implementierung der Dienste auf einem Server haben.
>

### Verbindung zu Ihrem Server

#### Linux

Sobald die Installation abgeschlossen ist, erhalten Sie eine E-Mail mit Anweisungen zum administrativen Zugriff. Sie können sich über ein Kommandozeileninterface oder mit Hilfe von Drittanbietersoftware mit Ihrem Server über das sichere Kommunikationsprotokoll SSH verbinden.

Verwenden Sie die folgenden Beispiele, um sich mit Ihrem Server zu verbinden, und ersetzen Sie die Login-Daten mit Ihren eigenen Werten (IP-Adresse und Serverreferenzname sind austauschbar).

**Beispiel mit Root:**

```bash
ssh root@IPv4_Ihres_Servers
```

**Beispiel mit einem vorkonfigurierten Benutzer:**

```bash
ssh root@Referenzname_Ihres_Servers
```

Weitere Informationen zu SSH finden Sie in unserer [Anleitung](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction).

#### Windows

Sobald die Installation abgeschlossen ist, erhalten Sie eine E-Mail mit Ihrem Passwort für den Administrator-Zugang (Root). Verwenden Sie diese Login-Daten, um sich via RDP (**R**emote **D**esktop **P**rotocol) mit dem Server zu verbinden. Wenn Sie eingeloggt sind, wird Windows Sie durch die Erstinstallation führen.

Beachten Sie auch unsere Anleitung zum [Konfigurieren einer neuen Windows Server Installation](/pages/bare_metal_cloud/dedicated_servers/windows_first_config).

### Neustart Ihres Dedicated Servers <a name="reboot"></a>

Ein Neustart kann notwendig sein, um aktualisierte Konfigurationen anzuwenden oder Fehler zu beheben. Wenn möglich, führen Sie über die Befehlszeile einen "Soft Reboot" des Servers durch:

```bash
reboot
```

Sie können jedoch jederzeit einen "Hard Reboot" in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) ausführen. Klicken Sie im Tab `Allgemeine Informationen`{.action} auf `...`{.action} neben "Status" im Bereich **Dienststatus** und klicken Sie dann im Kontextmenü auf `Neu starten`{.action} und `Bestätigen`{.action}.

![Neustart](images/rebooting-your-server.png){.thumbnail}

### Absicherung Ihres Dedicated Servers

Wie oben erläutert, sind Sie der Administrator Ihres dedizierten Servers. Als solcher sind Sie für Ihre Daten und deren Sicherheit verantwortlich. Mehr Informationen zur Sicherung Ihres Servers finden Sie in unserer Anleitung zur [Absicherung eines Servers](/pages/bare_metal_cloud/dedicated_servers/securing-a-dedicated-server).

Wenn Sie Windows Server einsetzen, verwenden Sie [diese Anleitung](/pages/bare_metal_cloud/dedicated_servers/activate-port-firewall-soft-win).

### OVHcloud Monitoring 

Sie können den Monitoring-Status eines Servers im [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) vom Tab `Allgemeine Informationen`{.action} aus einrichten (Abschnitt **Dienststatus**).

![Monitoring](images/monitoring-your-server.png){.thumbnail}

Klicken Sie auf den Button `Konfigurieren`{.action}. Im neu angezeigten Fenster haben Sie drei Optionen für das Überwachungsverhalten:

- **Deaktiviert**: Mit dieser Option werden Warnmeldungen und Eingriffe von OVHcloud gestoppt. Wählen Sie dies aus, wenn Sie auf dem Server relevante Administrationsmaßnahmen durchführen, die eine ICMP-Antwort verhindern.
- **Aktiviert mit proaktivem Eingriff**: Wenn der Server nicht mehr reagiert wird Ihnen eine Benachrichtigung per E-Mail gesendet und der Server von einem Techniker überprüft.
- **Aktiviert ohne proaktiven Eingriff**: Sie erhalten eine Benachrichtigung per E-Mail, wenn der Server nicht mehr reagiert. Um eine Intervention zu veranlassen, muss eine Support-Anfrage erstellt werden.

![Monitoring](images/monitoring-your-server2.png){.thumbnail}

Klicken Sie auf `Bestätigen`{.action}, um Ihre Monitoring-Konfiguration zu aktualisieren.

Weitere Informationen zum OVHcloud Monitoring finden Sie in [unserer Anleitung](/pages/bare_metal_cloud/dedicated_servers/network_ip_monitoring).

### Netzwerkkonfiguration

> [!primary]
>
> Beachten Sie, dass [zusätzliche IP Adressen](https://www.ovhcloud.com/de/bare-metal/ip/) nicht mit der **Kimsufi** Reihe kompatibel sind.
>

#### IP-Bridge-Modus

Network Bridging bezeichnet die Aktion, die Netzwerkgeräte ausführen, um ein aggregiertes Netzwerk aus zwei oder mehr Kommunikationsnetzwerken oder zwei oder mehr Netzwerksegmenten zu erstellen. Bridging unterscheidet sich vom Routing insofern als die Netzwerke unabhängig kommunizieren können, während sie voneinander getrennt bleiben.

Diese Konfiguration wird vor allem in der Virtualisierung verwendet, damit jede virtuelle Maschine über eine eigene öffentliche IP-Adresse verfügt.

Weitere Informationen zum Bridge-Modus finden Sie in unserer Anleitung zum [IP-Bridge-Modus](/pages/bare_metal_cloud/dedicated_servers/network_bridging).

#### IP-Alias

Beim IP-Aliasing werden zwei oder mehr IP-Adressen mit demselben Netzwerkinterface verknüpft. So kann Ihr Server mehrere Verbindungen zu einem Netzwerk herstellen, die jeweils einen anderen Zweck erfüllen.

Detaillierte Anweisungen zur Konfiguration des IP-Alias finden Sie in der Anleitung zu [IP-Aliasing](/pages/bare_metal_cloud/dedicated_servers/network_ipaliasing).

#### IPv6 Konfiguration

> [!primary]
>
> Beachten Sie, dass Server der **Kimsufi** Reihe nur jeweils eine IPv4 Adresse und eine IPv6 Adresse haben. Diese werden bei der Installation des Betriebssystems automatisch eingerichtet.
>

OVHcloud Dedicated Server werden mit einem /64 IPv6 Block geliefert. Um die Adressen dieses Blocks zu verwenden müssen Sie die Konfiguration des Netzwerks anpassen. Lesen Sie dazu unsere Anleitung "[IPv6 auf einem Dedicated Server konfigurieren](/pages/bare_metal_cloud/dedicated_servers/network_ipv6)".

### Rescue-Modus

Der erste Schritt zur Fehlerbehebung besteht stets darin, Ihren Server in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) im Rescue-Modus neu zu starten. Es ist wichtig, Serverfehler in diesem Modus zu identifizieren, um Probleme mit Software auszuschließen, bevor Sie unsere Support-Teams kontaktieren.

Folgen Sie unserer Anleitung zum [Rescue-Modus](/pages/bare_metal_cloud/dedicated_servers/rescue_mode).

### Zugang mit IPMI

> [!primary]
>
> Beachten Sie, dass diese Option nicht für Server der **Kimsufi** Reihe verfügbar ist.
>

OVHcloud stattet Dedicated Server mit einer IPMI-Konsole (Intelligent Platform Management Interface) aus, die in Ihrem Browser oder über ein Java-Applet ausgeführt wird. Sie können sich direkt mit Ihrem Server verbinden, auch wenn dieser über keine Netzwerkverbindung verfügt. Sie ist deshalb ein nützliches Werkzeug, um Fehler zu beheben, die Ihren Server unerreichbar machen.

Weitere Informationen finden Sie in unserer Anleitung zur [Verwendung der IPMI-Konsole](/pages/bare_metal_cloud/dedicated_servers/using_ipmi_on_dedicated_servers).

### Backup Storage

> [!primary]
>
> Beachten Sie, dass diese Option nicht für Server der **Kimsufi** Reihe verfügbar ist.
>

OVHcloud Dedicated Server verfügen über einen zugriffskontrollierten Speicherplatz als kostenlose Serviceoption. Er eignet sich am besten als ergänzende Backup-Option für den Fall, dass der Server selbst einen Datenverlust erleidet.

Zur Aktivierung und Nutzung des Backup Storage folgen Sie der [zugehörigen Anleitung](/pages/bare_metal_cloud/dedicated_servers/services_backup_storage).

## Weiterführende Informationen

Wenn Sie Schulungen oder technische Unterstützung bei der Implementierung unserer Lösungen benötigen, wenden Sie sich an Ihren Vertriebsmitarbeiter oder klicken Sie auf [diesen Link](https://www.ovhcloud.com/de/professional-services/), um einen Kostenvoranschlag zu erhalten und eine persönliche Analyse Ihres Projekts durch unsere Experten des Professional Services Teams anzufordern.

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.