.. _part3:


*************************************************************************************************
Module 3 | Analyse et manipulation de données
*************************************************************************************************

Objectifs
=========

À l'issue de ce module, chaque étudiant.e sera capable dans les deux langages (Python et R) de :

* Importer des données de différents formats (CSV, Excel, JSON)
* Identifier et traiter les valeurs manquantes et aberrantes
* Effectuer des transformations et des manipulations de données
* Calculer des statistiques descriptives (moyennes, médianes, corrélations)
* Filtrer, trier et grouper des données
* Fusionner et joindre des ensembles de données
* Appliquer une méthodologie d'analyse exploratoire


Notes théoriques
=======================================

Exercice introductif
""""""""""""""""""""

1. Quels formats de données avez-vous déjà manipulés dans vos travaux académiques ou professionnels ?
2. Comment traitez-vous actuellement les données manquantes ou incohérentes dans vos analyses ?
3. Qu'est-ce qu'une analyse exploratoire de données (EDA) selon vous ?
4. Quels sont les défis courants lors de l'importation et du nettoyage de données ?
5. Avez-vous déjà utilisé pandas (Python) ou dplyr/tidyverse (R) ?


Notes
""""""

**Import de données**

Python (pandas) :

- ``pd.read_csv("fichier.csv")`` : Lire un fichier CSV
- ``pd.read_excel("fichier.xlsx", sheet_name="Feuille1")`` : Lire Excel
- ``pd.read_json("fichier.json")`` : Lire JSON
- Paramètres courants : ``sep``, ``encoding``, ``na_values``, ``header``

R :

- ``read.csv("fichier.csv")`` : Lire CSV (base R)
- ``read_excel("fichier.xlsx", sheet = "Feuille1")`` : Lire Excel (readxl)
- ``fromJSON("fichier.json")`` : Lire JSON (jsonlite)
- ``read_csv("fichier.csv")`` : Lire CSV (tidyverse/readr) - plus rapide

**Exploration initiale**

Python :

- ``df.head()`` / ``df.tail()`` : Premières/dernières lignes
- ``df.shape`` : Dimensions (lignes, colonnes)
- ``df.info()`` : Types de données et valeurs non-nulles
- ``df.describe()`` : Statistiques descriptives
- ``df.columns`` : Noms des colonnes
- ``df.dtypes`` : Types de chaque colonne

R :

- ``head(df)`` / ``tail(df)`` : Premières/dernières lignes
- ``dim(df)`` : Dimensions
- ``str(df)`` : Structure des données
- ``summary(df)`` : Statistiques descriptives
- ``names(df)`` ou ``colnames(df)`` : Noms des colonnes
- ``sapply(df, class)`` : Types de chaque colonne

**Valeurs manquantes**

Python :

- ``df.isna()`` ou ``df.isnull()`` : Détecter les NA
- ``df.isna().sum()`` : Compter les NA par colonne
- ``df.dropna()`` : Supprimer les lignes avec NA
- ``df.fillna(valeur)`` : Remplacer les NA
- ``df.fillna(df.mean())`` : Remplacer par la moyenne

R :

- ``is.na(df)`` : Détecter les NA
- ``colSums(is.na(df))`` : Compter les NA par colonne
- ``na.omit(df)`` : Supprimer les lignes avec NA
- ``df[is.na(df)] <- valeur`` : Remplacer les NA
- Tidyverse : ``replace_na(df, list(col = valeur))``

**Sélection et filtrage**

Python (pandas) :

- ``df['colonne']`` ou ``df.colonne`` : Sélectionner une colonne
- ``df[['col1', 'col2']]`` : Sélectionner plusieurs colonnes
- ``df[df['age'] > 20]`` : Filtrer les lignes
- ``df.loc[ligne, colonne]`` : Sélection par label
- ``df.iloc[index, colonne]`` : Sélection par position
- ``df.query('age > 20 and note > 15')`` : Requête SQL-like

R (base) :

- ``df$colonne`` ou ``df[, "colonne"]`` : Sélectionner une colonne
- ``df[, c("col1", "col2")]`` : Plusieurs colonnes
- ``df[df$age > 20, ]`` : Filtrer les lignes
- ``subset(df, age > 20, select = c(nom, age))`` : Subset complet

R (dplyr - tidyverse) :

- ``select(df, col1, col2)`` : Sélectionner colonnes
- ``filter(df, age > 20)`` : Filtrer lignes
- ``arrange(df, desc(note))`` : Trier
- ``mutate(df, nouvelle_col = col1 + col2)`` : Créer/modifier colonne
- ``%>%`` : Pipe pour enchaîner les opérations

