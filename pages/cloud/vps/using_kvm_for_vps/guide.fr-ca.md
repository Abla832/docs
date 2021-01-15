---
title: Utiliser le KVM pour les VPS
excerpt: Découvrez comment accéder à votre VPS à l'aide de la fonctionnalité KVM
slug: utilisation-kvm-sur-vps
section: Premiers pas
---

**Dernière mise à jour le 7 septembre 2020**

## Objectif

La console KVM permet une connexion directe à votre VPS sans avoir à utiliser un logiciel externe (terminal, Putty, etc.). Cette console est accessible via votre espace client OVHcloud ou les API OVHcloud.  

**Ce guide détaille les deux méthodes d'accès au KVM.**

## Prérequis

- Un [VPS](https://www.ovhcloud.com/fr-ca/vps/) dans votre compte OVHcloud.
- Être connecté à l'[espace client](https://ca.ovh.com/auth/?action=gotomanager).

## En pratique

### Connexion au KVM depuis l'espace client OVHcloud

#### Gamme VPS actuelle

Connectez-vous à [l'espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager), accédez à la section `Bare Metal Cloud`{.action} et sélectionnez votre serveur dans le menu de navigation de gauche sous `VPS`{.action}. Dans cette section, cliquez sur `...`{.action} à droite du nom de votre VPS dans la zone « Votre VPS ».

![Ouvrir KVM](images/kvm-new1.png){.thumbnail}

#### Ancienne gamme VPS

Connectez-vous à [l'espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager), accédez à la section `Bare Metal Cloud`{.action} et sélectionnez votre serveur dans le menu de navigation de gauche sous `VPS`{.action}. Dans cette section, cliquez sur le lien de raccourci intitulé `KVM`{.action}.

![Cliquez sur le bouton KVM](images/kvm-new2.png){.thumbnail}

### Utilisation de la console KVM

L'écran KVM s'ouvre. Il s'agit d'une petite fenêtre indiquant la connexion à votre serveur. Étant donné que la fenêtre est assez petite, il peut être très difficile de naviguer dans l'interface de votre serveur à l'aide des barres de défilement. Par conséquent, nous vous recommandons d'ouvrir le KVM dans une nouvelle fenêtre plein écran à l'aide du bouton « Ouvrir dans une nouvelle fenêtre » situé dans l'angle inférieur droit de la fenêtre contextuelle.

> [!primary]
>
> Si vous rencontrez des soucis de double saisie, cela peut être dû à un réglage automatique de l'écran. Nous vous recommandons d'ouvrir le KVM dans une nouvelle fenêtre en cliquant sur le bouton « Ouvrir dans une nouvelle fenêtre ».
>
> Si vous rencontrez toujours des problèmes avec l'écran, nous vous recommandons de supprimer de l'URL la partie « auto ». Si l'URL est https://compute.sbg1.cloud.ovh.net:6080/vnc_auto.html?token=xxxxxxxxxxxx, elle doit devenir https://compute.sbg1.cloud.ovh.net:6080/vnc.html?token=xxxxxxxxxxxx (le lien pour vous peut être différent, l'exemple donné n'illustre que la partie de l'URL à supprimer)
>

![Connexion au KVM](images/kvm_screen.png){.thumbnail}

> [!primary]
>
> Le clavier peut avoir une disposition différente de la vôtre. Assurez-vous de le vérifier, car le clavier peut être AZERTY au lieu de QWERTY, par exemple.
>

### Connexion au KVM via les API

Il peut arriver que vous rencontriez des problèmes de connexion au KVM via votre panneau de configuration OVHcloud, en particulier avec les versions plus anciennes. Dans ce cas, vous pouvez utiliser la solution API. Pour ce faire, connectez-vous via l'API [OVHcloud](https://ca.api.ovh.com/).

#### Sur un VPS 2014

Si vous avez un VPS 2014, vous pouvez rencontrer  une *erreur 1006*. Passer en revue l'API à l'aide de l'appel ci-dessous pourrait résoudre ce problème.

> [!api]
>
> @api {POST} /vps/{serviceName}/openConsoleAccess
>
> Paramètres d'appel API :
>
>> serviceName *
>>> ID de votre VPS qui ressemble à vpsxxxxx.ovh.net
>> protocole
>>> VNC

Malgré le retour positif de l'API, il est possible que la connexion prenne une ou deux minutes pour s'établir, le temps que le port soit effectivement ouvert.

Nous vous recommandons d'utiliser l'un des clients suivants:

- [UltraVnc](https://www.uvnc.com/downloads/ultravnc.html){.external}
- [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/){.external}

Utilisez les détails fournis par l'appel API pour vous connecter à distance au VPS à l'aide de l'un des clients logiciels mentionnés ci-dessus.

#### Sur un VPS 2016

En cas de souci avec le KVM, voici l'API conseillée pour l'accès au KVM :

> [!api]
>
> @api {POST} /vps/{serviceName}/getConsoleUrl
>
> Paramètres d'appel API :
>
>> serviceName *
>>> ID de votre VPS qui ressemble à vpsxxxxx.ovh.net
>

> [!primary]
>
> Si vous rencontrez toujours des soucis avec l'écran, nous vous recommandons de supprimer de l'URL la partie « auto ». Si l'URL est (le lien pour vous peut être différent, cet exemple illustre uniquement la partie de l'URL à supprimer) https://compute.sbg1.cloud.ovh.net:6080/vnc_auto.html?token=xxxxxxxxxxxx alors elle doit devenir https://compute.sbg1.cloud.ovh.net:6080/vnc.html?token=xxxxxxxxxxxx
>

## Aller plus loin

Échangez avec notre communauté d’utilisateurs sur <https://community.ovh.com>.
