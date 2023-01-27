---
title: Acheter une Additional IP
slug: buy-additional-ip
excerpt: "Découvrez comment commander des adresses Additional IP pour vos instances"
section: Additional IP
order: 02
updated: 2023-01-04
---

**Dernière mise à jour le 04/01/2023**

> [!primary]
>
> Depuis le 6 octobre 2022, notre solution "IP Failover" s'appelle désormais [Additional IP](https://www.ovhcloud.com/fr-ca/network/additional-ip/). Cela n'a pas d'impact sur ses fonctionnalités.
>

## Objectif

Vous pouvez avoir besoin de configurer une adresse Additional IP sur vos instances pour différentes raisons :

- Vous avez plusieurs sites sur votre instance.
- Vous hébergez des projets internationaux.

Pour répondre à ces besoins, vous pouvez acheter une adresse Additional IP pour vos instances Public Cloud.<br>
Ces adresses Additional IP ne pourront être migrées que vers les instances d'un même projet.

**Ce guide explique comment acheter une Additional IP pour votre projet Public Cloud OVHcloud.**

## Prérequis

- Être connecté à l’[espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}.
- Disposer d'au moins une instance. Consultez à cet effet [le guide pour créer une instance depuis l'espace client](https://docs.ovh.com/ca/fr/public-cloud/premiers-pas-instance-public-cloud/).

> [!warning]
> Cette fonctionnalité n'est actuellement pas disponible pour les instances Metal.
>

## En pratique

Connectez-vous à l'[espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc), accédez à la section `Public Cloud`{.action} et sélectionnez le projet Public Cloud concerné.

Dans le menu de gauche, ouvrez `Public IPs`{.action} dans `Network`.

Ouvrez l'onglet `Additional IP`{.action} et cliquez sur le bouton `Actions`{.action}. Sélectionnez `Ajouter une nouvelle IP`{.action}.

![Ajout IP](images/buyaddIP_01.png){.thumbnail}

À l'étape 1 de la commande, cliquez sur `Suivant`{.action}.

![Ajout IP](images/buyaddIP_02.png){.thumbnail}

L'étape 2 permet de sélectionner un pays pour la nouvelle adresse IP.

![Ajout IP](images/buyaddIP_03.png){.thumbnail}

Les pays suivants sont disponibles pour la géolocalisation des IP :

|          |          |          |           |                |
|:--------:|:--------:|:--------:|:---------:|:--------------:|
| Belgique  | Finlande  | France   | Allemagne   | République Tchèque |
| Irelande  |  Italie   | Lituanie | Pays-bas | Royaume-Uni    |
| Portugal |  Espagne   |  Pologne |  Suisse |                 |

> [!primary] **Disponibilité**
> 
> Il est possible que certains de ces pays ne soient pas listés, en fonction de la disponibilité actuelle des adresses IPv4.
> 

> [!primary] **Location**
>
> La géolocalisation d’IP est uniquement basée sur des organismes de référence.
> 
> Par exemple, le [RIPE NCC](https://www.ripe.net/){.external} dessert l'Europe en tant que Registre Internet Régional.
>
> Si vous avez besoin de vérifier la géolocalisation d'une autre manière, contactez directement les organisations concernées. OVHcloud ne pourra vous founir d'assistance à ce sujet.

Une fois le pays sélectionné, cliquez sur `Suivant`{.action}.

A la dernière étape, sélectionnez votre instance dans le menu déroulant. Cliquez ensuite sur `Générer le bon de commande`{.action}.

![Ajout IP](images/buyaddIP_04.png){.thumbnail}

Le bon de commande s'ouvrira automatiquement afin de finaliser votre achat.

Consultez notre guide sur la [gestion des commandes OVHcloud](https://docs.ovh.com/ca/fr/billing/gerer-ses-commandes-ovh/) pour plus de détails.

Vous pouvez également retrouver le bon de commande dans votre espace client, rubrique `Tableau de bord`{.action}, en cliquant sur `Voir mes commandes`{.action}.

La prochaine étape consiste à configurer l’IP dans votre système d'exploitation. Consultez [notre guide dédié à cette configuration](https://docs.ovh.com/ca/fr/publiccloud/network-services/configure-additional-ip/).

## Aller plus loin

[Configurer une Additional IP](https://docs.ovh.com/ca/fr/publiccloud/network-services/configure-additional-ip/)

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
