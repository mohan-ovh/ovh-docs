---
title: 'Importer une IP Fail Over'
slug: importer-une-ip-fail-over
excerpt: 'Ce guide explique comment importer une IP Failover dans votre projet Public Cloud OVHcloud.'
legacy_guide_number: 1883
section: 'Réseau'
order: 11
---

**Dernière mise à jour le 10 mars 2022**

## Objectif

Si vous avez besoin de configurer une adresse IP Failover sur vos instances parce que :

- vous avez plusieurs sites sur votre instance 
- vous hébergez des projets internationaux
- vous voulez migrer votre activité depuis un serveur dédié vers une instance Public cloud

Il est possible d’importer une adresse IP Failover liée à un autre service OVHcloud.

**Ce guide explique comment importer une IP Failover dans votre projet Public Cloud OVHcloud.**

## Prérequis

- Un [projet Public Cloud](https://www.ovhcloud.com/fr/public-cloud/) dans votre compte OVHcloud.
- Être connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external}.
- Avoir [une IP Fail Over](https://www.ovhcloud.com/fr/bare-metal/ip/){.external}.

## En pratique

Tout d’abord, connectez-vous à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external} et sélectionnez votre projet dans la section `Public Cloud `{.action}. Ensuite, sélectionnez `Failover IP`{.action} dans la section "Network".

Cliquez sur `Actions`{.action} et sélectionnez `Importer une IP`{.action} pour afficher toutes les adresses IP pouvant être importées dans votre projet Public Cloud.

![Section IP](images/import1.png){.thumbnail}

Si vous ne disposez pas encore d’IP Failover sur votre projet public cloud, l’option d'importer une IP s’affichera alors sur la page d’accueil.

Cliquez sur les 3 points à droite de l’IP que vous voulez importer et cliquez sur `Importer cette IP Failover`{.action}.

![Importer une IP Failover](images/import2.png){.thumbnail}

Maintenant, cliquez sur `Importer`{.action} :

![Importer une IP Failover](images/importconfirm.png){.thumbnail}

Une fois que vous l’aurez fait, la page sera rechargée et vous obtiendrez un message confirmant que la migration de l’IP s’est effectuée avec succès.

Lorsque l’IP Failover a été importée avec succès, cliquez sur les 3 points à droite, puis sur `Modifier l’instance associée`{.action}.

![Importer une IP Failover](images/modifyinstance.png){.thumbnail}

Une fenêtre contextuelle apparaîtra pour vous permettre de choisir l'instance vers laquelle vous souhaitez déplacer votre IP :

![Importer une IP Failover](images/modifyinstance1.png){.thumbnail}

Cliquez sur `Joindre`{.action} puis vous verrez la page se recharger avec la confirmation que l’IP a été associée à l’instance :

![Importer une IP Failover](images/modifycompleted.png){.thumbnail}

Votre adresse IP Failover sera maintenant attachée à votre instance.

La prochaine étape portera sur la configuration de l’IP dans votre système d'exploitation, et vous pouvez consulter notre guide ici : [Configurer une IP Failover](https://docs.ovh.com/fr/public-cloud/configurer_une_ip_failover/){.external}.

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
