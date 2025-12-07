.. _part1:


*************************************************************************************************
Module 1 | Introduction aux fondamentaux de Python
*************************************************************************************************

Objectifs
=========

À l'issue de ce module, chaque étudiant.e sera capable de :

* Maîtriser les structures de données fondamentales en Python (listes, dictionnaires, tuples)
* Créer et manipuler efficacement les objets de base en Python
* Implémenter des structures de contrôle (conditions, boucles)
* Définir et utiliser des fonctions avec paramètres
* Gérer les erreurs et les exceptions dans un programme Python


Notes théoriques
=======================================

Exercice introductif
""""""""""""""""""""

1. Avez-vous déjà utilisé Python ou d'autres langages de programmation ? Lesquels ?
2. Qu'est-ce qu'une structure de données selon vous ? Pourquoi serait-elle importante en programmation ?
3. Quelles sont vos connaissances préalables sur Python ?
4. Dans vos études ou projets précédents, comment avez-vous organisé et manipulé des données ?
5. Quels sont selon vous les avantages d'utiliser Python pour l'analyse de données ?


Notes
""""""
- Python : langage de programmation généraliste, syntaxe claire et lisible, vaste écosystème de bibliothèques
- Largement utilisé en science des données, intelligence artificielle, développement web et automatisation
- Les structures de données sont fondamentales pour organiser et manipuler l'information efficacement
- **Listes** : séquences ordonnées et modifiables d'éléments (ex: `[1, 2, 3]`)
- **Tuples** : séquences ordonnées mais immuables d'éléments (ex: `(1, 2, 3)`)
- **Dictionnaires** : collections d'associations clé-valeur (ex: `{'nom': 'Jean', 'age': 25}`)
- Python indexe à partir de 0 (le premier élément est à l'indice 0)
- **Structures de contrôle** :
  
  * Conditions : `if`, `elif`, `else` pour la prise de décision
  * Boucles : `for` pour itérer sur des séquences, `while` pour des boucles conditionnelles
  
- **Fonctions** : blocs de code réutilisables définis avec `def`, acceptant des paramètres et retournant des valeurs
- **Gestion des exceptions** : mécanisme `try-except-finally` pour gérer les erreurs de manière robuste
- **Bonnes pratiques** :
  
  * Nommer les variables de manière explicite
  * Commenter le code pour expliquer la logique
  * Suivre les conventions PEP 8 (style de code Python)
  * Tester régulièrement son code
  
- Un code de qualité = lisible + bien structuré + documenté + testé


A lire / Aller plus loin
=======================================

**Slides du cours :**



**Documentation officielle :**


**Livres de référence :**


**Aller plus loin :**


Exercices théoriques
=======================================

.. note::
   Vous devez faire ces exercices avant la prochaine séance.

Exercice 1 : Manipulation de listes
""""""""""""""""""""""""""""""""""""

1. Créez une liste Python contenant les nombres de 1 à 10
2. Affichez uniquement les nombres pairs de cette liste
3. Ajoutez le nombre 11 à la fin de la liste
4. Supprimez le premier élément de la liste
5. Inversez l'ordre des éléments de la liste
6. Calculez la somme de tous les éléments

Exercice 2 : Travail avec les dictionnaires
""""""""""""""""""""""""""""""""""""""""""""

1. Créez un dictionnaire représentant un étudiant avec les clés : nom, âge, filière, notes (liste de notes)
2. Ajoutez une nouvelle clé 'email' au dictionnaire
3. Modifiez l'âge de l'étudiant
4. Calculez la moyenne des notes de l'étudiant
5. Affichez toutes les clés du dictionnaire
6. Créez une liste de 3 dictionnaires représentant 3 étudiants différents

Exercice 3 : Structures de contrôle
""""""""""""""""""""""""""""""""""""

1. Écrivez une fonction Python qui vérifie si un nombre est premier
2. Créez une fonction qui affiche la table de multiplication d'un nombre donné (de 1 à 10)
3. Écrivez une fonction qui prend une liste de nombres et retourne uniquement les nombres positifs
4. Créez une fonction qui catégorise des notes numériques en lettres :
   
   * A : 90-100
   * B : 80-89
   * C : 70-79
   * D : 60-69
   * F : 0-59

Exercice 4 : Fonctions et paramètres
"""""""""""""""""""""""""""""""""""""

1. Créez une fonction qui calcule la factorielle d'un nombre (utilisez une boucle)
2. Écrivez une fonction qui prend deux listes et retourne leur intersection (éléments communs)
3. Créez une fonction qui compte le nombre de voyelles dans une chaîne de caractères
4. Développez une fonction qui inverse une chaîne de caractères sans utiliser les fonctions intégrées

Exercice 5 : Gestion d'erreurs
"""""""""""""""""""""""""""""""

1. Écrivez un programme qui demande un nombre entier à l'utilisateur et gère les erreurs de saisie (ValueError)
2. Créez une fonction qui divise deux nombres et gère la division par zéro (ZeroDivisionError)
3. Développez une fonction qui ouvre un fichier et gère l'erreur si le fichier n'existe pas (FileNotFoundError)
4. Créez une fonction robuste qui convertit une chaîne en nombre et gère toutes les erreurs possibles


Travaux Pratiques
=======================================

.. note::
   Ces TPs sont à rendre et comptent pour l'évaluation finale.

TP1 : Fondamentaux de Python - Jeu "Plus ou Moins"
"""""""""""""""""""""""""""""""""""""""""""""""""""

**Objectif :** Mettre en pratique les structures de données et de contrôle de base en Python.

**Description du jeu :**

Créez un jeu "Plus ou Moins" où :

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
- Historique des parties jouées
- Différents niveaux de difficulté (plage de nombres variable)

**Consignes :**

- Code bien structuré avec des fonctions
- Gestion des erreurs (entrées invalides, valeurs hors limites)
- Commentaires explicatifs pour chaque fonction
- Testez votre programme avec plusieurs scénarios



**Critères d'évaluation :**

- Fonctionnalité : Le programme fonctionne correctement (40%)
- Structure et organisation du code (25%)
- Gestion des erreurs (20%)
- Documentation et commentaires (15%)

**À rendre avant la date limite indiquée par l'enseignant.**

**Format de rendu :** Un fichier `tp1_plusoumoins_nom.py`


TP2 : Le Pendu 
""""""""""""""""""""

**Objectif :** Créer un jeu du pendu en utilisant les concepts avancés de Python.

**Description du jeu :**

Créez un jeu du pendu classique où :

- Le programme choisit un mot aléatoirement dans une liste prédéfinie
- L'utilisateur doit deviner le mot lettre par lettre
- Le programme affiche le mot avec des underscores (_) pour les lettres non trouvées
- L'utilisateur a un nombre limité de tentatives (ex: 6)
- Le jeu se termine par une victoire (mot trouvé) ou une défaite (tentatives épuisées)

**Fonctionnalités requises :**

1. Liste de mots prédéfinie (au moins 10 mots)
2. Sélection aléatoire d'un mot
3. Affichage du mot masqué (ex: "_ _ _ _ _")
4. Saisie et validation d'une lettre
5. Mise à jour de l'affichage si la lettre est correcte
6. Gestion du nombre de tentatives restantes
7. Affichage des lettres déjà proposées
8. Messages de victoire ou de défaite
9. Affichage du dessin du pendu (optionnel, en ASCII art)

**Fonctionnalités bonus (optionnelles) :**

- Différents niveaux de difficulté (longueur des mots, nombre de tentatives)
- Catégories de mots (animaux, pays, sports, etc.)
- Système de score et de vies
- Possibilité de proposer le mot complet
- Interface graphique simple avec Tkinter

**Consignes :**

- Code bien structuré avec des fonctions réutilisables
- Gestion des erreurs (entrées invalides, lettres déjà proposées)
- Commentaires explicatifs détaillés
- Utilisation appropriée des structures de données (listes, dictionnaires, tuples)
- Tests unitaires pour les fonctions principales


**Critères d'évaluation :**

- Fonctionnalité complète du jeu (35%)
- Qualité de la structure et du code (25%)
- Gestion robuste des erreurs (20%)
- Documentation et clarté du code (15%)
- Créativité et fonctionnalités bonus (5%)

**À rendre avant la date limite indiquée par l'enseignant.**

**Format de rendu :** Un fichier `tp2_pendu_nom.py` et un fichier `README.txt` expliquant comment jouer