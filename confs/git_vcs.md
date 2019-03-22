# 1. Git, yet another VCS ou bien plus que ça

Par Loïc Guibert - Architecte logiciel à Eizhel SAS

<!-- TOC -->

- [1. Git, yet another VCS ou bien plus que ça](#1-git-yet-another-vcs-ou-bien-plus-que-ça)
  - [1.1. Dictionnaire](#11-dictionnaire)
  - [1.2. Les commandes classiques](#12-les-commandes-classiques)
  - [1.3. Les commandes plus évoluées / complexes](#13-les-commandes-plus-évoluées-complexes)

<!-- /TOC -->

Retrouvez la liste complète des commandes et des tutoriels sur la documentation en ligne : <https://git-scm.com/doc>

## 1.1. Dictionnaire

- Valider = Commiter
- Serveur de versioning distant = Le repository Git[Hub|Lab]
- Changements = Toutes modifications intervenues sur 0..n éléments du répertoire
- Statut de la branche distante = État de _origin_

## 1.2. Les commandes classiques

- `git add`
  - Pour ajouter les changements courant sur un fichier dans la liste des modifications à valider ( `git add *` )
  - Lien vers la documentation : <https://git-scm.com/docs/git-add>

- `git commit`
  - Valider les changements locaux et les envoyer sur le serveur de versioning distant en précisant le message de commit ( `git commit -m "<commit-message>"` )
  - Valider _tous_ les changements sans avoir eu à les ajouter au préalable avec `git add` ( `git commit -am "<commit-message>"` )
  - Lien vers la documentation : <https://git-scm.com/docs/git-commit>

- `git checkout`
  - Pour créer ( `git checkout -b <branch-name>` ) une branche ou se déplacer ( `git checkout <branch-name>` ) sur une autre
  - Pour réinitialiser un fichier avec la version de la branche courante ( `git checkout <file-name>` )
  - Lien vers la documentation : <https://git-scm.com/docs/git-checkout>

- `git merge`
  - Si vous êtes sur la branche _master_, cela va merger _develop_ dans _master_, créant une __fusion des commits__ ( `git merge develop` )
  - Lien vers la documentation : <https://git-scm.com/docs/git-merge>

- `git push`
  - Pousse les changements __validés__ sur le serveur de versioning distant
  - Lien vers la documentation : <https://git-scm.com/docs/git-push>

## 1.3. Les commandes plus évoluées / complexes

- `git fetch origin`
  - Permet de récupérer le statut des changements distants ( création de branches, etc... )
  - Lien vers la documentation : <https://git-scm.com/docs/git-fetch>

- `git cherry-pick`
  - Applique les changements effectués sur un autre commit
  - Lien vers la documentation : <https://git-scm.com/docs/git-cherry-pick>

- `git stash`
  - Conserve les changements courants dans une zone mémoire et réinitialise les fichiers selon la version distante ( `git stash` )
  - Réinjecte les changements précédemment conservés et les réapplique sur la nouvelle version des fichiers ( après changement de branche par exemple ) ( `git stash pop` )
  - Lien vers la documentation : <https://git-scm.com/docs/git-stash>

- `git rebase`
  - Équivalent proche du `git merge` mais pour avoir un historique linéaire ( utilisable et utile si les changements n'ont pas été poussés )
  - Permet de merger des commits précédents __mais non poussés__ ( `git rebase -i HEAD~4` va permettre de reprendre les 4 derniers commits non poussés pour en modifier l'histoire )
  - Lien vers la documentation : <https://git-scm.com/docs/git-rebase>

- `git gui`
  - Interface graphique intégrée pour la gestion des changements courants
  - Lien vers la documentation : <https://git-scm.com/docs/git-gui>

- `gitk`
  - Interface graphique intégrée pour la visualisation de l'historique du projet ( branches, commits, détails de commits )
  - Lien vers la documentation : <https://git-scm.com/docs/gitk>

[--> Retour au README](../README.md)
