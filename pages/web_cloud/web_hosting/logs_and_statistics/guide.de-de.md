---
title: Statistiken und Logs eines Webhostings einsehen
excerpt: Erfahren Sie hier, wie Sie die Statistiken und Logs Ihrer Webseiten abrufen
updated: 2023-08-04
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel 

Die Webserver-Protokolle und Website-Statistiken sind in Ihrem Webhosting inklusive und über das OVHcloud Kundencenter komfortabel abrufbar.

**Diese Anleitung bietet einen Überblick über die verfügbaren Logs und Statistiken.**

## Voraussetzungen

- Sie haben ein [OVHcloud Webhosting](https://www.ovhcloud.com/de/web-hosting/) in Ihrem Kunden-Account.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de).

## In der praktischen Anwendung

Melden Sie sich in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} an, klicken Sie im Bereich `Web Cloud`{.action} auf `Hosting-Pakete`{.action} und wählen Sie das gewünschte Webhosting aus.

Klicken Sie auf den Tab `Statistiken und Logs`{.action}.

![Hosting](images/statistics01.png){.thumbnail}

Dieser Tab besteht aus 3 Abschnitten. Der erste zeigt die **Statistiken** an, der zweite die **Website Logs** Ihres Webhostings, und der letzte ist für die **Verwaltung der Nutzer** bestimmt, die Zugriff auf die Statistiken haben.

![Hosting](images/statistics02u.png){.thumbnail}

### Verwaltung der Nutzer

Die Erstellung eines Benutzers ermöglicht es einer Person, auf die Statistiken Ihres Hostings zuzugreifen, ohne Zugang zu Ihrem OVHcloud Kundencenter zu haben. 

Klicken Sie im Bereich `Verwaltung der Nutzer` auf den Button `Einen neuen Nutzer erstellen`{.action} und folgen Sie den Anweisungen.  

![Hosting](images/user-statistics01.png){.thumbnail}

Um mit einem von Ihnen erstellten Benutzer auf die Statistiken Ihrer Website zuzugreifen, geben Sie die folgende Adresse ein. Ersetzen Sie dabei `000` mit der Cluster-Nummer Ihres Hostings und `mydomain.ovh` mit dem Domainnamen Ihrer Website (ohne "www""):

```bash
https://logs.cluster000.hosting.ovh.net/mydomain.ovh/
```

Klicken Sie im Bereich `Statistiken und Logs`{.action} auf `Die Statistiken anzeigen`{.action}.<br>
Rufen Sie im Tab Ihres Browsers, in dem das Statistikfenster angezeigt wird, den Link auf, über den Sie sich mit einem der erstellten Benutzer verbinden können.

![hosting](images/OWStatslink.png){.thumbnail}

> [!warning] 
>
> Wenn Sie die separaten Logs bei einem [Multisite-Eintrag](/pages/web_cloud/web_hosting/multisites_configure_multisite#schritt-2-eine-domain-oder-subdomain-hinzufugen) aktiviert haben, können die hier erstellten Benutzer nicht auf die Statistiken dieses Multisite-Eintrags zugreifen.
>

### Besucherstatistiken

Das **OVHcloud Web Statistics** Tool hilft Ihnen dabei, den Traffic der auf Ihrem Webhosting gehosteten Webseiten nachzuverfolgen und zu steuern, indem es Statistiken über Seitenbesuche und die Messung der Zuschauerzahlen visuell aufbereitet.

![Hosting](images/OWStats01.gif){.thumbnail}

Das Dashboard von OVHcloud Web Statistics ist in 6 Abschnitte im linken Bereich aufgeteilt.

- Dashboard: Visualisiert den Traffic der Website auf Ihrem Webhosting.
- Browsers: Zeigt ein Ranking der Webbrowser an, die am häufigsten für die Anzeige Ihrer Websites verwendet werden.
- Geolocalization: Gruppiert die Besucher der Website je nach Standort.
- Requests: Zeigt ein Ranking der Seiten an, die am häufigsten auf Ihren Webseiten besucht werden.
- Robots: Visualisiert automatische Verbindungsversuche zu Ihren Webseiten.
- Status: Zeigt Statistiken über Fehlschläge und Erfolge an, die anhand der zurückgegebenen HTTP-Codes ermittelt wurden.
- FAQ: Öffnet den Bereich für häufig gestellte Fragen.

Mit `Period selection` können Sie einen bestimmten Zeitraum auswählen.

### Logs

Sie können die ungefilterten Logs Ihres Hostings mit einer Verzögerung von etwa 5 Minuten anzeigen lassen.

![Hosting](images/logs01.png){.thumbnail}

Es stehen Ihnen verschiedene Log-Typen zur Verfügung:

- **web**: Hier finden Sie die verschiedenen Logs Ihrer Seitenaufrufe sowie die ausgehenden Aktionen Ihrer Website. So können Sie beispielsweise attackierende Zugriffsversuche erkennen.
- **ftp**: Die verschiedenen FTP Verbindungen werden in diesen Protokollen gespeichert.
- **error**: Diese Protokolle enthalten die von Ihrer Website generierten Fehler.
- **cgi**: Diese Logs sammeln die verschiedenen Aufrufe zu *cgi.bin* Skripten.
- **out**: Dies sind die externen Aufrufe Ihres Hostings.
- **ssh**: In diesen Logs sind die verschiedenen Verbindungen über SSH aufgeführt.
- **cron**: Die Ergebnisse der Ausführung Ihrer [geplanten Tasks](/pages/web_cloud/web_hosting/cron_tasks) werden hier geloggt.

### Aktivität des Webhostings

In diesem Abschnitt können Sie die Aktivität der Infrastruktur Ihres Webhostings sowie die Verwendung der Ressourcen anzeigen.

Wechseln Sie zum Tab `Allgemeine Informationen`{.action} und scrollen Sie zum Seitenende.

![Hosting](images/statistics03.png){.thumbnail}

Sie können im Dropdown-Menü in der oberen linken Ecke verschiedene Arten von Grafiken anzeigen:

- Ausgehende Verbindungen: Anfragen, die von Ihrer Website auf eine externe Seite gesendet werden.
- CPU Verwendung: CPU-Verbrauch auf Ihrer Hosting-Instanz
- Überschreitungen der Ressourcenobergrenzen: gibt an, wann Ihr Hosting die Ressourcen-Kapazität überschreitet.
- SQL Requests: Anzahl der Anfragen an die Datenbanken Ihres Hostings.
- SQL Antwortzeiten: Antwortzeit der an die Datenbanken Ihres Hostings gesendeten Anfragen.

## Weiterführende Informationen

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
