---
title: Object Storage - Premiers pas avec Object Storage
excerpt:
updated: 2023-04-28
---

**Dernière mise à jour le 28/04/2023**

## Objectif

Ce guide a pour objectif de vous familiariser avec la gestion de vos conteneurs / objets.

## Prérequis

- Un [projet Public Cloud](/pages/platform/public-cloud/create_a_public_cloud_project) dans votre compte OVHcloud
- Être connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr)
- Avoir créé un [utilisateur S3](/pages/cloud/storage/object_storage/s3_identity_and_access_management)

## En pratique

### Utilisation de AWS CLI

#### Installation

Entrez la commande suivante :

```bash
user@host:~$ pip3 install awscli awscli-plugin-endpoint
```

> [!primary]
>
> - `awscli-plugin-endpoint` est optionel  
> - Installez le package `groff` si vous souhaitez utiliser l'aide en ligne de commande.
>

#### Collecter les informations d'identification

- Vous aurez besoin de l'*Access key* et de la *Secret key* de votre utilisateur. Ces informations sont accessibles depuis l'onglet `Utilisateurs S3` dans votre espace client.
- Vous aurez également besoin de votre *url_endpoint*. Si vous avez déjà créé votre bucket, cette information est accessible depuis l'onglet `Mes conteneurs` puis dans les détails du votre bucket. En cas de besoin, suivez ce [guide](/pages/cloud/storage/object_storage/s3_location).

#### Configuration

Configurez le client aws comme suit :

```bash
user@host:~$ cat ~/.aws/credentials

[default]
aws_access_key_id = <access_key>
aws_secret_access_key = <secret_key>

user@host:~$ cat ~/.aws/config

# If you have not installed awscli-plugin-endpoint, delete the next two lines
[plugins]
endpoint = awscli_plugin_endpoint

[profile default]
region = <region_in_lowercase>
s3 =
  endpoint_url = <url_endpoint>
  signature_version = s3v4
s3api =
  endpoint_url = <url_endpoint>
```

> [!primary]
>
> Vous pouvez aussi utiliser la configuration interactive en exécutant la commande suivante :
> `aws --configure`
>

Voici les valeurs de configuration que vous pouvez définir spécifiquement  :

| Variable  | Type | Valeur | Définition  |
|:--|:--|:--|:--|
| max_concurrent_requests | Integer | **Défaut :** 10 | Le nombre maximum de requêtes simultanées. |
| max_queue_size | Integer | **Défaut :** 1000 | Le nombre maximal de tâches dans la file d'attente des tâches. |
| multipart_threshold | Integer<br>String | **Défaut :** 8MB | Le seuil de taille que l'interface CLI utilise pour les transferts multipart de fichiers individuels. |
| multipart_chunksize | Integer<br>String | **Défaut :** 8MB<br>**Minimum for uploads:** 5MB | Lors de l'utilisation de transferts multipart, il s'agit de la taille de morceau que l'interface CLI utilise pour les transferts multipart de fichiers individuels. |
| max_bandwidth | Integer | **Défaut :** None | La bande passante maximale qui sera consommée pour le chargement et le téléchargement de données vers et depuis vos buckets. |
| verify_ssl | Boolean | **Défaut :** true | Active / Désactive la vérification des certificats SSL |

Pour connaître la liste des endpoints par région et par classe de stockage, vous pouvez vous référer à [cette page](/pages/cloud/storage/object_storage/s3_location).

#### Utilisation

> [!primary]
>
> Si vous n'avez pas installé `awscli-plugin-endpoint`, vous devez ajouter `--endpoint-url https://s3.<region_in_lowercase>.<storage_class>.cloud.ovh.net` à la ligne de commande.
>

> [!primary]
>
> Si vous avez défini plusieurs profils, ajoutez `--profile <profile>` à la ligne de commande
>

**Créer un bucket**

```bash
aws s3 mb s3://<bucket_name>
aws --endpoint-url https://s3.<region_in_lowercase>.<storage_class>.cloud.ovh.net --profile default s3 mb s3://<bucket_name>
```

**Lister vos buckets**

```bash
aws s3 ls
```

**Téléverser vos fichiers en tant qu'objets dans votre bucket**

```bash
aws s3 cp /datas/test1 s3://<bucket_name>
```

**Par défaut, les objets prennent le nom des fichiers mais ils peuvent être renommés**

```bash
aws s3 cp /datas/test1 s3://<bucket_name>/other-filename
```

**Télécharger un objet depuis un bucket**

```bash
aws s3 cp s3://<bucket_name>/test1 .
```

**Télécharger un objet d'un bucket vers un autre bucket**

```bash
aws s3 cp s3://<bucket_name>/test1 s3://<bucket_name_2>
```

**Télécharger ou téléverser un bucket entier vers l'hôte/bucket**

```bash
aws s3 cp s3://<bucket_name> . --recursive
aws s3 cp s3://<bucket_name> s3://<bucket_name_2> --recursive
```

**Synchronisation des buckets**

```bash
aws s3 sync . s3://<bucket_name>
aws s3 sync s3://<bucket_name> s3://<bucket_name_2>
```

**Supprimer des objets et des buckets**

```bash
# Suppression d'un objet
aws s3 rm s3://<bucket_name>/test1
# Suppression de tous les objets d'un bucket
aws s3 rm s3://<bucket_name> --recursive
# Suppression d'une zone de stockage. Pour supprimer un bucket, il doit être vide.
aws s3 rb s3://<bucket_name>
# Si le bucket n'est pas supprimé, vous pouvez utiliser la même commande avec l'option --force.
# Cette commande supprime tous les objets du bucket, puis supprime le bucket.
aws s3 rb s3://<bucket_name> --force
```

**Définir des tags sur un bucket**

```bash
aws s3api put-bucket-tagging --bucket <bucket_name> --tagging 'TagSet=[{Key=myKey,Value=myKeyValue}]'
aws s3api get-bucket-tagging --bucket <bucket_name>
```
```json
{
  "TagSet": [
    {
    "Value": "myKeyValue",
    "Key": "myKey"
    }
  ]
}
```

**Supprimer les tags sur un bucket**

```bash
aws s3api s3api delete-bucket-tagging --bucket <bucket_name>
```

**Définir des tags sur un objet**

```bash
aws s3api put-object-tagging --bucket <bucket_name> --key test1 --tagging 'TagSet=[{Key=myKey,Value=myKeyValue}]'
aws s3api get-bucket-tagging --bucket <bucket_name>
```
```json
{
  "TagSet": [
    {
    "Value": "myKeyValue",
    "Key": "myKey"
    }
  ]
}
```

**Supprimer les tags sur un objet**

```bash
aws s3api s3api delete-object-tagging --bucket <bucket_name> --key test1
```

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
