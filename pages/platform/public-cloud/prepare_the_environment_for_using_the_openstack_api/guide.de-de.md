---
title: 'Umgebung für die Verwendung der OpenStack-API vorbereiten'
slug: prepare_the_environment_for_using_the_openstack_api
excerpt: 'Installieren Sie die OpenStack-Umgebung, um Ihre Instanzen über die API zu verwalten.'
legacy_guide_number: 1851
section: 'OpenStack'
updated: 2022-03-30
---

**Letzte Aktualisierung am 22.12.2021**

## Einleitung

Es ist möglich, Public Cloud Dienste mit Befehlen aus der Systemkonsole zu verwalten, wenn die OpenStack-Tools heruntergeladen und installiert wurden.

Mithilfe der OpenStack-API können Sie die Verwaltung automatisieren, indem Sie Skripte erstellen. Mit dem OpenStack-Nova-Client können Sie Instanzen und Festplattenspeicher verwalten. Mit dem OpenStack-Glance-Client können Sie Images und Backups verwalten, während der Swift-Client für die Verwaltung von Objektspeicherplatz verwendet wird.

**In dieser Anleitung erfahren Sie, wie Sie diese OpenStack-Tools installieren.**

## Voraussetzungen

- Sie haben **root**-Zugriff auf die Umgebung, die Sie konfigurieren möchten.

## Beschreibung

### Unter Debian

Öffnen Sie das Terminal oder verbinden Sie sich via SSH mit der Umgebung, die Sie vorbereiten möchten.

Aktualisieren Sie den Paket-Cache mit dem Befehl `apt-get update`:

```sh
apt-get update
```

Verwenden Sie den nachstehenden Befehl, um die Nova- (Compute-Anwendung) und Swift-Clients zu installieren:

```sh
apt-get install python-openstackclient python-novaclient python-swiftclient -y
```

Python3 Version

```sh
apt-get install python3-openstackclient python3-novaclient python3-swiftclient -y
```

Wir empfehlen Ihnen, nach diesem Schritt einen speziellen Benutzer zu erstellen, um nicht den root-Benutzer zu verwenden.

Um auf die Hilfe-Tools zuzugreifen, führen Sie folgenden Befehl aus:

```sh
openstack --help
nova help
```

> [!primary]
> 
> Die Dokumentation für die OpenStack-API ist [auf dieser Seite](https://docs.openstack.org/python-openstackclient/latest/){.external} verfügbar.
> 

### Unter CentOS

Öffnen Sie das Terminal oder verbinden Sie sich via SSH mit der Umgebung, die Sie vorbereiten möchten.

Aktualisieren Sie den Paket-Cache mit folgendem Befehl:

```sh
yum update -y
```
Installieren Sie das rpm-Paket rdo-release mit folgendem Befehl:

```sh
yum install -y https://rdoproject.org/repos/rdo-release.rpm
```

Installieren Sie dann den OpenStack-Client:

```sh
yum install -y python-openstackclient
```

Installieren Sie anschließend den Nova-Client:

```sh
yum install -y python-novaclient
```

Wir empfehlen Ihnen, nach diesem Schritt einen speziellen Benutzer zu erstellen, um nicht den root-Benutzer zu verwenden.

Um auf die Hilfe-Tools zuzugreifen, führen Sie folgenden Befehl aus:

```sh
openstack --help
nova help
```

> [!primary]
> 
> Die Dokumentation für die OpenStack-API ist [auf dieser Seite](https://docs.openstack.org/python-openstackclient/latest/){.external} verfügbar.
> 

### Unter Windows

Laden Sie die Version 2.7.14 von Python herunter und installieren Sie diese. Sie können die Python-Programmiersprache automatisch zu Path hinzufügen, indem Sie diese Option in der Installationskonfiguration auswählen:

![Automatische Installation](images/1_preparation_openstack_environment_windows.png){.thumbnail}

Sie können die Installation auch selbst durchführen. Befolgen Sie hierzu die nachstehenden Aktionen:

#### Schritt 1: Umgebungsvariablen des Systems bearbeiten

Suchen Sie nach den Systemumgebungsvariablen und klicken Sie auf “Systemumgebungsvariablen bearbeiten”:

![Einstellungen der Umgebungsvariablen](images/2_preparation_openstack_environment_windows.png){.thumbnail}

#### Schritt 2: Systemeinstellungen bearbeiten

Gehen Sie in den Tab `Erweitert`{.action} und klicken Sie auf `Umgebungsvariablen`{.action}, um die Einstellungen zu ändern.

![Umgebungseinstellungen](images/3_preparation_openstack_environment_windows.png){.thumbnail}

#### Schritt 3: Umgebungsvariablen konfigurieren 

Im Bereich “Systemvariablen”, wählen Sie “Neu”, verwenden Sie den Namen “PYTHON_HOME” und fügen Sie den Pfad bis Python hinzu. Dieser ist standardmäßig: “C:\\Python27”.

![Zugriffspfad hinzufügen](images/4_edit_system_variables.png){.thumbnail}

#### Schritt 4: Pfad der Variablen hinzufügen

Wenn Sie Python hinzugefügt haben, ändern Sie “Path” (Pfad) in den Systemvariablen und fügen Sie folgendes zum Ende des Pfads hinzu:

`...;%PYTHON_HOME%\;%PYTHON_HOME%\Script`

#### Schritt 5: Windows neu starten

Starten Sie Windows neu, damit die vorgenommen Änderungen angewandt werden.

#### Schritt 6: OpenStack-Client installieren

Wenn Sie als Administrator eingeloggt sind, öffnen Sie das Programm in der Kommandozeile (CMD) und installieren Sie den OpenStack-Client mit folgendem Befehl:

```sh
# pip install python-openstackclient
```

Wurde die Operation erfolgreich ausgeführt, wird eine Zusammenfassung geöffnet:

![Automatische Installation](images/5_preparation_openstack_environment_windows.png){.thumbnail}

Sie können die installierte Version im neu geöffneten CMD-Fenster (Kommandozeile) überprüfen, indem Sie “python-V” eingeben (egal, wo Sie sich im System befinden).

![Überprüfung](images/6_preparation_openstack_environment_windows.png){.thumbnail}

#### Unter MacOS

Sie können [HomeBrew](https://brew.sh), einen Paketmanager für MacOS verwenden.

Öffnen Sie das Terminal und geben Sie folgenden Befehl ein:

```bash
brew install openstackclient
```

Verwenden Sie die folgenden Befehle, um die Nova (Computing-App) und Swift Clients zu installieren:

Für Python2:

```sh
pip install python-novaclient
pip install python-swiftclient
```

Für Python3:

```sh
pip3 install python-novaclient
pip3 install python-swiftclient
```

Um auf die Tools zuzugreifen, führen Sie folgenden Befehl aus:

```sh
openstack --help
nova help
```

## Weiterführende Informationen

[OpenStack Umgebungsvariablen einrichten](https://docs.ovh.com/de/public-cloud/set-openstack-environment-variables/).

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
