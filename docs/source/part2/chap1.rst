.. _part2_chap1:

***************************************************
Chapitre 1 : Manipulation de données et nettoyage
***************************************************

La manipulation et le nettoyage de données sont des étapes cruciales dans tout projet d'analyse de données. 
Ce chapitre couvre les techniques essentielles pour préparer les données à l'analyse dans Python et R.

Définition et importance
========================

**Définition** : La manipulation et le nettoyage de données consistent à préparer les données brutes pour l'analyse 
en les rendant propres et cohérentes. Cela inclut la gestion des valeurs manquantes, la suppression des doublons 
et la correction des erreurs.

**Importance** : Ces processus garantissent l'exactitude et l'exhaustivité des données pour l'analyse, 
ce qui est crucial pour prendre des décisions éclairées basées sur les données.

**Exemples Python et R** :

.. code-block:: python

   # Python (Pandas)
   import pandas as pd
   df.drop_duplicates()  # Supprime les doublons
   df.isnull().sum()     # Compte les valeurs manquantes

.. code-block:: r

   # R (Tidyverse)
   library(dplyr)
   distinct(df)          # Supprime les doublons
   sum(is.na(df))       # Compte les valeurs manquantes

Processus de préparation des données
=====================================

Vue d'ensemble
--------------

Le processus de préparation des données comprend généralement :

1. **Collecte des données** : Acquisition depuis diverses sources
2. **Nettoyage** : Traitement des problèmes de qualité
3. **Manipulation** : Transformation et restructuration
4. **Analyse** : Application des techniques statistiques

**Exploration initiale** :

.. code-block:: python

   # Python
   df.info()       # Vue d'ensemble du dataset
   df.head()       # Premières lignes
   df.describe()   # Statistiques descriptives

.. code-block:: r

   # R
   library(dplyr)
   glimpse(df)     # Vue d'ensemble structurée
   head(df)        # Premières lignes
   summary(df)     # Statistiques descriptives

Types et structures de données
===============================

Types de données
----------------

**Numériques** : Entiers et décimaux

.. code-block:: python

   # Python
   df['age'] = pd.to_numeric(df['age'])
   df.dtypes  # Vérifier les types

.. code-block:: r

   # R
   df$age <- as.numeric(df$age)
   str(df)    # Vérifier la structure

**Catégorielles** : Variables avec un nombre limité de valeurs

.. code-block:: python

   # Python
   df['category'] = pd.Categorical(df['category'])

.. code-block:: r

   # R
   df$category <- as.factor(df$category)

**Date/Heure** : Données temporelles

.. code-block:: python

   # Python
   df['date'] = pd.to_datetime(df['date'])

.. code-block:: r

   # R
   df$date <- as.Date(df$date, format="%Y-%m-%d")

**Texte** : Chaînes de caractères

.. code-block:: python

   # Python
   df['text'] = df['text'].astype(str)

.. code-block:: r

   # R
   df$text <- as.character(df$text)

Structures de données
---------------------

**Vecteurs** (éléments du même type) :

.. code-block:: python

   # Python - Liste comme vecteur
   vec = [1, 2, 3, 4, 5]
   
   # NumPy array (plus efficace)
   import numpy as np
   vec_np = np.array([1, 2, 3, 4, 5])

.. code-block:: r

   # R
   vec <- c(1, 2, 3, 4, 5)

**Listes** (collections hétérogènes) :

.. code-block:: python

   # Python
   liste = [1, "texte", 3.14, True]

.. code-block:: r

   # R
   liste <- list(1, "texte", 3.14, TRUE)

**Matrices** (tableaux 2D homogènes) :

.. code-block:: python

   # Python (NumPy)
   import numpy as np
   matrice = np.array([[1, 2], [3, 4]])

.. code-block:: r

   # R
   matrice <- matrix(c(1, 2, 3, 4), nrow=2, ncol=2)

**Data Frames** (tableaux structurés) :

.. code-block:: python

   # Python (Pandas)
   import pandas as pd
   df = pd.DataFrame({
       'nom': ['Alice', 'Bob'],
       'age': [25, 30]
   })

.. code-block:: r

   # R
   df <- data.frame(
       nom = c('Alice', 'Bob'),
       age = c(25, 30)
   )

Import de données
=================

Fichiers CSV
-------------

.. code-block:: python

   # Python
   import pandas as pd
   df = pd.read_csv('fichier.csv', 
                    encoding='utf-8',
                    sep=',',
                    na_values=['NA', 'NULL'])

.. code-block:: r

   # R (readr - tidyverse)
   library(readr)
   df <- read_csv('fichier.csv',
                  na = c("NA", "NULL"))
   
   # R (base)
   df <- read.csv('fichier.csv',
                  stringsAsFactors = FALSE)

