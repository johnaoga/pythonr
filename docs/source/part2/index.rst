.. _part2:


*************************************************************************************************
Module 2 | Introduction aux fondamentaux de R
*************************************************************************************************

Objectifs
=========

À l'issue de ce module, chaque étudiant.e sera capable de :

* Manipuler les objets de base du langage R (vecteurs, matrices, data frames, listes)
* Créer et manipuler efficacement les structures de données en R
* Utiliser les fonctions d'indexation et de sélection en R
* Programmer des fonctions personnalisées en R
* Comprendre le système de packages et installer des bibliothèques
* Appliquer les bonnes pratiques de programmation en R


Notes théoriques
=======================================

Exercice introductif
""""""""""""""""""""

1. Avez-vous déjà utilisé R ou RStudio ? Quelles ont été vos premières impressions ?
2. Qu'est-ce qui différencie R des autres langages de programmation selon vous ?
3. Pourquoi R est-il particulièrement populaire en statistiques et en analyse de données ?
4. Connaissez-vous la différence entre un vecteur et une liste en R ?
5. Quels sont selon vous les avantages d'utiliser R plutôt qu'Excel pour l'analyse statistique ?


Notes
""""""
**R : Langage spécialisé pour l'analyse de données**

- R : langage open-source conçu spécifiquement pour les statistiques et l'analyse de données
- RStudio : environnement de développement intégré (IDE) qui facilite l'utilisation de R
- Syntaxe orientée vers les manipulations statistiques et vectorielles
- Vaste écosystème de packages spécialisés (CRAN : Comprehensive R Archive Network)

**Structures de données fondamentales en R**

- **Vecteurs** : séquences homogènes d'éléments du même type
  
  * Numériques : ``c(1, 2, 3, 4, 5)``
  * Caractères : ``c("a", "b", "c")``
  * Logiques : ``c(TRUE, FALSE, TRUE)``
  
- **Matrices** : tableaux à deux dimensions d'éléments homogènes
  
  * Création : ``matrix(1:9, nrow=3, ncol=3)``
  * Toutes les valeurs doivent être du même type
  
- **Data frames** : tableaux structurés où chaque colonne peut avoir un type différent
  
  * Structure la plus utilisée pour l'analyse de données
  * Équivalent des tableaux Excel ou des bases de données
  * Création : ``data.frame(nom=c("Jean", "Marie"), age=c(25, 30))``
  
- **Listes** : conteneurs flexibles pouvant contenir différents types d'objets
  
  * Peuvent contenir vecteurs, matrices, data frames, autres listes
  * Création : ``list(vecteur=1:5, texte="bonjour", data=df)``

**Différence clé : Indexation**

- R indexe à partir de 1 (le premier élément est ``x[1]``)
- Python indexe à partir de 0 (le premier élément est ``x[0]``)

**Fonctions d'indexation et de sélection**

- **Sélection par position** : ``x[3]``, ``df[1, 2]`` (ligne 1, colonne 2)
- **Sélection par nom** : ``df$nom``, ``df[["nom"]]``, ``df["nom"]``
- **Sélection conditionnelle** : ``x[x > 5]``, ``df[df$age > 20, ]``
- **Sélection de plages** : ``x[1:5]`` (éléments 1 à 5)
- **Exclusion** : ``x[-3]`` (tous sauf le 3ème), ``x[-c(1, 3)]`` (exclure 1 et 3)

**Fonctions en R**

- Définition avec ``function()``
- Peuvent avoir des paramètres avec valeurs par défaut
- Retournent automatiquement la dernière expression évaluée
- Peuvent retourner explicitement avec ``return()``

**Packages R**

- Installation : ``install.packages("nom_package")``
- Chargement : ``library(nom_package)`` ou ``require(nom_package)``
- Packages essentiels : ``dplyr``, ``ggplot2``, ``tidyr``, ``readr``

**Bonnes pratiques R**

- Utiliser des noms de variables explicites et en minuscules
- Préférer ``<-`` à ``=`` pour l'assignation (convention R)
- Commenter le code avec ``#``
- Utiliser le pipe ``%>%`` (dplyr) pour enchaîner les opérations
- Organiser le code en fonctions réutilisables
- Tester régulièrement son code avec des exemples simples

**Opérations vectorielles**

- R applique automatiquement les opérations sur tous les éléments d'un vecteur
- Recyclage : R réutilise les éléments courts pour s'adapter aux longs
- Exemple : ``c(1, 2, 3) + c(10, 20, 30)`` donne ``c(11, 22, 33)``


À lire / Aller plus loin
=======================================

**Slides du cours :**