**Transformation de données**

Python :

- ``df['nouvelle'] = df['col1'] + df['col2']`` : Créer colonne
- ``df.rename(columns={'ancien': 'nouveau'})`` : Renommer
- ``df.drop('colonne', axis=1)`` : Supprimer colonne
- ``df.drop_duplicates()`` : Supprimer doublons
- ``df.sort_values('colonne', ascending=False)`` : Trier

R (dplyr) :

- ``mutate(df, nouvelle = col1 + col2)`` : Créer colonne
- ``rename(df, nouveau = ancien)`` : Renommer
- ``select(df, -colonne)`` : Supprimer colonne
- ``distinct(df)`` : Supprimer doublons
- ``arrange(df, desc(colonne))`` : Trier

**Groupement et agrégation**

Python :

- ``df.groupby('categorie').mean()`` : Moyenne par groupe
- ``df.groupby('categorie').agg({'note': ['mean', 'std']})`` : Plusieurs stats
- ``df.groupby(['cat1', 'cat2']).sum()`` : Groupement multiple
- ``df.pivot_table(values='note', index='classe', columns='matiere')`` : Tableau croisé

R (dplyr) :

- ``group_by(df, categorie) %>% summarise(moyenne = mean(note))`` : Moyenne par groupe
- ``df %>% group_by(categorie) %>% summarise(across(c(note1, note2), mean))`` : Plusieurs colonnes
- ``aggregate(note ~ categorie, data = df, FUN = mean)`` : Base R

**Fusion de données**

Python :

- ``pd.merge(df1, df2, on='id')`` : Jointure sur une colonne
- ``pd.merge(df1, df2, how='left')`` : Left join
- ``pd.concat([df1, df2])`` : Concaténer verticalement
- ``pd.concat([df1, df2], axis=1)`` : Concaténer horizontalement

R (dplyr) :

- ``inner_join(df1, df2, by = "id")`` : Inner join
- ``left_join(df1, df2, by = "id")`` : Left join
- ``right_join(df1, df2, by = "id")`` : Right join
- ``full_join(df1, df2, by = "id")`` : Full join
- ``bind_rows(df1, df2)`` : Concaténer verticalement
- ``bind_cols(df1, df2)`` : Concaténer horizontalement

**Statistiques descriptives**

Python :

- ``df['colonne'].mean()`` : Moyenne
- ``df['colonne'].median()`` : Médiane
- ``df['colonne'].std()`` : Écart-type
- ``df['colonne'].min()`` / ``df['colonne'].max()`` : Min/Max
- ``df.corr()`` : Matrice de corrélation
- ``df['col1'].corr(df['col2'])`` : Corrélation entre deux colonnes

R :

- ``mean(df$colonne)`` : Moyenne
- ``median(df$colonne)`` : Médiane
- ``sd(df$colonne)`` : Écart-type
- ``min(df$colonne)`` / ``max(df$colonne)`` : Min/Max
- ``cor(df)`` : Matrice de corrélation
- ``cor(df$col1, df$col2)`` : Corrélation entre deux colonnes

**Méthodologie d'analyse exploratoire**

1. **Compréhension des données** : dimensions, types, aperçu
2. **Nettoyage** : valeurs manquantes, doublons, incohérences
3. **Transformation** : création de variables, normalisation
4. **Analyse descriptive** : statistiques, distributions
5. **Analyse des relations** : corrélations, groupements
6. **Détection d'anomalies** : outliers, valeurs aberrantes
7. **Documentation** : conclusions et insights


Tableau récapitulatif : Équivalences Python ↔ R
""""""""""""""""""""""""""""""""""""""""""""""""

