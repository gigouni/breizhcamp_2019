# 1. Micro frontend, the micro-services puzzle extended to frontend

<!-- TOC -->

- [1. Micro frontend, the micro-services puzzle extended to frontend](#1-micro-frontend-the-micro-services-puzzle-extended-to-frontend)
  - [1.1. Remise en contexte](#11-remise-en-contexte)
  - [1.2. Next step](#12-next-step)
  - [1.3. Un cas d'exemple plus concret chez Saagie](#13-un-cas-dexemple-plus-concret-chez-saagie)
  - [1.4. Best practices & tips](#14-best-practices--tips)

<!-- /TOC -->

Par Audrey Neveu, Saagie, dev fullstack

## 1.1. Remise en contexte

- Évolution des architectures des applications, du monolith vers des services
- Quand on travaillait sur un monolith, on avait une équipe, plus maintenant : Front / Back, etc...
  - Evolution des façons de travailler pour se mettre en "micro team"
- Diviser en micro team apporte des avantages : spécialisation, choix de la stack technique, rapidité de développement
- Si toutes les parties backend se divisent, pourquoi ne pas diviser le frontend ?

## 1.2. Next step

- FrontEnd micro-services = agrégation de composants avec des logiques métiers communes
- Chaque partie d'une application peut être travaillée par une équipe dédiée ( barre de recherche travaillée par l'équipe dédiée à la barre de recherche, etc... )
- Pourquoi ne pas permettre à chaque équipe front d'utiliser, pour les composants, les technologies qu'elles veulent ?
  - Équipe plus petite, dédiée, spécialisée
  - Liberté des choix techniques
  - Autonomie dans le développement
  - Autonomie dans le cycle de livraisons des fonctionnalités

## 1.3. Un cas d'exemple plus concret chez Saagie

- Applications existantes
  - L'application "Manager" utilisait en 2015 AngularJS
  - L'application "Governance" utilisait en 2017 Angular
  - L'application "Operations" utilisait en 2017 VueJS
- Besoin de réorganisation de leurs équipes suite à des besoins clients en changement
- Utilité de passer en micro frontend si il y a un besoin d'homogénéisation des applications
- Intégration de toutes ces applications dans une même plateforme, avec intégration via encapsulation des applications sous forme de Web components
  - Compatibilité quasi-totale pour les web components, sauf pour Edge mais cela va se régler tout seul d'ici l'intégration du moteur Chromium
  - __Avantages__
    - Experience utilisateur consistante, pas de débordement d'interface d'une application à l'autre
    - Possibilité d'afficher plusieurs composants sur la même page
    - Déploiement indépendant
  - __Inconvénients__
    - Ce n'est pas une SPA, donc à chaque changement de composant principal, la page et les données se rechargeaient ( lourd / "hard navigation" )
    - Mauvaises performances
    - Grande dépendance sur les différentes versions de librairies utilisées
    - Plusieurs applications avec un système de routing spécifique, intégrées dans chaque composant, basées sur des hash de path
    - Besoin de faire tourner toute la stack en local
  - Utilisation d'une nouvelle façon
    - Utilisation de _Layout-as-lib_, une librairie JS qui charge les composants
    - En fonction des droits de chaque utilisateur, la lib parente va charger les contenus et les composants appropriés
      - Plus rapide
      - Plus facile à intégrer
      - Mais des incohérences dans l'expérience utilisateur (si une autre équipe met à jour des composants communs mais pas une autre application, des éléments vont être incohérents)

## 1.4. Best practices & tips

- Penser au use case d'abord : est-ce que je suis sur une agrégation de composants ou une agrégation de SPA ?
- Penser au design : faire en sorte d'avoir une réponse plus rapide voire erronée ( dans la plupart des cas, la demande se passera bien donc on part du principe quelle s'est bien passé. Si ce n'est pas le cas, on rétropédale et on avertit l'utilisateur)
- Partager des ressources, des composants
- Resources
  - Micro-frontends.org <https://github.com/neuland/micro-frontends>
  - Experiences Using Micro Frontends at IKEA
  - Project Mosaic ( Zalando ) <https://www.mosaic9.org>
  - Single SPA JS <https://single-spa-js.org>

[--> Retour au README](../README.md)
