---
title: 'DMZ &#58; couplage OverTheBox avec un autre routeur'
keywords: 'DMZ, Routeur'
description: 'DMZ &#58; couplage OverTheBox avec un autre routeur'
updated: 2021-11-26
---

## Objectif

Si vous souhaitez conserver un routeur, tel qu'un pfSense par exemple, pour gérer votre  LAN, vos  VPNs, etc, vous pouvez configurer OverTheBox en mode transparent en créant une DMZ.

**Découvrez comment coupler OverTheBox avec un autre routeur en créant une DMZ.**

## Prérequis

L'intégralité de votre réseau **LAN** sera gérée par votre routeur personnel. Cela comprend le **serveur DHCP**. Veuillez donc d'abord désactiver le **serveur DHCP** de votre **OverTheBox** comme indiqué sur le guide suivant :

[Désactiver le serveur DHCP d’OverTheBox](/pages/web_cloud/internet/overthebox/middle_desactiver_le_serveur_dhcp_doverthebox)

## En pratique

Rendez-vous sur [http://overthebox.ovh (192.168.100.1)](http://overthebox.ovh){.external} depuis votre ordinateur connecté au modem principal.

- Cliquez sur **"Network"**, puis sur **"Firewall"** et enfin sur **"Port Forwards"**.
- Configurez votre redirection :
    - **Name** : DMZ
    - **Protocol** : TCP + UDP
    - **External zone** : indiquez **TUN**
    - **External port** : laissez vide
    - **Internal zone** : indiquez **LAN**
    - **Internal Ip** : Indiquer l'adresse IP de votre routeur
    - **Internal port** : laissez vide
- Cliquez d'abord sur **"Add"** puis sur **"Save & Apply"**.

![overthebox](images/4433.png){.thumbnail}

## Aller plus loin

N'hésitez pas à échanger avec notre communauté d'utilisateurs sur vos produits Télécom sur notre site [OVHcloud Community](https://community.ovh.com/c/telecom)
