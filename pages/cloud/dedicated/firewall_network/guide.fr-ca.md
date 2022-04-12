---
title: 'Configurer le Firewall Network'
slug: firewall-network
excerpt: 'Découvrez comment configurer votre Firewall Network'
section: 'Réseau & IP'
---

**Dernière mise à jour le 23/12/2021**

## Objectif

Pour protéger son infrastructure globale et les serveurs de ses clients, OVHcloud propose un pare-feu paramétrable et intégré à la solution **Anti-DDoS** : le Firewall Network. Cette option vous permet de limiter l'exposition de votre service aux attaques provenant du réseau public.

**Ce guide vous explique comment configurer votre Firewall Network.**


> [!primary]
>
> Pour plus d'informations sur notre solution Anti-DDoS, cliquez ici : <https://www.ovh.com/ca/fr/anti-ddos/>.
> 

![Le VAC en détail](images/vac-inside.png){.thumbnail}


## Prérequis

- Posséder un service OVHcloud bénéficiant d’un Firewall Network ([ serveur dédié](https://www.ovh.com/ca/fr/serveurs_dedies/){.external}, [ VPS](https://www.ovh.com/ca/fr/vps/){.external},[ instance Public Cloud](https://www.ovh.com/ca/fr/public-cloud/){.external}, [Private Cloud](https://www.ovh.com/ca/fr/cloud-prive){.externalP}, [IP fail-over](https://www.ovh.com/ca/fr/serveurs_dedies/ip_failover.xml){.external}, etc.)
- Avoir accès à votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}.

> [!warning]
> Cette fonctionnalité peut être indisponible ou limitée sur les [serveurs dédiés **Eco**](https://eco.ovhcloud.com/fr-ca/about/).
>
> Consultez notre [comparatif](https://eco.ovhcloud.com/fr-ca/compare/) pour plus d’informations.

## En pratique

### Activer le Firewall Network

> [!primary]
>
> Le Firewall Network protège les adresses IP associées à une machine. Vous devez donc configurer chaque adresse IP indépendamment. Une configuration globale du serveur est impossible.
> 

Connectez-vous à[ l’espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external} et accédez à la section `Bare Metal Cloud`{.action}. Ensuite, ouvrez la section `IP`{.action} et cliquez sur `...`{.action} pour activer le pare-feu sur une adresse IPv4.

![Activation du Firewall Network](images/firewall_creation2022.png){.thumbnail}

Vous serez alors invité à confirmer votre action.

![Confirmation](images/creationvalid.png){.thumbnail}

Cliquez ensuite sur ` Activer le firewall`{.action} (1), puis sur ` Configurer le firewall`{.action} (2) pour commencer le paramétrage.

![Activation de la configuration](images/activationconfig.png){.thumbnail}

Vous pouvez configurer jusqu'à **20 règles par adresse IP**.

> [!warning]
>
> Le pare-feu s’active automatiquement à chaque attaque DDoS et ne peut pas être désactivé avant la fin de l'attaque. C'est pourquoi il est important de maintenir à jour les règles de pare-feu.
> Par défaut, vous n’avez pas de règles configurées. Toutes les connexions peuvent donc être établies.
> Si vous en possédez, nous vous recommandons de les vérifier régulièrement, même si le pare-feu est désactivé.
> 


> [!primary]
>
> - La fragmentation UDP est bloquée (DROP) par défaut. Lorsque vous activez le Firewall Network, n'oubliez pas de configurer correctement votre unité de transmission maximale (<i>Maximum Transmission Unit</i> ou MTU) si vous utilisez un VPN. Par exemple, sur OpenVPN, vous pouvez cocher `MTU test`{.action} .
> - Le Firewall Network n'est pas pris en compte au sein du réseau OVHcloud. Par conséquent, les règles configurées n'affectent pas les connexions de ce réseau interne.
>


### Configurer le Firewall Network

Pour ajouter une règle, cliquez sur ` Ajouter une règle`{.action}.

![Ajouter une règle](images/ajoutregle1.png){.thumbnail}

Pour chaque règle, vous devez choisir :
- une priorité (de 0 à 19, 0 étant la première règle à appliquer) ;
- une action (`Autoriser`{.action} ou ` Refuser`{.action}) ;
- le protocole ;
- une adresse IP (facultatif) ;
- le port source (TCP uniquement) ;
- le port de destination (TCP uniquement) ;
- les options TCP (TCP uniquement).

![Détails sur l'ajout d'une règle](images/ajoutregle4.png){.thumbnail}


> [!primary]
>
> - Priorité 0 : nous vous conseillons d'autoriser le protocole TCP sur toutes les adresses IP avec une option `établie`{.action}. Celle-ci vous permet de vérifier que le paquet fait partie d'une session précédemment ouverte (déjà initiée). Si vous ne l'autorisez pas, le serveur ne recevra pas les retours du protocole TCP des requêtes SYN/ACK.
> - Priorité 19 : nous vous conseillons de refuser tout trafic de protocole IPv4 qui n'a été accepté par aucune règle antérieure.
> 

### Exemple de configuration

Pour vous assurer que seuls les ports SSH (22), HTTP (80), HTTPS (443) et UDP (10 000) restent ouverts lors de l'autorisation de l'ICMP, suivez les règles ci-dessous :

![Exemple de configuration](images/exemple.png){.thumbnail}

Les règles sont triées de 0 (la première règle lue) à 19 (la dernière). La chaîne cesse d'être analysée dès qu'une règle est appliquée au paquet reçu.

Par exemple, un paquet pour le port 80/TCP sera capturé par la règle 2 et les règles qui suivent ne seront pas appliquées. Un paquet pour le port 25/TCP ne sera attrapé qu'à la dernière règle (19) qui le bloquera, car le pare-feu n'autorise pas la communication sur le port 25 dans les règles précédentes.

> [!warning]
>
> Si notre solution anti-DDoS limite une attaque, votre Firewall Network sera activé, même si vous l'avez désactivé par défaut. Si vous souhaitez le désactiver, n'oubliez pas de supprimer vos règles.
> 

### Configurer le pare-feu Armor (Firewall Game)

> [!primary]
> Par défaut, le pare-feu Armor est préconfiguré avec certaines règles qu'OVHcloud a déterminé fonctionner avec les jeux les plus courants. Cependant, pour les clients disposant d’un serveur dédié Game, nous vous permettons d’aller plus loin et de configurer également des règles pour les ports.
>

Afin de configurer les règles de vos ports sur Armor, vous devez d'abord vous connecter à votre espace client OVHcloud.<br>
Ensuite, rendez-vous dans le menu `Bare Metal Cloud`{.action} et cliquez sur la section `IP`{.action} dans la barre latérale de gauche. Cliquez sur `...`{.action} à côté de l'adresse IP de votre serveur de jeu puis sur `Configurer le firewall game`{.action}.

![Game_wall](images/GAMEwall2021.png){.thumbnail}

Sur l’écran suivant, cliquez sur le bouton `Ajouter une règle`{.action} pour ajouter une règle à Armor.

![Configure_Armor](images/ConfigureArmor2021.png){.thumbnail}

Activez les ports selon vos besoins sur l'écran suivant et cliquez sur le bouton `Confirmer`{.action} lorsque vous avez fini d'ajouter vos règles. Le pare-feu Armor a maintenant été configuré avec succès.

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
