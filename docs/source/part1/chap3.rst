.. _part1_chap3:

**********************************
Chapitre 3 : Les fondamentaux de R
**********************************

Introduction
============

R est un langage de programmation et un environnement logiciel pour le calcul statistique et les graphiques. 
Conçu spécifiquement pour l'analyse de données, R offre une grande variété de techniques statistiques et graphiques.

Programme "Hello World" en R
============================

**Définition** : Le programme "Hello World" en R est un script simple qui affiche "Hello, World!" à l'écran. 
C'est communément utilisé comme première étape dans l'apprentissage d'un nouveau langage de programmation.

**Syntaxe** : ``print("Hello, World!")``

**Exemple** :

.. code-block:: r

   print("Hello, World!")
   # Résultat : [1] "Hello, World!"

Variables en R
==============

**Définition** : Les variables R stockent des valeurs de données. Sur la base de la valeur assignée, 
R détermine automatiquement le type de données de la variable.

**Syntaxe** : ``variable_name <- value``

**Exemple** :

.. code-block:: r

   x <- 5
   name <- "Alice"
   print(x)
   print(name)
   # Résultat :
   # [1] 5
   # [1] "Alice"

.. note::
   Il est possible d'utiliser le symbole ``=`` également, mais ``<-`` est la convention recommandée en R.

Règles de nommage pour les variables R
---------------------------------------

**Règles de nommage** :

