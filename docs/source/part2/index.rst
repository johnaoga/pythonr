.. _part2:


*************************************************************************************************
Chapitre 2 | Manipulation de données et visualisation
*************************************************************************************************

Objectifs
=========

À l'issue de cette partie, chaque étudiant.e sera capable dans les deux langages (Python et R) de :

* Importer des données de différents formats (CSV, Excel, JSON)
* Identifier et traiter les valeurs manquantes et aberrantes
* Effectuer des transformations et des manipulations de données
* Calculer des statistiques descriptives (moyennes, médianes, corrélations)
* Créer des graphiques de base (histogrammes, boxplots, nuages de points)
* Développer des visualisations avec les bibliothèques spécialisées
* Personnaliser l'apparence des graphiques
* Choisir le type de graphique approprié selon les données
* Créer des applications web interactives avec Streamlit (Python) et Shiny (R)


Notes théoriques
=======================================

Exercice introductif
""""""""""""""""""""

1. Quels formats de données avez-vous déjà manipulés dans vos travaux académiques ou professionnels ?
2. Comment traitez-vous actuellement les données manquantes ou incohérentes dans vos analyses ?
3. Quels outils ou logiciels avez-vous utilisés pour créer des graphiques ? Quelles ont été leurs limites ?
4. Selon vous, qu'est-ce qui rend une visualisation de données efficace ?
5. Avez-vous déjà entendu parler de bibliothèques comme pandas, matplotlib, ggplot2 ou dplyr ?


Tableau récapitulatif : Équivalences Python ↔ R
""""""""""""""""""""""""""""""""""""""""""""""""

.. list-table::
   :header-rows: 1
   :widths: 35 35 30

   * - Python
     - R
     - Fonction
   * - **Import de données**
     -
     -
   * - ``pd.read_csv()``
     - ``read.csv()``
     - Lire fichier CSV
   * - ``pd.read_excel()``
     - ``read_excel()`` (readxl)
     - Lire fichier Excel
   * - ``pd.read_json()``
     - ``fromJSON()`` (jsonlite)
     - Lire fichier JSON
   * - **Manipulation de données**
     -
     -
   * - ``df[['col1', 'col2']]``
     - ``select(df, col1, col2)``
     - Sélectionner colonnes
   * - ``df[df['age'] > 18]``
     - ``filter(df, age > 18)``
     - Filtrer lignes
   * - ``df.sort_values('col')``
     - ``arrange(df, col)``
     - Trier données
   * - ``df['new'] = df['a'] + df['b']``
     - ``mutate(df, new = a + b)``
     - Créer/modifier colonne
   * - ``df.groupby('cat').mean()``
     - ``group_by() %>% summarise()``
     - Grouper et agréger
   * - ``pd.merge(df1, df2)``
     - ``left_join(df1, df2)``
     - Fusionner DataFrames
   * - **Valeurs manquantes**
     -
     -
   * - ``df.isna()``
     - ``is.na(df)``
     - Détecter valeurs manquantes
   * - ``df.dropna()``
     - ``na.omit(df)``
     - Supprimer lignes avec NA
   * - ``df.fillna(value)``
     - ``replace_na(df, value)``
     - Remplacer NA
   * - **Statistiques descriptives**
     -
     -
   * - ``df['col'].mean()``
     - ``mean(df$col)``
     - Calculer moyenne
   * - ``df['col'].median()``
     - ``median(df$col)``
     - Calculer médiane
   * - ``df['col'].std()``
     - ``sd(df$col)``
     - Écart-type
   * - ``df.corr()``
     - ``cor(df)``
     - Matrice de corrélation
   * - ``df.describe()``
     - ``summary(df)``
     - Statistiques complètes
   * - **Visualisation**
     -
     -
   * - ``matplotlib.pyplot``
     - ``ggplot2``
     - Bibliothèque principale
   * - ``plt.hist()``
     - ``geom_histogram()``
     - Histogramme
   * - ``plt.boxplot()``
     - ``geom_boxplot()``
     - Boxplot
   * - ``plt.scatter()``
     - ``geom_point()``
     - Nuage de points
   * - ``plt.plot()``
     - ``geom_line()``
     - Courbe
   * - ``plt.bar()``
     - ``geom_bar()``
     - Diagramme en barres
   * - ``seaborn.heatmap()``
     - ``geom_tile()``
     - Carte de chaleur
   * - ``plt.title()``
     - ``ggtitle()``
     - Ajouter titre
   * - ``plt.xlabel() / ylabel()``
     - ``xlab() / ylab()``
     - Labels des axes


Applications web interactives
""""""""""""""""""""""""""""""

**Streamlit (Python)**

Streamlit permet de créer rapidement des applications web de data science sans connaissances en développement web.