Fichiers Excel
--------------

.. code-block:: python

   # Python
   df = pd.read_excel('fichier.xlsx', 
                      sheet_name='Feuille1',
                      header=0)

.. code-block:: r

   # R
   library(readxl)
   df <- read_excel('fichier.xlsx',
                    sheet = 'Feuille1')

Fichiers JSON
-------------

.. code-block:: python

   # Python
   df = pd.read_json('fichier.json')

.. code-block:: r

   # R
   library(jsonlite)
   df <- fromJSON('fichier.json')

Identification et traitement des problèmes de données
======================================================

Valeurs manquantes
-------------------

**Identification** :

.. code-block:: python

   # Python
   # Détecter les valeurs manquantes
   df.isnull()           # DataFrame booléen
   df.isnull().sum()     # Compte par colonne
   df.isnull().sum().sum()  # Total
   
   # Pourcentage de valeurs manquantes
   (df.isnull().sum() / len(df)) * 100

.. code-block:: r

   # R
   # Détecter les valeurs manquantes
   is.na(df)             # Matrice logique
   colSums(is.na(df))    # Compte par colonne
   sum(is.na(df))        # Total
   
   # Pourcentage de valeurs manquantes
   (colSums(is.na(df)) / nrow(df)) * 100

**Traitement** :

.. code-block:: python

   # Python
   # Supprimer les lignes avec NA
   df_clean = df.dropna()
   
   # Supprimer les colonnes avec NA
   df_clean = df.dropna(axis=1)
   
   # Remplacer par une valeur
   df_filled = df.fillna(0)
   
   # Remplacer par la moyenne
   df['col'] = df['col'].fillna(df['col'].mean())
   
   # Remplacer par la médiane
   df['col'] = df['col'].fillna(df['col'].median())
   
   # Forward fill (dernière valeur valide)
   df['col'] = df['col'].fillna(method='ffill')
   
   # Interpolation
   df['col'] = df['col'].interpolate()

.. code-block:: r

   # R
   # Supprimer les lignes avec NA
   df_clean <- na.omit(df)
   
   # Remplacer par une valeur
   df[is.na(df)] <- 0
   
   # Tidyverse - remplacer par la moyenne
   library(dplyr)
   library(tidyr)
   df <- df %>%
     mutate(col = replace_na(col, mean(col, na.rm = TRUE)))
   
   # Remplacer par la médiane
   df$col[is.na(df$col)] <- median(df$col, na.rm = TRUE)

Valeurs dupliquées
------------------

.. code-block:: python

   # Python
   # Identifier les doublons
   df.duplicated()              # Booléen par ligne
   df.duplicated().sum()        # Nombre de doublons
   
   # Afficher les doublons
   df[df.duplicated()]
   
   # Supprimer les doublons
   df_unique = df.drop_duplicates()
   
   # Supprimer selon certaines colonnes
   df_unique = df.drop_duplicates(subset=['col1', 'col2'])
   
   # Garder la dernière occurrence
   df_unique = df.drop_duplicates(keep='last')

.. code-block:: r

   # R
   # Identifier les doublons
   duplicated(df)               # Booléen par ligne
   sum(duplicated(df))          # Nombre de doublons
   
   # Afficher les doublons
   df[duplicated(df), ]
   
   # Supprimer les doublons
   df_unique <- unique(df)
   
   # Tidyverse
   library(dplyr)
   df_unique <- distinct(df)
   
   # Supprimer selon certaines colonnes
   df_unique <- distinct(df, col1, col2, .keep_all = TRUE)

Valeurs aberrantes (Outliers)
------------------------------

**Identification avec la méthode IQR** :

.. code-block:: python

   # Python
   Q1 = df['col'].quantile(0.25)
   Q3 = df['col'].quantile(0.75)
   IQR = Q3 - Q1
   
   # Définir les limites
   lower_bound = Q1 - 1.5 * IQR
   upper_bound = Q3 + 1.5 * IQR
   
   # Identifier les outliers
   outliers = df[(df['col'] < lower_bound) | (df['col'] > upper_bound)]
   
   # Visualisation
   import matplotlib.pyplot as plt
   import seaborn as sns
   
   plt.figure(figsize=(10, 6))
   sns.boxplot(data=df, x='col')
   plt.title('Détection des outliers')
   plt.show()

.. code-block:: r

   # R
   Q1 <- quantile(df$col, 0.25)
   Q3 <- quantile(df$col, 0.75)
   IQR <- Q3 - Q1
   
   # Définir les limites
   lower_bound <- Q1 - 1.5 * IQR
   upper_bound <- Q3 + 1.5 * IQR
   
   # Identifier les outliers
   outliers <- df[df$col < lower_bound | df$col > upper_bound, ]
   
   # Visualisation
   library(ggplot2)
   ggplot(df, aes(x = col)) +
     geom_boxplot() +
     theme_minimal() +
     labs(title = "Détection des outliers")

