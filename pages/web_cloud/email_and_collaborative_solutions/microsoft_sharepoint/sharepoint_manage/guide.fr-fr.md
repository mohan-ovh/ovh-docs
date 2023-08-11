---
title: 'Activer et gérer votre SharePoint OVHcloud'
excerpt: 'Découvrez comment commander et configurer une plateforme SharePoint.'
updated: 2023-06-19
---

**Dernière mise à jour le 11/08/2020**

## Objectif

Les offres SharePoint permettent de bénéficier d'un espace de stockage de 1 To partagé avec les autres comptes de votre plateforme Sharepoint, pour votre travail collaboratif.

Vous disposez également de 100 Go d'espace de stockage personnel, pour chacun des comptes de votre plateforme sharepoint.

**Découvrez comment commander et configurer une plateforme SharePoint.**

## Prérequis

- Être connecté à [l'espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).
- Avoir souscrit à une plateforme [Hosted Exchange](https://www.ovhcloud.com/fr/emails/hosted-exchange/){.external} pour la commande d'une plateforme SharePoint associée.

## En pratique

### Étape 1 : commander une plateforme SharePoint

Connectez-vous à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) et dirigez-vous dans la section `Webcloud`{.action} pour initier la commande de votre plateforme SharePoint .

Il y a deux types de plateformes qui vous sont proposées :

| SharePoint associé                                                                                                                      	| SharePoint standalone                                                                                                                                                                       	|
|-----------------------------------------------------------------------------------------------------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| ![sharepoint](images/order-manage-sharepoint-02.png){.thumbnail}                                                                        	| ![sharepoint](images/order-manage-sharepoint-03.png){.thumbnail}                                                                                                                            	|
| Si vous possédez une plateforme Hosted Exchange sur votre espace client, vous pouvez associer ses comptes à une plateforme SharePoint. Cochez le ou les comptes auxquels vous souhaitez associer une licence SharePoint 	| Si vous n'avez pas de plateforme Exchange Hosted OVHcloud ou que vous souhaitez une plateforme SharePoint indépendante, choisissez la commande d'une plateforme SharePoint Standalone. <br>Définissez le nombre de licences que vous souhaitez en fonction du nombre d'utilisateurs.	|

Une fois votre choix effectué, Cliquez sur `Commander votre service`{.action} afin de finaliser votre commande.

### Étape 2: activer la plateforme SharePoint

Une fois votre commande validée et réglée, vous recevrez sur l'adresse e-mail de référence de votre espace client un e-mail de confirmation indiquant que la plateforme est prête à la configuration.

Pour consulter cet e-mail, connectez-vous à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) puis cliquez sur votre profil en haut à droite et enfin cliquez sur vos initiales. Dirigez-vous sur l'onglet `Emails reçus`{.action} et recherchez l'e-mail ayant pour objet :

> **[xx-11111-ovh] Configurer votre service Microsoft SharePoint !**

Pour débuter cette configuration, dirigez-vous dans la section `Web Cloud` de votre espace client. Cliquez sur `Microsoft`{.action} puis sur `Sharepoint`{.action} et sélectionnez la plateforme SharePoint concernée.

Définissez le nom de votre plateforme dans la case « URL du SharePoint » puis cliquez sur `Valider l'URL`{.action} 

> [!warning]
>
> Une fois validé, le nom de la plateforme ne peut pas être modifié.

### Étape 3: configuration de la plateforme SharePoint

Connectez-vous à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) et dirigez-vous dans la section `Web Cloud`. Cliquez sur `Microsoft`{.action} puis sur `Sharepoint`{.action} et sélectionnez la plateforme SharePoint concernée.

#### **SharePoint standalone**

Cette plateforme est indépendante, il faut d'abord y associer un nom de domaine avant de configurer vos utilisateurs.

##### ***Ajouter un domaine***

Dirigez-vous dans l'onglet `Domaines` et cliquez sur `Ajouter un domaine`{.action}. Sélectionnez un domaine que vous possédez dans votre espace client ou tapez un nom de domaine externe que vous gérez. 

- Si vous choisissez un nom de domaine présent dans votre espace client, celui-ci sera automatiquement validé, il ne vous restera plus qu'à configurer vos utilisateurs.
 
- Si vous choisissez un nom de domaine externe, il est nécessaire d'ajouter un enregistrement CNAME dans la zone DNS du nom de domaine pour le valider sur la plateforme SharePoint. L'enregistrement CNAME à renseigner est accessible en cliquant sur l'icône d'information `i` à côté de la mention « Validation de domaine en cours », comme ci-dessous.


![sharepoint](images/order-manage-sharepoint-05.png){.thumbnail}

##### ***Configurer un utilisateur***

Dirigez-vous dans l'onglet `Utilisateur`, cliquez sur `...`{.action} à droite du compte puis cliquez sur `Modifier le compte`{.action}

![sharepoint](images/order-manage-sharepoint-06.png){.thumbnail} 

Complétez la fenêtre qui apparaît avec les informations de l'utilisateur et cliquez sur `valider`{.action}

Pour obtenir les droits administrateur sur la plateforme SharePoint, cliquez à nouveau sur `...`{.action} à droite du compte puis cliquez sur `Activer les droits administrateur`{.action}

#### **SharePoint associé**

Comme son nom l'indique, cette plateforme est associée à la plateforme Exchange que vous avez choisie lors de votre commande, il n'y a donc pas de nom de domaine à associer.

##### ***Configurer un utilisateur***

Dirigez-vous dans l'onglet `Utilisateurs` de votre plateforme pour y visualiser l'ensemble des comptes Exchange qui peuvent bénéficier d'une licence SharePoint.

![sharepoint](images/order-manage-sharepoint-07.png){.thumbnail} 

Une colonne `Compte activé` indique si le compte de la plateforme Exchange bénéficie d'une licence sharePoint. 

> [!primary]
>
> Si vous souhaitez activer une licence sur un compte qui n'en possède pas, cliquez sur `...`{.action} à droite du compte puis cliquez sur `Activer SharePoint`{.action}.

Par défaut, un compte bénéficiant d'une licence n'a pas les droits administrateur. Pour les activer, Cliquez sur `...`{.action} à droite du compte puis sur `Activer les droits administrateur`{.action}.

![sharepoint](images/order-manage-sharepoint-08.png){.thumbnail} 

#### **Rétablir les droits administrateur**

Sur les deux types de plateformes SharePoint, vous retrouvez le bouton `Rétablir droits administrateur`{.action} dans l'onglet `Utilisateur`. Il permet de remettre en place les droits administrateur de la plateforme en cas de mauvaise manipulation depuis l'interface SharePoint.

![sharepoint](images/order-manage-sharepoint-09.png){.thumbnail}

#### **Editer les fichiers Office 365 en ligne**

Il est possible d'éditer directement en ligne vos fichiers Office 365 tel qu'un fichier *.docx* ou *.xls*.

Pour cela vous devez posséder une licence Office 365 valide et le confirmer dans votre espace client OVHcloud.

Dirigez-vous dans l'onglet `Utilisateurs` de votre plateforme puis cliquez sur `...`{.action} à droite du compte et enfin sur `Ajouter une licence Office`{.action}

![sharepoint](images/order-manage-sharepoint-10.png){.thumbnail}

Cliquez sur `valider`{.action} après avoir confirmé que vous possédez bien une licence Office 365.

![sharepoint](images/order-manage-sharepoint-11.png){.thumbnail}

Il vous sera ensuite possible d'éditer vos fichiers Office 365 directement depuis l'interface web de votre sharepoint.

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.