.. _part4:


*************************************************************************************************
Module 4 | Visualisation de données
*************************************************************************************************

Objectifs
=========

À l'issue de ce module, chaque étudiant.e sera capable dans les deux langages (Python et R) de :

* Créer des graphiques de base (histogrammes, boxplots, nuages de points)
* Développer des visualisations avec les bibliothèques spécialisées (matplotlib, seaborn, ggplot2)
* Personnaliser l'apparence des graphiques (couleurs, légendes, titres, axes)
* Choisir le type de graphique approprié selon les données et l'objectif
* Créer des applications web interactives avec Streamlit (Python) et Shiny (R)
* Communiquer efficacement des insights à travers des visualisations


Notes théoriques
=======================================

Exercice introductif
""""""""""""""""""""

1. Quels types de graphiques connaissez-vous ? Dans quels contextes les utiliseriez-vous ?
2. Qu'est-ce qui rend une visualisation de données efficace selon vous ?
3. Avez-vous déjà créé des graphiques avec des outils de programmation ? Lesquels ?
4. Selon vous, quelles sont les erreurs courantes dans la création de visualisations ?
5. Connaissez-vous les principes de base du design de visualisation (couleurs, échelles, etc.) ?


Notes
""""""

**Principes de visualisation de données**

- **Objectif** : Choisir le graphique selon ce qu'on veut montrer
  
  * Distribution : histogramme, density plot, boxplot
  * Comparaison : bar plot, boxplot
  * Relation : scatter plot, line plot
  * Composition : pie chart, stacked bar
  * Évolution : line plot, area plot

- **Clarté** : Un bon graphique doit être immédiatement compréhensible
- **Simplicité** : Éviter la surcharge d'information
- **Honnêteté** : Ne pas déformer les données (échelles, axes)
- **Esthétique** : Un graphique agréable retient l'attention

**Bibliothèques Python**

**Matplotlib** : Bibliothèque de base, contrôle total

- ``plt.plot()`` : Courbe
- ``plt.scatter()`` : Nuage de points
- ``plt.bar()`` : Diagramme en barres
- ``plt.hist()`` : Histogramme
- ``plt.boxplot()`` : Boîte à moustaches
- Personnalisation : ``plt.title()``, ``plt.xlabel()``, ``plt.ylabel()``, ``plt.legend()``, ``plt.grid()``

**Seaborn** : Interface de haut niveau, graphiques statistiques élégants

- ``sns.histplot()`` : Histogramme avec KDE
- ``sns.boxplot()`` : Boxplot par catégorie
- ``sns.scatterplot()`` : Scatter avec régression
- ``sns.heatmap()`` : Carte de chaleur (corrélations)
- ``sns.pairplot()`` : Matrice de scatter plots
- ``sns.violinplot()`` : Violin plot
- Styles prédéfinis : ``sns.set_style("darkgrid")``

**Plotly** : Graphiques interactifs

- ``px.scatter()``, ``px.line()``, ``px.bar()``
- Zoom, hover, export intégré
- Idéal pour les applications web

**Bibliothèques R**

**ggplot2** : Grammaire des graphiques, approche déclarative

- Principe : ``ggplot(data) + geom_*() + options``
- ``geom_point()`` : Points (scatter)
- ``geom_line()`` : Ligne
- ``geom_bar()`` / ``geom_col()`` : Barres
- ``geom_histogram()`` : Histogramme
- ``geom_boxplot()`` : Boxplot
- ``geom_violin()`` : Violin plot
- ``geom_density()`` : Densité
- ``geom_heatmap()`` via ``geom_tile()`` : Carte de chaleur
- Personnalisation : ``labs()``, ``theme()``, ``scale_*()``, ``facet_*()``

**Base R Graphics** : Fonctions de base

- ``plot()`` : Graphique générique
- ``hist()`` : Histogramme
- ``boxplot()`` : Boxplot
- ``barplot()`` : Diagramme en barres
- Moins flexible que ggplot2 mais plus rapide pour des graphiques simples

**Applications web interactives**

**Streamlit (Python)**

Framework pour créer des applications de data science sans HTML/CSS/JS

Composants clés :

- ``st.title()`` : Titre principal
- ``st.header()`` / ``st.subheader()`` : Sous-titres
- ``st.write()`` : Texte, dataframes, graphiques
- ``st.dataframe()`` : Tableau interactif
- ``st.pyplot(fig)`` : Graphique matplotlib
- ``st.plotly_chart(fig)`` : Graphique plotly (interactif)
- ``st.selectbox()`` : Menu déroulant
- ``st.slider()`` : Curseur
- ``st.multiselect()`` : Sélection multiple
- ``st.file_uploader()`` : Upload de fichiers
- ``st.columns()`` : Layout en colonnes
- ``st.sidebar`` : Barre latérale

