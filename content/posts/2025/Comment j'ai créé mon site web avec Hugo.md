---
title: Comment j'ai créé mon site web avec Hugo
date: "2025-04-12"
slug: /creation-de-site-web-avec-hugo/
description: Étapes détaillées de la création de mon site web statique avec Hugo, depuis l'idée jusqu'à la mise en ligne.
image: images/hugo.png
caption: 
categories:
- web
- projet
tags:
- hugo
- markdown
- git
- github
- feature
draft: false
---


## Comment j'ai créé mon site web avec Hugo

Créer un site web peut sembler intimidant, mais avec des outils modernes comme Hugo, c’est à la fois rapide, efficace et très flexible. Dans cet article, je vous explique comment j’ai conçu et réalisé ce site web, de A à Z.

Pour en savoir plus sur Hugo : https://gohugo.io

## 🌱 Pourquoi Hugo ?

Avant tout, pourquoi avoir choisi Hugo ? Voici mes critères :
- Générateur de site statique rapide
- Prise en charge native de Markdown
- Facile à déployer (notamment avec GitHub Pages ou Netlify)
- Possibilité de personnalisation avec des thèmes

## 🛠️ Pré-requis & outils utilisés

Voici les outils que j’ai utilisés pour mettre en place le site :

- [Hugo](https://gohugo.io/) (générateur de site statique)
- [Git](https://git-scm.com/) pour la gestion de version
- [GitHub](https://github.com/) pour héberger le dépôt et pour la publication automatique
- Un éditeur de texte : VS Code
- Et bien sûr, **Markdown** pour écrire mes articles

> À noter que je réalise ce projet sur Mac.

## 🧱 Mise en place du projet
### Hugo et Git

```bash
# Installer Go (si ce n'est pas déjà fait)
brew install go
# Vérifier l'installation
go version

# Installer Hugo (si ce n’est pas déjà fait)
brew install hugo
# Vérifier l'installation
hugo version


# Se déplacer dans le dossier de création de votre site
cd /Documents/projets
# Créer un nouveau site
hugo new site mon-blog

# Se rendre dans le dossier
cd mon-blog

# Initialiser un dépôt Git
git init
# Configurer Git
git config --global user.name "your name"
git config --global user.email "your email"
```

Ajouter un fichier `.gitignore` pour éviter de versionner certains fichiers inutiles (comme les fichiers générés à la compilation).

```
.DS_Store
.hugo_build.lock
```

### Thème

Il faut ensuite choisir un **thème** afin de l'importer. 

Tous les thèmes sont disponibles ici : [https://gohugo.io](https://gohugo.io/).

Le thème que j'ai choisi pour ce projet : https://themes.gohugo.io/themes/pehtheme-hugo/.

```bash
# Import du thème dans mon projet
git submodule add https://github.com/fauzanmy/pehtheme-hugo.git themes/pehtheme-hugo
```

Remplacer les 2 dossiers et le fichiers suivant du dossier `exampleSite` à la racine du projet :

```bash
    exampleSite/
    ├── assets/
    ├── content/
    └── hugo.toml
```

Tester le site en local 

```bash
hugo server
```

Le site est disponible à l'adresse suivante : http://localhost:1313/
### GitHub

#### Git 

```bash
# Assurez vous d'être dans le bon dossier 
cd mon-blog

# Ajouter tous les fichiers à l'index git
git add .
# Réaliser le premier commit
git commit -m "Initial commit: site Hugo avec thème"
```

#### Créer un nouveau dépôt sur GitHub

Se créer un compte GitHub (si ce n'est pas fait) : https://github.com. 
Lien vers la documentation : [Comment se créer un compte GitHub](https://docs.github.com/fr/get-started/start-your-journey/creating-an-account-on-github#signing-up-for-a-new-personal-account)

Se rendre sur [github.com/new](https://github.com/new) et créer un nouveau dépôt **sans README** (on l’a déjà localement).

Exemple :
- Nom du repo : `mon-blog-hugo`
- Visibilité : Public ou Privé

#### Générer une clé SSH pour `push` sans entrer ses identifiants à chaque fois.

```bash
# Se déplacer dans le dossier .ssh
cd /Users/your-username/.ssh
# Générer une clé SSH (si vous n'en avez pas)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# Afficher le contenu de la clé SSH
cat id_rsa.pub
```

Ajouter la clé SSH à GitHub
1. Allez sur [https://github.com/settings/keys](https://github.com/settings/keys)
2. Cliquez sur **"New SSH key"**
3. Donnez un nom à votre clé (ex. : "MacBook Pro", "PC du boulot", etc.)
4. Collez la clé dans le champ **"Key"**
5. Cliquez sur **"Add SSH key"**

Tester la connexion SSH

```bash
ssh -T git@github.com
```


Vous pouvez maintenant cloner, puller, pousser votre dépôt sans mot de passe.

#### Ajouter le dépôt distant à votre projet 

```bash
# Assure toi d'être dans le bon dossier 
cd mon-blog

# Ajoute le lien comme remote
# Remplace `ton-utilisateur` et `mon-blog-hugo` par les bons noms.
git remote add origin https://github.com/ton-utilisateur/mon-blog-hugo.git

# Pousse le projet vers GitHub
# Si la branche s'appelle `master`, remplace `main` par `master`.
git push -u origin main
```

## ✍️ Écriture des articles

Hugo permet de créer facilement de nouveaux articles :

```bash
hugo new posts/comment-j-ai-cree-mon-site.md
```


Cela génère un fichier Markdown avec les métadonnées de l’article. Je n’ai plus qu’à le remplir :

```md

--- title: "Comment j'ai créé mon site" date: 2025-04-10 draft: false ---  Contenu de l’article...
```

J’écris mes articles dans ce format, en `.md`, puis je les pousse sur GitHub.

## 🎨 Personnalisation

J’ai ensuite personnalisé :

- Le thème (couleurs, typographies)
- Le fichier `config.toml` (titre du site, liens sociaux, etc.)
- La structure des menus

```toml
baseURL = "https://monsite.netlify.app/"
title = "Mon Blog"
languageCode = "fr"
theme = "terminal"

[params]
  backgroundColor = "dark"
  contentTypeName = "posts"
```

## 🚀 Déploiement avec GitHub Pages

### Créer la branche de déploiement 

```bash
# Assurez vous d'être dans le bon dossier 
cd mon-blog

# Génèrer le site statique dans le dossier `public/`
hugo

# Créer une branche temporaire `hostinger-deploy` contenant uniquement le contenu du dossier `public`.
git subtree split --prefix public -b hostinger-deploy

# Pousser cette branche vers la branche distante `hostinger` (celle utilisée par ton hébergement sur Hostinger)
git push origin hostinger-deploy:hostinger --force

# Nettoyer la branche temporaire
git branch -D hostinger-deploy
```

💡 Pourquoi c’est cool ?

- Tu gardes une seule branche `main` propre avec tout ton code source
- Tu n’as pas besoin de commit ou de versionner le dossier `public/`
- Tu déploies uniquement ce qui est nécessaire
- Tu peux faire ça à chaque changement avec un petit script

### Configurer GitHub Pages

1. Va dans ton repo GitHub
2. Onglet **Settings** > **Pages**
3. Sélectionne la branche **`hostinger`**, dossier `/ (root)`
4. Valide

 Ton site sera accessible à :  `https://ton-utilisateur.github.io/nom-du-repo/`

### 🧠 Bonus : script bash pour automatiser

Tu peux créer un script `deploy.sh` :

```bash
#!/bin/bash  
hugo || exit 1 
git subtree split --prefix public -b hostinger-deploy 
git push origin hostinger-deploy:hostinger --force 
git branch -D hostinger-deploy`
```

Puis rends-le exécutable :

```bash
chmod +x deploy.sh
```

Et à chaque mise à jour, tu lances :

```bash
sh deploy.sh
```

## ✅ Bilan

Créer ce site m’a permis de :

- Maîtriser le cycle complet d’un site statique
- Avoir un espace personnel simple et rapide à maintenir
- Me concentrer sur le contenu plutôt que sur la technique

## 🧩 Idées d’améliorations futures

- Ajouter un moteur de recherche (par exemple Fuse.js)
- Ajouter un mode sombre/clair
- Héberger le site sur Hostinger
## Ressources

- [https://youtu.be/dnE7c0ELEH8](https://youtu.be/dnE7c0ELEH8)
- [https://blog.networkchuck.com/posts/my-insane-blog-pipeline/](https://blog.networkchuck.com/posts/my-insane-blog-pipeline/)
