## Introduction

Ce cours est axé sur plusieurs aspects fondamentaux :

- Le versioning et son importance dans la gestion de projet
- L'utilisation de Git comme outil de versioning

## Git et le versioning

### Introduction

Le versioning est une stratégie qui permet, grâce à des outils tels que Git, de centraliser le travail d’une équipe tout en conservant un historique des modifications. Il enregistre l’évolution du code source tout au long de la vie du projet, permettant ainsi une traçabilité efficace des modifications apportées.

Le versioning apporte plusieurs avantages :

- Revenir en arrière en cas d'erreur bloquante
- Comparer les changements entre différentes versions
- Identifier l’auteur d’un commit
- Travailler efficacement en équipe sur un même projet

### Mots clés du versioning

- **Traçabilité** : chaque modification est enregistrée avec son auteur et sa date
- **Collaboration** : plusieurs développeurs peuvent travailler simultanément
- **Backup & rétablissement** : possibilité de restaurer une version antérieure
- **Branching & merging** : gestion des branches pour développer des fonctionnalités en parallèle

### Nomenclature du versioning

La numérotation des versions suit généralement le schéma suivant :

`MAJEURE.MINEURE.CORRECTIF`

- **MAJEURE** : Changements incompatibles avec les versions précédentes
- **MINEURE** : Ajout de nouvelles fonctionnalités
- **CORRECTIF** : Corrections de bugs et patchs

### Différents systèmes de versioning

#### SVN (Subversion)

SVN est un système de versioning centralisé. Il nécessite une connexion au réseau pour apporter des modifications au code source. Un inconvénient majeur est que si le serveur est perdu, tout l’historique l’est également.

Les commits sous SVN sont atomiques : **soit toutes les modifications sont appliquées, soit aucune ne l’est**.

**Remarque** : _Un commit est une opération locale sur Git, mais pas sur SVN._

#### Git

Git est un système de versioning distribué, ce qui signifie que chaque contributeur possède une copie complète du code source avec tout son historique.

Voici une comparaison entre un système centralisé et un système distribué :

| **Critère**          | **SVN (Centralisé)**            | **Git (Distribué)**        |
| -------------------- | ------------------------------- | -------------------------- |
| Connexion requise    | Oui                             | Non, sauf pour push/pull   |
| Disponibilité        | Dépend du serveur central       | Chaque machine a une copie |
| Performances         | Plus lent sur les grosses bases | Plus rapide                |
| Gestion des branches | Complexe                        | Très fluide et optimisée   |

### Git en détail

La principale différence entre Git et les autres systèmes de gestion de versions (SCM) est que Git ne stocke pas les modifications comme une série de différences successives, mais comme une collection de snapshots du projet à un instant T.

**Important** : La plupart des actions sur Git sont locales, ce qui permet de travailler sans connexion internet et de pousser les modifications plus tard.

Git garantit l’intégrité des données grâce à un système de hachage cryptographique : **SHA-1**. Chaque commit est identifié par un hash unique de 40 caractères hexadécimaux.

### Configuration de Git

La configuration de Git permet notamment de :

- Se connecter à son compte GitHub ou GitLab
- Assurer la traçabilité des commits (auteur, email...)
- Activer la coloration syntaxique et d’autres paramètres personnalisés

Il existe trois niveaux de configuration :

- **Global** : s’applique à tous les dépôts de l’utilisateur (`~/.gitconfig`)
- **Local** : spécifique au dépôt en cours (`.git/config`)
- **Système** : configuration globale pour tous les utilisateurs de la machine

### Exemples pratiques de Git

1. **Initialiser un dépôt Git** :

   ```bash
   git init
   ```

2. **Ajouter et valider des modifications** :

   ```bash
   git add .
   git commit -m "First commit"
   ```

3. **Créer une branche et y basculer** :

   ```bash
   git branch nom-nouvelle-branche
   git checkout nom-nouvelle-branche
   ```

4. **Pousser les modifications vers un dépôt distant** :
   ```bash
   git push origin nom-nouvelle-branche
   ```

---

Ce document présente les bases du versioning et de Git. Il est recommandé de pratiquer ces commandes pour bien comprendre leur fonctionnement et d’explorer des concepts avancés comme les **rebase**, **merge**, et la gestion des conflits.
