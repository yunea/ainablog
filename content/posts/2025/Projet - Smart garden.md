---
title: Projet - Smart garden
date: "2025-04-13"
slug: /projet-smart-garden/
description: "Projet visant à améliorer l'organisation des jardins partagés grâce à une plateforme web accessible à tous."
image: images/logo-reactjs.png
caption:
categories:
- projet
- web
tags:
- reactjs
- docker
- fastAPI
draft: false
---

## 1. État de l'art : les jardins partagés, entre écologie et lien social

Les jardins partagés connaissent un essor notable en France, notamment dans les zones urbaines où ils répondent à un besoin croissant de nature et de convivialité. Ces espaces verts collectifs favorisent la biodiversité, renforcent les liens sociaux et contribuent à une alimentation plus durable. Leur développement s'inscrit dans des scénarios de transition écologique, promus par des institutions comme l'ADEME, qui valorisent des approches frugales et coopératives.​

### Conclusion de l'état de l'art

Notre réflexion a débuté avec deux thèmes principaux concernant les hypothèses de départ : la gestion des ressources, notamment de l’eau et la gestion des plantes en temps réel. Dans le but d’affiner ces hypothèses, nous avons par notre recherche pu identifier des premières difficultés rencontrées dans les jardins, appréhender les solutions existantes pouvant y être liées et déterminer la liste des acteurs de ces espaces, que nous avons par la suite pu rencontrer pour confirmer notre recherche documentaire et compléter certaines informations. 

La problématique qui ressort de toutes ces recherches est donc “Comment faciliter l’organisation des jardins partagés qui ne possèdent pas d’animateur et fédérer les habitants lorsqu’il y a un manque de compétences techniques ?”.

