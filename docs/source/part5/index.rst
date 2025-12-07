.. _part5:


*************************************************************************************************
Module 5 | Projet d'analyse de données
*************************************************************************************************

Objectifs
=========

À l'issue de ce module, chaque étudiant.e sera capable de :

* Formuler des questions de recherche pertinentes à partir d'un jeu de données
* Appliquer une méthodologie complète d'analyse exploratoire de données
* Intégrer toutes les compétences acquises (manipulation, analyse, visualisation)
* Développer du code Python et R fonctionnel, structuré et documenté
* Présenter les résultats d'analyse de manière professionnelle
* Rendre un code propre et exécutable au professeur


Introduction
=======================================

Le projet final constitue la synthèse de tous les modules précédents. Il s'agit d'une opportunité 
de démontrer votre maîtrise des langages Python et R dans un contexte d'analyse de données réelles.



Description du projet
=======================================

Méthodologie d'analyse exploratoire
""""""""""""""""""""""""""""""""""""

Votre projet doit suivre les étapes suivantes :

**1. Définition du contexte et des objectifs (10%)**

- Présenter le jeu de données choisi (source, description, contexte)
- Formuler 3 à 5 questions de recherche claires et pertinentes
- Justifier l'intérêt de ces questions
- Définir les objectifs de l'analyse



**2. Import et exploration initiale (10%)**

En Python ET en R :

- Importer les données (CSV, Excel, JSON)
- Afficher les dimensions, types de données, aperçu
- Identifier les variables (catégorielles, numériques, temporelles)
- Détecter les problèmes potentiels (valeurs manquantes, incohérences)

**3. Nettoyage et préparation des données (20%)**

- Traiter les valeurs manquantes 
- Identifier et gérer les valeurs aberrantes 
- Supprimer les doublons si nécessaire
- Corriger les incohérences
- Créer de nouvelles variables si pertinent 
- Normaliser ou standardiser si nécessaire

**4. Analyse exploratoire approfondie (25%)**

**Statistiques descriptives :**

- Calculer les mesures de tendance centrale (moyenne, médiane, mode)
- Calculer les mesures de dispersion (écart-type, variance, IQR)
- Analyser les distributions des variables
- Calculer les corrélations entre variables

**Analyse par groupes :**

- Segmenter les données selon des critères pertinents
- Comparer les statistiques entre groupes
- Identifier les différences significatives

**Détection de patterns :**

- Identifier des tendances temporelles (si applicable)
- Détecter des clusters ou groupements naturels
- Analyser les relations non-linéaires

**5. Visualisations (25%)**

Créer au minimum 6 visualisations pertinentes et professionnelles :

- Au moins 2 graphiques pour montrer des distributions
- Au moins 2 graphiques pour montrer des relations/corrélations
- Au moins 2 graphiques pour comparer des groupes
- Tous les graphiques doivent être :
  
  * Personnalisés (titres, labels, couleurs appropriées)
  * Lisibles et esthétiques
  * Directement liés aux questions de recherche
  * Accompagnés d'interprétations

**6. Synthèse et conclusions (10%)**

- Répondre à chaque question de recherche formulée
- Présenter les insights principaux découverts
- Discuter des limitations de l'analyse
- Proposer des pistes d'amélioration ou d'analyse future


Choix du jeu de données
=======================================

**Option 1 : Datasets proposés**

Le professeur peut proposer une liste de datasets.



**Option 2 : Dataset personnel**

Vous pouvez choisir votre propre dataset.


Livrables du projet
=======================================

Vous devez rendre les éléments suivants :

**1. Code Python (30%)**

Fichier : ``projet_python.py`` ou ``projet_python.ipynb`` (Jupyter Notebook)

Contenu :

- Import des bibliothèques nécessaires
- Import et exploration des données
- Nettoyage et préparation
- Analyses statistiques
- Visualisations
- Commentaires détaillés expliquant chaque étape
- Code structuré en sections claires
- Utilisation de fonctions pour le code répétitif


**2. Code R (30%)**

Fichier : ``projet_r.R`` ou ``projet_r.Rmd`` (R Markdown)

Contenu identique au code Python mais en R :

- Utilisation de tidyverse (dplyr, ggplot2, tidyr)
- Structure similaire avec sections commentées
- Mêmes analyses et visualisations
- Documentation claire

**3. Fichier README (10%)**

Fichier : ``README.md`` ou ``README.txt``

Contenu :

- Titre du projet
- Description du dataset (source, nombre de lignes/colonnes)
- Questions de recherche
- Instructions pour exécuter le code Python
- Instructions pour exécuter le code R
- Liste des bibliothèques/packages nécessaires
- Résumé des principaux résultats (3-5 points clés)
- Auteur et date

**4. Données (10%)**

Fichier : ``data.csv`` (ou autre format)

- Le fichier de données utilisé doit être fourni
- Si le dataset est trop volumineux (>50 MB), fournir un lien de téléchargement
- Documenter la source et la licence d'utilisation


Critères d'évaluation détaillés
=======================================

Le projet est noté sur 30% de la note finale selon la grille suivante :

**Code Python (30% du projet = 9% de la note finale)**