Structure typique :

.. code-block:: python

   import streamlit as st
   import pandas as pd
   import matplotlib.pyplot as plt
   
   st.title("Mon Application")
   
   # Sidebar
   st.sidebar.header("Paramètres")
   option = st.sidebar.selectbox("Choisir", ["A", "B"])
   
   # Main content
   df = pd.read_csv("data.csv")
   st.dataframe(df)
   
   # Graphique
   fig, ax = plt.subplots()
   ax.plot(df['x'], df['y'])
   st.pyplot(fig)

**Shiny (R)**

Framework pour créer des applications web interactives en R

Structure ui/server :

.. code-block:: r

   library(shiny)
   
   # Interface utilisateur
   ui <- fluidPage(
     titlePanel("Mon Application"),
     
     sidebarLayout(
       sidebarPanel(
         selectInput("var", "Variable:", choices = names(df)),
         sliderInput("bins", "Bins:", min = 5, max = 50, value = 30)
       ),
       
       mainPanel(
         plotOutput("plot"),
         tableOutput("table")
       )
     )
   )
   
   # Logique serveur
   server <- function(input, output) {
     output$plot <- renderPlot({
       hist(df[[input$var]], breaks = input$bins)
     })
     
     output$table <- renderTable({
       head(df)
     })
   }
   
   # Lancer l'app
   shinyApp(ui = ui, server = server)

Composants UI Shiny :

- ``titlePanel()`` : Titre
- ``sidebarLayout()`` : Layout avec sidebar
- ``selectInput()`` : Menu déroulant
- ``sliderInput()`` : Curseur
- ``checkboxInput()`` : Case à cocher
- ``textInput()`` : Champ texte
- ``fileInput()`` : Upload fichier
- ``plotOutput()`` : Zone pour graphique
- ``tableOutput()`` : Zone pour tableau
- ``textOutput()`` : Zone pour texte

Composants Server Shiny :

- ``renderPlot({})`` : Générer graphique
- ``renderTable({})`` : Générer tableau
- ``renderText({})`` : Générer texte
- ``reactive({})`` : Données réactives
- ``observe({})`` : Observer changements
- ``input$nom`` : Accéder aux inputs


Tableau comparatif : Python ↔ R Visualisation
""""""""""""""""""""""""""""""""""""""""""""""

.. list-table::
   :header-rows: 1
   :widths: 40 40 20

   * - Python
     - R
     - Type de graphique
   * - **Matplotlib/Seaborn**
     - **ggplot2**
     -
   * - ``plt.plot(x, y)``
     - ``geom_line()``
     - Courbe
   * - ``plt.scatter(x, y)``
     - ``geom_point()``
     - Nuage de points
   * - ``plt.bar(x, y)``
     - ``geom_bar()`` / ``geom_col()``
     - Barres
   * - ``plt.hist(x)``
     - ``geom_histogram()``
     - Histogramme
   * - ``plt.boxplot(x)``
     - ``geom_boxplot()``
     - Boxplot
   * - ``sns.heatmap(data)``
     - ``geom_tile()``
     - Carte de chaleur
   * - ``sns.violinplot()``
     - ``geom_violin()``
     - Violin plot
   * - ``sns.pairplot(df)``
     - ``pairs()`` / ``GGally::ggpairs()``
     - Matrice de plots
   * - **Personnalisation**
     -
     -
   * - ``plt.title("Titre")``
     - ``ggtitle("Titre")`` / ``labs(title=)``
     - Titre
   * - ``plt.xlabel("X")``
     - ``xlab("X")`` / ``labs(x=)``
     - Label axe X
   * - ``plt.ylabel("Y")``
     - ``ylab("Y")`` / ``labs(y=)``
     - Label axe Y
   * - ``plt.legend()``
     - ``theme(legend.position=)``
     - Légende
   * - ``plt.grid(True)``
     - ``theme(panel.grid=)``
     - Grille
   * - ``plt.xlim() / ylim()``
     - ``xlim() / ylim()``
     - Limites axes
   * - ``color=, alpha=``
     - ``color=, alpha=``
     - Couleurs
   * - ``figsize=(10,6)``
     - ``width=, height=``
     - Taille figure
   * - **Apps Web**
     -
     -
   * - Streamlit
     - Shiny
     - Framework
   * - ``st.pyplot(fig)``
     - ``renderPlot({})``
     - Afficher graphique
   * - ``st.selectbox()``
     - ``selectInput()``
     - Menu déroulant
   * - ``st.slider()``
     - ``sliderInput()``
     - Curseur
   * - ``st.file_uploader()``
     - ``fileInput()``
     - Upload fichier


Choix du graphique approprié
"""""""""""""""""""""""""""""

