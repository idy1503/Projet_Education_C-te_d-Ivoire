# 📊 Analyse du système éducatif ivoirien avec Power BI

## 📌 Présentation du projet

Ce projet consiste à analyser les statistiques du système éducatif ivoirien à travers un tableau de bord interactif réalisé avec **Microsoft Power BI**.

À partir de trois fichiers Excel issus du portail ivoirien des données ouvertes [data.gouv.ci](https://data.gouv.ci/), j'ai réalisé un travail de préparation, de nettoyage, d'harmonisation et de consolidation des données relatives aux trois niveaux d'enseignement : préscolaire, primaire et secondaire.

L'objectif est de transformer des données brutes en indicateurs exploitables afin de faciliter l'analyse de l'évolution du système éducatif, la comparaison entre les niveaux d'enseignement et l'identification de certaines tendances et anomalies dans les données.

## 🎯 Objectifs du projet

- Analyser les effectifs des élèves, des enseignants et des établissements scolaires.
- Étudier la répartition des élèves entre les établissements publics et privés.
- Suivre l'évolution du nombre d'établissements par année scolaire.
- Analyser le taux de redoublement et la proportion de filles.
- Étudier le ratio élèves/enseignants selon le niveau d'enseignement.
- Comparer les principaux indicateurs du préscolaire, du primaire et du secondaire.
- Contrôler la cohérence des données issues des sources publiques.
- Concevoir un tableau de bord interactif facilitant l'exploration des indicateurs.

## 🛠️ Outils et technologies

| Outil              | Utilisation                                                        |
|--------------------|--------------------------------------------------------------------|
| Microsoft Power BI | Création du tableau de bord et visualisation des données           |
| Power Query        | Nettoyage, transformation et combinaison des données               |
| Langage M          | Gestion des étapes de transformation dans les requêtes Power Query |
| DAX                | Création des mesures et calcul des indicateurs                     |
| Microsoft Excel    | Consultation et exploitation des fichiers sources                  |
| data.gouv.ci       | Collecte des jeux de données publics                               |

## 📚 Sources des données

Les données utilisées proviennent du portail ivoirien des données ouvertes [data.gouv.ci](https://data.gouv.ci/).

Trois jeux de données ont été exploités :

| Niveau scolaire | Période   | Source                                                                                                                           |
|-----------------|-----------|----------------------------------------------------------------------------------------------------------------------------------|
|Préscolaire      |2008–2025  | [Statistiques de l'enseignement préscolaire](https://data.gouv.ci/datasets/statistiques-du-prescolaire-entre-2008-et-2025)       |
| Primaire        |2010–202 5 | [Statistiques de l'enseignement primaire](https://data.gouv.ci/datasets/statistiques-de-lenseignement-primaire-entre-2008-et-2025)
| Secondaire      |2008–2024  | [Statistiques de l'enseignement secondaire](https://data.gouv.ci/datasets/statistiques-de-lenseignement-secondaire-entre-2008-et-2018) |

Les périodes disponibles diffèrent selon le niveau d'enseignement. Les comparaisons doivent donc tenir compte des années effectivement renseignées dans chaque fichier.

## 🔄 Méthodologie de préparation des données

L'ensemble des opérations de nettoyage et de transformation a été réalisé dans **Power Query**, à travers des requêtes. Les modifications sont ainsi organisées dans un processus reproductible lors de l'actualisation des données.

### 1. Importation des fichiers Excel

Importation des trois fichiers Excel en utilisant la feuille `Données` de chaque fichier comme source brute.

### 2. Suppression des lignes de total

Filtrage de la colonne `Statut` pour exclure les lignes portant la valeur `Total`.

Cette opération permet d'éviter le double comptage des effectifs lorsque les lignes détaillées par statut sont agrégées.

### 3. Harmonisation des noms de colonnes

Renommage des colonnes afin d'obtenir des intitulés communs dans les trois requêtes.

Par exemple, les colonnes `Écoles` et `Établissement` ont été harmonisées sous un même nom. Cette étape facilite l'alignement des colonnes lors de la combinaison des données.

### 4. Ajout de la colonne `Niveau`

Ajout d'une colonne `Niveau` permettant d'identifier l'origine de chaque ligne :

- Préscolaire
- Primaire
- Secondaire

Cette information permet de comparer les indicateurs entre les niveaux d'enseignement dans un même modèle de données.

### 5. Suppression des colonnes de pourcentages et de ratios

Suppression des colonnes contenant des pourcentages et des ratios déjà calculés dans les fichiers sources.

Ces indicateurs ont ensuite été recalculés avec DAX dans Power BI afin de maîtriser les formules utilisées et d'assurer une méthode de calcul cohérente dans le rapport.

### 6. Contrôle de cohérence des données

Vérification de la concordance entre la somme des effectifs par statut et les totaux publiés dans les fichiers sources.

Ce contrôle a notamment permis de mettre en évidence une anomalie concernant l'année scolaire **2013-2014**, soulignant l'importance de vérifier la qualité des données avant de les exploiter dans une analyse.

### 7. Combinaison des trois requêtes

Utilisation de la fonctionnalité **Ajouter des requêtes en tant que nouvelle requête** dans Power Query pour regrouper les données du préscolaire, du primaire et du secondaire.

Cette opération a permis de créer une table consolidée appelée `Statistique`, qui constitue la base des analyses et des visualisations du tableau de bord.

## 🧮 Calcul des indicateurs avec DAX

Après le nettoyage et la consolidation des données, des mesures DAX ont été créées pour calculer les indicateurs nécessaires à l'analyse.

Les principaux indicateurs exploités sont :

- Nombre d'établissements.
- Nombre d'élèves.
- Nombre d'enseignants.
- Ratio élèves/enseignants.
- Pourcentage de filles.
- Pourcentage d'élèves dans le privé.
- Taux de redoublement.

Les mesures DAX permettent de centraliser les règles de calcul et d'adapter les résultats aux filtres et aux sélections effectués dans le rapport.

## 📈 Présentation du tableau de bord

Le rapport Power BI est organisé en quatre pages complémentaires.

### 🧸 1. Enseignement préscolaire

Cette page présente les principaux indicateurs du préscolaire :

- Nombre d'établissements, d'élèves et d'enseignants.
- Ratio élèves/enseignants.
- Répartition des élèves par type d'établissement.
- Évolution du nombre d'établissements par année scolaire.
- Évolution des groupes pédagogiques.

### 📚 2. Enseignement primaire

Cette page permet d'explorer les principales caractéristiques de l'enseignement primaire :

- Effectifs des élèves, des enseignants et des établissements.
- Taux de redoublement par année scolaire.
- Évolution du ratio élèves/enseignants.
- Évolution du pourcentage de filles.

### 🎓 3. Enseignement secondaire

Cette page met en évidence :

- Le nombre d'établissements et d'élèves.
- Le pourcentage de filles.
- Le taux de redoublement.
- La répartition des élèves entre le public et le privé.
- L'évolution du nombre d'établissements.
- L'évolution de la proportion d'élèves dans le privé.

### 📊 4. Synthèse des trois niveaux

Cette page rassemble les indicateurs essentiels pour faciliter les comparaisons entre le préscolaire, le primaire et le secondaire.

Elle comprend :

- Un tableau comparatif des principaux indicateurs.
- Une comparaison de la proportion de filles parmi les élèves et les enseignants.
- Une comparaison du pourcentage d'élèves scolarisés dans le privé selon le niveau d'enseignement.

### 🎛️ Interactivité

Des filtres permettent d'explorer les données selon l'année scolaire et, lorsque cela est applicable, le statut des établissements.

Les visualisations facilitent l'analyse des tendances temporelles et la comparaison des indicateurs.

## 🔍 Principaux axes d'analyse

Le tableau de bord permet notamment d'explorer les questions suivantes :

- Comment évolue le nombre d'établissements scolaires au fil des années ?
- Quelle est la répartition des élèves entre le secteur public et le secteur privé ?
- Comment évolue le ratio élèves/enseignants selon le niveau d'enseignement ?
- Quelle est la place des filles dans les effectifs scolaires et parmi les enseignants ?
- Comment évolue le taux de redoublement dans l'enseignement primaire ?
- Quelles différences observe-t-on entre les trois niveaux d'enseignement ?

Ces axes d'analyse permettent de transformer les statistiques disponibles en informations plus accessibles pour l'exploration du système éducatif ivoirien.

## 🚀 Utilisation du projet

1. Cloner ou télécharger le dépôt GitHub.
2. Ouvrir le fichier `.pbix` avec Microsoft Power BI Desktop.
3. Vérifier les chemins d'accès aux fichiers Excel si ceux-ci sont utilisés comme sources externes.
4. Actualiser les données si nécessaire.
5. Explorer les différentes pages du tableau de bord à l'aide des filtres disponibles.

## 💡 Compétences mobilisées

Ce projet m'a permis de mettre en pratique les compétences suivantes :

- Collecte et exploration de données publiques.
- Nettoyage et transformation de données avec Power Query.
- Utilisation du langage M à travers les requêtes de transformation.
- Harmonisation et combinaison de plusieurs fichiers Excel.
- Contrôle de cohérence et détection d'anomalies dans les données.
- Création de mesures analytiques avec DAX.
- Conception de visualisations adaptées aux objectifs d'analyse.
- Création d'un tableau de bord interactif avec Power BI.
- Analyse comparative et temporelle d'indicateurs.

## 👤 Auteur: Lydie KOUAKOU

**Projet personnel de Data Analytics — Système éducatif ivoirien**

Technologies : **Power BI · Power Query · DAX · Excel**

---

*Ce projet illustre une démarche d'analyse de données de bout en bout : de la collecte et de la préparation des données à la création d'indicateurs et à leur restitution dans un tableau de bord interactif.*
