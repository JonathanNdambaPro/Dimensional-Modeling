# Data warehouse

## Introduction

Tout d’abord nous devons déterminer pourquoi nous avons besoin des données dans une entreprise.

Le premier objectif est pour les décisions opérationnelles :

- Recevoir des ordres
- Réagir aux plaintes
- Organiser les stocks
- etc

On appelle ces données des OLTP (Online Transactional Processing).

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.001.jpeg" />
</p>

Les caractéristiques des OLTP sont souvent :

- Une données à la fois
- On se concentre sur l’écriture de la données
- Historique souvent faible (on se concentre sur le présent)

Le Deuxième objectif est de comprendre notre entreprises en analysant les données que nous avons stocker tout au long de la vie de l’entreprise pour la comprendre et prendre des décisions pour le futur.

- Qu’elle est la meilleure catégorie de nos produits
- Comment se comporte nos ventes par rapport au mois dernier
- Comment améliorer notre entreprise

On appelle ces données des OLAP (Online Analytical Processing)

- Analyse d’énormément des données (de milliers à millions)
- Concentrer sur la lecture (des querys optimisées pour ça)
- Historique conséquent

Au vu des objectifs différents, on a souvent des OLTP et OLAP séparé.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.002.png" />
</p>

## Data Warehouse

Un datawarehouse est une base de données optimisées pour des objectifs d’analyses.

Il suit quelque règles :

- Facile d’utilisation
- Des performances de requêtage important (surtout en lecture)
- Permettre l’analyse de données

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.003.png" />
</p>

Les data warehouses sont la combinaison de différentes sources de données, on les centralise, les joints pour permettre une analyse complète de nos données. Comme les données des différentes sources ne sont pas issues de la même source, on doit les transformer pour qu’elles aient un format compatible au data warehouse et qu’elles puissent interagir entre elles, puis on les charge dans le data warehouse, C’est ce qu’on appelle un ETL cette méthode est celle que vous rencontrerez dans 95% des cas. à la fin on fait souvent du reporting et de la data visualisation pour le métier.

## Business intelligence

Les data darehouse ont était créé pour la Business intelligence (B.I). La Business Intelligence (BI), également appelée "intelligence d'affaires" ou "informatique décisionnelle", est un ensemble de méthodes, d'outils et de technologies utilisés pour collecter, analyser et présenter des données pertinentes afin d'aider les entreprises à prendre des décisions stratégiques éclairées. La BI vise à convertir les données brutes en informations significatives, puis en connaissances exploitables, en utilisant des techniques telles que l'extraction de données, le traitement analytique, la modélisation statistique et la visualisation des données.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.004.png" />
</p>

## Datalake vs Data warehouse

Ces termes désignent un endroit où nous pouvons centraliser nos données, mais il existe une différence notable, les datalakes sont des technologies qui sont utilisées pour stocker les données en format brutes, sans aucune transformation, ce qui nous permet (en plus des données tabulaires) de stocker des données non structurées comme les vidéos, les image et le texte.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.005.png" />
</p>

Le plus souvent on les utilise conjointement (surtout dans le cloud), le datalake sert d'espace où nous stockons les données avant de les retravailler sous format exploitable qui peuvent être chargé dans le data warehouse (si les données sont tabulaires sinon elle reste au niveau du datalake uniquement). Cependant, le datalake à quelques détracteur, la plupart des gens ont utilisé le datalake comme endroit où on peut stocker toutes les données sans réelle organisation ce qui a créé des data swamp.

Data swamp : Un "data swamp" est un terme utilisé pour décrire une situation où une entreprise ou une organisation accumule une grande quantité de données, mais sans structure ni organisation appropriée. Contrairement à un "datalake" bien géré, où les données sont organisées, catégorisées et étiquetées de manière cohérente, un "data swamp" est caractérisé par un manque de contrôle, de gouvernance et de gestion des données. Dans un "data swamp", les données peuvent être stockées dans des formats non standardisés, sans métadonnées claires ou sans documentation adéquate sur leur origine, leur signification ou leur qualité. Cela rend difficile la recherche, la récupération et l'utilisation efficace de ces données. En conséquence, les utilisateurs de l'entreprise peuvent avoir du mal à trouver les informations dont ils ont besoin, et la confiance dans la qualité et la précision des données peut être compromise.

## Les “Layers” d’un Data warehouse

un data warehouse à plusieurs couches (Layers en anglais) qui le compose.

Le premier layer est-ce qu’on appelle “staging” c’est l’étape où toutes les données qui sont censées être utilisé sont stockées sous format iso à la source (non travaillé/transformé).

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.006.png" />
</p>

On peut quelques fois faire de légères transformations comme concaténé les mêmes données en une seule table.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.007.png" />
</p>

