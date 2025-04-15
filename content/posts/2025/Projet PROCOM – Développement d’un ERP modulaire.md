---
title: Projet PROCOM – Développement d’un ERP modulaire
date: "2025-04-13"
slug: /projet-erp-modulaire/
description: L’objectif de ce projet est de concevoir un modèle pédagogique illustrant les enjeux des systèmes distribués.
image: images/logo-reactjs.png
caption:
categories:
- projet
- web
tags:
- docker
- reactjs
- feature
draft: true
---
## 🎯 Contexte et objectifs

Dans le cadre de ma dernière année d'ingénieur à l’IMT Atlantique, j’ai participé au développement d’un **ERP modulaire** dans le cadre de l’unité d’enseignement PROCOM. 

Avant de commencer, voici 2 questions importantes : 
1. Qu'est-ce qu'un ERP ?
2. Qu'est ce qu'un système distribué ?

Un progiciel de gestion intégré (**ERP**) est un système logiciel qui aide les entreprises à rationaliser leurs principaux processus, notamment ceux des fonctions Finance, RH, Production, Supply Chain, Ventes et Achats, grâce à une vue unifiée des activités, et qui fournit une version unique de la réalité. 

Les systèmes distribués sont un ensemble de composants, de machines et d'applications indépendants qui fonctionnent comme un système unifié.

Un ERP est donc parfait pour notre projet puisqu'il est composé de différentes parties fonctionnelles (Finance, RH, Production, Supply Chain, Ventes et Achats) qui peuvent être séparées afin de répondre au besoin du client.

L'objectif de ce projet est concevoir un modèle pédagogique illustrant les **enjeux des systèmes distribués**, à travers un projet concret, collaboratif et technique.

L’ERP développé vise à proposer une solution adaptable aux **petites entreprises** (commerces, restaurants, etc.), capable d’évoluer selon les besoins. Ce projet n’est pas destiné à la commercialisation, mais sert avant tout de **cas d’étude** pour les élèves ingénieurs.


!![Image Description](/ainablog/images/poster-procom.jpg)

