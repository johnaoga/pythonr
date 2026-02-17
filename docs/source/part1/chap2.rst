.. _part1_chap2:

***************************************
Chapitre 2 : Les fondamentaux de Python
***************************************

Python est un langage de programmation de haut niveau, interprété et orienté objet. Sa syntaxe claire et lisible 
en fait un excellent choix pour les débutants tout en restant puissant pour les développeurs expérimentés.


Notes théoriques
=======================================

"Hello World" 
""""""""""""""""""

Le programme "Hello World" est un script simple qui affiche "Hello, World!" à l'écran. 
C'est une façon traditionnelle de commencer l'apprentissage d'un nouveau langage de programmation.

**Syntaxe** : 

.. code-block:: python

   print("Hello, World!")

**Exemple** :

.. code-block:: python

   print("Hello, World!")
   # Résultat : Hello, World!

Variables en Python
"""""""""""""""""""

Les variables sont utilisées pour stocker des valeurs de données. En Python, une variable 
est créée au moment où vous lui assignez une valeur pour la première fois.

**Règles de nommage**

Les variables Python doivent respecter certaines règles :

* Doivent commencer par une lettre ou le caractère underscore (_)
* Ne peuvent pas commencer par un chiffre
* Peuvent contenir uniquement des caractères alphanumériques et des underscores (A-z, 0-9, et _)
* Sont **sensibles à la casse** (age, Age, et AGE sont trois variables différentes)

**Syntaxe** : ``variable_name = value``

**Exemple** :

.. code-block:: python

   x = 5
   name = "Alice"
   print(x, name)
   # Résultat : 5 Alice

Types de données en Python
""""""""""""""""""""""""""

Les types de données sont la classification ou catégorisation des éléments de données. 
Python a plusieurs types de données incluant Integer, Float, String, List, Tuple, et Dictionary.

**Types principaux** :

* Integer (entier)
* Float (nombre décimal)
* String (chaîne de caractères)
* List (liste)
* Tuple
* Dictionary (dictionnaire)
* Set (ensemble)
* Boolean (booléen)

**Taille en mémoire** : La taille en mémoire varie selon le type de données et la valeur qu'il contient.

**Exemple** :

.. code-block:: python

   integer_var = 10
   float_var = 20.5
   string_var = "Hello"

**Les littéraux**

* **Integer** : Nombres entiers, ex: ``5``
* **Float** : Nombres avec décimales, ex: ``5.0``
* **String** : Séquence de caractères, ex: ``"Hello"``
* **List** : Collection ordonnée et modifiable, ex: ``[1, 2, 3]``
* **Tuple** : Collection ordonnée et non-modifiable, ex: ``(1, 2, 3)``
* **Dictionary** : Collection avec paires clé-valeur, ex: ``{"name": "John", "age": 30}``
* **Set** : Collection non-ordonnée d'éléments uniques, ex: ``{1, 2, 3}``
* **Boolean** : Représente ``True`` ou ``False``

