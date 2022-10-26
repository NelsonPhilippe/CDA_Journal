# Secutiré côté navigateur

## Table des matières

1. [**Definition**](#definition)
    - [**Origin**](#origin)
    - [**SOP** (Same Origin Policy)](#sop)
    - [**CORS** (Cross-Origin Resource Sharing)](#cors)
    - [**CSP** (Content Security Policy)](#csp)
    - [**SRI** (Subresource Integrity)](#sri)
    - [**CSRF** (Cross-Site Request Forgery)](#csrf)
    - [**XSS** (Cross-Site Scripting)](#xss)
    - [**SQLI** (SQL Injection)](#sqli)
2. [**Stratégie de sécurité**](#strategie)
   - [**CORS**](#cors)
---


## 1. Definition <a name="definition"></a>

### Origin <a name="origin"></a>

L'origin définis le nom de domaine de la page sur laquelle on se trouve

Exemple : 

    - https://www.google.com (origin = google.com)
    - https://www.google.com/search?q=hello (origin = google.com)

### - SOP (Same Origin Policy) <a name="sop"></a>

La SOP (Same Origin Policy) est une poilitique de sécurisation des données, c'est une fonction par défaut du navigateur permattant de limiter l'acces au resource à la même Origin.

### - CORS (Cross-Origin Resource Sharing) <a name="cors"></a>

Les CORS (Cross-Origin Resource Sharing) est une fonctionnalité qui permet de définir des règles d'acces à des ressources d'origines différentes.

### - CSP (Content Security Policy) <a name="csp"></a>

Les CSP (Content Security Policy) est une fonctionnalité qui permet de définir des règles les resources accessible ou executable par un navigateur, ce qui ne se trouve pas dans cette liste ne pourra être executé.

### - SRI (Subresource Integrity) <a name="sri"></a>

Le SRI (Subresource Integrity) est une fonctionnalité qui permet de vérifier l'intégrité des ressources chargées par le navigateur.

### - CSRF (Cross-Site Request Forgery) <a name="csrf"></a>

Le CSRF (Cross-Site Request Forgery) est une classe d'attaque permettant d'injecter du code à l'insu de l'utilisateur authentifié.

### - XSS (Cross-Site Scripting) <a name="xss"></a>

Le XSS (Cross-Site Scripting) est une attaque permettant d'injecter du code à l'insu de l'utilisateur.

### - SQLI (SQL Injection) <a name="sqli"></a>

Le SQLI (SQL Injection) est une attaque permettant d'injecter du code SQL lors d'une requête SQL.

## 2. Stratégie de sécurité <a name="strategie"></a>

### Liste des recommendations

- **R1** : Mettre en œuvre TLS à l'état d'art
- **R2** : Mettre en œuvre HSTS

### CORS

En premiers lieux, il sera important de contourner la sécurité par défaut (SOP) du navigateur en utilisant le CORS (Cross-Origin Resource Sharing) pour permettre l'acces à des ressources d'origines différentes.
L'utilisation de CORS doit être suivie par un filtrage des resource externe utilisé par le site internet backend et front end.

Pourquoi est-il important d'utiliser CORS ?

La communication entre le back end et le front end ne pourrait pas être possible sans l'utilisation du CORS, le back et le front ne sera pas sur la même origin.
Il est aussi possible que lors du développement, d'autre resource soit utilisé.

C'est pour cela qu'une liste blanche doit être mise en place.


### CSP

La mise en place des CSP est aussi une obligation, celui-ci doit être mis en place pour limiter les ressources executable par le navigateur.
Aucun script externe ne doit pouvoir être chargé par celui-ci. Cela limitera la possibilité d'attaque XSS.

Il faut prendre en compte que la plus pars des Frameworks utilisés met en places cette sécurité par défaut.

### SRI

La mise en place de SRI n'aura probablement pas lieux d'être, celle-ci sera uniquement mis en place si lors de la création de l'application, celle ci se doit d'utiliser des librairies externes.
Cela nous permettra de vérifier l'authenticité des ressources et de limiter encore une fois la possibilité d'attaque XSS.

### HTTPS / TLS / HSTS

Le HTTPS est une obligation, celui-ci permet de sécuriser la communication entre le client et le serveur.
Il est important de mettre en place un certificat SSL (TLS) valide pour sécuriser le trafique de donnée pour qu'il ne puisse être intercepté par un tiers. 
La mise en œuvre du certificat SSL s'accompagne de l'utilisation de HSTS (HTTP Strict Transport Security) qui permet de forcer le navigateur à utiliser le HTTPS.

**Attention** : Une faille est présente lors de la première connexion à la page web avec la mise en œuvre HSTS, pour combler cette faille, il est possible de mettre en place une liste préchargée (HSTS preload) pour le rendre accessible uniquement en HTTPS.





