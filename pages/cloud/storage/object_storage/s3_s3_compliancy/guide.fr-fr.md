---
title: Object Storage - Compatibilité S3
slug: s3/s3-compliancy
excerpt: "Découvrez la compatibilité de l'API S3 OVHcloud par rapport à l'API AWS S3"
section: Informations générales
order: 010
updated: 2021-12-08
---

**Dernière mise à jour le 08/12/2021**

## Objectif

Ce guide a pour objectif d'énumérer les fonctionnalités de l'API S3 supportées par S3 Object Storage.

## En pratique

### Common operations

| Fonctionnalité | Disponibilité |
|:--|:-:|
| GET Service |	✅ |

### Bucket operations

| Feature | Availability |
|:--|:-:|
| DELETE Bucket | ✅ |
| DELETE Bucket cors | ✅ |
| DELETE Bucket encryption | |	 
| DELETE Bucket lifecycle | |
| DELETE Bucket policy | |
| DELETE Bucket replication | |
| DELETE Bucket tagging | ✅ |
| DELETE Bucket website | |
| GET Bucket (List Objects) Version 2 | ✅ |
| GET Bucket acl | ✅ |
| GET Bucket cors | ✅ |
| GET Bucket encryption | |
| GET Bucket lifecycle | |
| GET Bucket location | ✅ |
| GET Bucket notification | |	 
| GET Bucket Object versions | ✅ |
| GET Bucket policy | |
| GET Bucket replication | |
| GET Bucket tagging | ✅ |
| GET Bucket versioning | ✅ |
| GET Bucket website | |
| HEAD Bucket | ✅ |
| List Multipart Uploads | ✅ |
| PUT Bucket | ✅ |
| PUT Bucket acl | ✅ |
| PUT Bucket cors | ✅ |
| PUT Bucket encryption | |	 
| PUT Bucket lifecycle | |
| PUT Bucket notification | |	 
| PUT Bucket policy | |
| PUT Bucket replication | |
| PUT Bucket tagging | ✅ |
| PUT Bucket versioning | ✅ |
| PUT Bucket website 	| |

### Objects operations

| Feature | Availability |
|:--|:-:|
| DELETE Multiple Objects | ✅ |
| DELETE Object | ✅ |
| DELETE Object tagging | ✅ |
| GET Object | ✅ |
| GET Object ACL | ✅ |
| GET Object tagging | ✅ |
| GET Object torrent | |
| HEAD Object | ✅ |
| OPTIONS object | ✅ |
| POST Object | |
| POST Object restore | |
| PUT Object | ✅ |
| PUT Object - Copy | ✅ |
| PUT Object acl | ✅ |
| PUT Object tagging | ✅ |

### Multiparts objects operations

| Feature | Availability |
|:--|:-:|
| Abort Multipart Upload | ✅ |
| Complete Multipart Upload | ✅ |
| Initiate Multipart Upload | ✅ |
| List Parts | ✅ |
| Upload Part | ✅ |
| Upload Part - Copy | ✅ |

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
