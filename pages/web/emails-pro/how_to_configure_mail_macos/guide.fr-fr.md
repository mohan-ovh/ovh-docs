---
title: Configurer son compte E-mail Pro sur Mail de macOS
slug: configurer-email-pro-mail-macos
excerpt: Apprenez à configurer votre compte E-mail Pro sur Mail de macOS El Capitan, Sierra et High Sierra
section: Configuration client de messagerie
order: 4
---

**Dernière mise à jour le 17/05/2018**

## Objectif

Les comptes E-mail Pro peuvent être configurés sur un logiciel de messagerie compatible. Cela vous permet d'utiliser votre adresse e-mail depuis l'application de votre choix.

**Apprenez à configurer votre compte E-mail Pro sur Mail de macOS El Capitan, Sierra et High Sierra.**

> [!warning]
>
> OVH met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un prestataire spécialisé et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.
> 

## Prérequis

- Disposer d'une offre [E-mail Pro](https://www.ovh.com/fr/emails/email-pro/){.external}.
- Disposer de l'application Mail installée sur votre appareil.
- Disposer des identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

> [!primary]
>
> Cette documentation est applicable aux versions suivantes de macOS : El Capitan, Sierra, High Sierra.
>

## En pratique

Cet ajout peut s'effectuer de deux manières différentes :

- **en quelques clics depuis notre outil Apple Devices** : rendez-vous sur le lien [https://autodiscover.mail.ovh.net/AppleDevices/](https://autodiscover.mail.ovh.net/AppleDevices/){.external} et suivez les différentes étapes de configuration ;

- **en suivant l'assistant de configuration de l'application Mail** : lancez l'application Mail sur votre appareil.

À partir de ce point, cette documentation abordera uniquement la configuration depuis l'application Mail.

### Étape 1 : ajouter le compte

Une fois l'application Mail lancée sur votre appareil, l'ajout d'un compte peut s'initier de deux manières différentes.

- **Lors du premier démarrage de l'application** : une fenêtre vous invite à choisir un fournisseur de compte Mail. Sélectionnez `Autre compte Mail`{.action}, puis continuez.

- **Si un compte a déjà été paramétré** : cliquez sur `Mail`{.action} en haut de votre écran, puis sur `Ajouter un compte`{.action}. Sélectionnez `Autre compte Mail`{.action}, puis continuez.

![emailpro](images/configuration-mail-sierra-step1.png){.thumbnail}

Renseignez à présent les informations de votre compte :

|Information|Description|  
|---|---|  
|Nom|Renseignez le nom qui s'affichera en tant qu'expéditeur lorsque des e-mails seront envoyés avec cette adresse.| 
|Adresse e-mail|Renseignez l'adresse e-mail complète.| 
|Mot de passe|Renseignez le mot de passe de l'adresse e-mail.|  

Cliquez à présent sur le bouton `Se connecter`{.action}. Un message vous invitera à poursuivre, puis à renseigner plus d'informations :

|Information|Description|  
|---|---|  
|Type de compte|Laissez IMAP déjà sélectionné dans le menu déroulant.| 
|Serveur de réception|Renseignez le serveur « pro1.mail.ovh.net ».| 
|Serveur d'envoi|Renseignez le serveur « pro1.mail.ovh.net ».|  

Cliquez de nouveau sur le bouton `Se connecter`{.action}. Si les informations renseignées sont correctes, la connexion au compte réussira.

![emailpro](images/configuration-mail-sierra-step2.png){.thumbnail}

Lors du choix des applications, assurez-vous de bien laisser `Mail`{.action} coché afin que l'application puisse utiliser ce compte, puis cliquez sur `Terminé`{.action}.

Vous pouvez effectuer un test d'envoi pour vérifier que le compte est correctement paramétré.

Si vous êtes amené à renseigner manuellement des paramètres dans les préférences du compte, vous trouverez ci-dessous les paramètres techniques à utiliser avec notre offre E-mail Pro :

|Type de serveur|Nom du serveur|SSL|Port|
|---|---|---|---|
|Entrant|pro1.mail.ovh.net|Oui|993|
|Sortant|pro1.mail.ovh.net|Oui|587|

### Étape 2 : utiliser l'adresse e-mail

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages.

OVH propose une application web disposant de [fonctions collaboratives](https://www.ovh.com/fr/emails/){.external} accessible sur l’adresse [https://pro1.mail.ovh.net](https://pro1.mail.ovh.net){.external}. Vous pouvez y accéder grâce aux identifiants relatifs à votre adresse e-mail. 

## Aller plus loin

[Configurer son adresse e-mail comprise dans l’offre MX Plan ou dans une offre d’hébergement web sur Mail de macOS](https://docs.ovh.com/fr/emails/guide-configuration-mail-de-mac-el-capitan/){.external}.

[Configurer son compte Exchange sur Mail de macOS](https://docs.ovh.com/fr/microsoft-collaborative-solutions/exchange-configuration-automatique-sous-mail-mac/){.external}.

Échangez avec notre communauté d'utilisateurs sur [https://community.ovh.com](https://community.ovh.com){.external}.