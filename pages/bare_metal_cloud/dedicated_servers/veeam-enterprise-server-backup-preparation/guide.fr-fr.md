---
title: Préparer une sauvegarde de serveur Bare Metal avec Veeam Enterprise
excerpt: Découvrez comment préparer la sauvegarde de votre serveur Bare Metal à l'aide de Veeam Backup and Replication (Enterprise)
updated: 2024-03-07
---

## Objectif

Ce guide vous détaille comment préparer la sauvegarde de votre serveur Bare Metal avec Veeam Backup and Replication (Enterprise).

## Prérequis

- Un [serveur Bare Metal OVHcloud](https://www.ovhcloud.com/fr/bare-metal/)
- Une solution de sauvegarde [Veeam Enterprise](https://www.ovhcloud.com/fr/storage-solutions/veeam-enterprise/)
- Un service [OVHcloud Standard S3 Object Storage](https://www.ovhcloud.com/fr/public-cloud/object-storage/) (facultatif)

## En pratique

### Installation de votre serveur dédié

Votre serveur Bare Metal OVHcloud doit être installé et configuré.

Consultez nos [guides de premiers pas pour les serveurs dédiés](/products/bare-metal-cloud-dedicated-servers-getting-started).

### Mise en place de votre serveur de backup Veeam Enterprise

Téléchargez, installez et créez une licence pour votre serveur de sauvegarde Veeam Enterprise à l'aide de notre guide « [Installer Veeam Backup & Replication](/pages/storage_and_backup/backup_and_aster_recovery_solutions/veeam/veeam_backup_replication) ».

### Mise en place de l’Object Storage

La création et la configuration de l’Object Storage peuvent être effectuées dans la section `Public Cloud`{.action} de l’[espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).

Si vous n'avez pas encore de projet Public Cloud dans votre compte OVHcloud, consultez notre guide [Créer votre premier projet Public Cloud](/pages/public_cloud/compute/create_a_public_cloud_project).

[Créez un conteneur Object Storage](/pages/storage_and_backup/object_storage/s3_create_bucket) grâce à l’une des solutions **API S3 d’OVHcloud (Standard ou High Performance)**. La solution Standard est recommandée car notre cas d'usage (effectuer une sauvegarde) ne nécessite généralement pas de stockage High Performance.

Donnez à l'utilisateur S3 des droits sur le conteneur en copiant-collant le code ci-dessous dans un fichier JSON.

```json
{
  "Statement":[
    {
      "Action":
         [
             "s3:GetObject",
             "s3:PutObject",
             "s3:DeleteObject",
             "s3:ListBucket",
             "s3:ListMultipartUploadParts",
             "s3:ListBucketMultipartUploads",
             "s3:AbortMultipartUpload",
             "s3:GetBucketLocation"
          ],
      "Effect":"Allow",
      "Resource":
          [
              "arn:aws:s3:::<container name>",
              "arn:aws:s3::: :::<container name>/*"
          ],
      "Sid":"RWContainer"
     }
  ]
}
```

Veillez à remplacer `container name` par le nom réel de votre conteneur Object Storage.

Dans l’[espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr), sélectionnez `Public Cloud`{.action} puis `Object Storage`{.action} dans la section `Storage` . Cliquez sur le bouton Plus d'options `...`{.action} à droite de l'utilisateur S3 et choisissez `Importer S3 Policy (JSON)`{.action}.

Sélectionnez le fichier JSON que vous venez de modifier et cliquez sur `Importer`{.action}.

![Object Storage - Utilisateur S3 - Import JSON](images/backup-Preparation-01.png){.thumbnail}

### Configuration du repository S3 dans Veeam Enterprise

Depuis l'application Veeam, sélectionnez `Backup Infrastructure`{.action}, `Backup Repositories`{.action} et `Add Repository`{.action}.

![Veeam - ajouter un référentiel](images/backup-Preparation-02.png){.thumbnail}

Sélectionnez `Object storage`{.action} comme type de dépôt.

![Veeam - Object Storage](images/backup-Preparation-03.png){.thumbnail}

Sélectionnez `S3 Compatible`{.action}.

![Veeam - compatible S3](images/backup-Preparation-04.png){.thumbnail}

Attribuez un **Nom** au nouveau référentiel et cliquez sur `Next`{.action}.

![Veeam - nom du dépôt](images/backup-Preparation-05.png){.thumbnail}

Renseignez les informations **Service point** (Endpoint) et **Region** de votre service de stockage S3.

> Vous pouvez retrouver ces informations dans la section `Public Cloud`{.action} de votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).
> Cliquez sur `Object Storage`{.action} puis cliquez sur le bouton `...`{.action} à droite de votre conteneur et cliquez sur `Voir les objets`{.action}.
>
> ![Object storage - display objects](images/backup-Preparation-06.png){.thumbnail}
>
> ![Object storage - endpoint](images/backup-Preparation-07.png){.thumbnail}

![Veeam - service endpoint and region](images/backup-Preparation-08.png){.thumbnail}

Cliquez sur `Add`{.action} pour entrer vos informations d'identification. Entrez votre **Access key** et votre **Secret key**, puis cliquez sur `OK`{.action}.

> Ces informations sont disponibles dans votre espace client OVHcloud sous l'onglet `Utilisateurs S3`{.action} . La **clé d'accès** (Access key) est visible sur la page principale. 
> La **Clé secrète** (Secret key) se trouve en cliquant sur le bouton `...`{.action} et en sélectionnant `Voir la clé secrète`{.action}. 
>
> ![Object storage - keys](images/backup-Preparation-09.png){.thumbnail}

![Veeam - keys](images/backup-Preparation-10.png){.thumbnail}

Cliquez sur `Browse...`{.action} pour sélectionner le **Bucket**.

![Veeam - bucket](images/backup-Preparation-11.png){.thumbnail}

Sélectionnez le bucket et cliquez sur `OK`{.action}.

![Veeam - bucket](images/backup-Preparation-12.png){.thumbnail}

Cliquez sur `Browse...`{.action} pour sélectionner le **Dossier** (Folder).

![Veeam - folder](images/backup-Preparation-13.png){.thumbnail}

Cliquez sur `New Folder`{.action}, entrez un nom pour le dossier, sélectionnez-le, puis cliquez sur `OK`{.action}.

![Veeam - folder](images/backup-Preparation-14.png){.thumbnail}

A l'étape de montage du serveur, cliquez sur `Next`{.action}.

![Veeam - Mount Server](images/backup-Preparation-15.png){.thumbnail}

Sur l'écran de récapitulatif, cliquez sur `Apply`{.action}.

![Veeam - review](images/backup-Preparation-16.png){.thumbnail}

Une fois les processus exécutés avec succès, cliquez sur `Next`{.action}.

![Veeam - process end](images/backup-Preparation-17.png){.thumbnail}

Passez en revue la page de résumé et cliquez sur `Finish`{.action}.

![Veeam - summary](images/backup-Preparation-18.png){.thumbnail}

Les dépôts de sauvegarde doivent maintenant ressembler à ceci :

![Veeam - dépôts](images/backup-Preparation-19.png){.thumbnail}

Vous pouvez à présent effectuer une sauvegarde avec Veeam Enterprise. Consultez notre guide dédié : [Sauvegarder un serveur Bare Metal avec Veeam Enterprise](/pages/bare_metal_cloud/dedicated_servers/veeam-enterprise-server-backup)

## Aller plus loin

Échangez avec notre communauté d’utilisateurs sur <https://community.ovh.com/>.