.. list-table::
   :header-rows: 1
   :widths: 30 30 40

   * - Objectif
     - Type de données
     - Graphique recommandé
   * - Montrer une distribution
     - 1 variable continue
     - Histogramme, Density plot, Boxplot
   * - Comparer des catégories
     - 1 catégorielle + 1 continue
     - Bar plot, Boxplot par groupe
   * - Montrer une relation
     - 2 variables continues
     - Scatter plot, Regression plot
   * - Montrer une évolution
     - Temps + variable continue
     - Line plot, Area plot
   * - Montrer une composition
     - Catégories avec proportions
     - Pie chart, Stacked bar
   * - Montrer des corrélations
     - Plusieurs variables continues
     - Heatmap, Pair plot
   * - Comparer plusieurs distributions
     - 1 catégorielle + 1 continue
     - Violin plot, Multiple boxplots
   * - Montrer des valeurs extrêmes
     - 1 variable continue
     - Boxplot, Scatter avec seuils


À lire / Aller plus loin
=======================================

**Slides du cours :**


**Documentation officielle :**

Python :

- `Matplotlib Documentation <https://matplotlib.org/stable/contents.html>`_
- `Seaborn Gallery <https://seaborn.pydata.org/examples/index.html>`_
- `Streamlit Documentation <https://docs.streamlit.io/>`_
- `Plotly Python <https://plotly.com/python/>`_

R :

- `ggplot2 Documentation <https://ggplot2.tidyverse.org/>`_
- `R Graphics Cookbook <https://r-graphics.org/>`_
- `Shiny Documentation <https://shiny.rstudio.com/>`_
- `Shiny Gallery <https://shiny.rstudio.com/gallery/>`_

**Livres de référence :**



Exercices théoriques
=======================================

.. note::
   Vous devez faire ces exercices avant la prochaine séance dans les DEUX langages (Python ET R).

Exercice 1 : Graphiques de base
""""""""""""""""""""""""""""""""

Utilisez le dataset du Chapitre 3 :

1. Créez un histogramme de la distribution des moyennes
2. Créez un boxplot des moyennes par filière
3. Créez un scatter plot entre l'âge et la moyenne
4. Créez un bar plot du nombre d'étudiants par filière
5. Pour chaque graphique, ajoutez : titre, labels des axes, couleurs appropriées





Travaux Pratiques
=======================================

.. note::
   Ces TPs sont à rendre et comptent pour l'évaluation finale (8% chacun).

TP3 : Analyse de données et visualisation avec Streamlit
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""

**Objectif :** Créer une application web interactive d'analyse de données avec Streamlit.

**Description :**

Développez une application Streamlit complète permettant d'analyser et visualiser un jeu de données.
L'utilisateur doit pouvoir charger ses propres données CSV et explorer interactivement.

**Fonctionnalités requises :**

**1. Page d'accueil et upload (20%)**

- Titre et description de l'application
- Widget ``st.file_uploader()`` pour charger un fichier CSV
- Validation du fichier (format, contenu)
- Message d'erreur clair si le fichier est invalide
- Option pour utiliser un dataset d'exemple si pas de fichier uploadé

**2. Exploration des données (25%)**

- Afficher les premières lignes avec ``st.dataframe()``
- Afficher les dimensions du dataset
- Afficher les types de colonnes
- Calculer et afficher les statistiques descriptives
- Compter et afficher les valeurs manquantes
- Permettre de filtrer les colonnes à afficher

**3. Visualisations interactives (40%)**

Créer au minimum 4 types de visualisations différentes :

- **Histogramme** : avec sélection de la variable et nombre de bins via slider
- **Boxplot** : avec sélection de la variable numérique et de la variable catégorielle
- **Scatter plot** : avec sélection des variables X et Y, et option de coloration par catégorie
- **Heatmap de corrélation** : pour les variables numériques

Chaque visualisation doit :

- Être personnalisée (titre, labels, couleurs)
- S'adapter automatiquement aux données chargées
- Avoir des contrôles interactifs dans la sidebar