.. list-table::
   :header-rows: 1
   :widths: 40 40 20

   * - Python (pandas)
     - R (dplyr/base)
     - Fonction
   * - **Import de données**
     -
     -
   * - ``pd.read_csv()``
     - ``read.csv()`` / ``read_csv()``
     - Lire CSV
   * - ``pd.read_excel()``
     - ``read_excel()``
     - Lire Excel
   * - ``pd.read_json()``
     - ``fromJSON()``
     - Lire JSON
   * - **Exploration**
     -
     -
   * - ``df.head()``
     - ``head(df)``
     - Premières lignes
   * - ``df.shape``
     - ``dim(df)``
     - Dimensions
   * - ``df.info()``
     - ``str(df)``
     - Structure
   * - ``df.describe()``
     - ``summary(df)``
     - Statistiques
   * - **Sélection**
     -
     -
   * - ``df[['col1', 'col2']]``
     - ``select(df, col1, col2)``
     - Sélectionner colonnes
   * - ``df[df['age'] > 18]``
     - ``filter(df, age > 18)``
     - Filtrer lignes
   * - ``df.loc[:, 'col']``
     - ``df$col``
     - Accéder colonne
   * - **Transformation**
     -
     -
   * - ``df.sort_values('col')``
     - ``arrange(df, col)``
     - Trier
   * - ``df['new'] = df['a'] + df['b']``
     - ``mutate(df, new = a + b)``
     - Créer colonne
   * - ``df.rename(columns={})``
     - ``rename(df, new = old)``
     - Renommer
   * - ``df.drop_duplicates()``
     - ``distinct(df)``
     - Supprimer doublons
   * - **Valeurs manquantes**
     -
     -
   * - ``df.isna()``
     - ``is.na(df)``
     - Détecter NA
   * - ``df.dropna()``
     - ``na.omit(df)``
     - Supprimer NA
   * - ``df.fillna(value)``
     - ``replace_na(df, list())``
     - Remplacer NA
   * - **Agrégation**
     -
     -
   * - ``df.groupby('cat').mean()``
     - ``group_by() %>% summarise()``
     - Grouper et agréger
   * - ``df.pivot_table()``
     - ``pivot_wider()``
     - Tableau croisé
   * - **Fusion**
     -
     -
   * - ``pd.merge(df1, df2)``
     - ``left_join(df1, df2)``
     - Fusionner
   * - ``pd.concat([df1, df2])``
     - ``bind_rows(df1, df2)``
     - Concaténer
   * - **Statistiques**
     -
     -
   * - ``df['col'].mean()``
     - ``mean(df$col)``
     - Moyenne
   * - ``df['col'].median()``
     - ``median(df$col)``
     - Médiane
   * - ``df['col'].std()``
     - ``sd(df$col)``
     - Écart-type
   * - ``df.corr()``
     - ``cor(df)``
     - Corrélations


À lire / Aller plus loin
=======================================

**Slides du cours :**

