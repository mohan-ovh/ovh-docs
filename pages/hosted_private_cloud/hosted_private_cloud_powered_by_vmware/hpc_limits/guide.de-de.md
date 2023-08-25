---
title: Technische Kapazitäten
excerpt: 'Entdecken Sie die technischen Kapazitäten und Einschränkungen der Hosted Private Cloud Lösungen von OVHcloud'
updated: 2023-03-23
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>


## Ziel

**Diese Seite bietet einen Überblick über die Funktionen und technischen Einschränkungen der OVHcloud Hosted Private Cloud Dienste.**

## Bekannte Kapazitäten und Beschränkungen

| Element | Beschreibung | Wert |
|:-----:|:-----:|:----------:|
| Maximale Anzahl pro Client-ID | Anzahl der vCenter oder Pakete pro Organisation | Kein Limit |
| Anzahl der verbundenen PCC | vCenters Verbindung (Enhanced Link Mode) | 0 (nicht autorisiert) |
| Anzahl min. von Datastores pro PCC (SLA) | Anzahl der Datastores pro vCenter zur Aufrechterhaltung des Service Level Agreements | 2 |
| Anzahl min. von Hosts pro PCC (SLA) | Anzahl der Hosts pro vCenter zur Aufrechterhaltung des Service Level Agreements | 2 |
| Anzahl min. von Hosts pro PCC (ohne SLA) | Mindestanzahl der Hosts, die in vCenter ohne Service Level Agreement zu verwenden sind | 0 |
| Maximale Anzahl von Hosts pro Cluster | Hosts je Cluster | 64 |
| Maximale Anzahl Cluster pro vDc | Anzahl der Cluster im gleichen virtuellen Datacenter | Kein Limit |
| Maximale Anzahl vDc pro PCC | Anzahl der virtuellen Rechenzentren (vDC), die Kunden pro vCenter hinzufügen können | 400 |
| Maximale Anzahl von Hosts pro PCC | Host-Limits pro vCenter | 231 |
| Maximale Anzahl von Datastores pro PCC | Datastore-Limits pro vCenter | 110 |
| Maximale Anzahl virtuellen Maschinen pro SDDC | VMs, die von demselben vCenter verwaltet werden | 25 000 |
| Maximale Anzahl virtuellen Maschinen pro Host | VMs werden auf demselben physischen Host gehostet | 1024 |
| Maximale Anzahl IP-Adressen per PCC | Maximale Anzahl öffentlichen IP-Adressen, die über vCenter zugewiesen und nutzbar sind | 1 x /23 |
| vCPUs, RAM und Festplatte für vCenter Standard | vCenter (VCSA) zugewiesene Ressourcen | 4 virtuelle Prozessoren, 16 GB RAM, 290 GB Speicherplatz |
| vCPUs, RAM und Festplatte für NSX Standard | Dem Manager und dem Controller NSX zugewiesene Ressourcen | 4 virtuelle CPU, 4 GB RAM, 60 GB Speicherplatz<br>4 virtuelle CPU, 2 GB RAM, 28 GB Speicherplatz |
| vCPUs, RAM und Festplatte für vROPS | vROPS-Ressourcen | 4 virtuelle Prozessoren, 16 GB RAM |
| Maximale Anzahl von Edge Nodes | Maximale Anzahl von NSX zu implementierenden Peripheriegeräten | 2000 |
| Maximale Anzahl IPSec VPN Tunnel | Maximale Anzahl von VPN-Tunneln pro | 512 Compact Edge<br>1600 Edge<br>4096 quad large edge<br>6000 extra large Edge |
| Maximale Anzahl vRack pro vDc | Maximale Anzahl private Netzwerke von Virtual Data Center (VDC) | 1 |
| Maximale Anzahl L2 VPN Kunden | Anzahl zu verbindender VPN Clients | 5 |
| Maximale Anzahl autorisierte IP-Adressen | Anzahl der IP-Adressen, die sich mit Ihrer VMware Infrastruktur verbinden dürfen | 2048 |

## Weiterführende Informationen

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
