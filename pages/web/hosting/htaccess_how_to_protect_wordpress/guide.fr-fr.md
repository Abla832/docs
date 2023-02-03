---
title: 'Tutoriel - Utiliser le fichier htaccess avec WordPress'
slug: use-htaccess-with-wordpress
excerpt: 'Découvrez comment sécuriser votre blog WordPress avec un ou plusieurs fichiers htaccess'
section: 'Tutoriels'
order: 
---

**Dernière mise à jour le 13/01/2023**

## Objectif

Ce tutoriel vous explique comment configurer certaines fonctionnalités de votre hébergement web avec un ou plusieurs fichiers **.htaccess**. Notamment pour modifier les paramètres d'une partie ou de l'ensemble de votre site web (redirections, interdictions d'accès, autorisations restreintes, contrôle du cache, etc.).

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](https://partner.ovhcloud.com/fr/) ou [l'éditeur du CMS WordPress](https://wordpress.com/fr/support/){.external} si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section [« Aller plus loin »](#go-further) de ce guide.
>

**Découvrez comment sécuriser votre WordPress avec un ou plusieurs fichiers htaccess.**

## Prérequis

- Disposer d'un [hébergement web](https://www.ovhcloud.com/fr/web-hosting/) et avoir installé WordPress
- Être en capacité d'utiliser un client FTP tel que [FileZilla](https://filezilla-project.org/). Vous pouvez consulter notre guide «&nbsp;[Utiliser FileZilla pour récupérer et déposer vos données](https://docs.ovh.com/fr/dedicated/deposer-et-recuperer-donnees-via-sftp/#utiliser-filezilla-pour-recuperer-et-deposer-vos-donnees)&nbsp;».

## En pratique

Les fichiers **.htaccess** peuvent être créés et modifiés avec des éditeurs de texte comme&nbsp;: 

 - [Bloc-notes](https://support.microsoft.com/fr-fr/windows/aide-de-bloc-notes-windows-4d68c388-2ff2-0e7f-b706-35fb2ab88a8c){.external} de Windows;
 - [TextEdit](https://support.apple.com/fr-fr/guide/textedit/welcome/mac){.external} sur macOS; 
 - [Notepad++](https://notepad-plus-plus.org/){.external}.

### Quelques définitions

#### Qu'est-ce qu'un fichier **.htaccess** ?

Un fichier **.htaccess** permet de configurer un serveur web. Dans le cas d'un hébergement web mutualisé, il s'agit du serveur web open source «**Apache**». La syntaxe de ce fichier est définie par l'organisme qui édite et maintient **Apache**. Contrairement à la plupart des fichiers de configuration d'un serveur, les fichiers **.htaccess** sont situés dans les répertoires des sites web. Précisément dans l'espace de stockage FTP de votre hébergement web. Un fichier **.htaccess** aura des effets sur le répertoire dans lequel il est présent ainsi que dans tous les sous-répertoires présents à l'intérieur.

Nos offres d'hébergements mutualisés n'autorisent pas les fichiers de configuration serveur. Cependant, les fichiers **.htaccess** donnent la possibilité de modifier certaines caractéristiques et comportements. De plus, il n'est pas nécessaire de redémarrer le serveur **Apache** afin que les indications et modifications écrites dans le fichier **.htaccess** soient prises en compte. L'ensemble de nos offres d'[Hébergement web mutualisé OVHcloud](https://www.ovhcloud.com/fr/web-hosting/) permettent de configurer des fichiers  **.htaccess**.

Le point devant le nom du fichier **.htaccess** (qui n'a lui-même pas d'extension) désigne un fichier caché. De plus, ces fichiers ne sont pas accessibles par les utilisateurs extérieurs venant consulter votre site web.

#### Qu'est-ce qu'un serveur web ?

Un serveur web est un logiciel permettant l'échange des informations sur un réseau en utilisant le protocole *HTTP*.
Il en existe plusieurs, parmi lesquels *Apache*, *Nginx*, *Tomcat* ou encore le module http compris dans *NodeJS*.

### Créer un fichier .htaccess

#### Précautions à prendre

Une mauvaise configuration de votre fichier **.htaccess** peut générer des erreurs sur votre serveur (comme une erreur 500 : *Internal Server Error*), voire rendre totalement indisponible votre service, y compris pour vous. Prenez l'habitude de faire des sauvegardes systématiques des versions de vos fichiers fonctionnels, de manière à pouvoir revenir à un état antérieur en cas d'anomalie suite à une modification.

De la même façon, si vous n'avez pas l'habitude de manipuler ce type de fichier, faites un essai à chaque élément que vous modifiez. Vous éviterez ainsi de perdre du temps pour retrouver la ou les lignes à l'origine du dysfonctionnement de votre serveur web. Une erreur de configuration ou une uniquement une faute de frappe peut compromettre la configuration de votre serveur web et donc son fonctionnement.

#### Quels outils utiliser ?

- un client FTP pour récupérer vos fichiers (FileZilla, Cyberduck)
- un éditeur de texte.

### Où sont situés les fichiers .htaccess dans WordPress ?

Comme précisé en introduction, il est possible d'avoir plusieurs fichiers **.htaccess** sur un même hébergement web. Chacun de ces fichiers définissant les règles pour le répertoire où il se situe, ainsi que les sous-répertoires qu'il contient.

#### À la racine du site web

C'est à ce niveau que se fera la majorité des modifications. Installé par défaut, le fichier **.htaccess** placé à la racine du site contient les lignes suivantes&nbsp;:

```
# BEGIN WordPress
# Les directives (lignes) entre «&nbsp;BEGIN WordPress&nbsp;» et «&nbsp;END WordPress&nbsp;» sont générées
# dynamiquement, et doivent être modifiées uniquement via les filtres WordPress.
# Toute modification des directives situées entre ces marqueurs sera surchargée.

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress
```

**Explications du code ci-dessus**:

- **#** : caractère utilisé pour mettre une ligne en commentaire
- **RewriteEngine On** : active le module Apache `mod_rewrite`, permettant la réécriture d'URL à la volée (permet également de rediriger une URL vers une autre URL)
- **RewriteRule** : cette syntaxe s'écrit selon le schéma `RewriteRule Modèle Substitution`. L'écriture peut être présente plusieurs fois dans le fichier **.htaccess** (c'est le cas dans le fichier par défaut que vous trouvez à la racine de l'installation de votre WordPress). L'ordre d'écriture dans le fichier est primordial, soyez vigilant sur l'ordre dans lequel vous écrivez vos règles.
- **RewriteBase** : indique que la racine du site est `/`.
- **RewriteCond** : il s'agit de préconditions pour la règle qui suit directement. Dans notre cas, la première précondition exclut les URLs contenant un chemin vers un fichier réel, tandis que la deuxième exclut, elle, les sous-répertoires.

### Que puis-je rajouter dans un fichier **.htaccess** avec WordPress ?

Il existe plusieurs façons de définir et modifier les paramètres qui changeront le comportement du serveur avec, toutefois, certaines limitations en fonction de l'hébergement): 

- modifier les fichiers de configuration de votre serveur,
- ajouter ou modifier des directives dans le fichier de configuration **wp-config.php** à la racine de votre site web,
- modifier ou ajouter des directives dans le fichier **.htaccess** à la racine.

### Rediriger le protocole HTTP vers HTTPS

Pour rediriger toutes vos URLs du protocole HTTP vers HTTPS, il vous faudra générez votre certificat SSL depuis votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr):

![Activation du certificat SSL sur le manager cloud](images/htaccess_how_to_protect_wordpress%5B1%5D.png){.thumbnail}

Vous pouvez également consulter notre guide [« Passer son site internet en HTTPS grâce au SSL »](https://docs.ovh.com/fr/hosting/passer-site-internet-https-ssl/#etape-1-activer-le-certificat-ssl-sur-lhebergement).

### Empêcher l'affichage des répertoires et sous-répertoires

Pour éviter de permettre à l'ensemble des visiteurs de votre site web d'afficher le contenu des sous-répertoires (et accessoirement donner des informations à des pirates sur les thèmes ou extensions utilisés), bloquez la visualisation du contenu en ajoutant cette ligne dans votre fichier **.htaccess**:

```Options All -Indexes```

### Protéger votre fichier de configuration

Votre fichier **wp-config.php** présent à la racine de votre site web, contient des informations de configuration sensibles. Empêchez l'accès à ce fichier en ajoutant les  lignes suivantes dans votre fichier **.htaccess** :

```
<Files ~ "^.*\.([Hh][Tt][AaPp])">
    order allow,deny
    deny from all
    satisfy all
</Files>
```

Pour plus de détails sur le sujet, consultez notre guide sur la [« restriction d'accès par IP via le fichier .htaccess »](https://docs.ovh.com/fr/hosting/mutualise-htaccess-comment-bloquer-certaines-ip-au-niveau-de-mon-site/).

### Bloquer une adresse IP

Si vous avez identifié une adresse IP malveillante, voici la ligne à renseigner dans votre fichier **.htaccess**:

```
<Limit GET POST>
    order allow,deny deny from xxx.xxx.xxx.xxx
    allow from all
</Limit>
```

Où xxx.xxx.xxx.xxx désigne l'adresse IP à bloquer.

Pour plus de détails sur le sujet, consultez notre guide sur la [« restriction d'accès par IP via le fichier .htaccess »](https://docs.ovh.com/fr/hosting/mutualise-htaccess-comment-bloquer-certaines-ip-au-niveau-de-mon-site/).

#### Bloquer une adresse IP depuis le répertoire wp-admin (ou dans les autres répertoires)

C'est le répertoire permettant de vous connecter à votre interface d'administration (la méthode fonctionne également avec les autres répertoires, mais ils correspondent à des URLs qui n'aboutissent pas à une interface particulière). Pour protéger ce répertoire, autorisez spécifiquement l'accès à une ou plusieurs adresses IP à l'aide du code suivant à placer dans votre **.htaccess** :

```
<Limit GET POST PUT>
    order deny,allow deny from all
    allow from xxx.xxx.xxx.xxx
    allow from xxx.xxx.xxx.xxx
</Limit>
```

### Ce que vous devez retenir

- Gardez une version fonctionnelle de votre fichier **.htaccess** avant toute manipulation
- Si les modifications que vous avez faites provoquent une erreur, remplacez (via votre client FTP) le fichier **.htaccess** en ligne par la version précédente
- Vous pouvez gérer certains paramètres dans votre fichier **wp-config.php**
- Les fichiers **.htaccess** sont particulièrement efficaces pour la gestion des URLs, les redirections et la sécurité de votre site web.

## Aller plus loin

Consultez le [tutoriel disponible sur le site de la Fondation Apache](https://httpd.apache.org/docs/2.4/fr/howto/htaccess.html).


