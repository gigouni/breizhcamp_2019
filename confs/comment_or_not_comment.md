# 1. Comment... or not comment

Par Pascal Le Merrer (@pascallemerrer)

Lien vers les slides : <https://github.com/PascalLeMerrer/comment-or-not-comment>

<!-- TOC -->

- [1. Comment... or not comment](#1-comment-or-not-comment)
  - [1.1. Pourquoi commenter](#11-pourquoi-commenter)
  - [1.2. Commentaires utiles](#12-commentaires-utiles)
  - [1.3. Les commentaires inutiles](#13-les-commentaires-inutiles)
  - [1.4. Conclusion](#14-conclusion)

<!-- /TOC -->

## 1.1. Pourquoi commenter

- Faciliter la lecture du code par le lecteur
- "Code never lies, documentations sometimes does", Ron Jeffries
- "Writing system software: code comment", Salvatore Sanfilippo ( @antirez ), développeur chez Redis
  - Salvatore Sanfilippo définit [6 types de commentaires utiles](#12-commentaires-utiles) et [3 inutiles](#13-les-commentaires-inutiles)

## 1.2. Commentaires utiles

- __Commentaire de fonction__
  - Une majorité des personnes présentes commentent leurs fonctions
  - Le speaker considère que cela n'est pas toujours nécessaire, le nom de la fonction est la plupart du temps largement suffisant
- __Commentaire de conception__
  - Explique les solutions envisagées et celles retenues et pourquoi
- __Commentaire de raison__
  - Explique pourquoi cette fonction fait cela ( pas "comment ?" mais bien "pourquoi ?" )
- __Commentaire d'enseignement__
  - Donne les bases théoriques nécessaires à la compréhension de ce que fait le code
    - Rappelle des bases de géométries pour des fonctions de géolocalisation par exemple
    - Une minorité des personnes est d'accord
    - La majorité pense qu'un lien vers une doc suffit
- __Commentaire de checklist__
  - Prévient le prochain développeur des différentes étapes à suivre en cas de modifications sur la fonction courante
    - Peut faire penser à un problème de conception si il est nécessaire de faire ce genre de choses
- __Commentaire de guidage__
  - Chaque section du code est précédée par un petit commentaire pour expliquer ce qui va se passer
  - Le speaker est contre ce genre de choses, il préfère faire des sous-fonctions avec des noms équivoques

## 1.3. Les commentaires inutiles

- __Commentaire trivial__
  - Les commentaires plus long à lire qu'à lire le code
- __Commentaire de dettes techniques__
  - `TODO`, `FIXME`, etc...
    - Le speaker n'est pas contre, à condition qu'on prenne le temps, ultérieurement, de __vraiment__ le faire
  - Commentaire pour prévenir qu'il s'agit d'un hack
- __Commentaire de sauvegarde__
  - Commenter du code au cas où on pourrait en avoir besoin plus tard
    - Il suffit d'utiliser le système de versioning...

## 1.4. Conclusion

- Les commentaires ne sont pas la chose importante, à retenir
- L'important se situe sur la façon de communiquer avec son équipe

[--> Retour au README](../README.md)
