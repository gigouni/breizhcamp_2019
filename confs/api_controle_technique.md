# 1. Votre API passe-t-elle le contrôle technique

Par François-Guillaume RIBREAU de OuestFrance

<!-- TOC -->

- [1. Votre API passe-t-elle le contrôle technique](#1-votre-api-passe-t-elle-le-contrôle-technique)
  - [1.1. Quick story](#11-quick-story)
  - [Contrôle technique](#contrôle-technique)

<!-- /TOC -->

## 1.1. Quick story

- Années 60 : API = librairies
- Années 80/90 : Début des requêtes sur des ressources distantes
- Années 2000 : API REST
- Années 2010 : API publics, etc...

## Contrôle technique

- Un contrôle technique : _"131 points de contrôle et 410 défaillances"_
- Cela amène l'utilisation de checklists pour réduire les risques ou compenser les limites de la mémoire humaine
- Sur une API, on peut arriver jusqu'à 70 pints de contrôles, divisés en  grandes catégories, dont ...
  - Mettre le plus de contraintes dès le début _"C'est en forgeant que l'on devient forgeron"_
  - Le nommage doit être ennuyeux pour avoir des choses les plus simples et les plus descriptives possibles
  - Tout limiter dans l'espace et dans le temps
    - Mettre des timeouts sur tous les appels
    - Implémenter des retries
    - Définir des circuits-breakers
  - Ne pas utiliser des `auto-increment` mais plutôt des __UUID__
    - Problème de sécurité car il suffira aux pirates de chercher les instances avec l'ID suivant ou précédant
    - Problème de performance
  - Faire une exposition des erreurs possibles pour répondre rapidement aux clients sur les façons de résoudre les problèmes
  - Exposer l'API sur de l'HTTPS
  - Les contenus des headers HTTP
    - Content-Security-Policy
    - Refuser de placer notre application dans des iframes
    - Ne pas accepter qu'Internet Explorer sniff les MIME-TYPE pour qu'il exécute les `.exe`
  - Être capable de lancer des tests directement sur la production ( "smoke tests" toutes les cinq minutes pour être proactif et ne pas attendre que le client détecte un problème pour essayer de le corriger = lancer des tests d'utilisation de mon application toutes les cinq minutes par exemple pour vérifier que tout fonctionne )
  - Être capable de définir une notion de quota d'utilisation de l'API
    - Cloisonne les utilisations faites de l'API
    - Business vision de l'API
  - Faire du blue/green deployment, pour rediriger les utilisateurs sur deux plateformes différentes pour tester les rendus en fonction des versions
    - A l'image de Kubernetes avec la mise à disposition de la version legacy pendant que la nouvelle version est en cours de déploiement
  - Monitoring sans alarming ne sert à rien
    - On ne veut pas avoir à aller directement sur un dashboard pour être alerter d'un problème
    - Le système doit prévenir de manière proactive de tous les problèmes qui arrivent
  - Générer une documentation ( la générer à partir du code, pas dans un PDF )
    - Déployer automatiquement toutes les documentations pour les avoir en permanence ( voir Dredd sur GitHub ?)
  - Supprimer les fingerprints des requêtes
  - Séparer l'état et la logique des données ( dans des stores immutables )
  - Faire du support multi-tenant
  - Les équipes doivent taper sur la production des produits des autres équipes
    - Quand on tape sur une API comme Twitter, on ne tape pas sur l'API de staging de Twitter mais bien sur la production
    - Le staging est une API privée, elle n'est pas censée être ouverte aux autres tant qu'elle n'est pas considérée "en production"
  - Comment se passe la sécurité ?
    - Y a-t-il un système de 0-Trust (IAM) ? Un système qui, même si le système est caché derrière un firewall, une DMZ, doit venir demander une authentification
  - Exposer les API avec des pages de status
    - Avec des reports de dégradations de service
    - Ajouter des fichiers de sécurité
      - Bug Bounty et exposition de `.well-known/security.txt` et `.well-known/dnt-policy.txt`
  - Versionnage des API
    - Via les Changelog
    - Définir des backward-compatibilités
      - Quand j'ajoute un champ sur ma v2, comment cela se passe si on tape sur l'API v1 ?
      - Twitter utilise __"Diffy"__ qui lance la même requête sur les différentes versions de l'API pour déterminer si il y a des différences et des breaking changes

Voir le contenu du site <https://getnobullshit.com/> pour trouver un ouvrage achetable et partageable, du développeur au CTO en passant par l'architecte.