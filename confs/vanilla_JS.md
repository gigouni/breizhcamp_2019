# 1. Vanilla JS

Par Mathieu Luz

<!-- TOC -->

- [1. Vanilla JS](#1-vanilla-js)
  - [1.1. Fight club / Les règles](#11-fight-club--les-règles)
  - [1.2. Notes](#12-notes)
  - [1.3. Ce dont on a besoin / envie](#13-ce-dont-on-a-besoin--envie)
  - [1.4. Les Web Components](#14-les-web-components)
  - [1.5. Virtual DOM](#15-virtual-dom)
  - [1.6. State management](#16-state-management)
  - [1.7. Web Assembly](#17-web-assembly)

<!-- /TOC -->

## 1.1. Fight club / Les règles

- Pas dfe code source extérieur
- Utiliser un maximum de nouvelles normes
- Il faut que cela fonctionne sur au moins 2 navigateurs

## 1.2. Notes

- Pas de Webpack, pas de typescript, pas de Babel
- Application démo: le jeu 2048
- Organismes de normalisation : IETF (spécifications HTTP), ECMA (spécifications JS), W3C (gestions de la globalité des normes du web comme HTML, CSS), WHATWG (quand il y a des "incohérences" dans les normes de W3C)

## 1.3. Ce dont on a besoin / envie

- Utiliser les dernières syntaxes JS
- Faire attention à la table des compatibilités des features
- Pas de BabelJS pour du Vanilla
- Voir le post de Jake Archibald : "ECMAScript modules in browsers" pour voir ce qui fonctionne et ce ne fonctionne pas dans les navigateurs
- Existe mais peu utilisé, à part pour des démos
  - Problèmes de performances à cause de chargements synchrones des librairies importées via "import"
  - Contré par l'utilisé de HTTP2
    - Un seul pipe pour un chargement de fichier, pas besoin d'instancier plus pipes = gain de temps
    - Utilisation de "HTTP2 push" pour dire de pousser au client les fichiers à charger avant même qu'il ne les demande

## 1.4. Les Web Components

- Utilisation de composants normalisés : les Web Components ( agrégation de 4 normalisations )
  - Balise template pour définir des contenus HTML à afficher plus tard
  - Custom elements
    - Définition de nouveaux éléments réutilisables, en utilisant le Shadow DOM
      - Attention à la compatibilité avec Edge ( réglé avec l'intégration de Chromium ? )
      - Le Shadow DOM ne cache pas l'HTML aux autres personnes via les Dev Tools mais vient scoper le CSS au sein du component
  - Les HTML imports vont être virés de la normalisation en Avril 2019
    - On ne peut plus intégrer des fichiers HTML au sein d'autres fichiers HTML
    - Conflit technique entre Chrome ( pour ) et Mozilla ( contre ) car les fichiers JS suffisent
- Cons
  - API trop verbeuse pour une utilisation sans surcouche
  - On en parle depuis longtemps mais le support officiel est encore très récent
- Pros
  - Le DOM devient votre propre framework :

## 1.5. Virtual DOM

- On a un état de DOM e, on veut arriver à un état e', le virtual DOM n'a besoin que des nouvelles positions dans le DOM des éléments
- Une chose récente et très complexe
- Mais des articles existent pour en créer un avec du Vanilla ( 2ality, Medium )
- C'est un élément incontournable des frameworks récents

## 1.6. State management

- Évite du store par les WebWorkers et l'utilisation de threads ( bonne compatibilité )
- Écoute les événements pour gérer les états des données

## 1.7. Web Assembly

- Web Assembly ( = Wasm ) est un format binaire capable de tourner sur une VM
- Wasm est prévu comme étant la cible pour une compilation
- Une implémentation générale par les navigateurs après des années de batailles
- Il y a une liste de langages gérés par le Web Assembly
- Par choix d'amusement, le speaker a pris Rust pour s'amuser et apprendre un nouveau langage
- Pas d'utilisation du bundle Web Assembly / Rust, mais utilisation de la CLI de Rust pour bundler un Wasm
- La classe Web Assembly permet de récupérer le fichier généré pour le faire
- Pour le wrapping, besoin de taper dans les zones mémoires ( C-like ) pour allouer ou désallouer des données en mémoire
- En terme de performances, cela n'apporte pas de vraie différences
  - Le code du Wasm est compilé, tout comme le code interprété par Node.js par exemple

Lien vers les sources : <https://github.com/Swiip/vanilla-modern-js>
