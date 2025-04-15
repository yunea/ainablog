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
draft: false
---
## 🎯 Contexte 

Lors de ma dernière année à l’**IMT Atlantique**, j’ai participé, avec mon groupe, au développement d’un **ERP modulaire**dans le cadre de l’unité d’enseignement **PROCOM**.

Avant d’entrer dans le détail du projet, il est utile de clarifier deux notions essentielles :

### Qu’est-ce qu’un ERP ?

Un **ERP** (_Enterprise Resource Planning_, ou _progiciel de gestion intégré_) est un système logiciel qui centralise les processus clés d’une entreprise : **finance, ressources humaines, production, logistique, ventes, achats**, etc. Il fournit une vue unifiée des activités, facilitant la coordination et la prise de décision.

### Qu’est-ce qu’un système distribué ?

Un **système distribué** est un ensemble de composants (machines, applications ou services), exécutés sur des entités distinctes, mais fonctionnant ensemble comme un **système unifié et cohérent**.

---

Un ERP est donc un excellent **cas d’étude** pour illustrer les **principes des systèmes distribués** : chaque fonctionnalité (comptabilité, gestion RH, approvisionnement...) peut être conçue comme un **module indépendant**, interagissant avec les autres.

## 🔬 Objectif du projet

Notre objectif était de **concevoir une maquette pédagogique** permettant d’illustrer les enjeux des **systèmes distribués**, à travers une application web modulaire.

Nous avons développé un ERP destiné à de **petites structures** (TPE, restaurants, commerces...), reposant sur une architecture **flexible**, **personnalisable** et **scalable**. Ce projet n’avait pas vocation à être commercialisé, mais à servir de **support d’apprentissage** pour les élèves-ingénieurs.


![Image Description](/ainablog/images/poster-procom.jpg)

*👉 [Découvrez le projet sur GitHub](https://github.com/PROCOM-ERP/IMT-3A-PROCOM-ERP)*

## ⚙️ Stack technique & architecture

### Stack technique

Notre ERP repose sur une stack technique moderne :

- **Frontend** : React.js, HTML5, CSS3
- **Backend** : Java 17 avec Spring Boot 3
- **Base de données** : PostgreSQL 13
- **Infrastructure** : Docker, Docker Compose, Docker Swarm
- **CI/CD** : GitHub Actions
- **Environnements de développement** : IntelliJ, VS Code, Neovim
- **Outils divers** : Postman, Maven, Notion
### Architecture du projet

Le projet suit une **architecture micro-services**. Chaque fonctionnalité (authentification, commandes, inventaire...) est développée comme un service indépendant, facilitant l’évolutivité et la résilience de l’ensemble.

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


Le schéma d'architecture représente l'**organisation des services** de l'ERP :

![Image Description](/ainablog/images/schema-archi-procom.png)

- Services fonctionnels : Authentification, Commande, Inventaire, Annuaire
- Infrastructure : un Message Broker (RabbitMQ) permet la communication entre les services, et une Gateway centralise les requêtes API.
- Le Front-end sert d’interface visuelle à l’utilisateur.
- Chaque module peut évoluer indépendamment, ce qui reflète bien l’architecture des micro-services.

## 👥 Organisation

### Rôles de l’équipe

Le travail a été réalisé en équipe de 5. Voici les principaux rôles :

- BOPS : Project Manager, Backend, Sécurité, Système
- maestro-bene : Backend, Système, Sécurité
- Antoine : Frontend, UI/UX, Product Owner support
- ArthurMaquinImt : Backend Engineer
- yunea (moi) : Frontend, UI/UX

### Collaboration & organisation

Pour organiser notre travail, j’ai mis en place un espace collaboratif sur **Notion**. Il centralisait toutes les informations utiles au projet : planning, suivis de tâches (kanban, backlog, todo list) et ressources partagées. Cela nous a permis d’avoir une vision claire et structurée des avancements.

La communication quotidienne se faisait via un **serveur Discord dédié**. Ce dernier a joué un rôle essentiel, à la fois pour les échanges internes à l’équipe, mais aussi pour la communication avec le **corps enseignant**. Il nous permettait de poser rapidement nos questions, de réagir efficacement aux retours, et de maintenir une excellente fluidité dans les échanges. Des salons vocaux et textuels thématiques facilitaient la répartition des discussions et le suivi des décisions.
### Méthodologie agile

Nous avons adopté une méthode **Scrum**, avec des sprints de deux semaines. Chaque sprint définissait des objectifs concrets à atteindre, et des réunions hebdomadaires permettaient d’assurer un suivi régulier, de lever les blocages éventuels, et de renforcer la cohésion de groupe. L’implication de chacun était significative, avec un volume de travail hebdomadaire compris entre 20h et 30h par semaine.

## 💡 Ma contribution

En tant que **développeuse front-end**, j’ai participé activement à la conception des interfaces et à leur intégration dans l’application. J’ai travaillé sur :

- la création de la charte graphique et des maquettes via Figma,
- le développement de l’ensemble du site côté front-end, en assurant la création et l’intégration des différentes pages React,
- la logique conditionnelle des affichages et la gestion des droits utilisateurs,
- l’intégration des API fournies par les services back-end.

---

Voici quelques aperçus du travail réalisé :

**Figma**

Charte graphique : 

![[procom-charte-graphique.png|500]]

Templates des pages : 

![Image Description](/ainablog/images/procom-figma-pages.png)

---

**Interfaces front-end**

Page de connexion : 

![[procom-front-login.png|500]]

Page de l'annuaire : 

![Image Description](/ainablog/images/procom-directory.png)

Page de la gestion des commandes : 

![Image Description](/ainablog/images/procom-order-home.png)

## 🔺 Conclusion

Ce projet a été une véritable immersion dans une **stack technique complète** et un environnement proche du monde professionnel. Il m’a permis de renforcer mes compétences en **développement web**, en **architecture logicielle** et en **gestion de projet collaboratif**.