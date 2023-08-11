---
title: RACI Serveurs Dédiés
excerpt: RACI entre OVHcloud et le client pour l'utilisation des Serveurs Dédiés
updated: 2021-12-01
---

**Dernière mise à jour le 1er décembre 2021**

## Objectif

Le RACI ci-dessous détaille le partage des responsabilités entre OVHcloud et le client pour les services Serveurs Dédiés. Ce modèle peut aider le client à utiliser le service Serveur Dédié au mieux.

| Rôles |
| --- |
|R : Est en charge de la Réalisation du processus|
|A : Est gArant de la bonne fin du processus|
|C : Est Consulté pendant le processus|
|I : est Informé des résultats  du processus|

### 1. Avant la souscription

#### 1.1. Spécifier le service en fonction des besoins

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Choisir la localisation des serveurs dédiés | RA | I |
| Dimensionner les serveurs dédiés en fonction des besoins | RA | I |
| Choisir les options en fonction des besoins | RA | I |

### 2. Mise à disposition du service

#### 2.1. Installer le service

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Produire, acheminer, livrer et maintenir les machines physiques et les bâtiments d’hébergement | CI | RA |
| Installer et configurer les briques fonctionnelles internes au serveur dédié nécessaires au maintien en conditions opérationnelles et au maintien en conditions de sécurité (firmware, BIOS, BMC, IPMI...) |  | RA |
| Acheter et détenir les licences et droits d’utilisation pour les OS utilisés | RA |  |
| Déployer la configuration réseau initiale sur les équipements | I | RA |

#### 2.2. Modèle de réversibilité

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |

#### 2.3. Installation du SI client

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Installer l'OS | RA | RI |
| Installer l'ensemble des logiciels souhaités sur le serveur dédié | RA |  |

### 3. Utilisation du service

#### 3.1. Opérations

##### **3.1.1. Opérations quotidiennes**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Assurer l'accessibilité du Serveur Dédié sur le réseau |  | RA |
| Administrer les applicatifs installés sur le Serveur Dédié | RA |  |
| Décider d’ajouter / supprimer une option sur le Serveur Dédié, demander le remplacement d'un matériel défectueux sur le Serveur Dédié | RA | I |
| Réaliser l’ajout / suppression des options / du matériel sur le Serveur Dédié | I | RA |
| Adapter la configuration de l’OS aux ressources matérielles en présence | RA |  |

##### **3.1.2. Gestion des accès**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Gérer les accès et la politique de sécurité des utilisateurs du Service | RA |  |
| Gérer les accès physiques et logiques des équipes OVHcloud aux infrastructures | I | RA |
| Gérer les accès au manager | RA | I |

##### **3.1.3. Monitoring**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Surveiller le bon fonctionnement des dispositifs physiques (utilités) en support du Serveur Dédié | I | RA |
| Suivre les performances des ressources physiques | RA | R |
| Traiter et acquitter les alarmes provenant des dispositifs managés du Serveur Dédié | I | RA |
| Conserver les logs du système d’information hébergé sur le Serveur Dédié | RA |  |
| Conserver logs du Control Plane qui supervise le Serveur Dédié |  | RA |
| Suivre les performances des services installés sur le Serveur Dédié | RA |  |

##### **3.1.4. Stockage**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Créer, modifier, contrôler, restaurer, supprimer les jobs de backups | RA |  |
| Gérer le contenu hébergé sur les infrastructures | RA |  |
| Assurer la continuité et la durabilité des données | RA |  |
| Réaliser la maintenance des dispositifs de stockage et de sauvegarde fournis par OVHcloud |  | RA |

##### **3.1.5. Connectivité**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Assurer le fonctionnement des systèmes automatiques de gestion du réseau (architecture, mise en oeuvre, maintenance logicielle et matérielle pour les réseaux publics et privés déployés, IP primaire du serveur dédié) | I | RA |
| Gérer le plan d’adressage IP | RA | I |

##### **3.1.6. Gestion**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Assurer la sécurité des infrastructures de gestion (API, control plane) | R | RA |
| Assurer la sécurité des OS, Softwares et Middlewares installés sur les Serveurs Dédiés | RA |  |
| Gérer la sécurité des données déposées par le Client sur les Serveurs Dédiés | RA |  |
| Gérer la sécurité physique des équipements et infrastructures hébergés chez OVHcloud | I | RA |

##### **3.1.7. Continuité d'activité**
| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Gérer les systèmes de gestion automatiques de l’infrastructure mise à disposition | I | RA |
| Maintenir un plan de continuité d’activité et de reprise d’activité pour le SI hébergé | RA |  |

#### 3.2. Gestion des évènements

##### **3.2.1. Incidents**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Remplacer les éléments matériels défectueux du Serveur Dédié | I | RA |
| Traiter les incidents matériels et réseau (tickets et contacts téléphoniques) | AI | RA |
| Traiter les autres incidents | RA |  |
| Restaurer les sauvegardes de la machine | RA |  |

#### **3.2.2. Changements**

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Déployer les correctifs, mettre à jour et configurer les OS, softwares, middlewares et systèmes d’information hébergés sur les Serveurs Dédiés | RA |  |
| Planifier les changements demandés par le client | RA | RI |

### 4. Réversion

#### 4.1. Modèle de réversibilité

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Planifier les opérations de réversibilité | RA |  |
| Choisir les infrastructures de repli | RA |  |

#### 4.2. Récupération des données

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Gérer les opérations de réversibilité | RA |  |
| Migrer / transférer les données | RA |  |

### 5. Fin de service

#### 5.1. Destruction des configurations

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Rompre le contrat de fourniture de service | RA | I |
| Décommissionner les configurations associées au client |  | RA |

#### 5.2. Destruction des données

| **Activité** | **Client** | **OVHcloud** |
| --- | --- | --- |
| Opérer la destruction sécurisée des données sur les supports de stockage |  | RA |
| Détruire les supports de stockage arrivés en fin de vie ou sur lesquels le processus de destruction sécurisé génère des erreurs |  | RA |
| Fournir une attestation de destruction (sur demande) | I | RA |