[À compléter par l'enseignant]

**Documentation officielle :**

- `Documentation R officielle <https://www.r-project.org/>`_
- `RStudio Resources <https://education.rstudio.com/>`_
- `R for Data Science (livre gratuit en ligne) <https://r4ds.had.co.nz/>`_

**Livres de référence :**

- *R for Data Science* par Hadley Wickham et Garrett Grolemund
- *The Art of R Programming* par Norman Matloff
- *Advanced R* par Hadley Wickham (niveau avancé)
- *R Cookbook* par Paul Teetor

**Aller plus loin :**

- `R-bloggers <https://www.r-bloggers.com/>`_ - Blog communautaire R
- `Quick-R <https://www.statmethods.net/>`_ - Guide de référence rapide
- `DataCamp R Tutorials <https://www.datacamp.com/courses/free-introduction-to-r>`_
- `CRAN Task Views <https://cran.r-project.org/web/views/>`_ - Packages par domaine
- `Stack Overflow - R <https://stackoverflow.com/questions/tagged/r>`_


Exercices théoriques
=======================================

.. note::
   Vous devez faire ces exercices avant la prochaine séance.

Exercice 1 : Manipulation de vecteurs
""""""""""""""""""""""""""""""""""""""

1. Créez un vecteur numérique contenant les nombres de 1 à 20
2. Sélectionnez uniquement les nombres pairs de ce vecteur
3. Calculez la somme, la moyenne, le minimum et le maximum du vecteur
4. Créez un vecteur de caractères contenant 5 prénoms
5. Créez un vecteur logique indiquant si chaque prénom a plus de 5 lettres
6. Combinez deux vecteurs avec ``c()`` et vérifiez le résultat

Exercice 2 : Travail avec les matrices
"""""""""""""""""""""""""""""""""""""""

1. Créez une matrice 4x4 contenant les nombres de 1 à 16
2. Extrayez la deuxième ligne de la matrice
3. Extrayez la troisième colonne de la matrice
4. Calculez la somme de chaque ligne avec ``rowSums()``
5. Calculez la somme de chaque colonne avec ``colSums()``
6. Transposez la matrice avec ``t()``

Exercice 3 : Manipulation de data frames
"""""""""""""""""""""""""""""""""""""""""

1. Créez un data frame avec 5 étudiants contenant : nom, age, note1, note2, note3
2. Affichez les dimensions du data frame avec ``dim()``
3. Affichez la structure avec ``str()``
4. Sélectionnez uniquement la colonne "nom"
5. Sélectionnez les étudiants ayant plus de 20 ans
6. Ajoutez une colonne "moyenne" qui calcule la moyenne des trois notes
7. Triez le data frame par ordre décroissant de moyenne
8. Affichez un résumé statistique avec ``summary()``

Exercice 4 : Travail avec les listes
"""""""""""""""""""""""""""""""""""""

1. Créez une liste contenant : un vecteur numérique, un vecteur de caractères, et un data frame
2. Nommez les éléments de la liste
3. Accédez au deuxième élément avec ``[[2]]`` et avec ``$nom``
4. Ajoutez un nouvel élément à la liste
5. Affichez la longueur de la liste avec ``length()``

Exercice 5 : Fonctions personnalisées
""""""""""""""""""""""""""""""""""""""

1. Créez une fonction qui calcule la factorielle d'un nombre (avec une boucle)
2. Créez une fonction qui convertit des degrés Celsius en Fahrenheit
3. Créez une fonction qui prend un vecteur et retourne le nombre d'éléments positifs
4. Créez une fonction qui prend un data frame et retourne un résumé personnalisé :
   
   * Nombre de lignes et colonnes
   * Nombre de valeurs manquantes
   * Noms des colonnes numériques
   
5. Créez une fonction avec des paramètres par défaut qui calcule des statistiques (moyenne, médiane, écart-type)

Exercice 6 : Indexation avancée
""""""""""""""""""""""""""""""""

1. Créez un data frame avec 10 étudiants (nom, age, filière, note)
2. Sélectionnez les étudiants en "Informatique" avec une note > 15
3. Créez un sous-ensemble contenant uniquement les colonnes "nom" et "note"
4. Utilisez ``subset()`` pour filtrer les données
5. Utilisez l'opérateur ``%in%`` pour sélectionner plusieurs filières
6. Comptez le nombre d'étudiants par filière avec ``table()``


Travaux Pratiques
=======================================

.. note::
   Ces TPs sont à rendre et comptent pour l'évaluation finale. Bien que ces TPs utilisent R, 
   ils s'appuient aussi sur les concepts de programmation vus en Python au Module 1.

TP1 : Fondamentaux de R - Jeu "Plus ou Moins"
""""""""""""""""""""""""""""""""""""""""""""""

**Objectif :** Mettre en pratique les structures de données et de contrôle de base en R.

**Description du jeu :**

Créez un jeu "Plus ou Moins" en R où :

- Le programme génère un nombre aléatoire entre 1 et 100
- L'utilisateur doit deviner le nombre
- Le programme indique si le nombre à trouver est plus grand ou plus petit
- Le jeu compte le nombre de tentatives
- Le jeu se termine quand l'utilisateur trouve le nombre

**Fonctionnalités requises :**

1. Génération d'un nombre aléatoire 
2. Boucle de jeu avec demande de saisie utilisateur 
3. Validation des entrées (nombre entre 1 et 100)
4. Comparaison et affichage d'indices ("Plus grand", "Plus petit")
5. Compteur de tentatives
6. Message de victoire avec le nombre de tentatives
7. Option de rejouer

**Fonctionnalités bonus (optionnelles) :**

- Limite du nombre de tentatives (mode difficile)
- Système de score basé sur le nombre de tentatives
- Historique des parties jouées (stocké dans un data frame)
- Différents niveaux de difficulté (plage de nombres variable)

**Consignes :**

- Code bien structuré avec des fonctions
- Gestion des erreurs et validation des entrées
- Commentaires explicatifs pour chaque fonction
- Respect des conventions de nommage R
- Testez votre programme avec plusieurs scénarios


**Critères d'évaluation :**

- Fonctionnalité : Le programme fonctionne correctement (40%)
- Structure et organisation du code (25%)
- Gestion des erreurs et validation (20%)
- Documentation et commentaires (15%)

**À rendre avant la date limite indiquée par l'enseignant.**

**Format de rendu :** Un fichier ``tp1_plusoumoins_nom.R``


TP2 : Le Pendu en R
"""""""""""""""""""

**Objectif :** Créer un jeu du pendu en utilisant les concepts avancés de R.

**Description du jeu :**

Créez un jeu du pendu classique en R où :

- Le programme choisit un mot aléatoirement dans un vecteur prédéfini
- L'utilisateur doit deviner le mot lettre par lettre
- Le programme affiche le mot avec des underscores (_) pour les lettres non trouvées
- L'utilisateur a un nombre limité de tentatives (ex: 6)
- Le jeu se termine par une victoire (mot trouvé) ou une défaite (tentatives épuisées)

**Fonctionnalités requises :**

1. Vecteur de mots prédéfini (au moins 10 mots)
2. Sélection aléatoire d'un mot avec 
3. Affichage du mot masqué (ex: "_ _ _ _ _")
4. Saisie et validation d'une lettre
5. Mise à jour de l'affichage si la lettre est correcte
6. Gestion du nombre de tentatives restantes
7. Affichage des lettres déjà proposées 
8. Messages de victoire ou de défaite

**Fonctionnalités bonus (optionnelles) :**

- Différents niveaux de difficulté (longueur des mots, nombre de tentatives)
- Catégories de mots (animaux, pays, sports) stockées dans une liste
- Système de score et de vies
- Possibilité de proposer le mot complet
- Statistiques de jeu (taux de réussite, meilleurs scores) dans un data frame

**Consignes :**

- Code bien structuré avec des fonctions réutilisables
- Gestion des erreurs (entrées invalides, lettres déjà proposées)
- Commentaires explicatifs détaillés
- Utilisation appropriée des structures de données R (vecteurs, listes, data frames)
- Tests pour les fonctions principales


**Astuces R utiles pour ce TP :**

- ``strsplit(mot, "")[[1]]`` : Séparer un mot en lettres
- ``paste(vecteur, collapse = " ")`` : Joindre des éléments avec un séparateur
- ``toupper()`` / ``tolower()`` : Convertir en majuscules/minuscules
- ``%in%`` : Vérifier si un élément est dans un vecteur
- ``all()`` : Vérifier si tous les éléments sont TRUE
- ``cat()`` : Afficher du texte (mieux que ``print()`` pour le formatage)

**Critères d'évaluation :**

- Fonctionnalité complète du jeu (35%)
- Qualité de la structure et du code (25%)
- Gestion robuste des erreurs (20%)
- Documentation et clarté du code (15%)
- Créativité et fonctionnalités bonus (5%)

**À rendre avant la date limite indiquée par l'enseignant.**

**Format de rendu :** Un fichier ``tp2_pendu_nom.R`` et un fichier ``README.txt`` expliquant comment jouer