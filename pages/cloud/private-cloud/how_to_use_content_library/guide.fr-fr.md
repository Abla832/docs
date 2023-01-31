---
title: Déployer un template OVF à travers les bibliothèques de contenu (content libraries)
slug: deploiement-template-ovh-content-library
excerpt: Découvrez comment déployer un template OVF à travers les bibliothèques de contenu (content library)
section: Gestion des machines virtuelles
order: 03
---

**Dernière mise à jour le 31 janvier 2023**
 
## Objectif

OVHcloud propose des templates OVF que vous pouvez déployer directement depuis votre vSphere *(version 7.0 ou ultérieure)* à travers les [bibliothèques de contenu *(content libraries)*](https://docs.vmware.com/fr/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-254B2CE8-20A8-43F0-90E8-3F6776C2C896.html){.external}.
Ce guide vous explique comment procéder pour déployer ces templates.
  
## Prérequis

- Avoir accès au client Web (HTML5)

## En pratique

### 1. Déployer un template d'une bibliothèque de contenu

#### Déployer un template depuis une bibliothèque de contenu

Vous pouvez trouver les bibiliothèques de contenu auxquelles votre vSphere est souscrit via la page d'acceuil de celui-ci, et en cliquant sur l'icône `Content libraries`{.action}.

![Content libraries button](images/Content%20library%20button.png){.thumbnail}

Il sera alors possible de cliquer sur l'une des bibliothèques pour en afficher le contenu, et déployer une nouvelle machine virtuelle depuis l'onglet `OVF & OVA Templates`{.action}.

![Content library overview](images/Content%20library%20overview.png){.thumbnail}


#### Déployer un template directement depuis la vue *Cluster*

Vous pouvez également déployer du contenu des bibliothèques directement depuis la vue *Cluster* en faisant un clic droit sur l'un de vos clusters et en sélectionnant `New Virtual Machine`{.action}.

![Cluster overview](images/Hosts%20view%20deploy.png){.thumbnail}

Sélectionnez alors l'option `Deploy from template`{.action}

![Deploy from template](images/Deploy%20from%20template.png){.thumbnail}

Il sera alors possible de cliquer sur l'un des templates offerts par les bibliothèques de contenu installées sur votre vSphere.

![Deploy from template overview](images/Deploy%20from%20template%20-%20content%20library%20overview.png){.thumbnail}

## 2. Configurer le template

Le processus de déploiement de template vous demandera de confirmer les détails, ansi qu'une destination pour la nouvelle machine virtuelle (datacenter, cluster, datastore, etc.).

![Template overview](images/Template%20overview.png){.thumbnail}

Certains templates acceptent des propriétés au déploiement qui permettent de configurer rapidement la nouvelle machine virtuelle, en créant par example un utiliseur privilégié ou en configurant l'interface de réseau principale.

![Template customization](images/Template%20customization.png){.thumbnail}

Les templates n'offrant pas de personnalisation auront les identifiants par défaut spécifiés dans les notes de la machine virtuelle.
  
## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
