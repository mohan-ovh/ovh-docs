---
title: 'Mode bridge IP'
excerpt: 'Apprenez à utiliser le mode bridge pour configurer l’accès à Internet de vos machines virtuelles'
updated: 2022-12-20
---

**Dernière mise à jour le 23/02/2023**

> [!primary]
>
> Depuis le 6 octobre 2022, notre solution "IP Failover" s'appelle désormais [Additional IP](https://www.ovhcloud.com/fr-ca/network/additional-ip/). Cela n'a pas d'impact sur ses fonctionnalités.
>

## Objectif

La mise en réseau en mode bridge peut être utilisée pour configurer vos machines virtuelles. Quelques modifications sont nécessaires pour que la configuration fonctionne sur notre réseau.

**Ce guide vous montre comment utiliser le mode bridge pour configurer l'accès à Internet pour vos machines virtuelles.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/TZZbPe9hCOk?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Prérequis

* Posséder un serveur dédié avec un hyperviseur installé ([VMware ESXi](http://www.vmware.com/products/esxi-and-esx/overview.html){.external}, Citrix Xen Server, Proxmox, par exemple).
* Bénéficier d'au moins une adresse [Additional IP](https://www.ovhcloud.com/fr-ca/bare-metal/ip/) connectée au serveur.
* Être connecté à votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}.

> [!warning]
> Cette fonctionnalité peut être indisponible ou limitée sur les [serveurs dédiés **Eco**](https://eco.ovhcloud.com/fr-ca/about/).
>
> Consultez notre [comparatif](https://eco.ovhcloud.com/fr-ca/compare/) pour plus d’informations.
>
> Le présent guide n'est pas applicable aux serveurs des gammes [Scale](https://www.ovhcloud.com/fr-ca/bare-metal/scale/) et [High Grade](https://www.ovhcloud.com/fr-ca/bare-metal/high-grade/).
>
> Rendez-vous sur la [page de configuration dédiée](/pages/bare_metal_cloud/dedicated_servers/proxmox-network-HG-Scale).


## En pratique

Les étapes de base sont toujours les mêmes, indépendamment des systèmes utilisés :

* création d'une adresse MAC virtuelle pour une adresse IP de basculement ;
* régler l'adresse MAC de la machine virtuelle (VM) sur cette nouvelle adresse ;
* configurer l'adresse IP, le masque réseau, la passerelle et la route vers la passerelle à l'intérieur de la machine virtuelle.

Pour cet exemple, nous utiliserons les valeurs suivantes dans nos exemples de code. Celles-ci devront être remplacées par vos propres valeurs :

* « SERVER_IP » : l’adresse IP principale de votre serveur ;
* « ADDITIONAL_IP » : votre adresse Additional IP ;
* « GATEWAY_IP » : l’adresse de votre passerelle par défaut.

### Assigner une adresse MAC virtuelle

Connectez-vous à votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}, cliquez sur le menu `Bare Metal Cloud`{.action} puis sur la section `IP`{.action}.

Cliquez sur l'onglet `Additional IP`{.action}.

![manage IPs](images/manageIPs2022.png){.thumbnail}

Cliquez sur le bouton `...`{.action} à côté de l'Additional IP de votre choix puis sur `Ajouter une MAC virtuelle`{.action}.

![Ajouter une MAC virtuelle (1)](images/addvmac.png){.thumbnail}

Sélectionnez « ovh » dans la liste déroulante « Type », tapez un nom dans le champ « Nom de la machine virtuelle », puis cliquez sur `Valider`{.action}.

![Ajouter une MAC virtuelle (2)](images/addvmac2.png){.thumbnail}

### Déterminer l'adresse de la passerelle

Pour configurer vos machines virtuelles pour l'accès à Internet, vous devez connaître la passerelle de votre machine hôte, c’est-à-dire, votre serveur dédié. L'adresse de la passerelle est constituée des trois premiers octets de l'adresse IP principale de votre serveur, le dernier octet étant de 254. Par exemple, si l’adresse IP principale de votre serveur est :

* 169.254.10.020

Votre adresse de passerelle sera alors :

* 169.254.10.254

### Préparer l'hôte

> [!primary]
>
Pour tous les systèmes d'exploitation et distributions, vous devez configurer votre machine virtuelle avec l'adresse MAC virtuelle créée dans votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}.
>

#### Proxmox

Après avoir créé la machine virtuelle et lorsque celle-ci est encore éteinte :
 1. Sélectionnez la machine virtuelle ;
 2. Ouvrez la section « Matériel » ;
 3. Sélectionnez `Périphérique réseau`{.action} ;
 4. Cliquez sur le bouton `Modifier`{.action}.

![naviguer jusqu'au périphérique réseau](images/proxmox_01.png){.thumbnail}

Ajoutez ensuite l'adresse MAC que vous avez créée précédemment.
![ouvrir un périphérique réseau](images/proxmox_02.png){.thumbnail}


Vous pouvez maintenant démarrer votre machine virtuelle et passer aux étapes suivantes, en fonction du système d'exploitation choisi.

#### VMware ESXi

Après avoir créé la machine virtuelle et lorsqu'elle est hors tension, effectuez un clic droit sur celle-ci et cliquez sur `Modifier les paramètres`{.action}.

![Menu contextuel VM](images/vmware_01.png){.thumbnail}

Dépliez `Netwok Adapter 1`{.action} et changez la valeur dans le menu déroulant `Adresse MAC`{.action} en mode « Manuel » et entrez l'adresse MAC VMware créée précédemment.

![Modifier les paramètres](images/vmware_02.png){.thumbnail}

Vous pouvez maintenant démarrer votre machine virtuelle et passer aux étapes suivantes, selon votre système d'exploitation.

### Configurer les machines virtuelles

#### Debian

Connectez-vous à l'interface système (ou *shell*) de votre machine virtuelle. Une fois connecté, ouvrez le fichier de configuration réseau de la machine virtuelle, situé dans `/etc/network/interfaces`.
Modifiez le fichier pour qu'il reflète la configuration ci-dessous. N'oubliez pas de remplacer nos variables par vos propres valeurs :

- Distributions anciennes :

```console
auto lo eth0
iface lo inet loopback
iface eth0 inet static
    address ADDITIONAL_IP
    netmask 255.255.255.255
    broadcast ADDITIONAL_IP
    post-up route add GATEWAY_IP dev eth0
    post-up route add default gw GATEWAY_IP
    pre-down route del GATEWAY_IP dev eth0
    pre-down route del default gw GATEWAY_IP
```

- Distributions récentes :

```console
auto lo eth0
iface lo inet loopback
iface eth0 inet static
    address ADDITIONAL_IP
    netmask 255.255.255.255
    broadcast ADDITIONAL_IP
    post-up ip route add GATEWAY_IP dev eth0
    post-up ip route add default via GATEWAY_IP
    pre-down ip route del GATEWAY_IP dev eth0
    pre-down ip route del default via GATEWAY_IP
```

Remplacez également `eth0` si votre système utilise des noms d'interface réseau prévisibles. Vous pouvez trouver les noms d'interface réseau à l'aide de la commande suivante :

```bash
ls /sys/class/net
```
Enregistrez et fermez le fichier, puis redémarrez la machine virtuelle.

#### Systèmes d'exploitation Red Hat et basés sur Red Hat (CentOS 6, Scientific Linux, ClearOS, etc.)

Ouvrez un terminal sur votre machine virtuelle. Une fois connecté, ouvrez le fichier de configuration réseau de la machine virtuelle. Celui-ci est situé dans `/etc/network/interfaces`. Modifiez le fichier pour qu'il reflète la configuration ci-dessous. N'oubliez pas de remplacer nos variables par vos propres valeurs :

```console
DEVICE=eth0
BOOTPROTO=none
ONBOOT=yes
USERCTL=no
IPV6INIT=no
PEERDNS=yes
TYPE=Ethernet
NETMASK=255.255.255.255
IPADDR=ADDITIONAL_IP
GATEWAY=GATEWAY_IP
ARP=yes
HWADDR=MY:VI:RT:UA:LM:AC
```

Maintenant, enregistrez et fermez le fichier.

Ensuite, ouvrez le fichier de routage de la machine virtuelle. Celui-ci se trouve dans `/etc/sysconfig/network-scripts/route-eth0`. Modifiez le fichier pour qu'il reflète la configuration ci-dessous. N'oubliez pas de remplacer nos variables par vos propres valeurs :

```console
GATEWAY_IP dev eth0
default via GATEWAY_IP dev eth0
```

Enregistrez et fermez le fichier, puis redémarrez la machine virtuelle.

#### CentOS 7

> [!primary]
> 
> Concernant CentOS 7, le nom de la carte réseau varie en fonction des options d'installation. Vous devrez vérifier le nom de l'adaptateur et l'utiliser pour configurer votre machine virtuelle. Vous pouvez trouver les noms d'interface réseau avec la commande `ls /sys/class/net`.
> 

Ouvrez un terminal sur votre machine virtuelle. Une fois connecté, ouvrez le fichier de configuration réseau de la machine virtuelle, qui se trouve dans `/etc/sysconfig/network-scripts/ifcfg-(nom de l'interface)`. Modifiez le fichier pour qu'il reflète la configuration ci-dessous. N'oubliez pas de remplacer nos variables par vos propres valeurs :

```console
DEVICE=(interface-name)
BOOTPROTO=none
ONBOOT=yes
USERCTL=no
IPV6INIT=no
PEERDNS=yes
TYPE=Ethernet
NETMASK=255.255.255.255
IPADDR=ADDITIONAL_IP
GATEWAY=GATEWAY_IP
ARP=yes
HWADDR=MY:VI:RT:UA:LM:AC
```

Sauvegardez et fermez le fichier.

Ouvrez ensuite le fichier de routage de la machine virtuelle, qui se trouve dans `/etc/sysconfig/network-scripts/route-(nom-de l’interface)`. Modifiez le fichier pour qu'il reflète la configuration ci-dessous. N'oubliez pas de remplacer nos variables par vos propres valeurs :

```console
GATEWAY_IP - 169.254.10.254 (nom-interface)
NETWORK_GW_VM - 255.255.255.0 (insérez le nom de l'interface)
default GATEWAY_IP
```
Enregistrez et fermez le fichier.

Ensuite, ouvrez le fichier de routage de la machine virtuelle. Celui-ci se trouve dans `/etc/sysconfig/network/resolv.conf`.

```console
nameserver 213.186.33.99
```

Après avoir enregistré et fermé le fichier, redémarrez votre réseau ou votre machine virtuelle.

#### FreeBSD

Ouvrez un terminal sur votre machine virtuelle. Une fois connecté, ouvrez le fichier de configuration réseau de la machine virtuelle, situé dans le dossier `/etc/rc.conf`. Modifiez le fichier pour qu'il reflète la configuration ci-dessous. Dans cet exemple, le nom de l'interface est « em0 ». Vous pouvez le modifier si nécessaire.

```console
ifconfig_em0="inet ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP"
static_routes="net1 net2"
route_net1="-net GATEWAY_IP/32 -interface em0"
route_net2="default GATEWAY_IP"
```

Enregistrez et fermez le fichier. Ensuite, éditez le fichier `/etc/resolv.conf`. Créez-le si nécessaire.

```console
nameserver 213.186.33.99
```

Enregistrez et fermez le fichier, puis redémarrez la machine virtuelle.

#### Ubuntu 18.04

En premier lieu, établissez une connexion SSH à votre machine virtuelle et ouvrez le fichier de configuration réseau situé dans `/etc/netplan/` à l'aide de la commande suivante. À des fins de démonstration, notre fichier s'appelle « 50-cloud-init.yaml ».

```bash
# nano /etc/netplan/50-cloud-init.yaml
```

Une fois le fichier ouvert, modifiez-le avec le code suivant :

```yaml
network:
    ethernets:
        (nom-interface) :
            addresses:
                - ADDITIONAL_IP/32
            nameservers:
                addresses:
                    - 213.186.33.99
                search: []
            optional: true
            routes:
                - to: 0.0.0.0/0
                  via : GATEWAY_IP
                  on-link: true
    Version : 2
```

Une fois les modifications effectuées, enregistrez et fermez le fichier, puis exécutez la commande suivante :

```bash
# netplan try
Warning: Stopping systemd-networkd.service, but it can still be activated by:
  systemd-networkd.socket
Do you want to keep these settings?

Press ENTER before the timeout to accept the new configuration

Changes will revert in 120 seconds
Configuration accepted.
```

#### Windows Server 2012/Hyper-V

Avant de configurer votre machine virtuelle, vous devrez créer un commutateur virtuel.

À partir de la ligne de commande de votre serveur dédié, exécutez `IPconfig / ALL`{.action}, puis notez le nom de la carte réseau contenant l'adresse IP principale du serveur.

Dans le panneau de configuration Hyper-V, créez un nouveau commutateur virtuel et définissez le type de connexion sur `External`{.action}.

Sélectionnez l'adaptateur avec l'adresse IP du serveur, puis cochez `Autoriser le système d'exploitation à partager cette carte réseau`{.action}.

![networkbridging](images/network-bridging-windows-2012-1.jpg){.thumbnail}

> [!primary]
> 
>Cette étape n'est requise qu'une seule fois pour un serveur Hyper-V. Pour toutes les machines virtuelles, un commutateur virtuel est nécessaire pour connecter les cartes réseau virtuelles de la machine virtuelle à la carte physique du serveur.
> 

Ensuite, sélectionnez la machine virtuelle à laquelle vous souhaitez ajouter l'Additional IP. Utilisez le panneau de configuration Hyper-V pour modifier les paramètres de la machine virtuelle, puis fermez-le.

Ensuite, déployez la carte réseau et cliquez sur `Advanced Features`{.action}, définissez l'adresse MAC sur `Static`{.action} et entrez l'adresse MAC virtuelle pour l'adresse Additional IP. Une fois que vous avez entré ces paramètres, appuyez sur `OK`{.action} pour appliquer les modifications.

![networkbridging](images/network-bridging-windows-2012-2.jpg){.thumbnail}

Ensuite, démarrez la machine virtuelle et connectez-vous en tant qu'administrateur, puis accédez à `Control Panel`{.action} et `Network and Sharing Center`{.action}. Cliquez sur le lien `Connections : Ethernet`{.action}, puis cliquez sur le bouton `Properties`{.action} pour afficher les propriétés Ethernet.

Sélectionnez `Internet Protocol Version 4 (TCP/IPv4)`{.action}, puis cliquez sur le bouton `Properties`{.action} pour afficher les propriétés IPv4.

![networkbridging](images/network-bridging-windows-2012-3.jpg){.thumbnail}

Dans la fenêtre de propriétés de l’IPv4, sélectionnez `Use the following IP address`{.action}. Entrez l'adresse Additional IP dans le champ d'adresses IP et entrez « 255.255.255.255 » dans le masque de sous-réseau.

Ensuite, entrez l’adresse IP de la passerelle de votre serveur dans la passerelle par défaut (par exemple, l’IP de votre serveur se terminant par 254) et entrez « 213.186.33.99 » dans le champ `Preferred DNS Server`{.action}.

Cliquez sur `OK`{.action} et ignorez le message d'avertissement relatif à l'adresse IP de la passerelle et à l'adresse IP attribuée qui ne figurent pas dans le même sous-réseau.

Finalement, redémarrez le serveur. La machine virtuelle doit alors être connectée à Internet à l'aide de l'adresse Additional IP.

![networkbridging](images/network-bridging-windows-2012-4.jpg){.thumbnail}

#### Résolution des défauts

Si vous ne parvenez pas à établir une connexion entre votre machine virtuelle et le réseau public et que vous soupçonnez un problème de réseau, redémarrez le serveur en mode rescue et configurez l'interface réseau passerelle directement sur l'hôte.

Pour ce faire, une fois que vous avez redémarré votre serveur en mode rescue, entrez les commandes suivantes :

```bash
ip link add name test-bridge link eth0 type macvlan
ip link set dev test-bridge address MAC_ADDRESS
ip link set test-bridge up
ip addr add ADDITIONAL_IP/32 dev test-bridge
```

Remplacez « MAC_ADDRESS » par l'adresse MAC virtuelle générée dans le panneau de configuration et « ADDITIONAL_IP » par l'Additional IP réel.

Ensuite, il vous suffit d'effectuer un ping sur votre Additional IP depuis l'extérieur. Si cela fonctionne, cela signifie probablement qu'il y a une erreur de configuration sur la machine virtuelle ou sur l'hôte qui empêche l'Additional IP de fonctionner en mode normal. Si, au contraire, l'IP ne fonctionne toujours pas, veuillez ouvrir un ticket à l'équipe d'assistance via votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external} pour une enquête complémentaire.

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/en/>.
