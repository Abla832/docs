---
title: Capacités et limites techniques
slug: occ-limits
excerpt: 'Découvrez les capacités et limites techniques de l offre OVHcloud Connect'
section: Ressources techniques
order: 1
---

**Dernière mise à jour 07/092020**

## Objectif

**Découvrez les capacités et limitations techniques de l'offre OVHcloud Connect.**

## En pratique

### Capacités de la connexion

* 1000Base-LX/LH pour 1Gb
* 10GBase-LR pour 10Gb
* Jumbo Frame: jusqu'à 9000 bytes
* Auto-négociation non supportée

### Fonctionnalités non supportées

#### Mode Layer 2

* CoS avec 802.1p
* DCBX et protocoles apparentés (802.1Qbb, 
802.1Qaz, 802.1Qau)
* TRILL, SPF et FabricPath
* FCoE
* Spannning-tree
* IGMP et Multicast
* EtherChannel, PaGP pour l'aggrégation de liens

#### Mode Layer-3

* Tout mécanisme de qualité de service
* Tag 802.1q
* Multi-VRF
* eBGP Multi-Hop
* iBGP
* Routage statique sur EntryPoint/POP

### Fonctionnalités prochainement disponibles

* IPv6

### Problèmes connus

Les problèmes suivants sont présents sur OVHcloud Connect.

| Problème | Détail | Cause | Contournement | Sites impactés |
|:--------:|:------:|:-----:|:-------------:|:--------------:|
| Routes du EndPoint/DC non propagées jusqu'au EntryPoint/POP | En utilisant l'AS65501, les routes annoncées en BGP depuis le vRack ne remontent pas | Configuration OVHcloud interne | Ne pas utiliser AS65501 | ALL |
| ECMP non fonctionnel | Quand ECMP est activé sur un même POP par le client, les flux en sortie sont mal répartis | Limitation | Diviser les annonces pour répartir le trafic | Tous les POP |
| Lumière en réception mais absence de lien | L'équipement échoue à activer le lien malgré des valeurs optiques en réception correctes | L'auto-négociation est configurée | Désactiver l'auto-négociation | Tous les POP |

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>