Opérateurs Python
"""""""""""""""""

Les opérateurs sont utilisés pour effectuer des opérations sur des variables et des valeurs. 
Python possède des opérateurs arithmétiques, de comparaison, d'assignation, logiques, d'identité, d'appartenance et binaires.

**Exemple** :

.. code-block:: python

   # Opérateur arithmétique
   a = 10
   b = 3
   print(a + b)  # Addition : 13
   print(a * b)  # Multiplication : 30

**Types d'opérateurs** :

* Opérateurs arithmétiques
* Opérateurs de comparaison (relationnels)
* Opérateurs d'assignation
* Opérateurs logiques
* Opérateurs d'identité
* Opérateurs d'appartenance
* Opérateurs binaires

**Exemple** :

- **Opérateurs arithmétiques** : ``+``, ``-``, ``*``, ``/``, ``%``, ``//``, ``**``

.. code-block:: python

   a = 10
   b = 3
   print(a + b)   # Addition : 13
   print(a - b)   # Soustraction : 7
   print(a * b)   # Multiplication : 30
   print(a / b)   # Division : 3.333...
   print(a % b)   # Modulo : 1
   print(a // b)  # Division entière : 3
   print(a ** b)  # Puissance : 1000

- **Opérateurs de comparaison** : ``==``, ``!=``, ``>``, ``<``, ``>=``, ``<=``

.. code-block:: python

   x = 5
   y = 10
   print(x == y)  # Égal à : False
   print(x != y)  # Différent de : True
   print(x > y)   # Plus grand que : False
   print(x < y)   # Plus petit que : True
   print(x >= y)  # Plus grand ou égal : False
   print(x <= y)  # Plus petit ou égal : True

- **Opérateurs d'assignation** : ``=``, ``+=``, ``-=``, ``*=``, ``/=``, etc.

.. code-block:: python

   x = 5
   x += 3   # Équivalent à x = x + 3
   print(x) # 8
   x *= 2   # Équivalent à x = x * 2
   print(x) # 16

- **Opérateurs logiques** : ``and``, ``or``, ``not``

.. code-block:: python

   a = True
   b = False
   print(a and b)  # False
   print(a or b)   # True
   print(not a)    # False

- **Opérateurs d'identité** : ``is``, ``is not``

.. code-block:: python

   x = [1, 2, 3]
   y = [1, 2, 3]
   z = x
   print(x is z)     # True (même objet)
   print(x is y)     # False (objets différents)
   print(x == y)     # True (même contenu)

- **Opérateurs d'appartenance** : ``in``, ``not in``

.. code-block:: python

   liste = [1, 2, 3, 4, 5]
   print(3 in liste)     # True
   print(6 not in liste) # True

- **Opérateurs binaires** : ``&``, ``|``, ``^``, ``~``, ``<<``, ``>>``

**Règle PEMDAS** : Parenthèses, Exposants, Multiplication/Division, Addition/Soustraction

Instruction de sortie : la fonction print()
""""""""""""""""""""""""""""""""""""""""""""""""""""""

La fonction ``print()`` est utilisée pour afficher des données à l'écran.

**Syntaxe de base** :

.. code-block:: python

   print(value1, value2, ..., sep=' ', end='\n')

**Exemples** :

.. code-block:: python

   # Affichage simple
   print("Bonjour")
   
   # Affichage de plusieurs valeurs
   print("Age:", 25)
   
   # Personnalisation du séparateur
   print("A", "B", "C", sep="-")
   # Résultat : A-B-C
   
   # Personnalisation de la fin
   print("Première ligne", end=" ")
   print("Sur la même ligne")
   # Résultat : Première ligne Sur la même ligne

Instruction de saisie : la fonction input()
""""""""""""""""""""""""""""""""""""""""

La fonction ``input()`` permet de lire une entrée de l'utilisateur.

**Syntaxe** :

.. code-block:: python

   variable = input(prompt)

**Exemple** :

.. code-block:: python

   nom = input("Entrez votre nom : ")
   print("Bonjour", nom)
   
   # Conversion de type pour les nombres
   age = int(input("Entrez votre âge : "))
   print("Dans 10 ans, vous aurez", age + 10, "ans")

Conversion de types (Casting)
""""""""""""""""""""""""""""""""""""

Le casting consiste à convertir une variable d'un type à un autre.

**Fonctions de conversion** :

* ``int()`` : Convertit en entier
* ``float()`` : Convertit en nombre décimal
* ``str()`` : Convertit en chaîne de caractères
* ``list()`` : Convertit en liste
* ``tuple()`` : Convertit en tuple
* ``bool()`` : Convertit en booléen

**Exemples** :

.. code-block:: python

   # String vers Integer
   age_str = "25"
   age_int = int(age_str)
   print(type(age_int))  # <class 'int'>
   
   # Integer vers String
   nombre = 100
   nombre_str = str(nombre)
   print(type(nombre_str))  # <class 'str'>
   
   # Float vers Integer
   prix = 19.99
   prix_int = int(prix)
   print(prix_int)  # 19
   
   # String vers Float
   taille = "1.75"
   taille_float = float(taille)
   print(taille_float)  # 1.75

Chaînes de caractères (Strings)
"""""""""""""""""""""""""""""""

Les chaînes de caractères sont des séquences de caractères entourées de guillemets.

**Création** :

.. code-block:: python

   simple = 'Hello'
   double = "World"
   multi_ligne = '''Ceci est
   une chaîne
   sur plusieurs lignes'''

**Opérations sur les chaînes** :

.. code-block:: python

   # Concaténation
   prenom = "Alice"
   nom = "Dupont"
   nom_complet = prenom + " " + nom
   print(nom_complet)  # Alice Dupont
   
   # Répétition
   echo = "Ha" * 3
   print(echo)  # HaHaHa
   
   # Indexation (commence à 0)
   mot = "Python"
   print(mot[0])   # P
   print(mot[-1])  # n (dernier caractère)
   
   # Slicing
   print(mot[0:3])  # Pyt
   print(mot[2:])   # thon
   print(mot[:4])   # Pyth