Pour les étapes qui nécessitent des transformations plus lourdes, nous devons utiliser le Core/Data warehouse

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.008.png" />
</p>

Dans certains cas, le Core est layers finale que nous exposons au métiers

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.009.png" />
</p>

Quelques fois quand nous avons un data warehouse très grand, nous pouvons subdiviser en sous ensemble pour des besoins spécifiques et les exposer, c’est ce qu’on appelle des data mart.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.010.png" />
</p>

Dans de rare cas, quand les données sont vraiment “Raw” et nécessitent des grosses transformations, nous pouvons ajouter un nouveau layer qui est spécialisé dans le cleaning de ces données.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.011.png" />
</p>Même si on considère que le Core est considéré comme le data warehouse il est important de comprendre que tous ces élément sont des composantes du “vrai” data warehouse

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.012.png" />
</p>

## Staging Area

Le “Staging” est la partie du data warehouse qui est conçu pour recevoir les données sous formats raw/iso des source de données. C’est le E de ETL soit l’extraction (E = Extract).

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.013.png" />
</p>

À partir de cette couche, on peut commencer à transformation et les push dans le Core/Data warehouse pour la valorisation de nos données.

Les principales raisons de l’utilisation d’un staging sont :

- Nous pouvons rapidement extraire les données des OLTPs, étant le plus souvent en production, nous ne voulons pas prendre trop de temps sur des opérations directement sur ces dernières, car nous pourrions les ralentir et données une mauvaise expérience client.
- Nous voulons un format unifier pour les transformation qui vont suivre l’étape d’extraction.

## Data Mart

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.014.png" />
</p>

Le Core Data mart layers est souvent vu comme le layers qui sert de layers d’exposition des données pour que les métiers puissent commencer leur tâches pour valoriser la données, cependant il peut arriver que les data warehouse soit trop grand, dans ce cas de figure, nous allons créer des sous ensemble issus du core/data warehouse pour créer des data mart plus spécialiser (souvent un par usecase) qui rendra la tâche d’acquisition de la données plus simple pour les utilisateurs.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.015.png" />
</p>

Avantages :

- Plus facilement utilisable et user-friendly pour les profil non technique
- Augmentation des performance grâce au Dimensional modeling (prochain session du cours)

Ce concept est souvent controversé, il faut réfléchir en amont pour savoir s'il faut ou non utiliser les data mart.

## Relational Database

Une base de données où les données sont structuré comme des tables (ligne, colonne) où les données sont requétées grâce à SQL. L’une des particularité des base de données relationnelles est qu’elle utilise des “keys” (clé) qui permettent d’avoir des “relations” entre les tables.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.016.png" />
</p>

- Primary key (clé primaire) : permet d’identifier chacune des lignes de manière unique.
- Foreign key (clé étrangère) : permet de faire la jointure avec d’autres tables, cette foreign key est souvent la primary keys d’une autre table

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.017.png" />
</p>

## In-memory database

Les in-memory database sont optimisées pour les avoir de meilleures performances pour les querys ce qui implique que ce sont de bons outils pour l’analytique, elles sont souvent utilisées pour les data marts.

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.018.png" />
</p>

Les base de données traditionnelles vont aller chercher les données en deux étapes :

- Il va chercher les données dans le disque
- Une fois trouvait, elles seront transférées dans la mémoire pour être ensuite remonté les résultats

Les base de données in memory stockent toutes les données directement dans les base de données, on élimine le temps de réponse dû à l’accès au disque

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.019.png" />
</p>

Il y a certain compromis cependant :

- Quand la base de données est “éteint” elle perd toutes les informations, pour contourner cette lacune, il faut utiliser un snapshot
- Le coût est plus élevé

## OLAP Cubes

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.020.png" />
</p>

Les data warehouse sont souvent composé de deux manières :

- avec des base de données relationnelles
- avec des cubes

Nous avons déjà vu le fonctionnement des base de relationnelle, pour les Cubes les données sont organisées différemment, les cubes sont souvent vu comme des ensemble de données multidimensionnelles, à la place des tables, on utilise des arrays et la raison principale de cette nouvelle modélisation est qu’elle permet d’augmenter la performance des querys (et donc très utile pour l’analytique).

<p align="center">
  <img src="Aspose.Words.4518f7f8-6e9a-4328-a0ad-35a1f5e5d7c2.021.png" />
</p>

- Les données sont pré-calculées.
- Le langage est MDX.
- Ils doivent être utilisés uniquement pour des usecase spécifique pour ne pas augmenter la complexité (datamart)
- cette modélisation est optionnel et à faire après le star schema (cours suivant)
- De moins en moins utilisé car les hardware sont de plus en plus performant
