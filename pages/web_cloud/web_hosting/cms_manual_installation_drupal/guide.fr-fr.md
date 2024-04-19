---
title: "Tutoriel - Installer manuellement Drupal"
excerpt: "Découvrez comment installer manuellement votre CMS Drupal"
updated: 2023-03-17
---

## Objectif

Vous trouverez ici tous les éléments pour installer manuellement le CMS (Content Management System) Drupal en quelques étapes.

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition ce tutoriel afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](/links/partner) ou [l'éditeur du CMS Drupal](https://www.drupal.org/support){.external} si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Retrouvez plus d'informations dans la section [« Aller plus loin »](#go-further) de ce tutoriel.
>

> [!success]
>
> Pour installer Drupal **automatiquement** depuis votre [espace client OVHcloud](/links/manager), consultez notre documentation sur l'[installation d'un module « en un clic »](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>
> Pour installer **manuellement un autre CMS** (WordPress, Joomla!, PrestaShop), consultez notre documentation sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation).
>

**Découvrez comment installer manuellement votre CMS Drupal**

## Prérequis

- Disposer d'une offre d'[hébergement web](/links/web/hosting) qui contient au moins une base de données.
- Disposer d'un [nom de domaine](/links/web/domains)
- Être connecté à l'[espace client OVHcloud](/links/manager){.external}

## En pratique

### Etape 1 - préparer l'installation <a name="step1"></a>

Pour installer le CMS **Drupal** sur votre offre d'[hébergement web](/links/web/hosting), quelques préparatifs sont nécessaires.

Suivez l'**ensemble des étapes** décrites dans notre tutoriel sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) avant de poursuivre à l'étape 2 ci-dessous.

### Etape 2 - finaliser l'installation manuelle <a name="step2"></a>

> [!success]
>
> Avant de continuer l'installation, videz le cache de votre navigateur Internet, afin d'éviter toute erreur.
>

#### 2.1 - Se rendre sur votre site Drupal via votre navigateur

Saisissez votre nom de domaine dans la barre de recherche de votre navigateur Internet.

Si les fichiers sources de Drupal ont été placés correctement dans votre dossier racine, la page de sélection de la langue pour Drupal apparaît :

![Drupal installation step 1](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/drupal/install-language-1.png){.thumbnail}

Sélectionnez la langue du site puis cliquez sur `Enregistrer et continuer`{.action}.

#### 2.2 - Choisir le type d'installation

Drupal propose plusieurs niveaux d'installation :

- une version standard (recommandée), 
- une version minimale
- une version de présentation 

![Drupal installation step 2](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/drupal/install-profil-2.png){.thumbnail}

Nous vous recommandons d'effectuer une installation **Standard**. Cliquez ensuite sur `Enregistrer et continuer`{.action}.

#### 2.3 - Lier votre Drupal et votre base de données

Renseignez les informations demandées concernant la base de données :

![Drupal installation step 3](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/drupal/install-db-config-3.png){.thumbnail}

Munissez-vous des identifiants de votre base de données (au besoin, consultez **l'étape 1.4** du guide sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation)).

- *Type de base de données* : sélectionnez, parmi les choix proposés, le type de votre base de données.

- *Nom de la base de données* : ce nom a été défini lors de la création de la base de données dans l'[espace client OVHcloud](/links/manager).

- *Utilisateur de la base de données* : il est identique au nom de la base de données si vous utilisez une base de données incluse avec votre hébergement web. Pour les bases de données créées sur un service Web Cloud Databases, référez-vous aux informations indiquées dans **l'étape 1.4** du tutoriel sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation).

- *Mot de passe de la base de données* : vous l'avez vous-même défini lors de la création de votre base de données. Il est possible que vous l'ayez modifié entre temps.

Cliquez sur `Options avancées`{.action} pour découvrir le reste du menu.

- *Adresse de la base de données/Host* : renseignez le nom du serveur de votre base de données, présent dans l'e-mail d'installation ou dans votre espace client OVHcloud. 

> [!primary]
> 
> - Le nom du serveur d'une base de données incluse avec votre offre d'hébergement Web a généralement cette forme : `NameOfYourDatabase.mysql.db`. 
>
> - Le nom du serveur d'une base de données Web Cloud Databases commence par votre identifiant client OVHcloud et a la forme suivante : `aa00000-XXX.eu.clouddb.ovh.net`, **«aa00000»** correspond à votre identifiant OVHcloud sans le **« -ovh »** et les **« X »** sont à remplacer par le reste de la référence de votre service Web Cloud Databases.
>

- *Numéro de port* : si vous utilisez une base de données incluse avec votre hébergement OVHcloud, laissez par défaut **3306**. Si vous utilisez un service *Web Cloud Databases*, référez-vous à **l'étape 1.4** du tutoriel sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) pour récupérer le bon numéro de port.

- *Préfixe du nom des tables* : si l'installation se fait avec une toute nouvelle base de données, renseignez le « préfixe » de votre choix. Si vous utilisez une base de données déjà utilisée par un autre site, référez-vous à **l'étape 1.4** du tutoriel sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) pour ne pas renseigner un « préfixe » de table déjà utilisé dans votre base de données.

Cliquez sur `Enregistrer et continuer`{.action}.

Si tout a été réalisé correctement, l'installation de Drupal se lance :

![Drupal installation step 4](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/drupal/install-4.png){.thumbnail}

#### 2.4 - Configurer les informations du site et l'accès « Administrateur »

Une fois l'étape précédente terminée, la page suivante s'affiche :

![Drupal installation step 5-1](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/drupal/install-configure-site-5-1.png){.thumbnail}

Renseignez les éléments demandés :

- *Nom du site* : saisissez le nom de votre futur site Drupal.

- *Adresse e-mail du site* : saisissez une adresse e-mail valide qui sera utilisée par votre site Drupal.

- *Nom d'utilisateur* : définissez un nom d'utilisateur pour vous connecter à votre espace d'administration Drupal (Back Office).

- *Mot de passe* et *Confirmer le mot de passe* : définissez le mot de passe qui sera associé à votre nom d'utilisateur pour accéder à votre *Back Office* Drupal.

Poursuivez ensuite vers le bas de la page :

![Drupal installation step 5-1](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/drupal/install-configure-site-5-2.png){.thumbnail}

- *Adresse e-mail* : saisissez votre adresse e-mail. Idéalement, renseignez la même adresse que celle choisie plus haut dans le formulaire *Adresse e-mail du site*.

- *Région par défaut* : choisissez le pays où votre site va être le plus consulté.

- *Fuseau horaire par défaut* : sélectionnez le fuseau horaire par défaut pour votre site web.

Cliquez sur `Enregistrer et continuer`{.action}.

Si tout s'est bien passé, la page suivante apparaît :

![Drupal installation step 6](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/drupal/install-ending-6.png){.thumbnail}

> [!success]
>
> L'installation de Drupal est terminée, vous pouvez maintenant démarrer la création du contenu de votre site Drupal !
>

## Aller plus loin <a name="go-further"></a>

[Site officiel Drupal](https://www.drupal.org/){.external}

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.