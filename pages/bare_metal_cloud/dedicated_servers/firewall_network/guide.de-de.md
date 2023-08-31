---
title: Konfiguration der Network Firewall
excerpt: Erfahren Sie hier, wie Sie die Network Firewall konfigurieren
updated: 2023-05-10
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel

Zum Schutz seiner weltweiten Infrastruktur und der Server seiner Kunden bietet OVHcloud eine konfigurierbare Network Firewall an, die in die **Anti-DDoS** (VAC) Lösung integriert ist. Mithilfe dieser Option kann die Anfälligkeit der Dienste für Angriffe aus dem öffentlichen Netz begrenzt werden.

**Diese Anleitung erklärt, wie Sie die Network Firewall konfigurieren.**

> [!primary]
>
> Weitere Informationen zu unserer Anti-DDoS-Lösung finden Sie hier: <https://www.ovhcloud.com/de/security/anti-ddos/>.
> 

![VAC im Detail](images/vac-inside.png){.thumbnail}

## Voraussetzungen

- Sie haben eine OVHcloud Dienstleistung abonniert, in der die Option Network Firewall enthalten ist ([Dedicated Server](https://www.ovhcloud.com/de/bare-metal/){.external}, [VPS](https://www.ovhcloud.com/de/vps/){.external}, [Public Cloud Instanz](https://www.ovhcloud.com/de/public-cloud/){.external}, [Hosted Private Cloud](https://www.ovhcloud.com/de/hosted-private-cloud/){.external}, [Floating IPs](https://www.ovhcloud.com/de/bare-metal/ip/){.external}, etc.).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de).

> [!warning]
> Diese Funktion kann nur eingeschränkt oder nicht verfügbar sein, falls ein Dedicated Server der [**Eco** Produktlinie](https://eco.ovhcloud.com/de/about/) eingesetzt wird.
>
> Weitere Informationen finden Sie auf der [Vergleichsseite](https://eco.ovhcloud.com/de/compare/).

## Beschreibung

### Network Firewall aktivieren

> [!primary]
>
> Die Network Firewall schützt die einem Server zugeordneten IP-Adressen. Wenn Sie also einen Server mit mehreren IP-Adressen haben, müssen Sie jede IP unabhängig konfigurieren. Eine globale Serverkonfiguration ist nicht möglich.
> 

Wenn Sie in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} eingeloggt sind, gehen Sie in den Bereich `Bare Metal Cloud`{.action} und klicken Sie auf `IP`{.action}.

Sie können das Dropdown-Menü unter "Meine öffentlichen IP-Adressen und dazugehörigen Dienste" verwenden, um Ihre Dienste nach Kategorie zu filtern.

![filter service](images/selectservice.png){.thumbnail}

Klicken Sie auf `...`{.action}, um die Firewall für eine IPv4-Adresse zu aktivieren.

![Aktivierung der Network Firewall](images/firewall_creation2022.png){.thumbnail}

- Anschließend werden Sie nach einer Bestätigung gefragt.

![Bestätigung](images/creationvalid.png){.thumbnail}

- Klicken Sie danach auf `Firewall aktivieren`{.action} (1) und dann auf `Firewall konfigurieren`{.action} (2), um mit der Konfiguration zu beginnen.

![Aktivierung der Konfiguration](images/activationconfig.png){.thumbnail}

Sie können bis zu **20 Regeln für jede IP-Adresse** festlegen.

> [!warning]
>
> Wenn Network Firewall mit Regeln konfiguriert ist, werden diese Regeln automatisch auf jeden DDoS-Angriff angewendet. Die Firewall kann vor Ende des Angriffs nicht deaktiviert werden, deshalb ist es wichtig, die Firewall-Regeln auf dem neuesten Stand zu halten.
> Standardmäßig sind keine Regeln konfiguriert, so dass alle Verbindungen offen sind.
> Sollten Sie Firewall-Regeln angelegt haben, denken Sie bitte daran, diese regelmäßig zu überprüfen, auch wenn Sie die Firewall deaktivieren.
> 

> [!primary]
>
> - Die UDP-Fragmentierung (DROP) ist standardmäßig blockiert. Wenn Sie ein VPN verwenden, denken Sie nach der Aktivierung der Network Firewall daran, Ihre maximale Übertragungseinheit (MTU) korrekt zu konfigurieren. In OpenVPN können Sie z.B. `MTU Test`{.action} anhaken.
> - Die Network Firewall hat keinen Einfluss auf die Verbindungen innerhalb des OVHcloud Netzwerks. Die definierten Regeln haben also keine Auswirkungen auf die Verbindungen im internen Netzwerk.
>

### Konfiguration der Network Firewall

> [!warning]
> Bitte beachten Sie, dass die Network Firewall von OVHcloud nicht verwendet werden kann, um Ports auf einem Server zu öffnen. Um Ports auf einem Server zu öffnen müssen Sie die Firewall des auf dem Server installierten Betriebssystems einrichten.<br>
> Weitere Informationen finden Sie in diesen Anleitungen: [Firewall auf einem Windows Server konfigurieren](/pages/bare_metal_cloud/dedicated_servers/activate-port-firewall-soft-win) und [Konfiguration der Linux Firewall mit iptables](/pages/bare_metal_cloud/dedicated_servers/firewall-Linux-iptable).
>

Um eine Regel hinzuzufügen, klicken Sie rechts auf die Schaltfläche `Eine Regel hinzufügen`{.action}:

![Regel hinzufügen](images/addarule2022.png){.thumbnail}

Legen Sie dann für jede Regel folgende Einstellungen fest:

- Die Priorität (von 0 bis 19, wobei die Regel mit dem Wert 0 als erste Regel angewendet wird, danach in aufsteigender Reihenfolge)
- Die auszuführende Aktion (`Erlauben`{.action} oder `Verbieten`{.action})
- Das Protokoll
- Dine IP-Adresse (optional)
- Den Quell-Port (nur bei TCP)
- Den Ziel-Port (nur bei TCP)
- Die TCP-Optionen (nur bei TCP)

![Details zum Hinzufügen einer Regel](images/ajoutregle4.png){.thumbnail}

> [!primary]
>
> - Priorität 0: Es wird empfohlen, das TCP-Protokoll auf allen IPs mit der `ESTABLISHED`{.action} Option zuzulassen. Mit dieser Option kann überprüft werden, ob das Paket Teil einer zuvor geöffneten (bereits initiierten) Sitzung ist. Wenn Sie diese Option nicht zulassen, wird der Server keine TCP-Rückmeldungen für SYN/ACK-Anfragen erhalten.
> - Priorität 19: Die empfohlene Einstellung ist, mit der Regel 19 das Verwerfen aller IPv4-Pakete einzustellen, damit alle Pakete, die durch keine der vorangegangenen Regeln akzeptiert wurden, blockiert werden.
> 

### Konfigurationsbeispiel

Um nur die Ports für SSH (22), HTTP (80), HTTPS (443) und UDP (auf Port 10000) zu öffnen, wenn ICMP erlaubt ist, nutzen Sie die folgenden Regeln:

![Konfigurationsbeispiel:](images/exemple.png){.thumbnail}

Die Regeln sind numerisch geordnet von 0 (erste angewandte Regel) bis 19 (zuletzt angewendete Regel). Die sequentielle Überprüfung der Regelkette wird abgebrochen, sobald eine Regel auf das empfangene Paket zutrifft.

Im Beispiel wird ein Paket für den TCP-Port 80 von der Regel 2 angenommen, die nachfolgenden Regeln werden also nicht mehr angewendet. Ein Paket, das für TCP-Port 25 bestimmt ist, wird nur von der letzten Regel (Nummer 19) abgefangen. Die Regel 19 blockiert daraufhin das Paket, da die Firewall in den voranstehenden Regeln die Kommunikation auf Port 25 nicht explizit erlaubt hat.

> [!warning]
> Wie erwähnt ist die vorstehende Konfiguration nur ein Beispiel und sollte nur als Referenz verwendet werden, wenn die Regeln nicht für die auf Ihrem Server gehosteten Dienste gelten. Es ist absolut notwendig, die Regeln Ihrer Firewall entsprechend den auf Ihrem Server gehosteten Diensten zu konfigurieren. Eine fehlerhafte Konfiguration Ihrer Firewall-Regeln kann dazu führen, dass der rechtmäßige Traffic blockiert wird und die Serverdienste nicht erreichbar sind.
>

### Schutzmodus

Unsere Anti-DDoS-Lösung (VAC) umfasst drei Varianten des Schutzmodus: Automatisch, Permanent und Erzwungen.

**Automatischer Schutz (permanente Erkennung)**: Standardmäßig unterliegen alle OVHcloud IPs dem automatischen Schutz.  Bei diesem Modus läuft Traffic nur über das Abwehrsystem, wenn er im Vergleich zum Traffic, den der Server normalerweise empfängt, als "ungewöhnlich" erkannt wird.

**Permanenter Schutz**: Dieser Modus kann über Ihr Kundencenter aktiviert oder deaktiviert werden. Wenn aktiviert, wird damit über unsere "Shield"-Hardware ein konstanter Erstfilter angewendet.<br>
Der gesamte Traffic läuft permanent über das Schutzsystem, bevor er den Server erreicht. Wir empfehlen diesen Modus für Dienste mit häufigen Angriffen.<br>
Bitte beachten Sie, dass der permanente Schutz Teil unserer Anti-DDoS-Lösung (VAC) ist. Sie können ihn auf Ihrer IP einsetzen, ohne Network Firewall zu aktivieren.

Öffnen Sie das Menü `IP`{.action} und klicken Sie auf `...`{.action} rechts neben der betreffenden IPv4. Wählen Sie `Schutz: permanenter Modus`{.action}.

**Erzwungener Schutz**: Dieser Modus wird automatisch aktiviert, sobald ein Angriff auf den Server erkannt wurde. Sobald der Modus für DDoS-Schutz aktiviert ist, kann er nicht deaktiviert werden. Zum Schutz unserer Infrastruktur wird der Schutz während des gesamten Angriffs aktiviert, bis er vollständig abgeschwächt ist.

> [!warning]
>
> Wenn unsere DDoS-Schutz-Funktion einen Angriff begrenzt, werden die Ihrerseits konfigurierten Regeln der Network Firewall auch dann angewendet, wenn Sie die Firewall deaktiviert haben. Wenn Sie möchten, dass während eines Angriffs keine Regeln angewandt werden, müssen Sie alle zuvor erstellten Regeln löschen.
> 
> Da die Abwehr in unseren DDoS-Schutz (VAC) integriert ist, kann sie nicht für einzelne Dienste deaktiviert werden. Alle OVHcloud Produkte werden mit DDoS-Schutz geliefert.

### Armor Firewall konfigurieren (Game Firewall)

> [!primary]
> Die Armor Firewall ist mit bestimmten Regeln vorkonfiguriert, die OVHcloud für die gängigsten Spiele festgelegt hat. Für Kunden, die über einen dedizierten Game Server verfügen, erlauben wir jedoch, einen Schritt weiter zu gehen und auch Regeln für Ports zu konfigurieren.
>

Um die Regeln Ihrer Ports in Armor zu konfigurieren müssen Sie sich zuerst in Ihrem OVHcloud Kundencenter einloggen.<br>
Gehen Sie anschließend in das Menü `IP`{.action} und klicken Sie auf `...`{.action}. neben der IP-Adresse Ihres Gameservers und anschließend auf `Game Firewall konfigurieren`{.action}.

![Game_wall](images/GAMEwall2021.png){.thumbnail}

Klicken Sie auf dem folgenden Bildschirm auf den Button `Regel hinzufügen`{.action}, um Armor hinzuzufügen.

Sie können bis zu **30 Regeln für jede IP-Adresse** festlegen.

![configure_Armor](images/ConfigureArmor2021.png){.thumbnail}

Aktivieren Sie die Ports nach Bedarf auf der folgenden Seite und klicken Sie auf `Bestätigen`{.action}, wenn Sie Ihre Regeln hinzugefügt haben. Die Armor Firewall wurde nun erfolgreich konfiguriert.

## Weiterführende Informationen

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
