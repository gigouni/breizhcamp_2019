# 1. Boostez le chargement de vos images

Par Jean-Michael Legait (@jmlegait) de CrossKnowledge

<!-- TOC -->

- [1. Boostez le chargement de vos images](#1-boostez-le-chargement-de-vos-images)
  - [1.1. Astuces](#11-astuces)
    - [1.1.1. Le format WebP](#111-le-format-webp)
    - [1.1.2. Les dimensions de l'image](#112-les-dimensions-de-limage)
    - [1.1.3. Le "lazy loading"](#113-le-lazy-loading)
    - [1.1.4. Le "progressive loading"](#114-le-progressive-loading)
    - [1.1.5. Le "progressive JPEG ( PJPEG )](#115-le-progressive-jpeg-pjpeg)

<!-- /TOC -->

"La moitié du poids d'une page web est constitué d'images"

## 1.1. Astuces

### 1.1.1. Le format WebP

- Réduit de 25 à 35% le poids des images
- Open source depuis 2010, par Google
- Utilisé en production par Youtube, Facebook, Netflix, Amazon, etc...
- Supporté par Chrome > v32, Edge > v18 et Firefox > v65 ( pas de support Safari ou Internet Explorer) = +/- 72% des utilisateurs
- Des images JPG et autres peuvent être converties en WEBP en CLI via des scripts _Node.js_ par exemple ou via des tasks _Gulp_
- Encapsuler les images dans des balises HTML `<picture ...>` et `<source ...>`
  - Balise `<picture ...>` : <https://developer.mozilla.org/fr/docs/Web/HTML/Element/picture>
  - Balise `<source ...>` : <https://developer.mozilla.org/fr/docs/Web/HTML/Element/Source>
- Utiliser _Lighthouse_ : donne des points d'optimisation pour les sites internet modernes comme pour les images

### 1.1.2. Les dimensions de l'image

- Utilisation des propriétés de balises HTML `srcset`, `sizes` et `src` pour adapter l'image chargée en fonction des dimensions des devices
- Adapter la taille de l'image et donc son poids au device cible

### 1.1.3. Le "lazy loading"

- Ne charger les images ou les contenus qu'au moment de la consultation par l'utilisateur
- Utilisation de la lib `lazysizes` par exemple
- Une option dans Google Chrome permet d'activer le lazy loading par défaut sur les sites internet ( expérimental )

### 1.1.4. Le "progressive loading"

- Avoir une grande image à charger ( 2Mb par exemple )
- Redimensionner l'image via un algorithme pour la rendre ultra légère et pixelisée ( 200 octets )
- Ajouter un effet de flou sur l'image pour ne pas voir directement les pixels mais être tout de même capable de distinguer les formes de l'image
- Envoyer cette première image au client
- En arrière-plan, charger l'image réelle et, via une transition CSS, l'afficher au client en taille réelle

### 1.1.5. Le "progressive JPEG ( PJPEG )

- Chargement de l'image en qualité faible, puis meilleure puis optimale au lieu de charger l'image ligne par ligne ( baseline JPEG )

[--> Retour au README](../README.md)
