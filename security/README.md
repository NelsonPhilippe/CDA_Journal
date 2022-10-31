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
   - [**Le CORS**](#cors_r)
   - [**Le CSP**](#csp_r)
   - [**Le SRI**](#sri_r)
   - [**HTTPS / TLS / HSTS**](#https_r)
   - [**Les failles XSS**](#xss_r)
   - [**WebStorage & IndexedDB**](#storage_r)
   - [**Les failles SQLI**](#sqli_r)
   - [**Sessions**](#sessions_r)
   - [**Tokens / UUID**](#tokens_r)
   - [**Password**](#password_r)
   - [**RBAC**](#rbac_r)
   - [**Confidentialité**](#confidentialite_r)
   - [**API Stateful & API Stateless**](#api_r)
   - [**Gestion de donnee envoyee et recupere**](#data_r)
   - [**Startegie de sauvegarde**](#backup_r)
   - [**Bug Bounty & Audit**](#bug_r)
   - [**Journalisation**](#journalisation_r)
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

> Cette stratégie de sécurité se base sur les recommendations de l'ANSII (American National Standards Institute) et OWASP (Open Web Application Security Project).
> Certaines explications sont aussi tirées du site Redhat.

### Les trois grands principes <a name="principes"></a>

- **Réduction de surface d'attaque** : Réduire au maximum la surface d'attaque pour exposer le moin de faille possible. 
- **Defense en profondeur** : Protéger le système et chaque sous service.
- **Moindres privilèges** : Donnée le moins de permission possible aux utilisateurs.

### Liste des recommendations <a name="recommendations"></a>

- **R1** : Mettre en œuvre TLS à l'état d'art
- **R2** : Mettre en œuvre HSTS

### Les CORS <a name="cors_r"></a>

En premiers lieux, il sera important de contourner la sécurité par défaut (SOP) du navigateur en utilisant le CORS (Cross-Origin Resource Sharing) pour permettre l'acces à des ressources d'origines différentes.
L'utilisation de CORS doit être suivie par un filtrage des resource externe utilisé par le site internet backend et front end.

Pourquoi est-il important d'utiliser CORS ?

La communication entre le back end et le front end ne pourrait pas être possible sans l'utilisation des CORS, le back et le front ne sera pas sur la même origin.
Il est aussi possible que lors du développement, d'autre resource soit utilisé.

C'est pour cela qu'une liste blanche doit être mise en place.

--- 

### CSP <a name="csp_r"></a>

La mise en place des CSP est aussi une obligation, celui-ci doit être mis en place pour limiter les ressources executable par le navigateur.
Aucun script externe ne doit pouvoir être chargé par celui-ci. Cela limitera la possibilité d'attaque XSS.

Il faut prendre en compte que la plus pars des Frameworks utilisés met en places cette sécurité par défaut.

---

### SRI <a name="sri_r"></a>

La mise en place de SRI n'aura probablement pas lieux d'être, celle-ci sera uniquement mis en place si lors de la création de l'application, celle ci se doit d'utiliser des librairies externes.
Cela nous permettra de vérifier l'authenticité des ressources et de limiter encore une fois la possibilité d'attaque XSS.

---

### HTTPS / TLS / HSTS <a name="https_r"></a>

Le HTTPS est une obligation, celui-ci permet de sécuriser la communication entre le client et le serveur.
Il est important de mettre en place un certificat SSL (TLS) valide pour sécuriser le trafique de donnée pour qu'il ne puisse être intercepté par un tiers.
La mise en œuvre du certificat SSL doit s'accompagner de l'utilisation de HSTS (HTTP Strict Transport Security) qui permet de forcer le navigateur à utiliser le HTTPS.

La mise en place de ces dispositifs empêche l'attaque la plus connue "Man in the middle (L'homme du milieu)".

> **Attention** : Une vulnérabilité est présente lors de la première connexion à la page web avec la mise en œuvre HSTS, pour combler cette faille, il est possible de mettre en place une liste préchargée (HSTS preload) pour le rendre accessible uniquement en HTTPS.

---

### XSS <a name="xss_r"></a>

Comment se protéger et réduire les failles XSS ?

Comme dit precedent, le CSP et le SRI participe à la réduction de possibilité d'attaque XSS, mais cela n'est pas suffisant, des règles de sécurités sur la façon de développé son application ont été mis en place.

Il est important d'isoler son composant lors du development de son application, par exemple, les iframes dans la plus pars des cas se doivent d'etre isole pour eviler toute fuite de donnee.

---

### WebStorage et IndexDB  <a name="storage_r"></a>

LocalStorage : Stockage persistent des donnees
SessionStorage : Stockage non persistent des donnees une fois l'onglet fermés.
Cookies : Stockage persistent des donnees

IndexDB : Stockage persistent des donnees

La difference entre le webStorage et IndexDB est la performance, le webStorage est utile pour stocker de petite quantite de donnees contrairement a l'indexDB aui lui va permettre l'indexion de grande quantitee de donnees structure.

Les cookies ne peuvent stocker que des chaines de caractères contrairement au localStorage aui lui permet de stocker different type de donnees.

---

### SQLI <a name="sqli_r"></a>

La mise en place d'une protection contre les attaques SQLI est une obligation, celle-ci permet de limiter les attaques SQLI.

---

### Session <a name="session_r"></a>

La mise en place d'une session est une obligation, celle-ci permet de limiter les attaques CSRF.

---

### Token / UUID <a name="token_r"></a>

La mise en place d'un token est une obligation, celui-ci permet de verifier l'authentification de l'utilisateur et ces authorizations.

L'UUID empêchera l'accès à des informations privées d'utilisateurs.
C'est une clé unique pour un utilisateur.

---

### Password <a name="password_r"></a>

Pour les mots de passe, une politique a été mis en place par l'ANSII pour sécuriser ces derniers, les mots de passe doivent contenir au moins 8 caractères, il ne doit pas être stocké en claire dans la base de données, c'est-à-dire qu'il doit subir un hashage puis un Salage avant d'être stocké.
La clé de salage de ne doit pas être connue par la publique. Il est fortement recommender de hasher le mot de passe en SHA256.

---

### RBAC <a name="rbac_r"></a>

L'api doit avoir le moin d'authorisation possible, il doit pouvoir execute que ce qu'il a besoin.
Par exemple, l'api ne doit pas pouvoir avoir un accès root à la base de données, si une faille est découverte, l'attaquant aurait un total contrôle sur la base de données.

L'utilisateur doit de même n'avoir qu'accès à la fonctionnalité utile, ne jamais faire confiance aux utilisateurs.

---

### Confidentialité <a name="confidentialite_r"></a>

La politique de confidentialité oblige l'application à prévenir les utilisateurs des données qui vont être stocker et utiliser, l'utilisateur doit aussi pouvoir modifier ou supprimer toute donnée le concernant.

---

### API Stateless & Stateful <a name="api_r"></a>


Pourquoi et comment utiliser et stocker un Token ?

Il est important de générer un JWT pour maintenir une connexion utilisateur, sans ce JWT, l'utilisateur doit de nouveau se connecter a chaques actions pour verifier son indentite.

Il est généré à partir d'une chaine de caractères et contient certaine donnee de l'utilisateur.

> **Attention** : Il ne faut pas stocker de donne confidentielle dans ce token.

Il y a plusieur solution pour stocker ce token ou d'utiliser ce Token, pour le stockage, il est recommender d'utiliser le IndexDB.

---

### Gestion de donnee envoyee et recupere <a name="data_r"></a>

Lors de l'envoie et la recuperation de donnee, il est important de traiter la donnee (Sanitization) pour eviter l'injection de code et de creer des failles.

---

#### Sanitization des donnees

> Un exemple de traitememt pour une protection contre les attaques XSS, creer une fonction d'echappememt permettant de supprimer le code javascript dans une chaine de charctere.

> Traitement de requete SQL, preparer une requete SQL avant de l'executer.

---

#### Fetch & XMLHttpRequest

Les fonctions Fetch et XMLHttpRequest permettent de créer des requètes HTTP vers une autre origin, celle-ci doit prévenir de potentielles attaques XSS.
Il est conseiller d'utiliser Fetch, celui-ci est plus flexible par l'utilisation des promises en Javascript.

L'utilisation de Fetch permettra d'éviter les attaques CSRF.

Option de la méthode fetch : 
   - no-cors
   - cors
   - same-origin


#### Les methodes

Lors de l'utilisation de requète HTTP, il est recommandé d'utiliser GET pour les données non confidentielles, il est aussi preferable d'utiliser PUT à POST, PUT permet l'utilisation d'un Preflight avec CORS.

Le preflight permet de ne pas envoyer de requête si il n'y a aucune réponse.

> **GET** : Uniquement des donnees publique. </br>
> **POST** : Pas de preflight CORS </br>
> **PUT** : Preflight CORS 

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