[À compléter par l'enseignant]

**Documentation officielle :**

Python :


R :


**Livres de référence :**


**Tutoriels :**



Exercices théoriques
=======================================

.. note::
   Vous devez faire ces exercices avant la prochaine séance dans les DEUX langages (Python ET R).

Exercice 1 : Import et exploration
"""""""""""""""""""""""""""""""""""

Créez un fichier CSV contenant des données d'étudiants (au moins 20 lignes) avec les colonnes : 
nom, prenom, age, filiere, note_examen1, note_examen2, note_projet, ville

1. Importez le fichier CSV en Python (pandas) et en R
2. Affichez les 5 premières et 5 dernières lignes
3. Affichez les dimensions du dataset (nombre de lignes et colonnes)
4. Affichez les types de données de chaque colonne
5. Générez un résumé statistique complet
6. Listez les filières uniques présentes dans les données

Exercice 2 : Nettoyage de données
""""""""""""""""""""""""""""""""""

À partir du dataset précédent, ajoutez intentionnellement :

- 3 valeurs manquantes dans différentes colonnes
- 2 lignes dupliquées
- 1 valeur aberrante dans une colonne numérique

Puis :

1. Identifiez et comptez les valeurs manquantes par colonne
2. Affichez le pourcentage de valeurs manquantes par colonne
3. Supprimez les lignes dupliquées
4. Remplacez les valeurs manquantes de la colonne "age" par la moyenne
5. Remplacez les valeurs manquantes des notes par 0
6. Détectez les valeurs aberrantes (outliers) dans les notes (ex: notes > 20 ou < 0)
7. Affichez le dataset nettoyé

Exercice 3 : Transformation et manipulation
""""""""""""""""""""""""""""""""""""""""""""

À partir du dataset nettoyé :

1. Créez une colonne "moyenne" qui calcule la moyenne des trois notes
2. Créez une colonne "mention" basée sur la moyenne :
   
   * "Insuffisant" : moyenne < 10
   * "Passable" : 10 ≤ moyenne < 12
   * "Assez Bien" : 12 ≤ moyenne < 14
   * "Bien" : 14 ≤ moyenne < 16
   * "Très Bien" : moyenne ≥ 16

3. Filtrez les étudiants ayant une moyenne supérieure à 12
4. Triez le dataset par ordre décroissant de moyenne
5. Sélectionnez uniquement les colonnes : nom, prenom, filiere, moyenne, mention
6. Renommez la colonne "filiere" en "specialite"

Exercice 4 : Groupement et agrégation
""""""""""""""""""""""""""""""""""""""

1. Calculez la moyenne générale par filière
2. Comptez le nombre d'étudiants par filière
3. Calculez la moyenne, la médiane et l'écart-type des notes par filière
4. Identifiez la filière avec la meilleure moyenne
5. Comptez le nombre d'étudiants par mention
6. Créez un tableau croisé : filière en lignes, mention en colonnes, avec le nombre d'étudiants

Exercice 5 : Fusion de données
"""""""""""""""""""""""""""""""

Créez un deuxième dataset avec des informations supplémentaires sur les étudiants :
nom, prenom, email, telephone

1. Fusionnez les deux datasets sur les colonnes "nom" et "prenom"
2. Vérifiez qu'il n'y a pas de perte de données
3. Identifiez les étudiants présents dans un dataset mais pas dans l'autre
4. Créez le dataset final avec toutes les informations

Exercice 6 : Analyse statistique
"""""""""""""""""""""""""""""""""

1. Calculez la matrice de corrélation entre les trois notes
2. Identifiez les deux notes les plus corrélées
3. Calculez les quartiles (Q1, Q2, Q3) pour chaque note
4. Identifiez les outliers pour chaque note (valeurs > Q3 + 1.5*IQR ou < Q1 - 1.5*IQR)
5. Calculez l'écart-type de la moyenne par filière
6. Testez si la moyenne diffère significativement entre les filières (analyse basique)


Travaux Pratiques
=======================================

.. note::
   Ces TPs ne sont PAS à rendre mais sont fortement recommandés pour préparer les modules suivants.
   Ils vous permettent de consolider vos compétences en manipulation de données qui seront
   essentielles pour les TPs 3 et 4 (Streamlit et Shiny).

TP - Analyse exploratoire de données (EDA)
"""""""""""""""""""""""""""""""""""""""""""

**Objectif :** Réaliser une analyse exploratoire complète d'un jeu de données réel.

**Description :**

Choisissez un dataset parmi les suivants (ou trouvez-en un sur Kaggle) :

- Dataset de ventes d'une boutique
- Dataset de résultats scolaires
- Dataset de données météorologiques
- Dataset de statistiques sportives
- Dataset de données de santé publique

**Étapes à suivre :**

**1. Import et découverte (Python ET R)**

- Importez le dataset
- Affichez les informations générales (dimensions, types, aperçu)
- Identifiez les variables catégorielles et numériques

**2. Nettoyage**

- Détectez et traitez les valeurs manquantes
- Identifiez et supprimez les doublons
- Vérifiez les types de données et corrigez si nécessaire
- Détectez les valeurs aberrantes

**3. Transformation**

- Créez de nouvelles variables pertinentes
- Catégorisez les variables continues si pertinent
- Normalisez ou standardisez si nécessaire

**4. Analyse descriptive**

- Calculez les statistiques descriptives pour toutes les variables numériques
- Analysez la distribution de chaque variable
- Identifiez les valeurs min, max, moyennes, médianes

**5. Analyse des relations**

- Calculez la matrice de corrélation
- Identifiez les variables fortement corrélées
- Analysez les relations entre variables catégorielles et numériques

**6. Analyse par groupes**

- Groupez les données selon une variable catégorielle pertinente
- Calculez des statistiques par groupe
- Comparez les groupes entre eux

**7. Détection d'anomalies**

- Identifiez les outliers pour chaque variable numérique
- Analysez ces outliers (erreurs de saisie ou valeurs légitimes ?)
- Décidez de leur traitement (conserver, supprimer, corriger)

**Livrables (pour votre apprentissage personnel) :**

En Python :

- Un notebook Jupyter (.ipynb) avec toute l'analyse
- Code bien commenté et organisé en sections
- Résultats et interprétations en markdown

En R :

- Un script R (.R) ou un R Markdown (.Rmd)
- Code structuré avec commentaires
- Résultats et conclusions

**Conseils :**

- Documentez chaque étape de votre analyse
- Notez les insights et observations intéressantes
- Posez-vous des questions sur les données
- Comparez les approches Python et R
- Identifiez les forces et faiblesses de chaque langage

**Critères d'auto-évaluation :**

- Complétude de l'analyse (toutes les étapes réalisées)
- Qualité du nettoyage de données
- Pertinence des transformations effectuées
- Profondeur de l'analyse statistique
- Clarté de la documentation et des commentaires

Ce TP vous prépare directement aux modules 4 et 5 sur la visualisation et le projet final !