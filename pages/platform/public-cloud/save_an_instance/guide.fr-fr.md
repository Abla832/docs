---
title: 'Sauvegarder une instance'
slug: sauvegarder-une-instance
excerpt: 'Apprenez à sauvegarder une instance Public Cloud dans votre espace client OVHcloud'
section: "Gestion depuis l'espace client"
order: 1
---

**Dernière mise à jour le 28/02/2022**

## Objectif

Vous pouvez créer une sauvegarde unique d'une instance ou configurer un planning afin d'automatiser les sauvegardes de vos instances. Les sauvegardes peuvent être utilisées pour restaurer votre instance à un état antérieur ou pour créer une nouvelle instance identique.

**Ce guide explique comment créer des sauvegardes manuelles et automatiques d'une instance Public Cloud.**

## Prérequis

- Avoir une instance [Public Cloud](https://www.ovhcloud.com/en-gb/public-cloud/) dans votre compte OVHcloud.
- Être connecté à votre espace client [OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr)

## Instructions

### Créer une sauvegarde d'une instance

Connectez-vous à votre espace client [OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) et ouvrez votre projet `Public Cloud`{.action}. Cliquez ensuite sur `Instances`{.action} dans le menu de gauche.

Cliquez sur le bouton `...`{.action} à droite de l'instance et sélectionnez `Créer une sauvegarde`{.action}.

![public-cloud-instance-backup](images/createbackup1.png){.thumbnail}

Renseignez un nom pour la sauvegarde sur la page suivante. Prenez connaissance des informations tarifaires et cliquez sur `Confirmer`{.action}.

![public-cloud-instance-backup](images/createbackup2.png){.thumbnail}

Une fois la sauvegarde terminée, celle-ci sera disponible dans la section `Instance Backup`{.action} .

![public-cloud-instance-backup](images/createbackup3.png){.thumbnail}

### Créer une sauvegarde automatisée d’une instance

Cliquez sur le bouton `...`{.action} à droite de l'instance et sélectionnez `Créer une sauvegarde`{.action} automatique.

![public-cloud-instance-backup](images/createbackup4.png){.thumbnail}

Vous pourrez configurer les paramètres de sauvegarde suivants sur la page suivante :

#### **Le workflow** 

Actuellement, un seul workflow existe. Il créera une sauvegarde pour l'instance et son volume principal.

![public-cloud-instance-backup](images/createbackup5.png){.thumbnail}

#### **La ressource** 

Vous pouvez sélectionner l'instance à sauvegarder.

![public-cloud-instance-backup](images/createbackup6.png){.thumbnail}

#### **Le planning** 

Vous pouvez définir une planification de sauvegarde personnalisée ou choisir l'une des fréquences par défaut :

- Sauvegarde quotidienne avec rétention des 7 dernières sauvegardes
- Sauvegarde quotidienne avec rétention des 14 dernières sauvegardes

![public-cloud-instance-backup](images/createbackup7.png){.thumbnail}

#### **Le nom** 

Entrez un nom pour la planification de la sauvegarde automatique. Prenez connaissance des informations de tarification et créez le planning avec `Confirmer`{.action}.
 
![public-cloud-instance-backup](images/createbackup8.png){.thumbnail}

### Gestion des sauvegardes et des plannings

Les planifications peuvent être créées et supprimées dans la section Public Cloud `Workflow Management`{.action}.

![public-cloud-instance-backup](images/createbackup9.png){.thumbnail}

Les sauvegardes de vos instances sont gérées dans la section Public Cloud `Instance Backup`{.action}.

![public-cloud-instance-backup](images/createbackup10.png){.thumbnail}

Découvrez comment utiliser les sauvegardes pour cloner ou restaurer des instances dans [ce guide](https://docs.ovh.com/fr/public-cloud/creer-restaurer-un-serveur-virtuel-a-partir-dune-sauvegarde/).

## Aller plus loin

[Créer / restaurer un serveur virtuel a partir d’une sauvegarde](https://docs.ovh.com/fr/public-cloud/creer-restaurer-un-serveur-virtuel-a-partir-dune-sauvegarde/)

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
