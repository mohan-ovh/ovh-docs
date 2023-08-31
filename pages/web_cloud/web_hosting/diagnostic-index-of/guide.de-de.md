---
title: Was tun, wenn eine “Index of“-Seite angezeigt wird?
excerpt: Erfahren Sie hier, wie Sie Ihre Website wieder online bringen, wenn eine “Index of“-Seite angezeigt wird
updated: 2023-05-04
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel 

Eine **Index of**-Seite erscheint in mindestens einem der folgenden Fälle:

- Ihr Domainname ist in der [Multisite-Konfiguration](/pages/web_cloud/web_hosting/multisites_configure_multisite) nicht korrekt auf Ihr Zielverzeichnis eingestellt.
- Das Zielverzeichnis, auf das Ihr Domainname verweist, enthält keine Datei namens **index.html** oder **index.php**.

![index_of](images/index_of.png){.thumbnail}

**Diese Anleitung erklärt, wie Sie die Anzeige einer "Index of"-Seite korrigieren.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](https://partner.ovhcloud.com/de/directory/) zu kontaktieren und/oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#gofurther).
>

## Voraussetzungen

- Sie verfügen über einen [Domainnamen](https://www.ovhcloud.com/de/domains/).
- Sie haben ein [OVHcloud Webhosting](https://www.ovhcloud.com/de/web-hosting/) in Ihrem Kunden-Account.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de).

## In der praktischen Anwendung

### Den Ursprung der "Index of"-Seite verstehen

Über die `Multisite`-Konfiguration Ihres Hostings wird Ihr Domainname mit einem Zielverzeichnis im [FTP-Speicherplatz](/pages/web_cloud/web_hosting/ftp_connection) Ihres Webhostings verknüpft. Dies geschieht über den Tab [Multisite](/pages/web_cloud/web_hosting/multisites_configure_multisite) Ihres Webhostings in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de).

Die Seite "**Index of**" ist ein Anzeichen dafür, dass Ihr Verzeichnis keine Indexdatei, also **index.php** oder **index.html** enthält. Eine solche Datei repräsentiert die Startseite bzw. den Einstiegspunkt Ihrer Website. Der Name dieser Datei ist standardisiert.

Ihr Domainname muss daher im Bereich `Multisite`{.action} Ihres Webhostings mit dem Wurzelverzeichnis verknüpft werden, das eine **index.php** oder **index.html** enthält.

> [!primary]
>
> Wenn Sie Ihren Domainnamen temporär mit einem `Wurzelverzeichnis` verknüpfen möchten, das keine **index.php** oder **index.html** Datei enthält, können Sie verhindern, dass die Auflistung von Ordnern auf Ihrer Website angezeigt wird, indem Sie [diesem Tutorial](/pages/web/hosting/htaccess_what_else_can_you_do#verzeichnis-browsing-verhindern) folgen. Sie können auch den Zugang zu Ihren Ordnern [mit einem Passwort schützen](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password).
>
> Wir empfehlen Ihnen, einen [spezialisierten Dienstleister](https://partner.ovhcloud.com/de/directory/) zu kontaktieren, falls Sie Schwierigkeiten haben, diese Konfiguration einzurichten. Unsere Support-Teams sind nicht in der Lage, Sie bei Änderungen an der internen Programmierung Ihrer Webseite zu unterstützen.

### Die häufigste Ursache einer "Index of"-Seite beheben

Sie haben die Dateien Ihrer Website **mydomain.ovh** per [FTP](/pages/web_cloud/web_hosting/ftp_connection) in den `www`-Ordner Ihres OVHcloud Webhostings importiert. Ihr Domainname ist jedoch nicht mit diesem Ordner in der Spalte `Wurzelverzeichnis` Ihrer `Multisite`-Konfiguration verknüpft.

![index_multisite](images/index_of_multisite.png){.thumbnail}

Ändern Sie das `Wurzelverzeichnis`, indem Sie in der Zeile des betreffenden Domainnames auf die Schaltfläche `...`{.action} klicken und dann `Domain bearbeiten`{.action} auswählen.

![modify_domain](images/modify_domain.png){.thumbnail}

Führen Sie im neuen Fenster die folgenden Aktionen aus:

- Setzen Sie einen Haken bei `Auch die Subdomain www.mydomain.ovh ändern`{.action} (1).
- Geben Sie den Ordnernamen Ihrer Webseite, der die **index.php** oder **index.html** enthält, als `Wurzelverzeichnis` (2) an.
- Klicken Sie auf `Weiter`{.action} (3).

![change_root_folder](images/change_root_folder01.png){.thumbnail}

> [!primary]
>
> Den `www`-Ordner als `Wurzelverzeichnis` zu verwenden ist nicht zwingend. Sie können Ihre Webseite auch in einem anderen Ordner innerhalb Ihres [FTP-Speicherplatzes](/pages/web_cloud/web_hosting/ftp_connection) installieren.
>

Klicken Sie anschließend auf `Bestätigen`{.action}.

![modify_root_folder_confirm](images/modify_root_folder_confirm.png){.thumbnail}

Sie erhalten das Ergebnis innerhalb weniger Minuten (denken Sie daran, Ihren Browser zu aktualisieren) wie in der folgenden Abbildung dargestellt:

![multisite_modified](images/multisite_modified.png){.thumbnail}

Überprüfen Sie, ob Ihre Webseite korrekt angezeigt wird. Wenn dies nicht der Fall ist, starten Sie Ihr Gerät neu und leeren Sie den Cache Ihres Browsers.

Stellen Sie außerdem sicher, dass eine Datei namens **index.php** oder **index.html** in Ihrem Zielverzeichnis vorhanden ist.

## Weiterführende Informationen <a name=“gofurther“></a>

[Die häufigsten Fehler bei 1-Klick-Modulen beheben](/pages/web_cloud/web_hosting/diagnostic_errors_module1clic)

[Fehler “Seite nicht installiert” beheben](/pages/web_cloud/web_hosting/multisites_website_not_installed)

[Mehrere Websites auf einem Webhosting einrichten](/pages/web_cloud/web_hosting/multisites_configure_multisite)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](https://partner.ovhcloud.com/de/directory/).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](https://www.ovhcloud.com/de/support-levels/).

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
