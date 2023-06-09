---
title: "Faire évoluer son offre d'hébergement web"
excerpt: "Découvrez comment modifier la formule d'abonnement de votre offre d'hébergement OVHcloud"
updated: 2023-04-18
---

**Dernière mise à jour le 18/04/2023**

## Objectif

Votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) vous permet d'augmenter les capacités de vos [offres d'hébergement Web](https://www.ovhcloud.com/fr/web-hosting/), afin de disposer d'un hébergement plus puissant, de plus d'espace de stockage, de bases de données, d'adresses e-mails ou de fonctionnalités supplémentaires comme les [mailing-lists](/pages/web/emails/feature_mailing_list) (à partir de [l'offre Pro](https://www.ovhcloud.com/fr/web-hosting/professional-offer/)) ou le [service SQL privé](https://www.ovhcloud.com/fr/web-hosting/options/private-sql/) (compris avec les offres de la [gamme Performance](https://www.ovhcloud.com/fr/web-hosting/performance-offer/)).

**Découvrez comment faire évoluer votre offre d'hébergement OVHcloud sans interruption.**

## Prérequis

- Disposer d'une [offre d'hébergement web](https://www.ovhcloud.com/fr/web-hosting/)
- Être connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr)

## En pratique

> [!warning]
>
> **Avant** tout changement sur votre abonnement actuel, vérifiez si vous êtes concerné par l'une de ces questions :
>
> - [Comment faire évoluer mon offre gratuite Start 10M vers une offre d'hébergement web ?](#start10m)
> - [Comment bénéficier d'un gain de performance temporaire sur mon offre d'hébergement performance ?](#boost)
> - [Vais-je perdre le temps restant sur mon offre d'hébergement actuelle lors de mon changement d'offre ?](#billing)
> - [Est-il possible de changer mon offre actuelle vers une offre inférieure ?](#checks)
>

### Modifier votre offre d'hébergement <a name="modify"></a>

Pour modifier votre abonnement, rendez-vous dans votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) dans la partie `Web Cloud`{.action}. Cliquez sur `Hébergements`{.action} et sélectionnez l'hébergement concerné.

Dans le cadre `Abonnement`, cliquez sur le bouton `...`{.action} à droite de `Offre` puis sur `Changer d'offre`{.action}.

![change_plan](images/change_plan.png){.thumbnail}

Sélectionnez ensuite votre nouvel abonnement, ainsi que sa durée. Validez les contrats correspondants puis cliquez sur `Envoyer`{.action}.

### Vérifier que votre hébergement est compatible avec une offre de la gamme inférieure <a name="checks"></a>

> [!warning]
>
> La modification de votre abonnement pour une offre de la gamme inférieure n'est possible que s'il s'agit de l'offre **immédiatement inférieure**.
> Par exemple, vous ne pourrez pas passer d'une formule *Performance 2* à une formule *Pro* en une seule opération.
> Vous devrez **d'abord** faire évoluer votre hébergement depuis la formule *Performance 2* vers l'offre *Performance 1* **puis** vers l'offre *Pro*.

Avant de réaliser votre changement vers une gamme inférieure, vérifiez les 7 éléments suivants:

#### 1 - Nombre de sites

L'offre [Kimsufi Web](https://www.kimsufi.com/fr/hosting.xml) ne permet pas d'avoir plus d'un nom de domaine sur le [multisite](/pages/web/hosting/multisites_configure_multisite) de votre hébergement.

Avant de passer de l'offre [Perso](https://www.ovhcloud.com/fr/web-hosting/personal-offer/) à l'offre [Kimsufi Web](https://www.kimsufi.com/fr/hosting.xml), vérifiez donc que votre hébergement ne comporte qu'un seul site.

#### 2 - Bases de données Start SQL

Avant de passer votre hébergement sur une offre inférieure, assurez-vous que la nouvelle offre comporte assez de [bases de données](https://www.ovhcloud.com/fr/web-hosting/options/start-sql/). Vérifiez aussi qu'elles sont de tailles suffisantes.

Dans le cas contraire, supprimez les bases de données inutilisées et réduisez, si nécessaire, la quantité de données qu'elles contiennent. Cette quantité ne devra pas dépasser la taille maximale des bases de données de la nouvelle offre (pour toute demande d'assistance sur les manipulations à effectuer, contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr/directory/)).

Suite à la suppression de données sur vos bases, pensez à recalculer le quota utilisé depuis l'onglet `Bases de données`{.action} dans la partie `Hébergements`{.action} de votre espace client. Cliquez sur le bouton `...`{.action} à droite de la base concernée puis sur `Recalculer le quota`{.action}.

![quota](images/quota.png){.thumbnail}

#### 3 - Web Cloud Databases

Si vous utilisez l'offre [Web Cloud Databases](/pages/web/clouddb/starting_with_clouddb#activation-de-votre-serveur-clouddb-inclus-avec-votre-offre-dhebergement-web) incluse avec votre hébergement [Performance](https://www.ovhcloud.com/fr/web-hosting/performance-offer/) et que vous souhaitez passer votre hébergement sur une offre [Pro](https://www.ovhcloud.com/fr/web-hosting/professional-offer/), rendez-vous dans la partie `Hébergements`{.action} de votre espace client.<br>
Cliquez sur le bouton `...`{.action} dans la partie `Bases de données privée`{.action} puis sur `Délier`{.action}.

![Web Cloud Databases](images/clouddb.png){.thumbnail}

Cette action vous permettra de commander une offre Web Cloud Databases indépendante de votre abonnement *Performance*. Les données de votre serveur seront conservées.

Si vous ne souhaitez pas conserver ces données, vous pouvez aussi supprimer votre SQL privé avant de passer sur l'offre *Pro* : 

1. Sauvegardez vos données en suivant les instructions de ce [guide](/pages/web/clouddb/save-export-on-database-server#en-pratique).<br>
2. Supprimez votre serveur Web Cloud Databases via votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr). Pour cela, cliquez en haut à droite sur votre nom puis sur `Gestion des services`{.action}. Cliquez ensuite sur le bouton `...`{.action} à droite de la ligne concernée puis sur `Supprimer mon hébergement SQL privé`{.action}.

#### 4 - Espace FTP

Avant de passer votre hébergement sur une offre inférieure, assurez-vous que la nouvelle offre propose suffisamment [d'espace de stockage FTP](/pages/web/hosting/ftp_connection) pour que l'import des fichiers de votre hébergement actuel soit possible.

Le quota utilisé sur votre hébergement FTP est visible dans la partie `Hébergements`{.action} de votre espace client. Cliquez sur l'onglet `Informations générales`{.action}, vous retrouverez le quota sous `Espace Disque`.

![ftp](images/ftp.png){.thumbnail}

#### 5 - Adresses e-mail

Vérifiez également que votre nouvelle offre propose un nombre suffisant d'adresses e-mail disponibles. Dans le cas contraire, supprimez les adresses superflues, après les avoir [sauvegardées](/pages/web/emails/manual_email_migration) si nécessaire.

Si vous souhaitez conserver le même nombre de boîtes e-mail, avant de passer votre hébergement sur une offre inférieure, vous pouvez également commander une nouvelle offre de messagerie **MX Plan**. Dans la partie `Emails`{.action} de votre espace client, cliquez sur l'offre concernée puis sur le bouton  `...`{.action} à droite de `Offre`. Cliquez enfin sur `Changer d'offre`{.action}.

![mxplan](images/mxplan.png){.thumbnail}

#### 6 - Mailing lists

La fonctionnalité [Mailing lists](/pages/web/emails/feature_mailing_list) est en option sur les hébergements [Perso](https://www.ovhcloud.com/fr/web-hosting/personal-offer/) et [Kimsufi Web](https://www.kimsufi.com/fr/hosting.xml).

Pour passer votre hébergement sur une offre [Perso](https://www.ovhcloud.com/fr/web-hosting/personal-offer/), vous devrez donc dans un premier temps en supprimer les mailing lists ou commander une offre de messagerie comprenant cette fonctionnalité (**MX Plan 100** ou **MX Plan Full**) depuis votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).

Dans la partie `Emails`{.action} de votre espace client, sélectionnez l'offre concernée puis cliquez sur `...`{.action} à droite de `Offre`{.action}. Cliquez enfin sur `Changer d'offre`{.action}.

#### 7 - Utilisateurs FTP

Avant de basculer votre hébergement sur une offre inférieure, assurez-vous que la nouvelle offre propose suffisamment d'utilisateurs FTP.

Le nombre d'utilisateurs FTP est visible dans votre espace client OVHcloud. Rendez-vous dans la partie `Web Cloud`{.action} puis sélectionnez l'hébergement concerné dans la section `Hébergements`{.action} sur votre gauche. Sur la page qui s'affiche, cliquez sur l'onglet `FTP-SSH`{.action}. Dans la partie inférieure de la page suivante, un tableau liste tous les utilisateurs FTP créés pour votre hébergement web.

Pour supprimer des utilisateurs FTP, cliquez sur le bouton `...`{.action} à droite de l'utilisateur FTP que vous souhaitez supprimer puis sur `Supprimer`{.action}.

![user FTP deletion](images/userFTP.png){.thumbnail} 

#### Finalisation

Une fois ces 7 éléments vérifiés, vous pouvez réaliser votre [changement d'offre](#modify).

### Cas particuliers

#### Vous possédez une offre Start 10M <a name="start10m"></a>

Dans le cadre d'un changement de l'offre [Start10M](/pages/web/hosting/activate_start10m), seule [l'offre Perso](https://www.ovhcloud.com/fr/web-hosting/personal-offer/) vous sera proposée. Néanmoins, après un changement vers l'offre Perso, il vous sera possible de faire évoluer cette dernière vers l'ensemble de nos [offres d'hébergement Web](https://www.ovhcloud.com/fr/web-hosting/).

Suivez [ces instructions](#modify) pour réaliser votre changement d'offre.

#### Booster temporairement votre hébergement Performance <a name="boost"></a>

Avec l'[option Boost](https://www.ovhcloud.com/fr/web-hosting/options/boost/), disponible sur nos offres *Performance*, vous pouvez augmenter temporairement les ressources CPU et RAM de votre hébergement pour absorber une augmentation ponctuelle du trafic. Si cette augmentation se prolonge dans le temps, vous pouvez également [basculer vers l'offre Performance de niveau supérieur](#modify) afin de disposer de ces ressources de manière permanente.

> [!warning]
>
> Lorsque vous décidez d'activer l'option Boost, celle-ci reste active et facturée **tant que vous ne l'avez pas désactivée**.

Si l'option **Boost** convient à votre besoin, vous trouverez ci-dessous les instructions pour **activer** ou **désactiver** cette option sur votre hébergement.

> [!tabs]
> **Activer l'option Boost**
>>
>> Dans le cadre `Informations générales` de votre hébergement, cliquez sur le bouton `...`{.action} à droite de `Boost` puis sur `Booster mon offre`{.action}.<br><br>
>> ![boost](images/enable_boost.png){.thumbnail}<br>
>>
> **Désactiver l'option Boost**
>>
>> Dans l'onglet `Plus` de votre hébergement, cliquez sur `Booster mon offre`{.action}.<br>
>> Le tableau d'utilisation de l'option Boost s'affiche, cliquez sur `Désactiver l'offre boost`{.action}.<br><br>
>> ![boost](images/disable_boost.png){.thumbnail}<br>

#### La facturation en cas de changement d'offre <a name="billing"></a>

Lorsque vous modifiez votre offre initiale vers une offre supérieure, un calcul au *prorata temporis* est alors appliqué jusqu'à la prochaine date de renouvellement de cet abonnement initial.
Ce calcul correspond à la différence de tarif entre votre offre initiale et votre nouvelle offre.

> **Exemple :**<br>
>
> Vous avez souscrit à un abonnement [Perso](https://www.ovhcloud.com/fr/web-hosting/personal-offer/) au 1er janvier 2022.
>
> Le 31 octobre 2022, vous passez de cette offre **Perso** à un abonnement sur l'offre [Pro](https://www.ovhcloud.com/fr/web-hosting/professional-offer/).<br>
>
> Par conséquent, le montant correspondant à la durée restante sur l'abonnement **Perso** (2 mois, du 1er novembre 2022 au 1er janvier 2023) est automatiquement soustrait du coût du nouvel abonnement **Pro**, jusqu'au 1er janvier 2023. Vous ne paierez que la différence.
> À partir du 1er janvier 2023, l'abonnement Pro vous est ensuite facturé à son tarif en vigueur.

Suivez [ces instructions](#modify) pour réaliser votre changement d'offre.

## Aller plus loin <a name="gofurther"></a>

[Consulter les statistiques et les logs de mon site hébergé sur une offre mutualisée](/pages/web/hosting/logs_and_statistics)

[Optimisation des performances de votre site](/pages/web/hosting/optimise_your_website_performance)

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr/directory/).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous invitons à consulter nos différentes [offres de support](https://www.ovhcloud.com/fr/support-levels/).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
