.. _part1:


*************************************************************************************************
Chapitre 1 | Introduction et les bases de la programmation
*************************************************************************************************

Objectifs
=========

À l'issue de cette partie, chaque étudiant.e sera capable de :

* Maîtriser les structures de données fondamentales (listes, dictionnaires, tuples, vecteurs, data frames)
* Créer et manipuler efficacement les objets de base en Python et R
* Implémenter des structures de contrôle (conditions, boucles)
* Définir et utiliser des fonctions avec paramètres
* Utiliser les fonctions d'indexation et de sélection
* Gérer les erreurs et les exceptions dans un programme


Notes théoriques
=======================================

Exercice introductif
""""""""""""""""""""

1. Avez-vous déjà utilisé des outils de programmation ou de traitement de données ? Lesquels ?
2. Qu'est-ce qu'une structure de données selon vous ? Pourquoi serait-elle importante en analyse de données ?
3. Avez-vous déjà entendu parler de Python et R ? Quelles sont vos connaissances préalables sur ces langages ?
4. Dans vos études ou projets précédents, comment avez-vous traité et analysé des données ?
5. Quels sont selon vous les avantages d'utiliser un langage de programmation plutôt qu'un tableur (Excel) pour l'analyse de données ?


Notes
""""""
- Python et R : deux langages complémentaires largement utilisés en science des données
- Python : langage généraliste, syntaxe claire, vaste écosystème de bibliothèques
- R : langage spécialisé pour les statistiques et l'analyse de données
- Les structures de données sont fondamentales pour organiser et manipuler l'information
- Python utilise des structures natives : listes (séquences modifiables), tuples (séquences immuables), dictionnaires (associations clé-valeur)
- R privilégie des structures orientées analyse : vecteurs (séquences homogènes), matrices, data frames (tableaux structurés), listes (conteneurs flexibles)
- Différence majeure : Python indexe à partir de 0, R indexe à partir de 1
- Les structures de contrôle (if/else, for, while) permettent de créer des programmes dynamiques
- Les fonctions permettent de réutiliser du code, améliorer la lisibilité et faciliter la maintenance
- La gestion d'erreurs (try-except en Python, tryCatch en R) est essentielle pour créer des programmes robustes
- Un code de qualité = lisible + bien structuré + documenté + testé


A lire / Aller plus loin
=======================================

Slides du cours :

Documentation officielle :

Livres de référence :

Aller plus loin :

Exercices théoriques
=======================================

.. note::
   Vous devez faire ces exercices avant la prochaine séance.

Exercice 1 : Structures de données
""""""""""""""""""""""""""""""""""""

- Créez une liste Python contenant les nombres de 1 à 10, puis affichez les nombres pairs
- Créez un dictionnaire Python représentant un étudiant (nom, âge, notes)
- Créez un vecteur R avec les mêmes nombres, puis calculez leur moyenne
- Créez un data frame R avec 3 étudiants et leurs informations

Exercice 2 : Structures de contrôle
""""""""""""""""""""""""""""""""""""

- Écrivez une fonction Python qui vérifie si un nombre est premier
- Écrivez une boucle qui affiche la table de multiplication d'un nombre donné
- Écrivez une fonction R qui calcule la factorielle d'un nombre
- Utilisez une structure conditionnelle pour catégoriser des notes (A, B, C, D, F)

Exercice 3 : Gestion d'erreurs
"""""""""""""""""""""""""""""""

- Écrivez un programme Python qui demande un nombre à l'utilisateur et gère les erreurs de saisie
- Créez une fonction qui divise deux nombres et gère la division par zéro
- En R, écrivez une fonction qui lit un fichier et gère les erreurs si le fichier n'existe pas



Travaux Pratiques
=======================================

.. note::
   Ces TPs sont à rendre et comptent pour l'évaluation finale.

TP1 : Fondamentaux de Python et R
"""""""""""""""""""""""""""""""""""""""

**Objectif :** Mettre en pratique les structures de données et de contrôle de base.

**Consignes :** 
- Implémenter les fonctions demandées en Python ET en R
- Tester vos fonctions avec plusieurs exemples
- Commenter votre code
- Rendre un fichier .py et un fichier .R

**À rendre avant la date limite indiquée par l'enseignant.**


TP2 : Le Pendu 
""""""""""""""""""""

**Objectif :** Créer un jeu du pendu en utilisant les concepts appris.

**Fonctionnalités requises :**
- Choisir un mot aléatoirement dans une liste
- Afficher le mot avec des underscores pour les lettres non trouvées
- Gérer les tentatives de l'utilisateur
- Compter le nombre d'essais restants
- Afficher un message de victoire ou de défaite

**Consignes :**
- Implémenter le jeu en Python OU en R (au choix)
- Code bien structuré avec des fonctions
- Gestion des erreurs (entrées invalides)
- Commentaires explicatifs

**À rendre avant la date limite indiquée par l'enseignant.**