---
title: Demarrer son serveur sur un noyau OVH
slug: kernel-netboot
excerpt: Retrouvez ici les Étapes a suivre pour demarrer votre serveur sur un noyau OVH depuis le reseau.
section: Divers
---

**Dernière mise à jour le 25/02/2022**

## Prérequis

Le Netboot est un service proposé gratuitement par OVHcloud et qui permet de démarrer le serveur dédié que vous louez chez OVHcloud sur un kernel déjà compilé. Une fois configuré de cette façon, votre serveur charge automatiquement le noyau depuis le réseau, vous n'avez rien d'autre à configurer. Cette méthode vous permet également de mettre à jour très simplement votre noyau car OVHcloud compile la dernière version du noyau dès sa disponibilité et la met à disposition sur le Netboot.

Pour pouvoir modifier le netboot, il faut :

- Posséder un [serveur dédié](https://www.ovhcloud.com/fr/bare-metal/).
- Avoir accès à [l'espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).


Pour démarrer votre serveur sur un noyau réseau, connecter à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).

Rendez-vous dans la section `Bare Metal Cloud`{.action} et sélectionnez votre serveur dans `Serveurs dédiés`{.action}.

Recherchez « Boot » dans la zone **Informations générales** et cliquez sur `...`{.action} puis sur `Modifier`{.action}. 

![Netboot](images/netboot_2022.png){.thumbnail}

Sélectionnez `Booter en mode Network`{.action}.

![Netboot](images/netboot_005.png){.thumbnail}

Sélectionnez le noyau (kernel) disponible puis entrez le Root Device (partition où se trouve la partition racine de votre serveur).

Pour déterminer le Root Device de votre serveur, consultez le fichier /etc/fstab de votre serveur.

En SSH :

<div> <style type="text/css" scoped>span.prompt:before{content:"# ";}</style> <pre class="highlight command-prompt"> <span class="prompt">cat /etc/fstab</span> <span class="output"># <file system> <mount point> <type> <options> <dump> <pass></span> <span class="output">/dev/sda1 / ext3 errors=remount-ro 0 1</span> <span class="output">/dev/sda2 /home ext3 defaults,grpquota,usrquota 1 2</span> <span class="output">/dev/sda3 swap swap defaults 0 0</span> <span class="blank">&nbsp;</span> <span class="output">proc /proc proc defaults 0 0</span> <span class="output">sysfs /sys sysfs defaults 0 0</span> <span class="output">shm /dev/shm tmpfs nodev,nosuid,noexec 0 0</span> </pre></div>

Dans notre exemple, le Root Device sera /dev/sda1.

Cliquez sur `Suivant`{.action} et `Valider`{.action}.

Une fois la modification terminée, cliquez sur `...`{.action} à droite de « Statut » dans la zone intitulée **Etat des services.** Cliquez sur `Redémarrer`{.action} pour que le netboot soit pris en compte.

![Netboot](images/netboot_004.png){.thumbnail}

## Allez plus loin

Échangez avec notre communauté d’utilisateurs sur <https://community.ovh.com/.>