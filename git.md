Objectif de git : garder une trace de tout ce qui a été fait sur le projet
Sélection d'un fichier pour commit : git add
Commit : git commit
Un commit est un genre de photo complète de l'état du projet
On peut se promener parmis tous les commit et les comparer
Pour voir tous les commits d'un projet : git log
Pour voir les différences entre 2 versions : git diff (utiliser plutôt des logiciels qui rendent la lecture plus faciles)

Pour ajouter une remote à un projet existant, on utilise git remote add
Lorsqu'un projet a une remote de configurée (99% des cas), on fait git push pour envoyer tout notre arbre de commit (tout le projet)

On peut se promener sur n'importe quel commit
Lorsqu'on fait un git checkout [nom du commit], git resitue tout le dossier du projet (tout tout, tout) dans l'état exact où il était au moment du commit
On peut aussi donner un nom de branche (par exemple master) et HEAD va suivre automatiquement la branche

Pour créer une nouvelle branche, on fait git checkout -b [nom de la nouvelle branche]
La nouvelle branche va automatiquement pointer vers le commit sur lequel on est actuellement (le commit qui est pointé par HEAD)

Une branche, c'est toujours **juste** un simple pointeur vers un commit. A chaque fois qu'on fait un nouveau commit, la branche "suit" notre travail et elle vient pointer le nouveau commit.
Si on créé 2 branche sur un commit, lorsqu'on travaillera sur ces deux branches, les commit se mettront à vraiment dessiner des branches.

L'intérêt des branches, c'est de pouvoir travailler sur plusieurs grosses features en même temps sans géner le travail sur d'autres features.

Pour réunir 2 branches (merger), il faut :
- se placer sur la branche **de destination**
- faire un `git merge <branche cible>`

Dans le cas où les deux branches sont sur une ligne droite :
- git fait une avance rapide sur la destination pour rejoindre la branche cible
rien de particulier dans ce cas là

Dans le cas où les branches **ne sont pas pas sur une ligne droite**, c'est à dire que la branche de destination contient du taff qui a divergé par rapport à notre branche :
- git recherche le parent commun le plus récent (le parent n'est rien d'autre qu'un commit)
- git détermine tout le taff qui a divergé depuis ce parent
- git créé automatiquement un nouveau commit qui contient le taff de la branche de destination **et** le taff qui avait divergé depuis le parent commun

A partir de là on a 2 cas possibles :
- git arrive à réunir les 2 taffs automatiquement : pas de conflit
- git n'arrive pas à réunir les 2 taffs automatiquement : conflit

# Conflits
Un conflit se produit quand git essaye de mettre ensemble du taff de 2 branches différentes qui ont divergé, et qu'il n'est pas capable de le faire tout seul
Quand il y a un conflit, git laisse des marqueurs pour nous aider à résoudre le conflit :

<<<<<< BRANCHE ACTUELLE
// le contenu
// de la branche
// actuelle
======
// le contenu
// de la branche
// cible
>>>>>> le nom de la branche cible


Quand on a résolu un conflit sur un fichier, on fait un git add le_fichier
Lorsqu'on est en train de résoudre un conflit, la commande 'add' sert à dire à git qu'un conflit est résolu

Une fois qu'on a résolu tous les conflits, on fait un git commit
Lorsqu'on est en train de résoudre un conflit, la commande 'commit' sert à dire à git "vas-y, continue"

Note importante : un merge ne peut bouger **que** la branche sur laquelle on est actuellement (HEAD)


Trucs intéressants à voir :
le stash
le rebase
comment se servir des branches

(détail les commits/working space/stage)