👉 Lire l'article complet : [Jardin Partagé – État de l'art](https://telefab.fr/2023/10/22/jardin-partage/)

## 2. Enquête terrain : comprendre les dynamiques locales

Pour mieux appréhender les réalités des jardins partagés, une enquête de terrain a été menée à Brest. Cette étude a révélé le rôle central des collectivités locales et des associations, telles que Vert le Jardin, dans la création et la gestion de ces espaces. Elle a également mis en lumière les défis liés à la coordination entre les différents acteurs et la nécessité d'outils facilitant l'organisation et la communication au sein des jardins.​

👉 Lire l'article complet : [Jardin Partagé – Enquête terrain](https://telefab.fr/2023/10/27/jardin-partage-enquete-terrain/)

## 3. Solution technique : SmartGarden, une application au service des jardiniers

Face aux défis identifiés, le projet SmartGarden propose une solution innovante combinant technologie et accessibilité. Il s'agit d'une application web connectée à des capteurs, permettant aux membres d'un jardin partagé de :​
- Suivre en temps réel les conditions du jardin (humidité, température, etc.)​
- Consulter et planifier les tâches à réaliser​
- Accéder à des fiches pratiques pour l'entretien des cultures​    

Le système repose sur une architecture modulaire avec un boîtier de capteurs, une base de données et une interface utilisateur développée en ReactJS. L'objectif est de faciliter la gestion des jardins, même en l'absence de référent, en favorisant l'autonomie et la collaboration entre les membres.​

👉 Lire l'article complet : [Jardin Partagé – Solution Technique](https://telefab.fr/2024/01/15/jardin-partage-solution-technique/)

## Ma contribution dans ce projet

### Cheffe de projet

Dans le cadre de ce projet, j’ai assuré le rôle de **cheffe de projet**, avec pour missions principales :
- La **répartition des tâches** de manière équitable entre les membres de l’équipe, en tenant compte des compétences, disponibilités et intérêts de chacun ;
- L’**animation des réunions hebdomadaires**, afin de suivre l’avancement, identifier les blocages et ajuster les priorités si nécessaire ;
- La **coordination globale de l’équipe**, pour assurer la cohérence des travaux et le respect du planning.

Nous avons adopté une organisation basée sur la **méthode agile**, et plus spécifiquement **SCRUM**, avec des sprints de trois semaines ponctués de points hebdomadaires. Chaque sprint était préparé en amont par la rédaction de user stories, l’attribution d’un poids (effort estimé) à chaque tâche, et leur organisation dans une application de gestion visuelle (type tableau Kanban). Ce cadre méthodologique nous a permis de garder une vue d’ensemble claire sur l’avancement, d’anticiper les éventuels blocages, et d’encourager une autonomie structurée au sein de l’équipe.

### Développeuse backend 

Le back-end de l’application se compose de trois éléments essentiels : le système d’exploitation, la base de données, et l’interface de programmation (API).

#### Système d’exploitation

Le cœur du système d’exploitation repose sur Docker. Docker est une plateforme qui permet de lancer des applications dans des conteneurs. L’objectif d’un conteneur est d’héberger des services sur un même serveur physique (dans notre cas nos machines personnelles) tout en les isolant les uns des autres.

Cette plateforme nous offre également un environnement uniforme pour tous les membres du projet. Cette uniformité facilite l’intégration et le regroupement des différentes composantes développées par chacun des contributeurs.

Le fonctionnement des conteneurs Docker au sein de notre infrastructure Smart Garden repose sur l’utilisation de deux composants essentiels : Docker Compose et les fichiers Dockerfile. Cette approche garantit une configuration simplifiée et une mise en œuvre efficace de l’environnement de développement.

Le fichier docker-compose.yml définit l’ensemble des services et des paramètres nécessaires à notre application. Chaque service, tel que la base de données MariaDB, l’interface PHPMyAdmin, le front-end, le back-end et le service de capteurs, est configuré de manière à interagir au sein du réseau dédié smartgarden-network. Des volumes sont utilisés pour assurer la persistance des données de la base de données, tandis que les dépendances entre les services sont gérées avec l’instruction depends_on, garantissant un démarrage ordonné.

Les fichiers Dockerfile, situés dans les répertoires ./frontend, ./backend, et ./sensor, définissent les instructions nécessaires pour construire les images Docker correspondantes. Chacun de ces fichiers permet de décrire l’environnement d’exécution, les dépendances et les étapes spécifiques à chaque composant de l’application. Ces fichiers Dockerfile sont intégrés dans le fichier docker-compose.yml pour assurer une cohérence lors du déploiement de l’ensemble de l’application.

Une fois l’application déployée dans Docker, il est possible d’accéder au front-end, à PHPMyAdmin (pour gérer et visualiser la base de données) et à la page de l’API depuis l’adresse du localhost en sélectionnant des ports dédiés. Ces ports sont configurés dans le fichier docker-compose.yml, les fichiers Dockerfile et parfois les fichiers de configuration des services.

#### Base de données

Pour la gestion des données, nous avons opté pour MariaDB, un système de gestion de base de données relationnelles. Cette solution est complétée par l’utilisation de PHPMyAdmin, une interface web qui simplifie la manipulation et la visualisation des données stockées.

PHPMyAdmin nous a principalement été utile au début du projet afin de mettre en place les premières versions des bases de données. Cet outil nous a permis de faire de nombreux tests avant que l’API ne soit disponible dans l’application.

Dans ce projet nous avons pensé à une base de données simple. Voici le schéma de la base de données : 
![Image Description](/ainablog/images/smartgarden-schema-bdd.png)
Diagramme UML de la base de données

#### API

L’interface de programmation (API) repose sur FastAPI, un framework Python moderne et performant. Le serveur Python s’interface avec la base de données et expose des points d’accès pour la gestion des différents éléments nécessaires dans le site web (front-end).

FastAPI utilise la librairie Pydantic pour définir les modèles de données, facilitant ainsi la validation des données entrantes et sortantes. Chaque point d’accès est défini comme une fonction asynchrone associée à une route particulière. Chaque entité (Jardin, Parcelle, Action, etc.) dispose de points d’accès spécifiques pour la création, la lecture, la mise à jour et la suppression des données.

En résumé, notre API FastAPI offre un ensemble de points d’accès structurés pour la gestion des données de notre application Smart Garden et les modèles Pydantic garantissent la validité des données.

Un serveur Python fonctionne en parallèle avec un script Python dédié à la récupération des relevés des capteurs à partir du protocole MQTT. Ces données sont ensuite intégrées de manière transparente dans la base de données, assurant ainsi une mise à jour constante et en temps réel.

![Image Description](/ainablog/images/smartgarden-schema-api.png)
Schéma représentant les interactions entre les services

👉 Découvrir le dépôt GitLab du projet : [Smart Garden - GitLab](https://gitlab.imt-atlantique.fr/m20chevr/smartgarden)

## Ressources

- Dépôt GitLab du projet : [Smart Garden - GitLab](https://gitlab.imt-atlantique.fr/m20chevr/smartgarden)
- Les articles du projet : 
	- [Jardin Partagé – État de l'art](https://telefab.fr/2023/10/22/jardin-partage/)
	- [Jardin Partagé – Enquête terrain](https://telefab.fr/2023/10/27/jardin-partage-enquete-terrain/)
	- [Jardin Partagé – Solution Technique](https://telefab.fr/2024/01/15/jardin-partage-solution-technique/)
