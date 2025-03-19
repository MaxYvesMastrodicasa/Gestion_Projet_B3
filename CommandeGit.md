## Les commandes de base

### `git status`

La commande `git status` permet de vérifier l'état des fichiers.

En <font color='red'>rouge</font> les fichiers modifiés et non stage.

En <font color='green'>vert</font> les fichiers stage et en attente de commit

Si il n'y a pas de fichiers cité c'est que notre branche sont à jour et aucun fichier n'a été modifié depuis le dernier commit.

### `git add`

La commande `git add` permet de stage les fichiers ayant eu des modifications depuis le dernier commit.

Plusieurs options sont intéressantes à faire suivre à la commande `git add`.
En voici quelques exemples fréquent :

- `git add .` : ajoute tout les fichiers du répertoire sur lequel nous sommes
- `git add *` : ajoute tout les fichiers modifiés
- `git add -p` : ajoute de façon intéractive les changements au sein des fichiers.

Pour la commande `git add -p` il est possible de passer un nom de fichier en paramètre.

```bash
git add -p <file-name>
```

### `git commit`

La commande `git commit` permet la sauvegarde des fichiers stage.
En entrant la commande `git commit` plusieurs options s'offrent à nous.
Nous pouvons commit un fichier précis en passant en paramètre de la commande le chemin du fichier.

Lorsque nous lançons cette commande un VIM ou l'éditeur par défaut sélectionné dans la config de GIT va s'ouvrir pour renseigner le titre du commit.

Comme il s'agit d'un éditeur type VIM il faut alors taper `i` afin d'entrer en mode `INSERT`, à partir de là on peut éditer notre titre de commit.
Pour sauvegarder ensuite il faut taper `ECHAP` puis `:wq` ou `:x`

Pour éviter d'avoir à entrer dans le VIM ou l'éditeur de texte il faut saisir la commande suivante :

```bash
git commit -m "titre de mon commit"
```

### `git push`

La commande `git push` permet de pousser nos commit sur le dépôt distant (ici GITHUB).

Il y a certaines options à connaitre mais avec lesquelles il faut être méticuleux.

`git push --force` ou `git push -f` cette commande force les commit en local à être push et donc **écrase et remplace** la branche distante par celle que nous avons en local.

Il est conseillé d'utiliser `git push --force-with-lease`, de cette manière seul nos commit et non ceux de nos collègues ayant agis sur la branches seront overwrite.

### `git pull`

Cette commande permet de récupérer les mises à jour apporté au distant en local.

Il suffit de se positionner sur la branche souhaitée et de saisir cette commande pour exécuter la mise à jour.

### `git checkout`

Cette commande permet de se placer sur un commit précis en lui passant le SHA de ce dernier ou bien de changer de branche.

```bash
git checkout <SHA-commit>
git checkout <nom-de-branche>
```

**Astuce**

_Réaliser un `git checkout -b <nom-de-branche>` permet de créer une nouvelle branche et de passer directement à celle-ci._

_Réaliser un `git checkout <nom-de-branche>` si la branche existe sur le dépôt distant la branche sera créée, on se placera dessus, track la branche distante et pull_

### `git branch`

La commande `git branch` permet plusieurs chose suivant les options passées à cette commande.

```bash
git branch <name-branch>            #Créer une branche
git branch -D <name-branch>         #Supprime la branche
git branch -m <old-name> <new-name> #Renomme la branche

#Récupération d'une branche distante en locale :
#Créez d'abord votre branche locale (de préférence de même nom que la distante
#Puis placez vous dessus et entrez la commande suivante en l'adaptant
git branch --set-upstream-to=origin/<branch-distante> <branche-locale>
git branch -u origin <branch-locale> #version plus courte de la commande au-dessus
```

### `git log`

Cette commande présente la liste des commits dans l'ordre chronologique, elle permet entre autre de récupérer le SHA d'un commit.

## Une bonne habitude

Une bonne habitude serait de réaliser toujours un cycle au moment de la création d'une branche ou bien de son travail sur une branche.

### Création d'unne branche

En partant de la branche develop :

- `git pull`
- `git checkout -b <nom de ma branche>`
- modifications nécessaires
- `git status`
- `git add <option souhaitée>`
- `git status`
- `git commit -m <message commit>`
- `git push`
