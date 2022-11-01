# Stratégie de sécurité

--- 

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
    - [**RBAC** (Role-Based Access Control)](#rbac)
2. [**Stratégie de sécurité**](#strategie)
   - [**Les trois grands principes**](#principes)
   - [**Liste des recommendations**](#recommendations)
   - [**La sécurité inter-domaines**](#inter-domaines_r)
   - [**Les classes et failles de sécurités**](#classes)
   - [**Authenticité des ressources**](#authenticite_r)
   - [**Sécurisation du trafic de données**](#securisation_r)
   - [**Le stockage de données côté client**](#stockage_r)
   - [**Authentification**](#auth_r)
   - [**La RGPD**](#rgpd_r)
   - [**Sécurisation de l'API**](#api_r)
   - [**Stratégie de sauvegarde**](#backup_r)
   - [**Bug Bounty et Audit**](#bug_r)
   - [**Journalisation**](#journalisation_r)
---

## 1. Definition <a name="definition"></a>

### Origin <a name="origin"></a>

L'origin défini le nom de domaine de la page sur laquelle on se trouve

Exemple : 

    - https://www.google.com (origin = google.com)
    - https://www.google.com/search?q=hello (origin = google.com)

### - SOP (Same Origin Policy) <a name="sop"></a>

Le SOP (Same Origin Policy) est une politique de même Origin, c'est une fonction par défaut du navigateur permettant de limiter l'accès au resources de l'Origin.
Le SOP permet d'envoyer des requêtes HTTP mais ne permet pas de recevoir de réponse si celle-ci ne provient pas de la même Origin.
Si le SOP n'est pas contourné, aucune origine ne peut communiquer avec celle-ci.

### - CORS (Cross-Origin Resource Sharing) <a name="cors"></a>

Les CORS (Cross-Origin Resource Sharing) partage de ressources entre différentes origin, est une fonctionnalité qui permet de contourner le SOP, celui-ci va permettre la communication entre les différentes origin.

### - CSP (Content Security Policy) <a name="csp"></a>

Les CSP (Content Security Policy) est une fonctionnalité qui permet de définir des règles des ressources executable par un navigateur, ce qui ne se trouve pas dans cette liste ne pourra être exécuté.

### - SRI (Subresource Integrity) <a name="sri"></a>

Le SRI (Subresource Integrity) est une fonctionnalité qui permet de vérifier l'intégrité des ressources chargées par le navigateur via un hash de la ressource en question.

### - CSRF (Cross-Site Request Forgery) <a name="csrf"></a>

Le CSRF (Cross-Site Request Forgery) est une classe d'attaque permettant d'injecter du code à l'insu de l'utilisateur authentifié.
Ces attaques visent à usurper l'identité de l'utilisateur et à exécuter des actions à son nom.

### - XSS (Cross-Site Scripting) <a name="xss"></a>

Le XSS (Cross-Site Scripting) est une attaque permettant d'injecter du code à l'insu de l'utilisateur.
Ces attaques visent à prendre le contrôle de l'application, ou d'exécuter des actions à l'insu de l'utilisateur.

### - SQLI (SQL Injection) <a name="sqli"></a>

Le SQLI (SQL Injection) est une attaque permettant d'injecter du code SQL lors de l'exécution d'une requête SQL.

## 2. Stratégie de sécurité <a name="strategie"></a>

> Cette stratégie de sécurité se base sur les recommendations de l'ANSII (American National Standards Institute) et OWASP (Open Web Application Security Project).
> Certaines explications sont aussi tirées du site Redhat.

### Les trois grands principes <a name="principes"></a>

- **Réduction de surface d'attaque** : Réduire au maximum la surface d'attaque pour exposer le moin de faille possible. 
- **Defense en profondeur** : Protéger le système et chaque sous service.
- **Moindres privilèges** : Donnée le moins de permission possible aux utilisateurs.

### Liste des recommendations <a name="recommendations"></a>

#### Recommendations pour la mise en œuvre d'un site web

- **R1** : Mettre en œuvre TLS à l'état d'art
- **R2** : Mettre en œuvre HSTS
- **R3** : Surveiller les CT logs
- **R4** : Utiliser l'API DOM à bon escient
- **R7** : Vérifier l'échappement des contenus inclus
- **R8** : Vérifier la conformité des ressources inclus
- **R9** : Proscrire l'usage de la fonction eval()
- **R10** : Proscrire l'usage de constructions basées sur l'évaluation du code.
- **R11** : Contrôler l'intégrité des contenus internes.
- **R12** : Contrôler l'intégrité des contenus tiers.
- **R13** : Restreindre les contenus aux ressources fiables.
- **R14** : Mettre en œuvre CSP par en-tête HTTP.
- **R15** : Interdire les contenus __inline__.
- **R16** : Définir la directive __default-src__.
- **R17** : Utiliser CSP contre le clickjacking.
- **R20** : Réduire l'impacte des requêtes silencieuses via CSP.
- **R23** : Ne pas stocker des informations sensibles dans les bases de données locales.
- **R24** : Ne pas stocker des informations sensibles dans les bases de données IndexDB.
- **R25** : Proscrire l'usage de l'API Web SQL Database.
- **R26** : Ne pas stocker d'informations sensibles dans les cookies.
- **R27** : Cloisonner les sessions aux moyens de nom de domaine distincts.
- **R29** : Maîtriser l'accès aux cookies en Javascript.
- **R31** : Limiter le transit des cookies aux flux sécurisés.
- **R32** : Définir une stratégie stricte d'envoi des cookies en cross-site.
- **R33** : Définir une stratégie stricte d'envoi des cookies de session en cross-site.
- **R35** : Choisir une API selon la méthode HTTP.
- **R36+** : Utiliser XHR avec la méthode PUT.
- **R37** : Compléter la mise en œuvre de XHR par une configuration CSP.
- **R38** : Protéger les appels XHR par un contrôle anti-CSRF.
- **R39** : Mettre en œuvre un preflight lors des appels CORS.
- **R40** : Vérifier la valeur de l'Origin lors de la réception d'une requête CORS.
- **R41** : Cloisonner les services web au moyen de noms de domaine distincts.
- **R42** : Eviter l'usage de bibliothèques publiques effectuant des appels CORS.
- **R44** : Préférer l'utilisation de l'API Fetch à XMLHttpRequest.

### La sécurité inter-domaine <a name="inter-domaines_r"></a>

#### CORS

En premiers lieux, il sera important de contourner la sécurité par défaut (SOP) du navigateur en utilisant le CORS (Cross-Origin Resource Sharing) pour permettre l'accès à des ressources d'origines différentes.
L'utilisation de CORS doit être suivie par un filtrage des resources externes utilisé par le site internet backend et front end.

Pourquoi est-il important d'utiliser CORS ?

La communication entre le back end et le front end ne pourrait être possible sans l'utilisation des CORS, le back et le front ne sera probablement pas sur la même origin.
Il est aussi possible que lors du développement, d'autre resource soit utilisé.

C'est pour cela qu'une liste blanche doit être mise en place.

---

### Les classes et failles de sécurités <a name="classes"></a>

#### CSRF

Comment se protéger des failles CSRF ?

Il est possible de se protéger des failles CSRF en utilisant un token CSRF, ce token est généré par le serveur et envoyé au client lors de la connexion.
Ce token est ensuite utilisé pour valider les requêtes POST, PUT, DELETE, etc.


#### XSS

Comment se protéger et réduire les failles XSS ?

Comme dit precedent, le CSP et le SRI participe à la réduction de possibilité d'attaque XSS, mais cela n'est pas suffisant, des règles de sécurités sur la façon de développé son application ont été mis en place.

Il est important d'isoler ses composants lors du development de son application, par exemple, les iframes dans la plupart des cas doivent être isolée pour éviter toutes fuites de données.

#### SQLI

La mise en place d'une protection contre les attaques SQLI est une obligation. Il est possible de se protéger en utilisant des ORM (Object Relational Mapping).

> Une ORM permet de simuler une base de données orienté objet, elle permet de définir des correspondence entre les schémas de la base de données et les classes du programme. </br>
> L'exécution des requêtes SQL est alors gérée par l'ORM, ce qui permet de se protéger des attaques SQLI.

---

### Authenticité des ressources <a name="authenticite_r"></a>

#### CSP

La mise en place des CSP est aussi une obligation, celui-ci doit être mis en place pour limiter les ressources executable par le navigateur.
Aucun script externe ne doit pouvoir être chargé par celui-ci. Cela limitera la possibilité d'attaques XSS et CSRF.

Le CSP doit aussi être mis en place lors de l'utilisation de requête XHR, il permettra de limiter les risques d'exfiltrations de données si l'attaquant parvient à remplacer les XHR par des appels CORS valides. 

Cette option est configurée par défaut par la plus pars des Frameworks.

#### SRI

La mise en place de SRI n'aura probablement pas lieux d'être, celle-ci sera uniquement mise en place si elle doit utiliser des librairies externes.
Cela nous permettra de vérifier l'authenticité des ressources et de limiter possibilité d'attaque XSS.

---

### Sécurisation du trafic de données <a name="securisation_r"></a>

#### HTTPS / TLS / HSTS

Le HTTPS est une obligation, celui-ci permet de sécuriser la communication entre le client et le serveur.
Il est important de mettre en place un certificat SSL (TLS) valide pour sécuriser le trafique de données pour qu'il ne puisse être intercepté par un tiers.
La mise en œuvre du certificat SSL doit s'accompagner de l'utilisation de HSTS (HTTP Strict Transport Security) qui permet de forcer le navigateur à utiliser le HTTPS.

La mise en place de ces dispositifs empêche l'attaque la plus connue "Man in the middle (L'homme du milieu)".

> **Attention** : Une vulnérabilité est présente lors de la première connexion à la page web avec la mise en œuvre HSTS, pour combler cette faille, il est possible de mettre en place une liste préchargée (HSTS preload) pour le rendre accessible uniquement en HTTPS.


#### Sanitization des données

La sanitization permet la validation des données entrantes et sortantes, cela permet de s'assurer que les données sont bien de type attendu et qu'elles ne contiennent pas de tentative d'injection de code.

> Par exemple pour éviter les attaques XSS, créer une fonction d'échappement permettant de supprimer le code javascript dans une chaine de caractère.

> Pour traiter une requête SQL il faut la preparer avant de l'exécuter. La préparation permet de vérifier que les données sont bien de type attendu et de les échapper si nécessaire.


#### Fetch & XMLHttpRequest

Les fonctions Fetch et XMLHttpRequest permettent de créer des requètes HTTP vers une autre origin, celle-ci doit prévenir de potentielles attaques XSS.
Il est conseiller d'utiliser Fetch, celui-ci est plus flexible par l'utilisation des promises en Javascript.

L'utilisation de Fetch permettra d'éviter les attaques CSRF.

Option de la méthode fetch :
- no-cors
- cors
- same-origin

##### Les méthodes

Lors de l'utilisation de requête HTTP, il est recommandé d'utiliser GET pour les données non confidentielles, il est aussi preferable d'utiliser PUT à POST, PUT permet l'utilisation d'un Preflight avec CORS.

Le preflight permet de ne pas envoyer de requête s'il n'y a aucune réponse.

> **GET** : Uniquement des donnees publique. </br>
> **POST** : Pas de preflight CORS </br>
> **PUT** : Preflight CORS

---

### Le stockage de données côté client <a name="storage_r"></a>

#### WebStorage et IndexDB 

LocalStorage : Stockage persistent des donnees
SessionStorage : Stockage non persistent des donnees une fois l'onglet fermés.
Cookies : Stockage persistent des donnees

IndexDB : Stockage persistent des donnees

La difference entre le webStorage et IndexDB est la performance, le webStorage est utile pour stocker de petites quantités de données contrairement à l'indexDB qui lui va permettre l'indexation de grandes quantités de données structure.

Les cookies ne peuvent stocker que des chaines de caractères contrairement au localStorage qui lui permet de stocker different type de donnees.

#### Token / UUID

La mise en place d'un token est une obligation, celui-ci permet de verifier l'authentification de l'utilisateur et ces authorizations.

L'UUID empêchera l'accès à des informations privées d'utilisateurs, il doit remplacer l'indexation de la base de données par défaut. Cette clé est unique par utilisateur.

---

### Authentification <a name="auth_r"></a>

#### Password 

Pour les mots de passe, une politique a été mis en place par l'ANSII pour sécuriser ces derniers, les mots de passe doivent contenir au moins 8 caractères, il ne doit pas être stocké en claire dans la base de données, c'est-à-dire qu'il doit subir un hashage puis un Salage avant d'être stocké.
La clé de salage de ne doit pas être connue par la publique. Il est fortement recommender de hasher le mot de passe en SHA256.

#### Session

La mise en place d'une session est une obligation, celle-ci permet de limiter les attaques CSRF en premiers lieux.
La session peut être stockée côté client ou côté serveur, il est important de limiter l'expiration de la session pour éviter les attaques de type session fixation.

Il est recommandé de diviser la clé et de la stocker dans deux endroits différents, par exemple dans les cookies et dans le localStorage.

La clé de session doit être unique et aléatoire, elle doit être générée par un générateur de nombres aléatoires cryptographique. Par exemple un token JWT (JSON WEB TOKEN).

> JWT peut aussi encoder certaines informations, par exemple le rôle de l'utilisateur, il est donc possible de vérifier l'authentification de l'utilisateur et ses permissions en une seule requête. </br>
> Il est important d'encoder des données non sensibles dans le token, car il est possible de le déchiffrer si la clé de chiffrage est découverte. </br>
> Il est aussi possible de définir une date d'expiration. </br>

---

### RGPD <a name="rgpd_r"></a>

#### Consentement 

L'utilisateur doit donner son consentement pour que ses données soient utilisées, il doit être informé de l'utilisation de ses données et de la manière dont elles seront utilisées.

#### Confidentialité 

La politique de confidentialité oblige l'application à prévenir les utilisateurs des données qui vont être stocké et utilisé, l'utilisateur doit aussi pouvoir modifier ou supprimer toute donnée le concernant.

---

### Sécurisation de l'API <a name="api_r"></a>

#### RBAC

L'api doit avoir le moin d'authorisation possible, il doit pouvoir execute que ce qu'il a besoin.
Par exemple, l'api ne doit pas pouvoir avoir un accès root à la base de données, si une faille est découverte, l'attaquant aurait un total contrôle sur la base de données.

L'utilisateur doit de même n'avoir qu'accès aux fonctionnalités utile, ne jamais faire confiance aux utilisateurs.


#### API Stateless & Stateful

Une API Stateless est une API qui ne conserve pas d'état, elle ne conserve pas les informations de l'utilisateur, elle ne conserve que les informations de la requête.

Une API Stateful est une API qui conserve l'état des données précédentes, elle est affectée par les requêtes précédentes.

> Le choix des types d'API dépend de la nature de l'application, une API Stateless est plus sécurisé, mais elle est plus difficile à mettre en place. </br>
> Une API Stateful est plus facile à mettre en place, mais elle est moins sécurisée. </br>

---

### Stratégie de sauvegarde <a name="backup_r"></a>

Il est important de sauvegarder de façon récurrente les données de l'application, il faut les sauvegarder sur un serveur distant, par exemple sur github dans un repo privé ou sur un autre serveur.

---

### Bug Bounty et Audit <a name="bug_r"></a>

Le bug bounty permet de trouver des failles dans l'application, il est important de faire appel à des professionnels pour trouver des failles dans l'application.

L'audit de code permet d'avoir une vision globale de l'application, il permet de trouver des failles dans le code.

Il faut mettre en place ces deux procédés pour avoir une application sécurisée.

---

### journalisation <a name="journalisation_r"></a>

La Journalisation est le traçage continue des actions effectué sur l'application et sur les différents serveurs.
Cela permet une traçabilité des actions si un problème survient.