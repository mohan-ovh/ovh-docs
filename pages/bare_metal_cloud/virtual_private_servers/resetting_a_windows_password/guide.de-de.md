---
title: 'Windows-Passwort zurücksetzen'
excerpt: Anleitung zum Zurücksetzen eines Passworts unter Windows
updated: 2020-11-25
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel

Möglicherweise müssen Sie das Windows-Passwort auf Ihrem VPS zurücksetzen. Diese Anleitung erklärt, wie Sie Ihr Passwort zurücksetzen und sich wieder erfolgreich auf Ihrem VPS einloggen.

## Voraussetzungen

- Der VPS muss sich im Rescue-Modus befinden (für weitere Informationen lesen Sie die [Anleitung zum Rescue-Modus](/pages/bare_metal_cloud/virtual_private_servers/rescue)).

## In der praktischen Anwendung

Loggen Sie sich über die VNC Konsole Ihres [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) mit den Login-Daten ein, die Sie per E-Mail erhalten haben.

Geben Sie folgende Befehle ein, um das Dateisystem zu mounten:

```sh
ntfsfix /dev/sdb2
mount -t ntfs-3g /dev/sdb2 /mnt
```

Starten Sie jetzt den Vorgang zum Zurücksetzen des Passworts:

```sh
cd /mnt/Windows/System32/config
chntpw -l SAM
```

Sie sehen eine Liste der Benutzer, darunter sollte der Administrator-Account sein. Befolgen Sie den Prozess für den Account, dessen Passwort Sie zurücksetzen müssen. In diesem Beispiel wird der Account `Administrator` verwendet. Beachten Sie, dass die Befehle Groß- und Kleinschreibung beachten.

```sh
chntpw -u Administrator SAM
```

Drücken Sie auf `1`{.action} und `Enter`{.action}, um das Passwort zu löschen. Drücken Sie `q`{.action}, um die Prozedur zur Änderung des Passworts zu verlassen. Drücken Sie anschließend auf `y`{.action}, um die Änderungen in die SAM-Datei zu schreiben.

Sie können den VPS nun aus dem Rescue-Modus entfernen. (Weitere Informationen finden Sie in der Anleitung [Rescue-Modus für VPS](/pages/bare_metal_cloud/virtual_private_servers/rescue).)

Bei Ihrer nächsten Anmeldung müssen Sie kein Passwort für die Windows-Session eingeben.

> [!warning]
>
> Es ist äußerst riskant, den Administrator-Account (oder jeden Account mit erweiterten Rechten) mit einem leeren Passwort zu belassen. Bitte loggen Sie sich umgehend in Windows ein und vergeben Sie ein neues Passwort.
> 

Wenn Sie eingeloggt sind, klicken Sie auf `CTRL`{.action} + `ALT`{.action} + `DELETE`{.action} und anschließend auf `Passwort ändern`{.action}. Wenn Sie VNC verwenden, klicken Sie oben rechts auf den Button `Send CtrlAltDel`{.action}.

Lassen Sie das Feld `Altes Passwort` leer und geben Sie Ihr neues Passwort zweimal ein. Bitte stellen Sie sicher, dass die Eingaben identisch sind.

## Weiterführende Informationen

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
