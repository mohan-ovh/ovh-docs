---
title: Cold Archive - Premiers pas avec Cold Archive
excerpt: Ce guide vous montre comment gérer vos données avec Cold Archive
updated: 2023-05-17
---

**Dernière mise à jour le 17/05/2023**

## Objectif

Cold Archive est un service de stockage de données à long terme.
Lorsqu'ils sont archivés, tous les objets d'un bucket sont stockés sur des bandes physiques.
La restauration peut prendre un certain temps car elle doit être lue sur des bandes.

**Ce guide explique comment configurer le stockage sur bandes avec Cold Archive.**

## Prérequis

- [Premiers pas avec Object Storage](/pages/cloud/storage/object_storage/s3_getting_started_with_object_storage#utilisation-de-aws-cli)
- `awscli` version >= 1.16.62

## En pratique

Dans ce guide, les **alias awscli** sont utilisés pour simplifier les commandes.

```bash
mkdir -p ~/.aws/cli
touch ~/.aws/cli/alias
```

Ajoutez ce contenu au fichier :

```bash
[toplevel]

put-ovh-archive = s3api put-bucket-intelligent-tiering-configuration --id myid --intelligent-tiering-configuration '{"Id": "myid", "Status": "Enabled", "Tierings": [{"Days": 999,"AccessTier": "OVH_ARCHIVE"}]}' --bucket

put-ovh-restore = s3api put-bucket-intelligent-tiering-configuration --id myid --intelligent-tiering-configuration '{"Id": "myid", "Status": "Enabled", "Tierings": [{"Days": 999,"AccessTier": "OVH_RESTORE"}]}' --bucket

get-ovh-bucket-status = s3api get-bucket-intelligent-tiering-configuration --id myid --bucket

delete-ovh-archive = s3api delete-bucket-intelligent-tiering-configuration --id myid --bucket
```

> [!primary]
>
> `Id` sera nécessaire pour les opérations ultérieures PUT, GET et DELETE sur la configuration de l'Intelligent-Tiering.
> `Status` et `Days` sont obligatoires mais non utilisés.
>

> [!primary]
>
> Le plugin `awscli-plugin-endpoint` ne fonctionne pas avec les alias, le paramètre `--endpoint-url` sera requis dans chaque commande.
>

> [!primary]
>
> Si vous avez défini plusieurs profils, ajoutez `--profile <profile>` à la ligne de commande.
>

### Archiver un bucket

Avant d'archiver un bucket, il est nécessaire de s'assurer qu'il n'y a pas de parts de MPU non complétées.
Cela peut se faire avec la commande :

```bash
aws --endpoint-url https://s3.rbx-archive.io.cloud.ovh.net s3api list-multipart-uploads --bucket <bucket_name>
```

Archiver un bucket:

```bash
aws --endpoint-url https://s3.rbx-archive.io.cloud.ovh.net put-ovh-archive <bucket_name>
```

Après cette requête, le bucket n'est pas encore archivé.<br>
L'archivage sur les bandes prendra un certain temps.<br>
A partir de cette commande et jusqu'à une restauration, le bucket ne peut accepter aucune requête de lecture ou d'écriture sur les objets (lister les objets est toujours autorisé).

### Restauration d'un bucket

Restaurer un bucket:

```bash
aws --endpoint-url https://s3.rbx-archive.io.cloud.ovh.net put-ovh-restore <bucket_name>
```

Après cette requête, le bucket n'est pas encore restauré.<br>
La restauration prendra du temps et l'accès aux objets sera en lecture seule (l'écriture est interdite).

### Supression d'un bucket

Supprimer la configuration Intelligent-Tiering et les objets d'un bucket:

```bash
aws --endpoint-url https://s3.rbx-archive.io.cloud.ovh.net delete-ovh-archive <bucket_name>
```

Après cette requête, les objets du bucket ne sont pas encore supprimés.<br>
La suppression des objets prendra un certain temps.<br>
Une fois les objets supprimés, le bucket peut être supprimé :

```bash
aws s3 rb s3://<bucket_name>
```

### Statut d'un bucket

Une fois qu'une configuration Intelligent-Tiering a été poussée (via une opération `put-bucket-intelligent-tiering-configuration`) et jusqu'à ce qu'elle soit retirée (via une opération `delete-bucket-intelligent-tiering-configuration`), l'état d'un bucket peut être lu via :

```bash
aws --endpoint-url https://s3.rbx-archive.io.cloud.ovh.net s3api get-bucket-tagging --bucket <bucket_name>
```

#### Liste des statuts d'un bucket

| État de l'archive (= bucket) | Description | Autorisations d'objets |
| --- | --- | --- |
| **`None`** | Aucune configuration Intelligent-Tiering n'a encore été appliquée au bucket. | Tous |
| **`Archiving`** | Archivage en cours sur bandes. | Liste |
| **`Archived`** | Objets archivés sur bandes uniquement. | Liste |
| **`Restoring`** | Restauration en cours à partir des bandes. | Liste |
| **`Restored`** | Objets restaurés et accessibles. | Lecture seule + Liste |
| **`Deleting`** | Suppression des objets des bandes (et des disques si restaurés) en cours. | Liste |
| **`Flushed`** | Le bucket est vide et peut être retiré en toute sécurité. | Liste (bucket vide) |

## Aller plus loin

Découvrez notre chaîne dédiée Discord : <https://discord.gg/ovhcloud>. Posez vos questions, faites vos commentaires et interagissez directement avec l’équipe qui conçoit nos services de stockage et de sauvegarde.

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
