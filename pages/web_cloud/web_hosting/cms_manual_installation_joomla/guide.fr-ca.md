---
title: "Tutoriel - Installer manuellement Joomla!"
excerpt: "Découvrez comment installer manuellement votre CMS Joomla!"
updated: 2023-03-17
---

## Objectif

Vous trouverez ici tous les éléments pour installer manuellement le CMS (Content Management System) Joomla! en quelques étapes.

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition ce tutoriel afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](/links/partner) ou [l'éditeur du CMS Joomla!](https://www.joomla.org/){.external} si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Retrouvez plus d'informations dans la section [« Aller plus loin »](#go-further) de ce tutoriel.
>

> [!success]
>
> Pour installer Joomla! **automatiquement** depuis votre [espace client OVHcloud](/links/manager), consultez notre documentation sur l'[installation d'un module « en un clic »](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>
> Pour installer **manuellement un autre CMS** (WordPress, Drupal, PrestaShop), consultez notre documentation sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation).
>

**Découvrez comment installer manuellement votre CMS Joomla!**

## Prérequis

- Disposer d'une offre d'[hébergement web](/links/web/hosting) qui contient au moins une base de données.
- Disposer d'un [nom de domaine](/links/web/domains)
- Être connecté à l'[espace client OVHcloud](/links/manager){.external}

## En pratique

### Etape 1 - préparer l'installation <a name="step1"></a>

Pour installer le CMS **Joomla!** sur votre offre d'[hébergement web](/links/web/hosting), quelques préparatifs sont nécessaires.

Suivez l'**ensemble des étapes** décrites dans notre tutoriel sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) avant de poursuivre à l'étape 2 ci-dessous.

### Etape 2 - finaliser l'installation manuelle <a name="step2"></a>

> [!success]
>
> Avant de continuer l'installation, videz le cache de votre navigateur Internet, afin d'éviter toute erreur.
>

#### 2.1 - Se rendre sur votre site Joomla! via votre navigateur

Saisissez votre nom de domaine dans la barre de recherche de votre navigateur Internet.

Si les fichiers sources de Joomla! ont été placés correctement dans votre dossier racine, la page de sélection de la langue pour Joomla! apparaît :

![Joomla installation step 1](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/joomla/install-select-language-1.png){.thumbnail}

Sélectionnez la langue, saisissez le nom de votre site web puis cliquez sur `Configuration des données de connexion`{.action}.

#### 2.2 - Configurer les données de connexion à votre Joomla!

Définissez les accès à votre espace d'administration (*Back Office*) Joomla! :

![Joomla installation step 2](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/joomla/install-define-admin-2.png){.thumbnail}

> [!primary]
>
> Le terme « Super Utilisateur » désigne la personne qui administre le CMS.

- *Entrer le nom réel de votre Super Utilisateur* : saisissez votre nom réel.
- *Définir le nom d'utilisateur de votre compte Super Utilisateur* : choisissez un nom d'utilisateur qui vous permettra de vous connecter à votre espace d'administration Joomla!.
- *Définir le mot de passe pour votre compte Super Utilisateur* : choisissez un mot de passe avec un minimum de **12 caractères**.
- *Entrer l'adresse e-mail du Super Utilisateur du site web* : saisissez une adresse e-mail valide. Celle-ci servira à recevoir les notifications envoyées par Joomla!.

Vérifiez les éléments renseignés puis cliquez sur `Configuration de la connexion à la base de données`{.action}.

#### 2.3 - Lier votre base de données avec votre Joomla!

Renseignez les informations demandées concernant la base de données :

![Joomla installation step 3](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/joomla/install-db-connect-3.png){.thumbnail}

Référez-vous aux informations indiquées dans **l'étape 1.4** du tutoriel sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) pour compléter les champs suivants :

- *Selectionner le type de base de données* : sélectionnez le type de votre base de données parmi les types disponibles pour Joomla!. Si vous utilisez une base de données mutualisée OVHcloud, vous pouvez laisser par défaut la valeur **MySQLi**.

- *Saisissez le nom de l'hôte, généralement "localhost" ou un nom fourni par votre hôte* : renseignez le nom du serveur de votre base de données, présent dans l'e-mail d'installation ou dans votre espace client OVHcloud.

> [!primary]
> 
> - Le nom du serveur d'une base de données incluse avec votre offre d'hébergement Web a généralement cette forme : `NameOfYourDatabase.mysql.db`. 
>
> - Le nom du serveur d'une base de données Web Cloud Databases commence par votre identifiant client OVHcloud et a la forme suivante : `aa00000-XXX.eu.clouddb.ovh.net`, **«aa00000»** correspond à votre identifiant OVHcloud sans le **« -ovh »** et les **« X »** sont à remplacer par le reste de la référence de votre service Web Cloud Databases.
>

- *Saisissez soit un nom d'utilisateur que vous avez créé, soit un nom d'utilisateur fourni par votre hébergeur* : il est identique au nom de la base de données si vous utilisez une base de données incluse avec votre hébergement web.
Pour les bases de données créées sur un Web Cloud Databases, référez-vous aux informations indiquées dans **l'étape 1.4** du guide sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation).

- *Saisissez soit un mot de passe que vous avez créé, soit un mot de passe fourni par votre hébergeur* : vous l'avez vous-même défini lors de la création de votre base de données. Il est également possible que vous l'ayez modifié entre temps, nous vous invitons à le vérifier.

- *Entrer le nom de la base de données* : ce nom a été défini lors de la création de la base de données dans l'[espace client OVHcloud](/links/manager). Il est identique au nom d'utilisateur de la base de données si vous utilisez une base de données incluse avec votre hébergement web.

- *Saisissez un préfixe de table ou utilisez celui qui est généré de manière aléatoire* : si l'installation se fait avec une toute nouvelle base de données, renseignez le « préfixe » de votre choix. Si vous utilisez une base de données déjà utilisée par un autre site, référez-vous à **l'étape 1.4** du guide sur l'[installation manuelle d'un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) pour ne pas renseigner un « préfixe » de table déjà utilisé dans votre base de données.

- **Chiffrement de la connexion** : laissez la valeur **Par défaut**.

Cliquez sur `Installer Joomla`{.action}.

Le message suivant apparaît :

![Joomla installation step 3-1](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/joomla/install-db-connect-3-1.png){.thumbnail}

Du fait que vous utilisez une base de données présente en dehors d'un hébergement local, vous devrez supprimer le *token* généré aléatoirement lors de l'installation de votre Joomla!.

Ce fichier à supprimer se trouve dans votre [espace de stockage FTP](/pages/web_cloud/web_hosting/ftp_connection).

Une fois connecté, rendez-vous dans le dossier **installation** de votre Joomla! puis supprimez uniquement le *token* indiqué par le message d'alerte. Il est présent sous la forme d'un fichier **.txt**.

Retournez ensuite dans votre navigateur internet puis cliquez de nouveau sur `Installer Joomla`{.action}.

#### 2.4 - Terminer l'installation

Une fois l'installation terminée, la page suivante apparaît :

![Joomla installation step 4](https://raw.githubusercontent.com/ovh/docs/develop/templates/external-elements/cms/joomla/install-ending-4.png){.thumbnail}

L'installation est terminée mais vous pouvez ajouter des langues supplémentaires à votre CMS si besoin.

>[!success]
>
> Félicitations, votre Joomla! est prêt à être utilisé et administré.
> 

## Aller plus loin <a name="go-further"></a>

[Site officiel Joomla!](https://joomla.org){.external}

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.