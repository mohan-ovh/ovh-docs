---
title: "Mettre à jour votre système d'exploitation"
slug: upgrade-os
excerpt: "Découvrez comment mettre à jour un système d'exploitation en fin de vie"
section: 'Tutoriels'
order: 14
---

**Dernière mise à jour le 09/07/2021**

## Objectif

Ce tutoriel décrit les étapes à suivre pour mettre à jour un système d'exploitation en fin de vie vers une nouvelle version.

> [!alert]
> Avertissement : comme pour toute mise à niveau majeure d'un système d'exploitation, il existe un risque de panne, de perte de données ou de défaillance de la configuration logicielle.
> Par conséquent, avant de suivre ce tutoriel, OVHcloud vous recommande vivement de [sauvegarder votre instance](../sauvegarder-une-instance/) et d'effectuer des tests approfondis sur vos applications, pour s'assurer qu'elles fonctionnent sur la nouvelle version du système d'exploitation.
>

> [!primary]
> Pour éviter les problèmes mentionnés ci-dessus, il est recommandé d'installer une nouvelle instance avec le nouveau système d'exploitation vers lequel vous effectuez la mise à jour, puis de migrer les données.
> Un examen des différences dans votre application peut encore s'avérer nécessaire, mais le système d'exploitation sera probablement plus stable.
>

## Prérequis

- Disposer d'un [accès root au serveur](../passer-root-et-definir-un-mot-de-passe/)
- Avoir effectué [une sauvegarde de votre instance](../sauvegarder-une-instance/)

## En pratique

### Ubuntu

Avant de procéder à la mise à jour de la version majeure de votre OS, assurez-vous de mettre à jour les versions les plus récentes de tous les paquets installés sur sa version actuelle :

```sh
$ sudo apt-get update
```

Procédez ensuite à la mise jour de vos paquets installés vers leurs dernières versions :

```sh
$ sudo apt-get upgrade -y
```

Une fois cette opération terminée, effectuez un *dist-upgrade* qui lancera d'autres mises à jour pouvant être nécessaires :

```sh
$ sudo apt-get dist-upgrade -y
```

La mise à jour de la version majeure peut alors être effectuée. Ubuntu fournit désormais un outil appelé *do-release-upgrade* qui rend la mise à jour plus sûre et plus facile. Commençez la mise à jour via cette commande :

```sh
$ sudo do-release-upgrade
```

Suivez les instructions présentées alors. Elles consistent principalement à confirmer que vous souhaitez poursuivre la mise à jour.

Remarques :

- L'outil peut vous demander de redémarrer votre serveur avant d'effectuer la mise à jour. Pour ce faire, tapez simplement « reboot » (redémarrer) et appuyez sur Entrée.
- Vous serez alerté sur le fait qu'effectuer cette opération via une connexion SSH n'est pas recommandé. Comme il n'y a pas d'accès physique au serveur, la connexion en SSH est le principal moyen d'accéder à votre serveur.
Ubuntu démarrera un nouveau service SSH sur un autre port afin que vous conserviez un autre accès en cas de défaut. En outre, vous pourrez toujours accéder au serveur par le biais de la console si vous n'y avez plus accès en SSH.
- Au cours de la mise à niveau, vous serez peut-être invité à confirmer la suppression des paquets qui ne sont plus pris en charge. Vérifiez que cela n'a aucun impact sur vos applications avant de continuer.

Une fois la mise à jour terminée, le serveur procédera à un redémarrage et vous perdrez la connexion jusqu'à ce qu'il redémarre.
Quelques minutes plus tard, vous devriez être en mesure de vous connecter et de voir un message similaire à celui ci-dessous (la version sera la prochaine version disponible par rapport à votre version précédente) :

```sh
$ Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-147-generic x86_64)
```

> [!primary]
> Lorsque vous mettez à jour le système d'exploitation au lieu de le réinstaller, la nouvelle version de votre OS n'est pas indiquée sur l'espace client / l'API OVHcloud, ni sur l'API Horizon / OpenStack.
>

Vérifiez alors que vos applications fonctionnent comme prévu. En cas de problème, nous vous recommandons de [restaurer la sauvegarde](../creer-restaurer-un-serveur-virtuel-a-partir-dune-sauvegarde/) effectuée avant la mise à jour.

### Fedora

Avant de commencer la mise à jour de la version majeure de l'OS, assurez-vous de mettre à jour les versions les plus récentes de tous les paquets installés sur sa version actuelle. Saisissez cette commande :

```sh
$ sudo dnf upgrade --refresh
```

Redémarrez ensuite le serveur :

```sh
$ reboot
```

Une fois le serveur redémarré, installez le paquet de mise à jour :

```sh
$ sudo dnf install dnf-plugin-system-upgrade
```

Maintenant que vous disposez du paquet requis, vous pouvez effectuer la mise à jour. Les mises à jur du système ne sont officiellement prises en charge et testées que sur 2 versions au maximum (par exemple, de 32 à 34).
Dans cet exemple, nous allons passer de Fedora 32 à 33 :

```sh
$ sudo dnf system-upgrade download --releasever=33
$ sudo dnf system-upgrade reboot
```

Une fois la version téléchargée et le processus de mise à jour lancé, le serveur redémarre pour terminer la mise à jour.
<br>Il peut s'écouler un certain temps avant que vous ne puissiez vous reconnecter au serveur, car la mise à jour prend du temps.

Vérifiez que vos applications fonctionnent comme prévu. En cas de problème, nous vous recommandons de [restaurer la sauvegarde](../creer-restaurer-un-serveur-virtuel-a-partir-dune-sauvegarde/) effectuée avant la mise à jour.

> [!primary]
> Si vous rencontrez des difficultés, vous trouverez des réponses à vos questions sur le site Web [Fedora Docs](https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/){.external}.
>

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