.. list-table::
   :header-rows: 1
   :widths: 30 15 15 20 20

   * - Critère
     - Inacceptable [0-1,25[
     - Insuffisant [1,25-2,5[
     - Correct [2,5-3,75[
     - Excellent [3,75-5]
   * - **Fonctionnalité**
     - Code non exécutable ou avec erreurs majeures
     - Code partiellement fonctionnel avec plusieurs erreurs
     - Code fonctionnel avec quelques erreurs mineures
     - Code parfaitement fonctionnel, bien structuré
   * - **Structures de données**
     - Utilisation incorrecte ou absente
     - Utilisation basique avec erreurs
     - Utilisation correcte des structures appropriées
     - Utilisation optimale et avancée des structures

**Code R (30% du projet = 9% de la note finale)**

.. list-table::
   :header-rows: 1
   :widths: 30 15 15 20 20

   * - Critère
     - Inacceptable [0-1,25[
     - Insuffisant [1,25-2,5[
     - Correct [2,5-3,75[
     - Excellent [3,75-5]
   * - **Fonctionnalité**
     - Code non exécutable ou avec erreurs majeures
     - Code partiellement fonctionnel avec plusieurs erreurs
     - Code fonctionnel avec quelques erreurs mineures
     - Code parfaitement fonctionnel, bien structuré
   * - **Objets R**
     - Utilisation incorrecte ou absente
     - Utilisation basique avec erreurs
     - Objets R utilisés correctement
     - Utilisation optimale et avancée des objets R

**Analyse exploratoire (20% du projet = 6% de la note finale)**

.. list-table::
   :header-rows: 1
   :widths: 30 15 15 20 20

   * - Critère
     - Inacceptable [0-1,25[
     - Insuffisant [1,25-2,5[
     - Correct [2,5-3,75[
     - Excellent [3,75-5]
   * - **Profondeur**
     - Analyse absente ou très superficielle
     - Analyse présente mais incomplète
     - Analyse correcte couvrant les aspects essentiels
     - Analyse complète et approfondie avec insights pertinents

**Visualisations (20% du projet = 6% de la note finale)**

.. list-table::
   :header-rows: 1
   :widths: 30 15 15 20 20

   * - Critère
     - Inacceptable [0-1,25[
     - Insuffisant [1,25-2,5[
     - Correct [2,5-3,75[
     - Excellent [3,75-5]
   * - **Qualité**
     - Graphiques absents ou non pertinents
     - Graphiques présents mais mal configurés
     - Graphiques corrects et informatifs
     - Graphiques excellents, esthétiques et très informatifs


Calendrier et modalités
=======================================

**Dates importantes**

- **Semaine 1-2** : Choix du dataset et validation par le professeur
- **Semaine 3-4** : Développement du projet
- **Semaine 5** : Finalisation et tests
- **Deadline** : [Date précise fournie par l'enseignant]

**Modalités de rendu**

- Format : Archive ZIP nommée ``Nom_Prenom_Projet.zip``
- Contenu de l'archive :
  
  * ``projet_python.ipynb`` ou ``projet_python.py``
  * ``projet_r.R`` ou ``projet_r.Rmd``
  * ``README.md``
  * ``data.csv`` (ou lien dans README)
  * ``requirements.txt`` (Python) - optionnel mais recommandé

- Mode de soumission : [Plateforme indiquée par l'enseignant]
- Retard : Pénalité de [X]% par jour de retard

**Travail individuel**

- Le projet est strictement individuel
- Tout plagiat sera sanctionné
- Vous pouvez utiliser des ressources en ligne mais devez citer vos sources
- Le code doit être votre propre travail


Conseils et bonnes pratiques
=======================================

**Pour réussir votre projet :**

1. **Commencez tôt** : Ne sous-estimez pas le temps nécessaire
2. **Choisissez un dataset qui vous intéresse** : La motivation est clé
3. **Posez de vraies questions** : Pas juste "montrer des stats"
4. **Documentez au fur et à mesure** : N'attendez pas la fin
5. **Testez régulièrement** : Vérifiez que tout fonctionne
6. **Demandez des retours** : Consultez le professeur en cas de doute
7. **Soignez la présentation** : Code lisible, graphiques clairs
8. **Relisez tout** : Vérifiez l'orthographe, la syntaxe, les résultats

**Erreurs à éviter :**

- Dataset trop simple ou trop complexe
- Questions de recherche vagues ou trop larges
- Code désorganisé sans commentaires
- Visualisations mal configurées ou non pertinentes
- Analyse superficielle sans interprétation
- Oublier de tester le code avant de rendre
- Ne pas fournir les données ou le README

**Ressources utiles :**

- Documentation des bibliothèques utilisées
- Exemples de projets sur Kaggle
- Tutoriels de visualisation
- Forums (Stack Overflow, Reddit r/datascience)
- Cours et exercices des modules précédents



Conclusion
=======================================

Ce projet final est l'occasion de démontrer toutes les compétences acquises durant ce cours. 
Prenez le temps de choisir un dataset intéressant, formulez des questions pertinentes, et 
menez une analyse rigoureuse et bien documentée.

**Bonne chance et bon travail !**

.. note::
   En cas de questions ou difficultés, n'hésitez pas à consulter le professeur pendant 
   les heures de permanence ou par email.