---
title: "Object Storage - Création d'un bucket"
slug: s3/create-bucket
section: Guides généraux pour débuter
order: 040
updated: 2022-09-27
---

**Dernière mise à jour le 27/09/2022**

## Objectif

**Ce guide a pour objectif de vous familiariser avec la création d'un bucket.**

> [!primary]
>
> - Si vous êtes intéressé par la classe de stockage ***Standard object storage - SWIFT API***, veuillez suivre ce [guide](https://docs.ovh.com/fr/storage/object-storage/pcs/create-container/).
> - Si vous êtes intéressé par la classe de stockage ***Cloud Archive - SWIFT API***, veuillez suivre ce [guide](https://docs.ovh.com/fr/storage/pca/creation-de-conteneur/).
>

## Prérequis

- Un [projet Public Cloud](https://www.ovhcloud.com/fr/public-cloud/) dans votre compte OVHcloud
- Être connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr)

## En pratique

### Utilisation de l'espace client

Pour créer un bucket Object Storage, vous devez d'abord vous connecter à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) et ouvrir votre projet `Public Cloud`{.action}. Cliquez sur `Object Storage`{.action} dans la barre de navigation à gauche puis sur l'onglet `Mes conteneurs`{.action}.

![My containers Dashboard](images/highperf-create-container-2022092808185322.png)

Cliquez sur `Créer un conteneur d'objet`{.action} et sélectionnez votre classe de stockage:

![Select your solution](images/highperf-create-container-20220928081750384.png)

Sélectionnez une région :

> [!primary]
>
> Les régions peuvent varier suivant la classe de stockage sélectionnée.
>

![Select a region](images/highperf-create-container-20220928082104424.png)

Vous devez lier un utilisateur au bucket :

![Link a user](images/highperf-create-container-20220928082210758.png)

Pour cela, vous pouvez lier un utilisateur S3 existant :

![Link a user](images/highperf-create-container-20220928082306958.png)

Vous pouvez voir les informations d'identification de l'utilisateur, en cliquant sur `View credentials`{.action} :

![view credentials](images/highperf-create-container-20220928082435427.png)

Si vous n'en avez pas déjà, vous pouvez créer un nouvel utilisateur S3 :

![Create S3 user](images/highperf-create-container-20220928082604314.png)

Les informations d'identification de l'utilisateur sont alors affichées :

![User created credentials](images/highperf-create-container-20220928082836834.png)

Pour finir, nommez votre bucket :

![Container name](images/highperf-create-container-20220928082938155.png)

Félicitations, votre bucket est créé :

![Result](images/highperf-create-container-20220928083209650.png)

### Où trouver l'URL Endpoint d'un bucket

Cliquez sur le nom de votre bucket pour en afficher les détails et le contenu :

![Bucket details](images/highperf-create-container-20220928091433895.png)

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
