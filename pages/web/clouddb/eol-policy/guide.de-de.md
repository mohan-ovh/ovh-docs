---
title: EOL Policy für Managed Databases
updated: 2023-03-07
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

**Letzte Aktualisierung am 07.03.2023**

## Ziel

Von OVHcloud verwaltete Datenbanken (*Managed Databases*) verwenden verschiedene Datenbankmanagementsysteme (DBMS) wie MySQL oder PostgreSQL. Jede Version dieser Software erreicht irgendwann das Ende des Verkaufs (EOS) und dann das Ende des Supports. Die Version kann dann jeweils aktualisiert oder eingestellt werden ("Lebensende"). Wir möchten Ihnen dabei helfen, den Lebenszyklus der von OVHcloud verwalteten Datenbanken zu verstehen, um deren Weiterentwicklung besser vorherzusehen und vorzubereiten.

**Erfahren Sie hier die EOL-Richtlinien für von OVHcloud verwaltete Datenbanken.**

## Voraussetzungen

Sie verfügen über einen der folgenden Dienste:

- Eine in einem [Webhosting](https://www.ovhcloud.com/de/web-hosting/) enthaltene Datenbank.
- Eine [Web Cloud Databases Instanz](https://www.ovh.de/cloud/cloud-databases/) (auch in einem [Performance Webhosting](https://www.ovhcloud.com/de/web-hosting/) enthalten).
- Ein [Start SQL Datenbank-Paket](https://www.ovhcloud.com/de/web-hosting/options/start-sql/).

## In der praktischen Anwendung

### Erfasste Dienste

Die von der EOL Policy betroffenen Dienste sind:

- Webhosting Web Cloud Databases (auch Private SQL Dienste genannt), dedizierte DBMS Instanzen, die über das Webhosting-Netzwerk erreichbar sind ([siehe Ankündigungen](/pages/web/clouddb/clouddb-eos-eol)).
- SharedSQL Web Hosting Dienste, MySQL Datenbanken, die über das Webhosting-Netzwerk erreichbar sind ([siehe Ankündigungen](/pages/web/hosting/sql_eos_eol)).

### Definitionen und Leitlinien für EOL-Richtlinien

![Timeline](images/ovh.eol.policy.timeline.png)

EOL = End of Life

#### EOL-Ankündigung

Dies ist die Ankündigung zum Verkaus- und Supportende. OVHcloud wird in der Regel 90 Tage zwischen Ankündigung und Anwendung von EOL einhalten.

#### Verkaufsende ("End of Sale")

Der betroffene Dienst kann nach diesem Datum nicht mehr bestellt werden. Diese Regel greift frühestens 90 Tage nach der EOL-Ankündigung.

#### Ende des Supports ("End of Support")

Bis zu diesem Datum hat der Kunde gemäß den Vertragsbedingungen der Dienstleistung oder den allgemeinen Garantiebedingungen Anspruch auf Produktunterstützung.
Nach diesem Zeitpunkt wird der Dienst nicht mehr unterstützt und gilt als veraltet.
Diese Phase tritt frühestens 6 Monate nach der EOL-Ankündigung ein.

#### Obsoleszenzphase

Sie folgt auf das Supportende.

Wenn ein Datenbankdienst obsolet wird, können die beiden nachfolgenden Fälle eintreten.
Da dies auf Ihre Dienstleistungen Auswirkungen haben kann, erhalten Sie mindestens einen Monat vor der Obsoleszenzphase eine E-Mail-Benachrichtigung.

**Großes Versionsupdate**

Die Dienstleistung bleibt aktiv und wir aktualisieren das DBMS auf eine Hauptversion.
Diese Art von Update kann zu unerwünschten Verhaltensweisen Ihrer Anwendungen führen. Deshalb empfehlen wir Kunden, Änderungen bei Datenbankenversionen im Blick zu behalten und nicht bis zum Supportende zu warten.

**Diensteinstellung**

Anstatt das DBMS der betroffenen Dienstleistung auf die nächste verfügbare Hauptversion zu aktualisieren, können wir aus mehreren Gründen den Dienst einstellen:

- Das Update wird vom Herausgeber des DBMS nicht empfohlen.

- Die Entwicklung des DBMS ist abgeschlossen.

Die Einstellung kann je nach Fall auf zwei Arten erfolgen:

- Wir stoppen die Verlängerung des Dienstes. In diesem Fall wird der Dienst am Ende des Vertragszeitraums eingestellt.

- Wir stellen den Service ein und schreiben Ihnen die Restlaufzeit gut.

## Weiterführende Informationen
 
Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](https://partner.ovhcloud.com/de/directory/).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](https://www.ovhcloud.com/de/support-levels/).

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