**4. Filtres et interactions (15%)**

Dans la sidebar, ajouter :

- ``st.selectbox()`` : Sélection de la variable à analyser
- ``st.slider()`` : Filtrage par plage de valeurs
- ``st.multiselect()`` : Sélection de catégories spécifiques
- ``st.checkbox()`` : Options d'affichage (grille, légende, etc.)

Les graphiques doivent se mettre à jour automatiquement selon les filtres.

**Fonctionnalités bonus (optionnelles) :**

- Téléchargement des données filtrées en CSV
- Téléchargement des graphiques en PNG
- Onglets multiples (``st.tabs()``) pour organiser l'application
- Graphiques Plotly interactifs au lieu de matplotlib
- Analyse de séries temporelles si données temporelles
- Tests statistiques simples (t-test, ANOVA)


**Consignes techniques :**

- Code propre, commenté et bien structuré
- Utiliser des fonctions pour organiser le code
- Gérer toutes les erreurs possibles (fichier vide, colonnes manquantes, etc.)
- Tester avec différents datasets
- Interface intuitive et professionnelle



**Critères d'évaluation :**

- Upload et validation des données (20%)
- Exploration et statistiques descriptives (25%)
- Qualité et diversité des visualisations (40%)
- Interactivité et filtres (15%)
- **Bonus** : Fonctionnalités supplémentaires, design, créativité (jusqu'à 10% supplémentaires)

**À rendre avant la date limite indiquée par l'enseignant.**

**Format de rendu :** 
- Un fichier ``tp3_streamlit.py``
- Un fichier ``requirements.txt`` avec les dépendances
- Un fichier ``README.md`` expliquant comment lancer l'application


TP4 : Analyse de données et visualisation avec Shiny
"""""""""""""""""""""""""""""""""""""""""""""""""""""

**Objectif :** Créer une application web interactive d'analyse de données avec Shiny (R).

**Description :**

Développez une application Shiny complète permettant d'analyser et visualiser un jeu de données.
L'utilisateur doit pouvoir charger ses propres données CSV et explorer interactivement.

**Fonctionnalités requises :**

**1. Interface utilisateur (UI) - Structure (20%)**


**2. Logique serveur - Exploration (25%)**

- Lecture du fichier CSV uploadé
- Affichage des premières lignes avec ``renderTable()``
- Calcul et affichage des statistiques descriptives
- Mise à jour dynamique des choix de variables dans les menus déroulants
- Gestion des valeurs manquantes

**3. Visualisations interactives (40%)**

Créer au minimum 4 visualisations avec ggplot2 :

- **Histogramme** : Variable sélectionnée avec nombre de bins ajustable
- **Boxplot** : Par catégorie, avec sélection des variables
- **Scatter plot** : Variables X et Y sélectionnables, avec ligne de régression optionnelle
- **Heatmap de corrélation** : Pour toutes les variables numériques

Chaque visualisation doit :

- Utiliser ``renderPlot({})`` dans le serveur
- Être réactive aux changements d'inputs
- Être personnalisée (titres, couleurs, thème ggplot2)

**4. Réactivité et filtres (15%)**

- Utiliser ``reactive({})`` pour créer des données réactives filtrées
- Ajouter des filtres (par plage de valeurs, par catégorie)
- Les graphiques et statistiques doivent se mettre à jour automatiquement

**Fonctionnalités bonus (optionnelles) :**

- Téléchargement des données filtrées
- Téléchargement des graphiques en PDF
- Graphiques interactifs 
- Validation des inputs
- Messages d'erreur personnalisés
- Dashboard avec plusieurs pages 
- Tests statistiques (t-test, corrélation)



**Consignes techniques :**

- Code R propre et bien commenté
- Utiliser des fonctions réactives 
- Gérer les erreurs (fichier invalide, colonnes manquantes)
- Tester avec différents datasets
- Interface intuitive



**Critères d'évaluation :**

- Structure UI claire et ergonomique (20%)
- Exploration et statistiques descriptives (25%)
- Qualité et diversité des visualisations (40%)
- Réactivité et interactivité (15%)
- **Bonus** : Fonctionnalités supplémentaires, design, créativité (jusqu'à 10% supplémentaires)

**À rendre avant la date limite indiquée par l'enseignant.**

**Format de rendu :**
- Un fichier ``tp4_shiny.R`` (ou ``app.R``)
- Un fichier ``README.txt`` expliquant comment lancer l'application
- Liste des packages nécessaires