*👉 [Découvrez le projet sur GitHub](https://github.com/PROCOM-ERP/IMT-3A-PROCOM-ERP)*

## ⚙️ Stack technique & architecture

### Stack technique

Le projet s’appuie sur une stack technique moderne et cohérente :

- **Frontend** : React.js, HTML5, CSS3
- **Backend** : Java 17 avec Spring Boot 3
- **Base de données** : PostgreSQL 13
- **Infrastructure** : Docker, Docker Compose, Docker Swarm
- **CI/CD** : GitHub Actions
- **Outils de développement** : IntelliJ, VS Code, Neovim
- **Autres outils** : Postman, Apache Maven, Notion (organisation de l’équipe)

### Architecture du projet

Le projet est structuré selon une **architecture modulaire**, chaque fonctionnalité (RH, stocks, ventes…) étant développée sous forme de **micro-service** :

```vbnet
IMT-3A-PROCOM-ERP/
├── src/
│   ├── frontend/       → Interface React
│   ├── backend/        → Microservices Java (Spring Boot)
│   └── databases/      → Scripts et confs PostgreSQL
├── docker/             → Dockerfiles, Docker Compose
├── system/             → Scripts système et entrypoints
├── security/           → Certificats, secrets, déploiement sécurisé
├── docs/               → Documentation technique et utilisateur
```

Voici un schéma plus visuel des interactions des différents modules entre eux :

!![Image Description](/ainablog/images/schema-archi-procom.png)

Chaque module (Authentification, Annuaire, Commande, Inventaire) est développé indépendamment des uns et des autres ce qui permet de fournir un service personnalisé à un client mais également, en cas de panne, il n'y a pas d'impact généralisé à l'ensemble des modules. 

## 👥 Organisation de l’équipe

### Équipe 

Le travail s’est effectué en équipe de 5 personnes. Dès le début du projet des rôles ont été attribués en fonction des appétences et de la personnalité de chacun.

- BOPS (from 2023-10-01 until 2024-03-31): _Project Manager_, _Backend Engineer & Developer_, _Security Support_, _System Support_
- maestro-bene (from 2023-10-01): _Backend Engineer & Developer_, _System Administrator_, _Head of Security_
- Antoine (from 2023-10-01 until 2024-03-31): _Product Owner Support_, _Frontend & UI/UX Support_
- ArthurMaquinImt (from 2023-10-01 until 2024-03-31): _Backend Engineer & Developer_
- yunea (from 2023-10-01 until 2024-03-31): _Frontend & UI/UX Developer_

### Frontend

J’ai personnellement contribué en tant que **développeuse Frontend & UI/UX** :
- Réalisation du design dans Figma
- Intégration des interfaces utilisateur en React
- Conception des modules front
- Collaboration avec les Backend Engineer dans la conception des API backend
- Intégration de la communication avec les API backend

**Figma**

Réalisation de la charte graphique
![[procom-charte-graphique.png|500]]

Réalisation de plusieurs templates des pages afin de choisir le visuel (UI/UX)
!![Image Description](/ainablog/images/procom-figma-pages.png)

**Frontend UI/UX**

Page de connection du site 
![[procom-front-login.png|500]]

Page d'annuaire de l'entreprise

!![Image Description](/ainablog/images/procom-directory.png)

Page de gestion de commande

!![Image Description](/ainablog/images/procom-order-home.png)

**Défis**
- Gestion des droits des différents utilisateurs
- Gestion des modules disponibles -> si un module n'est pas disponible, il ne doit pas apparaitre dans l'interface
- Gestion du temps 

### Notion

J’ai également **mis en place des outils collaboratifs**, notamment via un espace de travail **Notion** commun, qui a permis de centraliser toutes les informations liées au projet. Chaque membre de l'équipe possédait un espace personnel en plus de l'espace commun. Cet outil nous a permis d'assurer le partage homogène des informations au sein de l'équipe en les regroupant sous différente forme. 
Les informations disponibles étaient : 
- un calendrier avec toutes les informations nécessaires liées au projet (deadline, réunion, évènement, gantt)
- une page avec toutes les tâches à faire pour la réalisation du projet
- une page sous la forme d'un kanban avec toutes les tâches à réaliser lors du sprint en cours avec la possibilité d'ajouter des filtres à la convenance de chacun
- un tableau regroupant différentes ressources (idées, ressources, documents) avec des vues différentes en fonction des besoins

### Méthodologie

La méthodologie agile est celle choisi pour ce projet. Les sprints duraient 2 semaines avec des objectifs et des tâches précis. Le programme était serré puisque c'est un projet conséquent qui se déroulait en même temps que d'autre cours et sur une période de 5 mois avec une présentation du projet à réaliser à la fin lors d'un évènement. L'investissement horaire des membres du groupe était de 20h à 30h par semaine en fonction des rôles. Une réunion était organisée toutes les semaines afin de faire le point sur l'avancement et les difficultés de chacun. Ces réunions nous permettaient également de nous assurer du moral de tout le monde et qu'aucun retard n'était à annoncer.

## 💡 Défis rencontrés

Comme tout projet d'envergure, nous avons rencontré quelques obstacles intéressants :

- **Communication entre les services** (backend – base de données – frontend)
- La **coordination des modules**, parfois développés en parallèle
- L’adoption des **certificats de sécurité** pour les communications en HTTPS
- La mise en place d’un **environnement Dockerisé complet** (multi-conteneurs, mode Swarm)
- La gestion des contributions avec GitHub dans un cadre multi-dev

## 📚 Ce que j’ai appris

Cette expérience a été très riche :
- Approfondissement de mes compétences en **React**, intégration API et gestion des états
- Compréhension des **architectures distribuées**
- Collaboration autour de **micro-services**
- Utilisation avancée de **Docker et Docker Compose**
- Amélioration de mes pratiques de développement en équipe (versioning, code review, CI/CD)

## 🔚 Conclusion

Ce projet a été l’occasion de **travailler sur une vraie stack technique complète**, avec des exigences proches du monde professionnel. Il m’a permis de mieux appréhender la gestion de projet en équipe, les systèmes distribués, et les outils d’orchestration modernes.
