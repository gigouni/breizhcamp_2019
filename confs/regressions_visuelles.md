# 1. Les régressions visuelles

Par @jledentu - développeur web

<!-- TOC -->

- [1. Les régressions visuelles](#1-les-régressions-visuelles)
  - [1.1. Notes](#11-notes)
  - [1.2. Storybook](#12-storybook)
  - [1.3. Loki](#13-loki)
  - [1.4. Alternatives](#14-alternatives)

<!-- /TOC -->

## 1.1. Notes

- Un changement anodin dans le code qui crée une rupture/une perturbation de l'expérience utilisateur
- On ne peut pas faire de tests facilement sur tout
- Mais on peut faire des photos
  - Prendre une capture du résultat
  - Prendre une capture du résultat réel
  - Utiliser des comparateurs d'images pour comparer les deux images et trouver les perturbations

## 1.2. Storybook

- Permet d'afficher certains éléments graphiques dans différents états
- `npm install --save-dev storybook`
- Configurer via `.storybook/config.js`
- Découper par stories

## 1.3. Loki

- Utilise les images du storybook comme images de références et va effectuer des tests de non régressions visuelles
- `npm install --save-dev loki`
- `npx init loki`
- `npx init update`
- `npx init test`
- `npx init approve`
- Attention aux faux positifs, il faut jouer avec un seuil de tolérance
- Attention aux performances, accélérer en changeant le `diffingEngine` ( `gm` pour GraphicsMagick )
- Gérer les timeouts et l'asynchronisme avec `lokiAsync` ( pour les animations, pour les GIFs, etc... )
- Avantages
  - Pas ou peu de maintenance si il y a déjà un storybook
  - Débogage via le storybook et les fichiers de différence
- Limitations
  - Pas de scripting
  - Chrome / émulateurs iOS et Android uniquement

## 1.4. Alternatives

- jest-image-snapshot
- cypress-image-snapshot
- BackstopJS