* **Installation** : ``pip install streamlit``
* **Lancer une app** : ``streamlit run app.py``
* **Composants de base** :

  * ``st.title("Titre")`` : Ajouter un titre
  * ``st.write(data)`` : Afficher du texte ou des données
  * ``st.dataframe(df)`` : Afficher un DataFrame interactif
  * ``st.line_chart(df)`` : Graphique en ligne
  * ``st.bar_chart(df)`` : Graphique en barres
  * ``st.pyplot(fig)`` : Afficher un graphique matplotlib
  * ``st.selectbox()`` : Menu déroulant
  * ``st.slider()`` : Curseur de sélection
  * ``st.file_uploader()`` : Télécharger un fichier

**Shiny (R)**

Shiny permet de créer des applications web interactives pour visualiser et analyser des données en R.

* **Installation** : ``install.packages("shiny")``
* **Structure de base** :

  * ``ui`` : Interface utilisateur (layout, inputs, outputs)
  * ``server`` : Logique de l'application (calculs, graphiques)
  * ``shinyApp(ui, server)`` : Lancer l'application

* **Composants UI** :

  * ``titlePanel("Titre")`` : Titre de l'app
  * ``sidebarLayout()`` : Layout avec barre latérale
  * ``selectInput()`` : Menu déroulant
  * ``sliderInput()`` : Curseur
  * ``plotOutput("plot")`` : Zone pour afficher un graphique
  * ``tableOutput("table")`` : Zone pour afficher un tableau

* **Composants Server** :

  * ``output$plot <- renderPlot({...})`` : Générer un graphique
  * ``output$table <- renderTable({...})`` : Générer un tableau
  * ``input$variable`` : Accéder aux entrées utilisateur
  * ``reactive({...})`` : Créer des données réactives





À lire / Aller plus loin
=======================================

Slides du cours :

Livres de référence :


Tutoriels :



Exercices théoriques
=======================================

.. note::
   Vous devez faire ces exercices avant la prochaine séance.

Exercice 1 : Import et exploration
"""""""""""""""""""""""""""""""""""

1. Importez un fichier CSV contenant des données d'étudiants en Python et R
2. Affichez les 10 premières lignes, les dimensions et les types de colonnes
3. Calculez les statistiques descriptives (moyenne, médiane, écart-type) pour les notes
4. Identifiez le nombre de valeurs manquantes par colonne

Exercice 2 : Nettoyage et transformation
"""""""""""""""""""""""""""""""""""""""""

1. Supprimez les lignes avec valeurs manquantes dans la colonne "note"
2. Remplacez les valeurs manquantes de la colonne "âge" par la moyenne
3. Filtrez les données pour ne garder que les étudiants de plus de 20 ans
4. Créez une colonne "mention" : Passable (<12), AB (12-14), B (14-16), TB (>16)
5. Calculez la moyenne par mention

Exercice 3 : Visualisation
"""""""""""""""""""""""""""

Créez les visualisations suivantes en Python ET en R :

1. Histogramme de la distribution des notes
2. Boxplot des notes par mention
3. Scatter plot entre l'âge et la note
4. Bar plot du nombre d'étudiants par mention
5. Personnalisez chaque graphique (titre, labels, couleurs)

Exercice 4 : Analyse comparative
"""""""""""""""""""""""""""""""""

1. Comparez deux jeux de données (ex: notes 2023 vs 2024)
2. Calculez les statistiques pour chaque année
3. Créez des visualisations comparatives
4. Identifiez les différences majeures et interprétez les résultats



Travaux Pratiques
=======================================

.. note::
   Ces TPs sont à rendre et comptent pour l'évaluation finale.

TP3 : Analyse de données et visualisation avec Streamlit 
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

**Objectif :** Créer une application web interactive d'analyse de données avec Streamlit.

**Fonctionnalités requises :**
- Permettre le téléchargement d'un fichier CSV
- Afficher les premières lignes et les statistiques descriptives
- Créer au moins 3 types de visualisations différentes (histogramme, boxplot, scatter plot)
- Ajouter des widgets interactifs (selectbox, slider) pour filtrer les données
- Personnaliser l'interface (titre, sidebar, sections)

**Consignes :**
- Application fonctionnelle et bien structurée
- Code commenté et organisé
- Interface utilisateur intuitive
- Gestion des erreurs (fichier invalide, colonnes manquantes)

**À rendre avant la date limite indiquée par l'enseignant.**


TP4 : Analyse de données et visualisation avec Shiny 
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

**Objectif :** Créer une application web interactive d'analyse de données avec Shiny.

**Fonctionnalités requises :**
- Interface avec sidebar pour les contrôles
- Téléchargement et lecture d'un fichier CSV
- Affichage du tableau de données
- Au moins 3 visualisations interactives (graphiques réactifs)
- Filtres interactifs (selectInput, sliderInput)
- Calcul et affichage de statistiques descriptives

**Consignes :**
- Application avec structure ui/server claire
- Code R bien organisé et commenté
- Utilisation de reactive() pour la réactivité
- Interface ergonomique et professionnelle
- Gestion des erreurs

**À rendre avant la date limite indiquée par l'enseignant.**