---
title: "Consulter les statistiques et les logs de mon site hébergé sur une offre mutualisée"
excerpt: "Découvrez comment consulter les statistiques et logs de votre site internet"
updated: 2024-02-08
---

## Objectif

L'accès aux logs et aux statistiques de votre site est compris dans votre offre d'hébergement web, accessible via votre espace client OVHcloud.

**Découvrez comment consulter les statistiques et logs de votre site internet.**

## Prérequis

- Disposer d'une offre [d'hébergement web](https://www.ovhcloud.com/fr/web-hosting/){.external} compatible.
- Être connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external}.

## En pratique

Rendez-vous dans votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external}. Cliquez sur  l'onglet `Web Cloud`{.action}, puis sur `Hébergements`{.action}.

Dans le menu de gauche, sélectionnez l'hébergement concerné, puis cliquez sur l'onglet `Statistiques et logs`{.action}.

L'écran qui s’affiche est composé de 4 sections :

- **statistiques de visite** : présente de nombreuses statistiques concernant votre hébergement
- **logs du site web** : affiche les logs bruts de votre hébergement
- **statistiques de l'infrastructure** : présente des statistiques graphiques (requêtes HTTP et SQL, commandes FTP, etc.)
- **administration des utilisateurs** : affiche les utilisateurs autorisés à accéder aux statistiques

![hosting](images/tab.png){.thumbnail}

### Administration des utilisateurs

La création d'un utilisateur permettra à une personne d'accéder aux statistiques de votre hébergement sans avoir accès à votre espace client OVHcloud.

Cliquez sur le bouton `Créer un nouvel utilisateur`{.action} dans la section `Administration des utilisateurs` et suivez les instructions comme ci-dessous.

![hosting](images/create-a-new-user.png){.thumbnail}

Pour accéder aux statistiques de votre site web avec un utilisateur que vous avez créé, vous devez saisir l'adresse suivante en remplaçant `000` par le numéro du cluster de votre hébergement et `mydomain.ovh` par le nom de domaine de votre site web (sans les « www »):

```bash
https://logs.cluster000.hosting.ovh.net/mydomain.ovh/
```

Depuis la section `Statistiques et logs`{.action}, cliquez sur `Voir les statistiques`{.action}.<br>
Depuis l'onglet de votre navigateur qui affiche la fenêtre de statistiques, récupérez le lien qui servira à vous connecter avec l'un des utilisateurs créés.

![hosting](images/view-statistics.png){.thumbnail}

> [!warning]
>
> Si vous avez activé les logs séparés sur une [entrée multisite](/pages/web_cloud/web_hosting/multisites_configure_multisite#etape-2-ajouter-un-domaine-ou-un-sous-domaine), les utilisateurs créés ici ne peuvent pas accéder aux statistiques de cette entrée multisite.
>

### Statistiques des visites

Pour vous aider à mieux suivre et piloter le trafic de vos sites web, vous disposez d'un outil de statistiques de fréquentation et de mesure d’audience de vos sites internet hébergés sur votre hébergement mutualisé, **OVHcloud Web Statistics**.

![hosting](images/ows-presentation.gif){.thumbnail}

Le tableau de bord d'OVHcloud Web Statistics présente 7 sections :

- Dashboard : visualisation du trafic sur les sites de votre hébergement.
- Browsers : classement des navigateurs internet les plus utilisés pour visualiser vos sites.
- Geolocalization :  proportion de visiteurs en fonction de leur localisation.
- Requests : classement des pages les plus consultées sur vos sites.
- Robots : visualisation des robots qui passent sur vos sites.
- Status : statistiques des échecs et réussites rencontrés en fonction des codes HTTP retournés.
- FAQ : rubrique dédiée aux questions les plus fréquentes.

Le champ `Period selection` en haut à droite vous permet de sélectionner une période précise.

### Logs

Vous avez la possibilité de visualiser les logs bruts de votre site avec un différé d'environ 5 minutes.

![hosting](images/osl-statistics-board.png){.thumbnail}

Différents type de logs sont à votre disposition :

- Logs Web : retrouvez ici les différents logs de consultation de votre site, ainsi que les différentes actions réalisées à partir de votre site. Cela vous permet par exemple de repérer des tentatives d'actions malveillantes.
- Logs FTP : les différentes connexions FTP seront enregistrées et conservées dans ces logs.
- Logs erreur : les différentes erreurs générées par votre site.
- Logs CGI : les différents appels aux scripts cgi.bin qui ont été réalisés.
- Logs out : les statistiques de votre hébergement sur les différents appels externes réalisés.
- Logs SSH : ces logs indiquent les différentes connexions réalisées avec le protocole SSH.
- Logs CRON : le résultat de l'exécution de vos tâches planifiées ([Les tâches automatisées (CRON) sur votre hébergement](/pages/web_cloud/web_hosting/cron_tasks)).

### Activités de l’hébergement

Retrouvez dans cette section l'activité de l'infrastructure de votre hébergement, afin de visualiser la consommation des ressources mises à votre disposition.

Cliquez sur l'onglet `Informations générales`{.action}, puis descendez en bas de la page.

![hosting](images/infrastructure-statistics-graph.png){.thumbnail}

Il est possible d'afficher différent types de graphiques, depuis le menu déroulant en haut à gauche :

- Connexions sortantes : requêtes émises de votre site vers un site extérieur.
- Utilisation CPU : niveau de consommation du processeur sur votre instance d'hébergement.
- Dépassement du plafond des ressources: indique les moments ou votre hébergement dépasse son quota de ressources.
- Requêtes SQL : quantité de requêtes vers les bases de données de votre hébergement.
- Temps de réponse SQL : temps de réponse des requêtes émises vers les bases de données de votre hébergement.

## Aller plus loin

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr/directory/).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](https://www.ovhcloud.com/fr/support-levels/).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.