---
title: Einen Domainnamen zu einem anderen Registrar transferieren
slug: ausgehender-transfer-einer-generischen-oder-geografischen-domain
excerpt: Erfahren Sie hier, wie Sie Ihre Domain von OVHcloud zu einem Provider Ihrer Wahl transferieren
section: Transfer
order: 04
updated: 2022-12-09
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie beim geringsten Zweifel die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button «Mitmachen» auf dieser Seite.
>

**Letzte Aktualisierung am 09.12.2022**

## Ziel

**Domaintransfer** bezeichnet den Umzug einer Domain von einem Registrar zu einem anderen. Wenn Sie zum Beispiel eine Domain auf unserer Webseite bestellt haben, ist OVHcloud deren aktueller Registrar. Ein ausgehender Domaintransfer muss vom neuen Registrar gestartet werden.

Um unbefugte Transferanfragen zu verhindern, sind Domains in der Regel vom Registrar gesperrt, indem sie in den Status *clientTransferProhibited* gesetzt werden. Dieser Schutz muss im OVHcloud Kundencenter aufgehoben werden, bevor mit dem Transfer begonnen wird.

**Diese Anleitung erklärt, wie Sie Ihre Domain für einen ausgehenden Transfer vorbereiten.**

> [!warning]
>
> Soll der betreffende Domainname bei OVHcloud registriert bleiben, aber hinsichtlich der Verwaltungs- oder Eigentumsverhältnisse bearbeitet werden, ist ein ausgehender Transfer der Domain nicht der geeignete Vorgang.
>
> Um die Verwaltung des Domainnamens einem anderen OVHcloud Kunden-Account zu übertragen, muss stattdessen eine **Änderung der Kontakte** durchgeführt werden. Die Vorgehensweise wird in [dieser Anleitung](https://docs.ovh.com/de/customer/verwaltung-der-kontakte/) beschrieben.
>
> Wenn auch der **Inhaber des Domainnamens** geändert werden muss, sollte dies erfolgen, **bevor** Sie die Kontakte des Domainnamens ändern. Verwenden Sie dazu unsere Anleitung zum [Inhaberwechsel für Domainnamen](https://docs.ovh.com/de/domains/wechsel_des_domaininhabers/).
>

## Voraussetzungen

- Sie verfügen über einen bei OVHcloud registrierten [Domainnamen](https://www.ovhcloud.com/de/domains/).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) mit den erforderlichen Berechtigungen zum Verwalten der Domain (Domainadministrator).
- Die Registrierung der betreffenden Domain erfolgte vor mindestens 60 Tagen und sie wurde in den letzten 60 Tagen weder transferiert noch übertragen (Inhaberwechsel).

> [!primary]
>
> Wenn Sie der **Inhaber** der Domain sind, deren Verwaltung Ihnen im OVHcloud Kundencenter jedoch nicht möglich ist, weder über Ihren eigenen Zugang noch den Administrator-Kontakt der Domain, konsultieren Sie bitte [diese Anleitung](../../customer/verwaltung-der-kontakte/#sonderfall-bei-domaininhabern), bevor Sie fortfahren.
>

## In der praktischen Anwendung

> [!warning]
>
> Die folgenden Instruktionen beschreiben die gängigste Methode zum Transfer einer Domain, die für die meisten Top-Level-Domains (TLD) gültig ist. Die spezifischen Verfahrensvorschriften für TLDs werden jedoch ausschließlich von der zuständigen Vergabestelle, d.h. der **Registry** festgelegt. Registrare wie OVHcloud müssen diese Regeln einhalten und haben keinen Einfluss auf die Entscheidungen der Registry.
>
> Das genaue Verfahren für den Transfer von Domains kann daher variieren, insbesondere bei bestimmten Ländercode-TLDs (ccTLD, z.B. .lu, .uk, .hk, .ro) und einigen Spezial-TLDs (.am, .fm., etc.). Domaintransfers können auch aus außerordentlichen Gründen verhindert werden; hierzu zählen etwa: ausstehende Zahlung, Missbrauchsfall oder Registry-Sperre.
>
> Wir empfehlen, im Zweifelsfall folgende Ressourcen zu Rate zu ziehen:
>
> - die Webseite der zuständigen TLD-Registry
> - die [Liste der bei OVHcloud verfügbaren TLDs](https://www.ovhcloud.com/de/domains/tld/)
> - [Erläuterungen der ICANN zu den EPP-Statuscodes](https://www.icann.org/resources/pages/epp-status-codes-2014-06-16-en) (um herauszufinden, welche Statuscodes derzeit für Ihre Domain gelten, führen Sie eine *Whois*-Suche aus, vorzugsweise unter Verwendung der Webseite der entsprechenden TLD-Registry)
> - die Webseite und das Verwaltungsinterface Ihres neuen Registrars, insbesondere für Fragen im Zusammenhang mit einem ausstehenden Transferprozess
>

### Schritt 1: Transfer-Schutz der Domain aufheben

Loggen Sie sich in Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) ein und gehen Sie im Bereich `Web Cloud`{.action} auf `Domainnamen`{.action}. Wählen Sie die betreffende Domain aus.

Im Tab `Allgemeine Informationen`{.action} finden Sie den Regler `Transfer-Schutz` unter **Sicherheit** mit der Standardeinstellung `Aktiviert`{.action}.

![Schutz aktiviert](images/outgoing-transfer-step1.png){.thumbnail}

Klicken Sie auf den Slider-Button und bestätigen Sie im Popup-Fenster, dass Sie diesen Schutz entfernen möchten. Warten Sie einige Minuten, bis der Status sich auf `Deaktiviert`{.action} ändert.

![Deaktivierung](images/outgoing-transfer-step2.png){.thumbnail}

Sie können auch die Seite aktualisieren, falls zu lange keine Änderung eintritt.

> [!primary]
>
> Wenn der Schutz entfernt wird, bleibt die Domain sieben Tage lang entsperrt. Nach diesem Zeitraum wird der Schutz automatisch reaktiviert. Wenn Sie in dieser Zeit keinen Transfer Ihrer Domain bei Ihrem neuen Registrar beantragen, muss die Domain noch einmal entsperrt werden.
>

### Schritt 2: Transfer-Code abrufen

Sobald sich der Status der Domain auf `Deaktiviert`{.action} aktualisiert, erscheint unter `Transfer-Schutz` der Link `AUTH/INFO`{.action}. Klicken Sie darauf, um ein Fenster zu öffnen, in dem Ihr AUTH/INFO-Code angezeigt wird (auch als Transferschlüssel, Domainpasswort, AUTH-CODE oder EPP-Code bezeichnet).

![outgoingtransfer](images/outgoing-transfer-step3.png){.thumbnail}

Dieser Code wird von Ihrem neuen Registrar angefordert werden, um den Transfer abzuschließen. Sie können die Details bei Ihrem Provider überprüfen.

Anstatt den Code manuell einzugeben, empfehlen wir, diesen zu kopieren und einzufügen, da einige Zeichen leicht zu verwechseln sind.

> [!warning]
>
> Wenn die Domain gesperrt oder abgelaufen ist, muss über Ihr OVHcloud Kundencenter ein [Support-Ticket erstellt werden](https://www.ovh.com/manager/dedicated/#/support/tickets/new).

Sobald der Transfer-Code abgerufen wurde, reaktivieren Sie den Transfer-Schutz **nicht, es sei denn, Sie möchten den Transfer verhindern**.

### Schritt 3: Transfer zum neuen Registrar beauftragen

Nach erfolgreicher Durchführung der vorherigen Schritte können Sie den Transferprozess starten, in der Regel indem Sie eine Bestellung bei Ihrem neuen Provider aufgeben. Der Transfer kann dann bis zu 10 Tage dauern. 

Weitere Informationen hierzu erhalten Sie bei Ihren neuen Registrar.

> [!warning]
>
> Wenn Ihr neuer Registrar einen neuen Transfer-Code anfordert, dann können Sie den `Transfer-Schutz` für Ihre Domain erneut aktivieren und ihn einige Minuten später wieder deaktivieren. So können Sie einen neuen Transfer-Code abrufen.
>

## Weiterführende Informationen

[Transfer einer .co.uk Domain](https://docs.ovh.com/de/domains/transfer-ausgehend-einer-domainnamen-couk/)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](https://partner.ovhcloud.com/de/directory/).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](https://www.ovhcloud.com/de/support-levels/).

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