1. Doivent commencer par une lettre ou un **point** (mais un point ne peut pas être suivi d'un nombre)
2. Peuvent contenir des lettres, des nombres, des **points** et des caractères underscore
3. Sensibles à la casse (``age``, ``Age`` et ``AGE`` sont des variables différentes)

**Exemples valides et invalides** :

.. code-block:: r

   # Valides
   variable1 <- 10
   var.name <- "test"
   .hidden <- TRUE
   mon_age <- 25
   
   # Invalides (ces lignes causeraient des erreurs)
   # 2variable <- 10  # Ne peut pas commencer par un chiffre
   # .2var <- 5       # Point ne peut pas être suivi d'un chiffre
   # var-name <- 3    # Le tiret n'est pas autorisé

Types de données R
==================

Introduction aux types
----------------------

**Définition** : Les types de données en R représentent le type de données que vous pouvez stocker dans une variable.

**Types principaux** :

* Numeric (numérique)
* Integer (entier)
* Complex (complexe)
* Logical (logique)
* Character (caractère)

Détail des types
----------------

**Numeric** : Tout nombre avec ou sans décimale

.. code-block:: r

   x <- 5
   y <- 12.5
   class(x)  # "numeric"
   class(y)  # "numeric"

**Integer** : Nombres entiers

.. code-block:: r

   x <- 5L  # Le L indique à R de stocker comme entier
   class(x)  # "integer"
   
   # Vérification
   is.integer(x)  # TRUE
   is.numeric(x)  # TRUE (les entiers sont aussi numériques)

**Complex** : Nombres complexes

.. code-block:: r

   z <- 1 + 4i
   class(z)  # "complex"
   
   # Parties réelle et imaginaire
   Re(z)  # 1
   Im(z)  # 4

**Logical** : Valeurs booléennes

.. code-block:: r

   vrai <- TRUE   # ou T
   faux <- FALSE  # ou F
   class(vrai)    # "logical"
   
   # Opérations logiques
   resultat <- 5 > 3
   print(resultat)  # TRUE

**Character** : Données texte/chaîne

.. code-block:: r

   texte <- "Hello"
   phrase <- 'Bonjour le monde'
   class(texte)  # "character"
   
   # Longueur de la chaîne
   nchar(texte)  # 5

Opérateurs R
============

Vue d'ensemble
--------------

**Définition** : Les opérateurs sont des symboles qui indiquent à R d'effectuer des manipulations mathématiques ou logiques spécifiques.

**Types d'opérateurs** :

* Arithmétiques
* Relationnels
* Logiques
* D'assignation

Opérateurs arithmétiques
------------------------

**Opérateurs** : ``+``, ``-``, ``*``, ``/``, ``^`` ou ``**``, ``%%``, ``%/%``

.. code-block:: r

   a <- 10
   b <- 3
   
   # Opérations de base
   a + b   # Addition : 13
   a - b   # Soustraction : 7
   a * b   # Multiplication : 30
   a / b   # Division : 3.333...
   
   # Puissance
   a ^ b   # 1000
   a ** b  # 1000 (alternative)
   
   # Modulo (reste de la division)
   a %% b  # 1
   
   # Division entière
   a %/% b # 3

Opérateurs relationnels
-----------------------

**Opérateurs** : ``==``, ``!=``, ``>``, ``<``, ``>=``, ``<=``

.. code-block:: r

   x <- 5
   y <- 10
   
   x == y   # Égal à : FALSE
   x != y   # Différent de : TRUE
   x > y    # Plus grand que : FALSE
   x < y    # Plus petit que : TRUE
   x >= y   # Plus grand ou égal : FALSE
   x <= y   # Plus petit ou égal : TRUE

Opérateurs logiques
-------------------

**Opérateurs** : ``&``, ``|``, ``!``, ``&&``, ``||``

.. code-block:: r

   a <- TRUE
   b <- FALSE
   
   # Opérateurs vectorisés (travaillent sur des vecteurs)
   a & b    # ET : FALSE
   a | b    # OU : TRUE
   !a       # NON : FALSE
   
   # Exemple avec vecteurs
   v1 <- c(TRUE, FALSE, TRUE)
   v2 <- c(TRUE, TRUE, FALSE)
   v1 & v2  # [1] TRUE FALSE FALSE
   v1 | v2  # [1] TRUE TRUE TRUE
   
   # Opérateurs scalaires (évaluent seulement le premier élément)
   v1 && v2  # TRUE (seulement le premier élément)
   v1 || v2  # TRUE (seulement le premier élément)

Opérateurs d'assignation
------------------------

**Opérateurs** : ``<-``, ``=``, ``->``

.. code-block:: r

   # Assignation standard (recommandée)
   x <- 5
   
   # Assignation avec = (valide mais moins conventionnelle)
   y = 10
   
   # Assignation vers la droite (rare)
   15 -> z
   
   print(c(x, y, z))  # [1]  5 10 15

Fonction print()
================

**Définition** : La fonction print en R est utilisée pour afficher la valeur d'une variable ou le résultat d'un calcul.

**Syntaxe** : ``print(object)``

**Exemples** :

.. code-block:: r

   # Affichage simple
   print("Hello, R!")
   # [1] "Hello, R!"
   
   # Affichage de variables
   x <- 42
   print(x)
   # [1] 42
   
   # Affichage de vecteurs
   vec <- c(1, 2, 3, 4, 5)
   print(vec)
   # [1] 1 2 3 4 5
   
   # Sans print() dans la console interactive
   x  # Affiche aussi la valeur
   
   # cat() pour un affichage sans indices
   cat("Bonjour", "le", "monde", "\n")
   # Bonjour le monde

Fonction d'entrée
=================

**Définition** : La lecture de l'entrée utilisateur en R se fait avec la fonction ``readline``.

**Syntaxe** : ``input <- readline(prompt)``

**Exemples** :

.. code-block:: r

   # Lecture d'une chaîne
   nom <- readline("Entrez votre nom : ")
   print(paste("Bonjour", nom))
   
   # Lecture d'un nombre (nécessite conversion)
   age_str <- readline("Entrez votre âge : ")
   age <- as.numeric(age_str)
   print(paste("Dans 10 ans, vous aurez", age + 10, "ans"))
   
   # Fonction scan() pour lire des nombres directement
   # nombre <- scan(n = 1)  # Lit un nombre

Conversion de types (Casting)
==============================

**Définition** : Le casting en R implique la conversion du type d'une variable d'un type à un autre.

**Fonctions de conversion** :

.. code-block:: r

   # Conversion vers numérique
   x <- "123"
   x_num <- as.numeric(x)
   class(x_num)  # "numeric"
   
   # Conversion vers entier
   y <- 3.14
   y_int <- as.integer(y)
   print(y_int)  # 3
   
   # Conversion vers caractère
   z <- 42
   z_char <- as.character(z)
   class(z_char)  # "character"
   
   # Conversion vers logique
   a <- 1
   a_log <- as.logical(a)
   print(a_log)  # TRUE (0 devient FALSE, tout autre nombre devient TRUE)
   
   # Vérification de type
   is.numeric(x_num)    # TRUE
   is.character(z_char)  # TRUE
   is.logical(a_log)     # TRUE

Structures de contrôle
======================

Conditions if/else
------------------

.. code-block:: r

   # Structure if simple
   age <- 18
   if (age >= 18) {
     print("Majeur")
   }
   
   # Structure if/else
   note <- 15
   if (note >= 10) {
     print("Admis")
   } else {
     print("Échec")
   }
   
   # Structure if/else if/else
   score <- 85
   if (score >= 90) {
     grade <- "A"
   } else if (score >= 80) {
     grade <- "B"
   } else if (score >= 70) {
     grade <- "C"
   } else {
     grade <- "F"
   }
   print(paste("Note:", grade))
   
   # Opérateur conditionnel ifelse() (vectorisé)
   ages <- c(15, 18, 21, 16)
   statut <- ifelse(ages >= 18, "Majeur", "Mineur")
   print(statut)  # [1] "Mineur" "Majeur" "Majeur" "Mineur"

Boucles
-------

**Boucle for** :

.. code-block:: r

   # Boucle sur une séquence
   for (i in 1:5) {
     print(i)
   }
   
   # Boucle sur un vecteur
   fruits <- c("pomme", "banane", "orange")
   for (fruit in fruits) {
     print(paste("J'aime les", fruit))
   }
   
   # Boucle avec indices
   vec <- c(10, 20, 30, 40, 50)
   for (i in seq_along(vec)) {
     print(paste("Element", i, ":", vec[i]))
   }

**Boucle while** :

.. code-block:: r

   # Boucle while simple
   compteur <- 0
   while (compteur < 5) {
     print(compteur)
     compteur <- compteur + 1
   }
   
   # Boucle avec condition complexe
   x <- 100
   while (x > 10) {
     print(x)
     x <- x / 2
   }

**Boucle repeat** (spécifique à R) :

.. code-block:: r

   # Boucle repeat avec break
   x <- 1
   repeat {
     print(x)
     x <- x + 1
     if (x > 5) {
       break
     }
   }

**Contrôle de flux** :

.. code-block:: r

   # break : sort de la boucle
   for (i in 1:10) {
     if (i == 5) break
     print(i)
   }
   
   # next : passe à l'itération suivante
   for (i in 1:5) {
     if (i == 3) next
     print(i)
   }
   # Affiche : 1 2 4 5

Fonctions
=========

**Définition de fonctions** :

.. code-block:: r

   # Fonction simple
   saluer <- function() {
     print("Bonjour!")
   }
   saluer()  # Appel de la fonction
   
   # Fonction avec paramètres
   addition <- function(a, b) {
     return(a + b)
   }
   resultat <- addition(5, 3)
   print(resultat)  # 8
   
   # Fonction avec valeurs par défaut
   puissance <- function(base, exposant = 2) {
     return(base ^ exposant)
   }
   print(puissance(3))     # 9 (3^2)
   print(puissance(3, 3))  # 27 (3^3)
   
   # Retour implicite (dernière expression évaluée)
   multiplication <- function(x, y) {
     x * y  # Pas besoin de return()
   }
   
   # Fonction avec plusieurs valeurs de retour
   stats <- function(vec) {
     list(
       moyenne = mean(vec),
       mediane = median(vec),
       ecart_type = sd(vec)
     )
   }
   
   donnees <- c(1, 2, 3, 4, 5)
   resultats <- stats(donnees)
   print(resultats$moyenne)  # 3

Conclusion
==========

Ce chapitre a couvert les concepts fondamentaux de R :

* La syntaxe de base et le programme "Hello World"
* Les variables et leurs règles de nommage spécifiques à R
* Les types de données principaux en R
* Les opérateurs et leurs utilisations
* Les fonctions d'entrée/sortie
* La conversion de types
* Les structures de contrôle (conditions et boucles)
* La définition de fonctions

R se distingue de Python par plusieurs aspects :

* L'indexation commence à 1 (et non 0)
* L'opérateur d'assignation ``<-`` est préféré
* Les opérations sont naturellement vectorisées
* La syntaxe est orientée vers l'analyse statistique

Ces fondamentaux vous permettront de progresser vers des concepts plus avancés en R, 
notamment les structures de données complexes et les packages spécialisés pour l'analyse de données.
