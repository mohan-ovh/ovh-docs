---
title: 'Créer vos bases de données et vos utilisateurs sur votre serveur de bases de données'
excerpt: 'Découvrez comment créer une base de données sur votre serveur de bases de données.'
updated: 2023-02-15
---


## Objectif

Une base de données (*database*, « DB » ou « BDD ») permet de stocker des éléments dits dynamiques, comme des commentaires ou des articles par exemple. Ces bases sont aujourd'hui utilisées par la quasi-totalité des systèmes de gestion de contenu (*Content Management System* ou CMS) comme WordPress ou Joomla!.

**Découvrez comment créer une base de données sur votre serveur de bases de données.**

## Prérequis

- Disposer d'une [instance Web Cloud Databases](https://www.ovh.com/fr/cloud/cloud-databases/){.external} (incluse dans une offre d'[hébergement web Performance](https://www.ovhcloud.com/fr-ca/web-hosting/)).
- Être connecté à votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}.

## En pratique

### Créer une base de données

Rendez-vous dans votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}. Cliquez sur  l'onglet `Web Cloud`, puis sur `Web Cloud Databases`{.action}. Sélectionnez le nom de votre serveur de bases de données.

Dirigez-vous dans l'onglet `Bases de données` et enfin sur `Ajouter une base de données`{.action}

![web-cloud-databases](images/web-cloud-databases-createdb01.png){.thumbnail}

Renseignez les champs en respectant les critères indiqués. Il est possible de créer directement un utilisateur en cochant la case **«Créer un utilisateur»** :

- **Nom de la base** (obligatoire) : il s'agit du nom de votre future base de données.
- **Nom d'utilisateur** (seulement si la case `Créer un utilisateur` est cochée) : il s'agit de l'utilisateur qui pourra se connecter à votre base de données et y effectuer des requêtes.
- **Droits** (seulement si la case `Créer un utilisateur` est cochée) : il s'agit des droits qui seront associés à l'utilisateur sur la base de données. Pour une utilisation classique, sélectionnez `Administrateur`{.action}. Les droits peuvent être modifiés par la suite.
- **Mot de passe**/**Confirmer le mot de passe** (seulement si la case `Créer un utilisateur` est cochée) : sélectionnez un mot de passe, puis confirmez ce dernier.

Cliquez sur `Valider`{.action}.

![web-cloud-databases](images/web-cloud-databases-createdb02.png){.thumbnail}

### Créer un utilisateur

Pour utiliser un serveur de bases de données OVHcloud, il est nécessaire de créer des utilisateurs qui auront des droits spécifiques pour se connecter à une base de données.

Rendez-vous dans votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}. Cliquez sur  l'onglet `Web Cloud`, puis sur `Web Cloud Databases`{.action}. Sélectionnez le nom de votre serveur de bases de données.

Dirigez-vous dans l'onglet `Utilisateurs et droits` et cliquez sur `Ajouter un utilisateur`{.action}

![web-cloud-databases](images/web-cloud-databases-user01.png){.thumbnail}

Renseignez un « nom d'utilisateur  » et un « mot de passe » puis cliquez sur `Valider`{.action}.

### Gerer les droits des utilisateurs

Pour autoriser un utilisateur à effectuer des actions sur une base de données, il est nécessaire de lui attribuer des droits.

Pour gérer les droits de chaque utilisateur, rendez-vous dans votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}. Cliquez sur  l'onglet `Web Cloud`, puis sur `Web Cloud Databases`{.action}. Sélectionnez le nom de votre serveur de bases de données. Cliquez sur l'onglet `Utilisateurs et droits`.

Cliquez sur le bouton `...`{.action} à droite de l'utilisateur concerné puis sur `Gérer les droits`{.action}.

![web-cloud-databases](images/web-cloud-databases-rights01.png){.thumbnail}

Vous retrouverez dans la colonne de gauche **« base de données »**, la liste des bases de données présentes sur votre serveur de bases de données.

Voici la description des 3 types de droits proposés :

- `Administrateur`: autorisation des requêtes de type **Select / Insert / Update / Delete / Create / Alter / Drop**.
- `Lecture / Ecriture`: autorisation des requêtes de type **Select / Insert / Update / Delete**.
- `Lecture`: autorisation des requêtes de type **Select**.
- `Aucun`: aucun droit sur la base.

> [!primary]
> 
> La segmentation des droits mentionnés ci-dessus est propre à OVHcloud. Ainsi un utilisateur ayant les droits `Administrateur` pourra faire du **DLL** (Data Definition Language) et du **DML** (Data Manipulation Language) alors qu'un utilisateur ayant les droits `Lecture/Ecriture` ne fera uniquement que du **DML** (Data Manipulation Language)

![web-cloud-databases](images/web-cloud-databases-rights02.png){.thumbnail}

#### Supprimer une base de données

> [!warning]
>
> Pour supprimer une base de données sur un serveur de bases de données, il n'y a pas de
> vérification sur le contenu de la base. Celle-ci sera donc supprimée même si
> des données y sont encore enregistrées, il est donc recommandé de réaliser
> une sauvegarde et de la télécharger de votre côté avant toute suppression.
> 

Rendez-vous dans votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}. Cliquez sur  l'onglet `Web Cloud`, puis sur `Web Cloud Databases`{.action}. Sélectionnez le nom de votre serveur de bases de données.

Pour supprimer une base de données sur votre serveur de bases de données, dirigez-vous dans l'onglet `Bases de données` puis cliquez sur le bouton `...`{.action} à droite de la base de données concernée et enfin cliquez sur `Supprimer la base`{.action} .

![web-cloud-databases](images/web-cloud-databases-deldb01.png){.thumbnail}

## Aller plus loin

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr/).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](https://www.ovhcloud.com/fr-ca/support-levels/).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