**Traitement des outliers** :

.. code-block:: python

   # Python
   # Supprimer les outliers
   df_clean = df[(df['col'] >= lower_bound) & (df['col'] <= upper_bound)]
   
   # Remplacer par les limites (winsorization)
   df.loc[df['col'] < lower_bound, 'col'] = lower_bound
   df.loc[df['col'] > upper_bound, 'col'] = upper_bound
   
   # Transformation logarithmique
   df['col_log'] = np.log1p(df['col'])

.. code-block:: r

   # R
   # Supprimer les outliers
   df_clean <- df[df$col >= lower_bound & df$col <= upper_bound, ]
   
   # Remplacer par les limites
   df$col[df$col < lower_bound] <- lower_bound
   df$col[df$col > upper_bound] <- upper_bound
   
   # Transformation logarithmique
   df$col_log <- log1p(df$col)

Transformation de données
=========================

Création de nouvelles colonnes
-------------------------------

.. code-block:: python

   # Python
   # Opération simple
   df['total'] = df['col1'] + df['col2']
   
   # Avec conditions
   df['categorie'] = pd.cut(df['age'], 
                            bins=[0, 18, 65, 100],
                            labels=['Jeune', 'Adulte', 'Senior'])
   
   # Apply fonction
   df['nouveau'] = df.apply(lambda row: row['col1'] * 2, axis=1)

.. code-block:: r

   # R
   # Opération simple
   df$total <- df$col1 + df$col2
   
   # Avec conditions
   df$categorie <- cut(df$age,
                       breaks = c(0, 18, 65, 100),
                       labels = c('Jeune', 'Adulte', 'Senior'))
   
   # Tidyverse
   library(dplyr)
   df <- df %>%
     mutate(nouveau = col1 * 2,
            categorie = case_when(
              age < 18 ~ "Jeune",
              age < 65 ~ "Adulte",
              TRUE ~ "Senior"
            ))

Agrégation et groupement
-------------------------

.. code-block:: python

   # Python
   # Groupement simple
   grouped = df.groupby('categorie').mean()
   
   # Agrégations multiples
   agg = df.groupby('categorie').agg({
       'valeur': ['mean', 'std', 'count'],
       'prix': ['sum', 'min', 'max']
   })
   
   # Pivot table
   pivot = pd.pivot_table(df, 
                          values='valeur',
                          index='categorie',
                          columns='type',
                          aggfunc='mean')

.. code-block:: r

   # R (dplyr)
   library(dplyr)
   
   # Groupement simple
   grouped <- df %>%
     group_by(categorie) %>%
     summarise(moyenne = mean(valeur))
   
   # Agrégations multiples
   agg <- df %>%
     group_by(categorie) %>%
     summarise(
       valeur_mean = mean(valeur),
       valeur_sd = sd(valeur),
       count = n(),
       prix_sum = sum(prix),
       prix_min = min(prix),
       prix_max = max(prix)
     )
   
   # Pivot table
   library(tidyr)
   pivot <- df %>%
     pivot_wider(names_from = type,
                 values_from = valeur,
                 values_fn = mean)

Fusion de données
-----------------

.. code-block:: python

   # Python
   # Inner join
   merged = pd.merge(df1, df2, on='id', how='inner')
   
   # Left join
   merged = pd.merge(df1, df2, on='id', how='left')
   
   # Outer join
   merged = pd.merge(df1, df2, on='id', how='outer')
   
   # Concaténation verticale
   concat_v = pd.concat([df1, df2], axis=0, ignore_index=True)
   
   # Concaténation horizontale
   concat_h = pd.concat([df1, df2], axis=1)

.. code-block:: r

   # R (dplyr)
   library(dplyr)
   
   # Inner join
   merged <- inner_join(df1, df2, by = "id")
   
   # Left join
   merged <- left_join(df1, df2, by = "id")
   
   # Full join
   merged <- full_join(df1, df2, by = "id")
   
   # Concaténation verticale
   concat_v <- bind_rows(df1, df2)
   
   # Concaténation horizontale
   concat_h <- bind_cols(df1, df2)

Conclusion
==========

Ce chapitre a couvert les techniques essentielles de manipulation et de nettoyage de données en Python et R :

* Identification et traitement des valeurs manquantes
* Gestion des doublons
* Détection et traitement des valeurs aberrantes
* Transformation et création de nouvelles variables
* Agrégation et groupement de données
* Fusion de datasets

Ces compétences sont fondamentales pour tout projet d'analyse de données et constituent la base 
pour les visualisations et analyses plus avancées des chapitres suivants.
