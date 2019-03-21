# 1. Vanilla JS

Par Mathieu Luz de Zenika

<!-- TOC -->

- [1. Vanilla JS](#1-vanilla-js)
  - [1.1. Fight club / Les règles](#11-fight-club--les-règles)
  - [1.2. Notes](#12-notes)
  - [1.3. Ce dont on a envie / besoin](#13-ce-dont-on-a-envie--besoin)
    - [1.3.1. Les envies](#131-les-envies)
    - [1.3.2. Les besoins](#132-les-besoins)
  - [1.4. Les Web Components](#14-les-web-components)
  - [1.5. Virtual DOM](#15-virtual-dom)
  - [1.6. Les avantages et inconvénients](#16-les-avantages-et-inconvénients)
  - [1.7. State management](#17-state-management)
  - [1.8. Web Assembly](#18-web-assembly)

<!-- /TOC -->

## 1.1. Fight club / Les règles

- Pas de code source extérieur
- Utiliser un maximum de nouvelles normes
- Il faut que cela fonctionne sur au moins 2 navigateurs

## 1.2. Notes

- Pas de Webpack, pas de Typescript, pas de BabelJS
- Application démo : le jeu 2048
- Organismes de normalisation : IETF ( spécifications HTTP ), ECMA ( spécifications JS ), W3C ( gestions de la globalité des normes du web comme HTML, CSS ), WHATWG ( quand il y a des "incohérences" dans les normes de W3C )

## 1.3. Ce dont on a envie / besoin

### 1.3.1. Les envies

- Utiliser les dernières syntaxes JS
- Pas de BabelJS pour du Vanilla

### 1.3.2. Les besoins

- Faire attention à la table des compatibilités des features
- Voir le post de Jake Archibald : "ECMAScript modules in browsers" pour voir ce qui fonctionne et ce ne fonctionne pas dans les navigateurs
- Existe mais peu utilisé, à part pour des démos
  - Problèmes de performances à cause de chargements synchrones des librairies importées via "import"
  - Contré par l'utilisé de HTTP2
    - Un seul pipe pour un chargement de fichier, pas besoin d'instancier plus pipes = gain de temps
    - Utilisation de "HTTP2 push" pour dire de pousser au client les fichiers à charger avant même qu'il ne les demande

## 1.4. Les Web Components

- Utilisation de composants normalisés : les Web Components ( agrégation de 4 normalisations )
  - _Balise template_
    - Définition des contenus HTML à afficher plus tard
  - _Custom elements_
    - Définition de nouveaux éléments réutilisables, en utilisant le Shadow DOM
      - Attention à la compatibilité avec Edge ( réglé avec l'intégration de Chromium ? )
  - _Le Shadow DOM_
    - Ne cache pas l'HTML aux autres personnes via les Dev Tools mais vient scoper le CSS au sein du component
  - _Les HTML imports_ vont être virés de la normalisation en Avril 2019
    - On ne peut plus intégrer des fichiers HTML au sein d'autres fichiers HTML
    - Conflit technique entre Chrome ( pour ) et Mozilla ( contre ) car les fichiers JS suffisent

## 1.5. Virtual DOM

- On a un état de DOM _e_, on veut arriver à un état _e'_, le virtual DOM n'a besoin que des nouvelles positions dans le DOM des éléments
- C'est un élément incontournable des frameworks récents
- Une chose récente et très complexe à implémenter soit-même
- Mais des articles existent pour en créer un avec du Vanilla ( [2ality](http://2ality.com/2014/07/jsx-template-strings.html), [Medium](https://medium.com/@deathmood/how-to-write-your-own-virtual-dom-ee74acc13060) )

## 1.6. Les avantages et inconvénients

- Cons
  - API trop verbeuse pour une utilisation sans surcouche ( frameworks, etc ... )
  - On en parle depuis longtemps mais le support officiel est encore très récent ( Février / Mars 2019 )
- Pros
  - Le DOM devient votre propre framework :tada:

## 1.7. State management

- Évite le store en passant par les [WebWorkers](https://developer.mozilla.org/fr/docs/Web/API/Web_Workers_API/Utilisation_des_web_workers) et l'utilisation de threads ( bonne compatibilité )
- Écoute les événements pour gérer les états des données

## 1.8. Web Assembly

- [Web Assembly](https://webassembly.org/) ( ou __Wasm__ ) est _"un format binaire capable de tourner sur une VM de navigateur"_
- Wasm est prévu comme étant le résultat d'une compilation
- Une implémentation générale par les navigateurs après des années de batailles
- Il y a une [liste de langages](https://github.com/appcypher/awesome-wasm-langs) gérés par le Web Assembly
- Par choix d'amusement, le speaker a pris Rust pour s'amuser et apprendre un nouveau langage
- Pas d'utilisation du bundle [Web Assembly / Rust](https://rustwasm.github.io/), mais utilisation de la CLI de Rust pour bundler un Wasm
- La classe Web Assembly permet de récupérer le fichier généré pour le faire
- Pour le wrapping, besoin de taper dans les zones mémoires ( C-like ) pour allouer ou désallouer des données en mémoire
- En terme de performances, cela n'apporte pas de vraies différences entre une version compilée Wasm et Node.js
  - Le code du Wasm est compilé, tout comme le code interprété par Node.js par le moteur V8 par exemple

Lien vers les sources : <https://github.com/Swiip/vanilla-modern-js>

[--> Retour au README](../README.md)
