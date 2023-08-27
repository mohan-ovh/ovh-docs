---
title: "Utilisation d'Active Directory comme source d'authentification (Federation)"
routes:
    canonical: '/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/federation'
excerpt: "Découvrez comment utiliser votre serveur Active Directory comme source d'authentification pour vos utilisateurs vSphere"
updated: 2022-02-10
---

## Objectif

Ce guide a pour objectif d'expliquer les détails de la mise en place d'un serveur Active Directory comme source d'authentification sur l'offre Managed Bare Metal OVHcloud.

**Découvrez comment utiliser votre serveur Active Directory comme source d'authentification pour vos utilisateurs vSphere.**

## Prérequis

- Avoir souscrit une offre [Managed Bare Metal](https://www.ovhcloud.com/fr/managed-bare-metal/){.external}.
- Disposer d'un serveur Active Directory acessible depuis une adresse IP publique et possédant un [certificat SSL valide pour le service LDAPS](https://docs.microsoft.com/fr-fr/troubleshoot/windows-server/identity/enable-ldap-over-ssl-3rd-certification-authority){.external}.
- Disposer d'un accès utilisateur au domaine Active Directory associé, avec au minimum un accès en lecture seule (pour la connexion LDAPS).
- Avoir accès à l’interface de gestion vSphere de votre Managed Bare Metal.

## En pratique

### Récupérer les informations nécessaires

La connexion du vCenter au serveur Active Directory est réalisée via le protocole LDAPS fourni par le serveur Active Directory.

Afin de préparer la mise en place de la configuration, vous devez récupèrer les informations suivantes :

- Nom de domaine Active Directory (FQDN).
- Alias de domaine Active Directory (Nom NetBIOS).
- Adresse IP publique du serveur Active Directory.
- Nom d'hôte du serveur LDAPS Active Directory. Nom utilisé dans le certificat SSL du service LDAPS, ce nom doit résoudre sur l'adresse IP publique du serveur Active Directory.
- Port du service LDAPS (par défaut 636).
- Base DN (Base Distinguished Name) pour les utilisateurs. Il s'agit du DN à partir duquel seront recherchés les utilisateurs. Par exemple, dc=example,dc=com
- Base DN (Base Distinguished Name) pour les groupes. Il s'agit du DN à partir duquel seront recherchés les groupes. Par exemple, dc=example,dc=com
- Identifiant et mot de passe d'un utilisateur du domaine qui sera utilisé pour la connection au serveur LDAPS. Il doit être au minimum en lecture seule sur la section du serveur Active Directory pour les deux « Base DN » choisis précédemment. Identifiant pre-Windows 2000 sous la forme UPN (user@example.com).

Pour plus d'informations, vous pouvez vous réfèrer à la [documentation VMware à ce sujet](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.psc.doc/GUID-98B36135-CDC1-435C-8F27-5E0D0187FF7E.html){.external}.

En complément des informations précédentes, vous devez récupèrer l'empreinte du certificat SSL (SHA1 Fingerprint) du serveur LDAPS Active Directory.

Vous pouvez récupérer cette information par la méthode de votre choix.

- Via cette commande PowerShell sur le serveur Active Directory :

```shell
Get-ChildItem -Path Cert:\LocalMachine\MY | Select-Object -property FriendlyName, Subject, NotBefore, NotAfter, @{label='Thumbprint';'Expression'={$_.thumbprint -replace '(..(?!$))','$1:'}}
```

Ici, il s'agit de la valeur à droite du signe deux-points ( : ) :

```shell
> Thumbprint : BB:46:CA:6B:FC:92:4E:96:B4:BB:6E:44:7E:8F:AD:4C:C9:32:AB:AB
```

- Vous pouvez aussi utiliser la commande OpenSSL suivante (depuis une machine Linux/Unix/Mac distante) :

```shell
openssl s_client -connect ad.example.com:636 < /dev/null 2>/dev/null | openssl x509 -fingerprint -noout -in /dev/stdin
```

Ici, il s'agit de la valeur à droite du signe égal ( = ) :

```shell
> SHA1 Fingerprint=BB:46:CA:6B:FC:92:4E:96:B4:BB:6E:44:7E:8F:AD:4C:C9:32:AB:AB
```

### Autoriser la connexion au serveur Active Directory depuis votre Managed Bare Metal

Récupérez l'adresse IP de votre Managed Bare Metal par la méthode de votre choix.

Via cette commande sur le serveur Active Directory ou une machine Windows distante :

```shell
nslookup pcc-198-51-100-121.ovh.com
```

Ici, il s'agit de la valeur à la fin de la dernière ligne :

```shell
> Address:  198.51.100.121
```

Il est également possible d'utiliser la commande suivante (depuis une machine Linux/Unix/Mac distante) :

```shell
host pcc-198-51-100-121.ovh.com
```

Ici, il s'agit de la valeur à la fin de la ligne :

```shell
> pcc-198-51-100-121.ovh.com has address 198.51.100.121
```

Utilisez cette adresse IP pour autoriser votre Managed Bare Metal à accèder à votre serveur LDAPS Active Directory (par défaut sur le port TCP 636).

Cette opération s'effectue dans la configuration du pare-feu de votre Active Directory ou de votre entreprise.

Exemple de configuration de rgle de pare-feu entrant :

|Adresse IP distante (source)|Adresse IP locale (destination)|Port distant (source)|Port local (destination)|Protocole|
|---|---|---|---|---|
|198.51.100.121|Toutes les adresses|Tous les ports|636|TCP|

Adaptez cette configuration à votre entreprise et mettez en place la régle de pare-feu.

### Ajouter votre serveur Active Directory comme source d'authentification

La mise en place d'un serveur Active Directory comme source d'authentification peut être effectuée grâce à l'API OVHcloud.

Récupérez votre « serviceName » en utilisant l'appel API suivant :

> [!api]
>
> @api {GET} /dedicatedCloud
>

Effectuez ensuite la mise en place du serveur Active Directory comme source d'authentification.

Vous devrez spécifier les informations récupérées précédemment. Ne cochez pas la case « noSsl ».

> [!api]
>
> @api {POST} /dedicatedCloud/{serviceName}/federation/activeDirectory
>

![POST /dedicatedCloud/{serviceName}/federation/activeDirectory](images/federation_create.png){.thumbnail}

Assurez-vous que l'opération renvoyée s'effectue sans erreur. Vous pouvez la suivre depuis [l'espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr), dans l'onglet `Opérations`{.action} de votre Managed Bare Metal.

> [!primary]
>
> Si les informations fournies ne sont pas valides, l'opération concernée sera annulée et un message indiquera l'erreur renvoyée.
>
> ![Opération annulée](images/federation_canceled.png){.thumbnail}

### Autoriser un utilisateur Active Directory à accéder à votre Managed Bare Metal

Vous avez la possibilité d'autoriser un utilisateur issu de votre serveur Active Directory à accéder à votre Managed Bare Metal, grâce à l'API OVHcloud.

Récupérez votre « activeDirectoryId » en utilisant l'appel API suivant :

> [!api]
>
> @api {GET} /dedicatedCloud/{serviceName}/federation/activeDirectory
>

Effectuez l'ajout de l'utilisateur issu de votre Active Directory.

Vous devrez spécifier le nom d'utilisateur « pre-Windows 2000 » tel qu'indiqué dans votre Active Directory.

> [!api]
>
> @api {POST} /dedicatedCloud/{serviceName}/federation/activeDirectory/{activeDirectoryId}/grantActiveDirectoryUser

![POST /dedicatedCloud/{serviceName}/federation/activeDirectory/{activeDirectoryId}/grantActiveDirectoryUser](images/federation_grant_user.png){.thumbnail}

Assurez-vous que l'opération renvoyée s'effectue sans erreur. Vous pouvez la suivre depuis [l'espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr), dans l'onglet `Opérations`{.action} de votre Managed Bare Metal.<br>
Si les informations fournies ne sont pas valides, l'opération concernée sera annulée et un message indiquera l'erreur renvoyée.

Une fois autorisé, l'utilisateur et ses permissions seront modifiables directement depuis votre espace client OVHcloud comme n'importe quel utilisateur de votre Managed Bare Metal.

> [!primary]
>
> Par défaut, l'utilisateur ne possède aucune permission sur votre Managed Bare Metal. Il pourra se connecter à votre Managed Bare Metal mais n'aura aucun accès. Vous pouvez ajuster les permissions depuis l'espace client.
>

### Autoriser un groupe Active Directory à accéder à votre Managed Bare Metal

Vous avez la possibilité d'autoriser directement un ensemble d'utilisateurs (groupe) issu de votre serveur Active Directory à accéder à votre Managed Bare Metal, grâce à l'API OVHcloud.

Récupérez votre « activeDirectoryId » en utilisant l'appel API suivant :

> [!api]
>
> @api {GET} /dedicatedCloud/{serviceName}/federation/activeDirectory
>

Effectuez l'ajout du groupe issu de votre Active Directory.

Vous devrez spécifier le nom du groupe « pre-Windows 2000 » tel qu'indiqué dans votre Active Directory.

> [!api]
>
> @api {POST} /dedicatedCloud/{serviceName}/federation/activeDirectory/{activeDirectoryId}/grantActiveDirectoryGroup

![POST /dedicatedCloud/{serviceName}/federation/activeDirectory/{activeDirectoryId}/grantActiveDirectoryGroup](images/federation_grant_group.png){.thumbnail}

Assurez-vous que l'opération renvoyée s'effectue sans erreur. Vous pouvez la suivre depuis [l'espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr), dans l'onglet `Opérations`{.action} de votre Managed Bare Metal.<br>
Si les informations fournies ne sont pas valides, l'opération concernée sera annulée et un message indiquera l'erreur renvoyée.

Une fois autorisés, le groupe et ses permissions seront modifiables directement depuis votre espace client OVHcloud comme n'importe quel utilisateur de votre Managed Bare Metal.

> [!primary]
>
> Par défaut, le groupe ne possède aucune permission sur votre Managed Bare Metal. Ses membres pourront se connecter à votre Managed Bare Metal mais n'auront aucun accès. Vous pouvez ajuster les permissions depuis l'espace client.
>

## Aller plus loin

Échangez avec notre communauté d’utilisateurs sur <https://community.ovh.com/>.
