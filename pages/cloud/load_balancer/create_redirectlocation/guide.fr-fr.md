---
title: Configuration d'un service OVHcloud Load Balancer  avec les redirections
slug: redirect-location
universe: cloud
excerpt: Intégrez vos services web derrière un Load Balancer avec les Redirections
section: Configuration
---

**Dernière mise à jour le à 07/02/2022**

## Objectif

Le service OVHcloud Load Balancer agit par défault comme un mandataire ou "Proxy". Il peut aussi être configuré pour rediriger vos clients vers un site tiers dans le cas d'un changement de nom de domaine ou pour rediriger vos clients en HTTPS par exemple. C'est que l'on appelle la redirection HTTP.


## Prérequis

- Posséder une offre [OVHcloud Load balancer](https://www.ovh.com/fr/solutions/load-balancer/) dans votre compte OVHcloud.
- Être connecté à votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr).
- Être connecté à votreà l'[API OVH](https://api.ovh.com/){.external}.


## En pratique

### Présentation

Une redirection HTTP se présente ainsi :


```bash
HTTP/1.1 301 Moved Permanently
Location: http://www.example.org/
Content-Type: text/html
Content-Length: 174
```

Les Redirections personnalisées doivent être de la forme `<scheme>://<net_loc>/<path>;<params>?<query>#<fragment>`. Il n'est possible de spécifier qu'une seule Redirection par Frontend.

Les Redirections personnalisées peuvent être spécifiées via le Manager et via l'API, tant sur un nouveau `Frontend`{.action} qu'un existant.

### Ajouter une redirection personnalisée depuis l'espace client OVHcloud

Il est possible de définir une redirection personnalisée depuis l'[espace client](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external} dans la partie `Cloud`{.action}, section `Load Balancer`{.action}.
Cela peut-être effectué tant sur un nouveau Frontend pendant sa création, que sur un Frontend existant.

* Ajout d'un nouveau Frontend

Dans la section `Frontends`{.action} de votre Manager, cliquez sur le bouton `Ajouter un frontend`{.action} pour en créer un nouveau.

Dans la page d'édition d'un frontend, sélectionnez le protocole `HTTP`{.action} ou `HTTPS`{.action}.
Configurez les informations normalement.
Il est cependant inutile de préciser la `Ferme par défaut`{.action}, celle-ci ne sera pas utilisée.

Dans les paramètres avancés, renseignez la `Redirection HTTP`{.action}.

* Édition d'un Frontend existant

Dans la section `Frontends`{.action} de votre Manager, sélectionnez le frontend que vous souhaitez éditer.
Pour ce faire, cliquez que le bouton `...`{.action} et sélectionnez `Modifier`{.action} dans le menu apparu.
Assurez vous que le frontend choisi soit bien de  protocole `HTTP` ou `HTTPS`.

Dans la page d'édition du frontend, complétez la configuration du si besoin.
Il est cependant inutile de préciser la `Ferme par défaut`{.action}, celle-ci ne sera pas utilisée.

Dans les paramètres avancés, renseignez la `Redirection HTTP`{.action}.


![Configuration d'une Redirection d'un Frontend](images/add_redirectlocation.png){.thumbnail}

Une fois le frontend configuré, cliquez sur `Ajouter`{.action} ou `Modifier`{.action} selon que vous configuriez un nouveau frontend, ou un frontend existant.
N'oubliez pas de déployer la configuration.
Pour ce faire, vous pouvez au choix :

- dans la section `Statut`{.action} de la page d'accueil du Manager,
cliquez sur le bouton `...`{.action} de votre Load Balancer,
et sélectionnez `Appliquer la configuration`{.action} ;

- dans le bandeau de rappel du Manager vous précisant que la configuration n'est pas appliquée,
cliquez sur `Appliquer la configuration`{.action}.

![Application d'une Configuration d'un Load Balancer](images/apply_configuration.png){.thumbnail}


### Ajouter une redirection personnalisée depuis l'API OVHcloud

Dans l'[API OVH](https://api.ovh.com/){.external}, les Redirections sont spécifiées dans la chaîne de caractère redirectLocation :

* création d'un nouveau Frontend

> [!api]
>
> @api {POST} /ipLoadbalancing/{serviceName}/http/frontend
> 

|Paramètre|Signification|
|---|---|
|serviceName|Identifiant de votre service Load Balancer|
|port|Port(s) d'écoute du frontend|
|zone|Zone de déploiement du frontend|
|redirectLocation|URL de redirection HTTP|

* mise à jour d'un Frontend existant

> [!api]
>
> @api {PUT} /ipLoadbalancing/{serviceName}/http/frontend/{frontendId}
> 

|Paramètre|Signification|
|---|---|
|serviceName|Identifiant de votre service Load Balancer|
|frontendId|Identifiant du frontend à metter à jour|
|redirectLocation|URL de redirection HTTP|

Puis appliquer les modifications :


> [!api]
>
> @api {POST} /ipLoadbalancing/{serviceName}/refresh
>

|Paramètre|Signification|
|---|---|
|serviceName|Identifiant de votre service Load Balancer|
|zone|Zone de déploiement du frontend|


## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
