# 1. Règles UX : les formulaires

Par Bruno Sabot de Zenika Bordeaux (@brunosabot)

<!-- TOC -->

- [1. Règles UX : les formulaires](#1-règles-ux--les-formulaires)
  - [1.1. Les mots de passe](#11-les-mots-de-passe)
  - [1.2. Les captcha](#12-les-captcha)
  - [1.3. La validation](#13-la-validation)
  - [1.4. Liste de champs](#14-liste-de-champs)
  - [1.5. Les boutons](#15-les-boutons)
  - [1.6. Quoi d'autre](#16-quoi-dautre)
    - [1.6.1. Les labels](#161-les-labels)
    - [1.6.2. Le mobile](#162-le-mobile)
    - [1.6.3. Divers](#163-divers)

<!-- /TOC -->

## 1.1. Les mots de passe

- Beaucoup de contraintes pour le rendre plus robuste
- Beaucoup TROP de contraintes
- Ne pas demander de taper deux fois le même mot de passe
- Avoir un bouton pour afficher le mot de passe
- Avoir un indicateur de robustesse ( des librairies existent )
- Ne pas bloquer les caractères spéciaux, ou certains caractères

## 1.2. Les captcha

- Plus le captcha est compliqué plus je suis sûr que je ne suis pas un robot
- Utiliser plutôt un système anti-spam comme Akismet

## 1.3. La validation

- J'aimerais savoir très vite si je me suis trompé dans mon champ
- Attendre d'avoir au moins fait une tentative dans le champ avant de lever une alarme
- Supprimer l'erreur dès la reprise du focus sur le champ
- Mettre un marqueur pour dire que le champ est valide
- Prendre en compte toutes les manières de saisir ( téléphone en +33 ou en 06 )

## 1.4. Liste de champs

- Des formulaires trop longs pour afficher tous les champs à remplir, trop de scroll
- Découper en plusieurs étapes pour rassurer l'utilisateur si la validation par étape de ses informations
- Éviter de faire plusieurs champs pour la même chose
- Avoir un indicateur de progression si c'est un formulaire en plusieurs étapes pour ne pas perdre l'utilisateur
- S'assurer que tous les champs soient nécessaires ( "Est-ce que cette information est vraiment utile ?" )

## 1.5. Les boutons

- Trop de boutons tuent l'interface
- Ne pas nommer le bouton "Envoyer" mais "Créer le compte"
- Ne pas mettre de bouton "Reset" sur les formulaires, personne ne les utilise
- Notifier que le bouton ait bien été appuyé ( griser le bouton mais ne pas surcharger l'interface ou ne pas laisser le bouton tel quel pour éviter le multi-requête )

## 1.6. Quoi d'autre

### 1.6.1. Les labels

- Mettre un label, pas un placeholder, ce n'est pas son objectif
- Ne pas mettre de label en majuscule ( plus facile à lire pour l'oeil humain )
- Mettre les labels au dessus des champs et collé pour avoir un regard uniquement descendant
- Être proche de l'utilisateur ( "Votre nom" plutôt que "Nom" )

### 1.6.2. Le mobile

- Utiliser le bon type pour les champs ( type number pour les champs attendant que des chiffres )
- Un champ doit au moins faire 48px de haut ou de large à cause de la largeur des doigts
- Éviter les select lorsqu'il y a peu de champs ( privilégier les radio boxes )

### 1.6.3. Divers

- Formater correctement les données ( téléphone, CB, ... )
- Optionnel pour les facultatifs plutôt que * pour les obligatoires ( pour éviter d'y voir une contrainte dans le formulaire )
- Mettre les messages d'erreurs sous le champ associé, pas tout en dessous et avec une description précise du problème
- Le placeholder n'a lieu que pour des indications, pas pour faire office de labels ou de valeur
- Toujours faire l'usage de votre application pour en voir tous les problèmes