**Méthodes associées aux chaînes** :

.. code-block:: python

   texte = "  Python Programming  "
   
   # Méthodes de transformation
   print(texte.upper())      # PYTHON PROGRAMMING
   print(texte.lower())      # python programming
   print(texte.strip())      # "Python Programming" (sans espaces)
   print(texte.replace("Python", "R"))  # "  R Programming  "
   
   # Méthodes de test
   print("Python".startswith("Py"))  # True
   print("Python".endswith("on"))    # True
   print("123".isdigit())            # True
   print("abc".isalpha())            # True
   
   # Split et Join
   phrase = "Python est génial"
   mots = phrase.split()
   print(mots)  # ['Python', 'est', 'génial']
   
   rejoindre = "-".join(mots)
   print(rejoindre)  # Python-est-génial

**Formatage de chaînes**

.. code-block:: python

   nom = "Alice"
   age = 25
   
   # Méthode format()
   message1 = "Je m'appelle {} et j'ai {} ans".format(nom, age)
   
   # f-strings (Python 3.6+)
   message2 = f"Je m'appelle {nom} et j'ai {age} ans"
   
   # Formatage avec précision
   pi = 3.14159
   print(f"Pi vaut approximativement {pi:.2f}")  # 3.14


Structures de contrôle : conditions if/else
"""""""""""""""""""""""""""""""""""""""""""

Les structures de contrôle permettent de contrôler le flux d'exécution du programme. Les if/else sont des structures de contrôle qui permettent une exécution selon certaines conditions.

**Exemple** :

- **if** : s'exécute si la condition est vraie

.. code-block:: python

   age = int(input("Entrez votre âge: "))
   
   if age >= 18:
       print("Etant majeur, cette information vous concerne aussi")

   print("Ceci est destiné à tous")


- **if/else** : les instructions dans le `if` s'exécutent si la condition est vraie, sinon les instructions dans le `else` s'exécutent

.. code-block:: python

   age = 18
   
   if age >= 18:
       print("Vous êtes majeur")
   else:
       print("Vous êtes mineur")

- **if/elif/else** : permet de tester plusieurs conditions

.. code-block:: python

   score = 85
   
   if score >= 90:
       print("Excellent")
   elif score >= 80:
       print("Très bien")
   elif score >= 70:
       print("Bien")
   else:
       print("À améliorer")

- **plusieurs conditions avec des opérateurs logiques** : `and`, `or`, `not`

.. code-block:: python

   age = 25
   permis = True
   
   if age >= 18 and permis:
       print("Vous pouvez conduire")
   else:
       print("Vous ne pouvez pas conduire")


.. note:: 
   Python n'a pas de switch case, mais on peut utiliser un dictionnaire pour simuler un switch case

.. note::
   Il est possible d'écrire des conditions sur une seule ligne: `var = valeur1 if condition else valeur2`

.. code-block:: python

   age = 25
   statut = "majeur" if age >= 18 else "mineur"
   print(statut)  # majeur


Structures de contrôle : les boucles
"""""""""""""""""""""""""""""""""""""""""""""""

Les boucles sont des structures de contrôle qui permettent de répéter un bloc d'instructions plusieurs fois.

**Types de boucles** :

- **for** : répète un bloc d'instructions un nombre déterminé de fois
- **while** : répète un bloc d'instructions tant qu'une condition est vraie

**Exemple** :

- **for** :

.. code-block:: python

   for i in range(5):
       print(i)

- **while** :

.. code-block:: python

   i = 0
   while i < 5:
       print(i)
       i += 1

.. note::
   `range()` est une fonction qui retourne une séquence de nombres. Par exemple, `range(5)` retourne une séquence de 0 à 4.

**Contrôle de flux** :

- **break** : sort de la boucle
- **continue** : passe à l'itération suivante

.. code-block:: python

   for i in range(10):
       if i == 5:
           break
       print(i)
   
   for i in range(5):
       if i == 2:
           continue
       print(i)

Fonctions
""""""""""""

Les fonctions sont des blocs de code réutilisables qui effectuent une tâche spécifique. Une fonction a deux facettes:

- **Définition** : la fonction est créée
- **Appel** : la fonction est exécutée

.. code-block:: python

   # Définition de la fonction
   def saluer():
       print("Bonjour!")
   
   # Appel de la fonction
   saluer()

.. note::
   Une fonction est définie une seule fois, mais elle peut être appelée plusieurs fois.










