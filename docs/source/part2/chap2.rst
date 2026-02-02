.. _part2_chap2:

*************************
Chapitre 2 : Visualisation
*************************

Introduction
============

La visualisation de données est l'art de représenter l'information de manière graphique pour faciliter 
la compréhension, l'exploration et la communication des insights. Ce chapitre couvre les techniques 
de visualisation essentielles en Python et R.

Définition et importance
========================

**Définition** : La visualisation de données consiste à représenter les données dans un format graphique 
pour fournir un moyen accessible de voir et comprendre les tendances, les valeurs aberrantes et les patterns.

**Importance** :

1. **Simplification** : Rend les informations complexes plus accessibles
2. **Amélioration de la compréhension** : Les visuels facilitent l'apprentissage
3. **Prise de décision rapide** : Identification immédiate des tendances
4. **Communication efficace** : Partage d'insights de manière convaincante

Principes de design
===================

Principes fondamentaux
----------------------

**Clarté** : Un bon graphique doit être immédiatement compréhensible

**Simplicité** : Éviter la surcharge d'information

**Honnêteté** : Ne pas déformer les données (échelles appropriées, axes corrects)

**Esthétique** : Un graphique agréable retient l'attention et facilite la lecture

Choix du type de graphique
---------------------------

.. list-table:: Guide de sélection des graphiques
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

Bonnes et mauvaises pratiques
------------------------------

**Bonnes pratiques** :

* Toujours inclure un titre descriptif
* Étiqueter clairement les axes
* Utiliser une légende si nécessaire
* Choisir des couleurs appropriées (daltonisme)
* Commencer l'axe Y à zéro pour les barres

**À éviter** :

* Graphiques 3D inutiles
* Trop de couleurs ou effets
* Échelles trompeuses
* Légendes illisibles
* Surcharge d'information

Bibliothèques de visualisation
===============================

Python
------

**Matplotlib** : Bibliothèque de base, contrôle total

.. code-block:: python

   import matplotlib.pyplot as plt
   
   # Configuration de base
   plt.figure(figsize=(10, 6))
   plt.style.use('seaborn')  # Style prédéfini

**Seaborn** : Interface de haut niveau, graphiques statistiques

.. code-block:: python

   import seaborn as sns
   
   # Configuration du style
   sns.set_style("whitegrid")
   sns.set_palette("husl")

**Plotly** : Graphiques interactifs

.. code-block:: python

   import plotly.express as px
   import plotly.graph_objects as go

R
--

**ggplot2** : Grammaire des graphiques

.. code-block:: r

   library(ggplot2)
   
   # Thème personnalisé
   theme_set(theme_minimal())

**Base R** : Graphiques simples et rapides

.. code-block:: r

   # Configuration globale
   par(mfrow = c(2, 2))  # Grille 2x2

Types de graphiques essentiels
===============================

Histogrammes et distributions
------------------------------

**Histogramme** : Distribution d'une variable continue

.. code-block:: python

   # Python - Matplotlib
   plt.figure(figsize=(10, 6))
   plt.hist(data, bins=30, edgecolor='black', alpha=0.7)
   plt.xlabel('Valeur')
   plt.ylabel('Fréquence')
   plt.title('Distribution des valeurs')
   plt.show()
   
   # Python - Seaborn (avec KDE)
   plt.figure(figsize=(10, 6))
   sns.histplot(data=df, x='column', kde=True, bins=30)
   plt.title('Distribution avec courbe de densité')
   plt.show()

.. code-block:: r

   # R - ggplot2
   ggplot(df, aes(x = column)) +
     geom_histogram(bins = 30, fill = "steelblue", 
                    color = "black", alpha = 0.7) +
     labs(title = "Distribution des valeurs",
          x = "Valeur", y = "Fréquence") +
     theme_minimal()
   
   # Avec courbe de densité
   ggplot(df, aes(x = column)) +
     geom_histogram(aes(y = ..density..), bins = 30, 
                    fill = "steelblue", alpha = 0.5) +
     geom_density(color = "red", size = 1) +
     theme_minimal()

**Boxplot** : Résumé de la distribution avec quartiles

.. code-block:: python

   # Python - Seaborn
   plt.figure(figsize=(10, 6))
   sns.boxplot(data=df, x='categorie', y='valeur')
   plt.title('Distribution par catégorie')
   plt.xticks(rotation=45)
   plt.show()
   
   # Violin plot (distribution + boxplot)
   plt.figure(figsize=(10, 6))
   sns.violinplot(data=df, x='categorie', y='valeur')
   plt.show()

.. code-block:: r

   # R - ggplot2
   ggplot(df, aes(x = categorie, y = valeur)) +
     geom_boxplot(fill = "lightblue") +
     labs(title = "Distribution par catégorie") +
     theme_minimal() +
     theme(axis.text.x = element_text(angle = 45, hjust = 1))
   
   # Violin plot
   ggplot(df, aes(x = categorie, y = valeur)) +
     geom_violin(fill = "lightblue") +
     geom_boxplot(width = 0.1) +
     theme_minimal()

Graphiques de relation
-----------------------

**Scatter plot** : Relation entre deux variables continues

.. code-block:: python

   # Python - Matplotlib
   plt.figure(figsize=(10, 6))
   plt.scatter(df['x'], df['y'], alpha=0.6)
   plt.xlabel('Variable X')
   plt.ylabel('Variable Y')
   plt.title('Relation entre X et Y')
   plt.show()
   
   # Python - Seaborn avec régression
   plt.figure(figsize=(10, 6))
   sns.scatterplot(data=df, x='x', y='y', hue='categorie')
   sns.regplot(data=df, x='x', y='y', scatter=False, color='red')
   plt.title('Relation avec ligne de régression')
   plt.show()

.. code-block:: r

   # R - ggplot2
   ggplot(df, aes(x = x, y = y)) +
     geom_point(alpha = 0.6) +
     labs(title = "Relation entre X et Y",
          x = "Variable X", y = "Variable Y") +
     theme_minimal()
   
   # Avec régression et catégories
   ggplot(df, aes(x = x, y = y, color = categorie)) +
     geom_point(alpha = 0.6, size = 3) +
     geom_smooth(method = "lm", se = TRUE) +
     labs(title = "Relation avec régression") +
     theme_minimal()

**Line plot** : Évolution temporelle

.. code-block:: python

   # Python - Matplotlib
   plt.figure(figsize=(12, 6))
   plt.plot(df['date'], df['valeur'], marker='o', linestyle='-')
   plt.xlabel('Date')
   plt.ylabel('Valeur')
   plt.title('Évolution temporelle')
   plt.xticks(rotation=45)
   plt.grid(True, alpha=0.3)
   plt.show()
   
   # Python - Seaborn (plusieurs séries)
   plt.figure(figsize=(12, 6))
   sns.lineplot(data=df, x='date', y='valeur', hue='categorie')
   plt.title('Évolution par catégorie')
   plt.show()

.. code-block:: r

   # R - ggplot2
   ggplot(df, aes(x = date, y = valeur)) +
     geom_line(color = "steelblue", size = 1) +
     geom_point(color = "steelblue", size = 2) +
     labs(title = "Évolution temporelle",
          x = "Date", y = "Valeur") +
     theme_minimal() +
     theme(axis.text.x = element_text(angle = 45, hjust = 1))
   
   # Plusieurs séries
   ggplot(df, aes(x = date, y = valeur, color = categorie)) +
     geom_line(size = 1) +
     geom_point(size = 2) +
     labs(title = "Évolution par catégorie") +
     theme_minimal()

Graphiques de comparaison
--------------------------

**Bar plot** : Comparaison de catégories

.. code-block:: python

   # Python - Matplotlib
   plt.figure(figsize=(10, 6))
   plt.bar(df['categorie'], df['valeur'], color='steelblue', edgecolor='black')
   plt.xlabel('Catégorie')
   plt.ylabel('Valeur')
   plt.title('Comparaison par catégorie')
   plt.xticks(rotation=45)
   plt.show()
   
   # Python - Seaborn (avec erreurs)
   plt.figure(figsize=(10, 6))
   sns.barplot(data=df, x='categorie', y='valeur', ci=95)
   plt.title('Moyennes avec intervalles de confiance')
   plt.show()
   
   # Barres groupées
   plt.figure(figsize=(12, 6))
   sns.barplot(data=df, x='mois', y='valeur', hue='annee')
   plt.title('Comparaison par mois et année')
   plt.show()

.. code-block:: r

   # R - ggplot2
   ggplot(df, aes(x = categorie, y = valeur)) +
     geom_bar(stat = "identity", fill = "steelblue", 
              color = "black") +
     labs(title = "Comparaison par catégorie",
          x = "Catégorie", y = "Valeur") +
     theme_minimal() +
     theme(axis.text.x = element_text(angle = 45, hjust = 1))
   
   # Barres groupées
   ggplot(df, aes(x = mois, y = valeur, fill = annee)) +
     geom_bar(stat = "identity", position = "dodge") +
     labs(title = "Comparaison par mois et année") +
     theme_minimal()
   
   # Barres empilées
   ggplot(df, aes(x = categorie, y = valeur, fill = type)) +
     geom_bar(stat = "identity", position = "stack") +
     labs(title = "Composition par catégorie") +
     theme_minimal()

Heatmaps et corrélations
-------------------------

**Heatmap** : Visualisation de matrices

.. code-block:: python

   # Python - Seaborn
   # Matrice de corrélation
   corr_matrix = df.corr()
   
   plt.figure(figsize=(10, 8))
   sns.heatmap(corr_matrix, annot=True, fmt='.2f', 
               cmap='coolwarm', center=0,
               square=True, linewidths=1)
   plt.title('Matrice de corrélation')
   plt.show()
   
   # Heatmap de données
   pivot_table = df.pivot_table(values='valeur', 
                                index='ligne', 
                                columns='colonne')
   
   plt.figure(figsize=(12, 8))
   sns.heatmap(pivot_table, annot=True, fmt='.0f', 
               cmap='YlOrRd')
   plt.title('Heatmap des valeurs')
   plt.show()

.. code-block:: r

   # R - ggplot2
   library(reshape2)
   
   # Matrice de corrélation
   corr_matrix <- cor(df[, numeric_columns])
   corr_melted <- melt(corr_matrix)
   
   ggplot(corr_melted, aes(x = Var1, y = Var2, fill = value)) +
     geom_tile() +
     geom_text(aes(label = round(value, 2))) +
     scale_fill_gradient2(low = "blue", high = "red", 
                          mid = "white", midpoint = 0) +
     labs(title = "Matrice de corrélation") +
     theme_minimal() +
     theme(axis.text.x = element_text(angle = 45, hjust = 1))

**Pair plot** : Matrice de scatter plots

.. code-block:: python

   # Python - Seaborn
   sns.pairplot(df[['var1', 'var2', 'var3', 'categorie']], 
                hue='categorie',
                diag_kind='kde')
   plt.suptitle('Matrice de relations', y=1.02)
   plt.show()

.. code-block:: r

   # R - GGally
   library(GGally)
   
   ggpairs(df[, c('var1', 'var2', 'var3', 'categorie')],
           aes(color = categorie),
           upper = list(continuous = "points"),
           lower = list(continuous = "smooth"),
           diag = list(continuous = "densityDiag"))

Visualisations avancées
========================

Graphiques multiples (Subplots)
--------------------------------

.. code-block:: python

   # Python - Matplotlib
   fig, axes = plt.subplots(2, 2, figsize=(12, 10))
   
   # Graphique 1
   axes[0, 0].hist(df['var1'], bins=30)
   axes[0, 0].set_title('Distribution Var1')
   
   # Graphique 2
   axes[0, 1].scatter(df['x'], df['y'])
   axes[0, 1].set_title('Relation X-Y')
   
   # Graphique 3
   axes[1, 0].bar(categories, values)
   axes[1, 0].set_title('Comparaison')
   
   # Graphique 4
   axes[1, 1].plot(dates, values)
   axes[1, 1].set_title('Évolution')
   
   plt.tight_layout()
   plt.show()

.. code-block:: r

   # R - ggplot2 avec patchwork
   library(patchwork)
   
   p1 <- ggplot(df, aes(x = var1)) +
     geom_histogram(bins = 30) +
     ggtitle("Distribution Var1")
   
   p2 <- ggplot(df, aes(x = x, y = y)) +
     geom_point() +
     ggtitle("Relation X-Y")
   
   p3 <- ggplot(df, aes(x = categorie, y = valeur)) +
     geom_bar(stat = "identity") +
     ggtitle("Comparaison")
   
   p4 <- ggplot(df, aes(x = date, y = valeur)) +
     geom_line() +
     ggtitle("Évolution")
   
   # Combinaison
   (p1 + p2) / (p3 + p4)

Graphiques interactifs
----------------------

**Python - Plotly** :

.. code-block:: python

   import plotly.express as px
   
   # Scatter interactif
   fig = px.scatter(df, x='x', y='y', 
                    color='categorie',
                    size='taille',
                    hover_data=['info1', 'info2'],
                    title='Graphique interactif')
   fig.show()
   
   # Line plot interactif avec rangeslider
   fig = px.line(df, x='date', y='valeur',
                 title='Évolution avec sélecteur de plage')
   fig.update_xaxes(rangeslider_visible=True)
   fig.show()
   
   # 3D scatter
   fig = px.scatter_3d(df, x='x', y='y', z='z',
                       color='categorie')
   fig.show()

**R - Plotly** :

.. code-block:: r

   library(plotly)
   
   # Scatter interactif
   p <- plot_ly(df, x = ~x, y = ~y, 
                color = ~categorie,
                size = ~taille,
                text = ~paste("Info:", info),
                type = 'scatter', mode = 'markers')
   
   p <- p %>% layout(title = "Graphique interactif")
   p
   
   # ggplot2 vers plotly
   p_gg <- ggplot(df, aes(x = x, y = y, color = categorie)) +
     geom_point() +
     labs(title = "Conversion ggplot vers plotly")
   
   ggplotly(p_gg)

Personnalisation avancée
========================

Thèmes et styles
----------------

**Python** :

.. code-block:: python

   # Matplotlib - Style personnalisé
   plt.style.use('seaborn-darkgrid')
   
   # ou définir manuellement
   plt.rcParams['figure.figsize'] = [12, 8]
   plt.rcParams['font.size'] = 12
   plt.rcParams['lines.linewidth'] = 2
   plt.rcParams['axes.grid'] = True
   
   # Seaborn - Thème personnalisé
   sns.set_theme(style="whitegrid",
                 palette="husl",
                 font_scale=1.2,
                 rc={'figure.figsize': (12, 8)})

**R** :

.. code-block:: r

   # ggplot2 - Thème personnalisé
   theme_custom <- theme_minimal() +
     theme(
       text = element_text(size = 12),
       plot.title = element_text(size = 16, face = "bold"),
       axis.title = element_text(size = 14),
       axis.text = element_text(size = 12),
       legend.position = "bottom",
       panel.grid.minor = element_blank(),
       plot.background = element_rect(fill = "white"),
       plot.margin = margin(1, 1, 1, 1, "cm")
     )
   
   # Appliquer globalement
   theme_set(theme_custom)

Couleurs
--------

**Palettes de couleurs** :

.. code-block:: python

   # Python - Matplotlib
   colors = plt.cm.Set3(np.linspace(0, 1, n_colors))
   
   # Python - Seaborn
   palette = sns.color_palette("husl", n_colors)
   sns.set_palette(palette)
   
   # Palettes personnalisées
   custom_colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#96CEB4']

.. code-block:: r

   # R - ggplot2
   # Palettes prédéfinies
   scale_fill_brewer(palette = "Set3")
   scale_color_viridis_d()
   
   # Palette personnalisée
   custom_colors <- c("#FF6B6B", "#4ECDC4", "#45B7D1", "#96CEB4")
   scale_fill_manual(values = custom_colors)

Annotations
-----------

.. code-block:: python

   # Python
   plt.figure(figsize=(10, 6))
   plt.plot(x, y)
   
   # Texte
   plt.text(x_pos, y_pos, 'Annotation', fontsize=12, ha='center')
   
   # Flèche
   plt.annotate('Point important', xy=(x1, y1), xytext=(x2, y2),
                arrowprops=dict(arrowstyle='->', color='red'))
   
   # Ligne verticale/horizontale
   plt.axvline(x=5, color='red', linestyle='--', alpha=0.5)
   plt.axhline(y=10, color='blue', linestyle='--', alpha=0.5)
   
   # Zone colorée
   plt.axvspan(2, 4, alpha=0.3, color='yellow')

.. code-block:: r

   # R - ggplot2
   ggplot(df, aes(x = x, y = y)) +
     geom_line() +
     # Texte
     annotate("text", x = x_pos, y = y_pos, 
              label = "Annotation", size = 5) +
     # Flèche
     annotate("segment", x = x1, xend = x2, 
              y = y1, yend = y2,
              arrow = arrow(length = unit(0.3, "cm"))) +
     # Lignes de référence
     geom_vline(xintercept = 5, color = "red", 
                linetype = "dashed", alpha = 0.5) +
     geom_hline(yintercept = 10, color = "blue", 
                linetype = "dashed", alpha = 0.5) +
     # Zone colorée
     annotate("rect", xmin = 2, xmax = 4, 
              ymin = -Inf, ymax = Inf,
              alpha = 0.3, fill = "yellow")

Export et sauvegarde
====================

.. code-block:: python

   # Python
   # Matplotlib
   plt.savefig('graphique.png', dpi=300, bbox_inches='tight')
   plt.savefig('graphique.pdf', format='pdf')
   plt.savefig('graphique.svg', format='svg')
   
   # Seaborn (utilise matplotlib)
   fig = sns_plot.get_figure()
   fig.savefig('output.png', dpi=300)
   
   # Plotly
   fig.write_image("fig.png", width=1200, height=800)
   fig.write_html("fig.html")

.. code-block:: r

   # R - ggplot2
   ggsave("graphique.png", plot = p, 
          width = 10, height = 6, dpi = 300)
   
   ggsave("graphique.pdf", plot = p, 
          width = 10, height = 6)
   
   # Base R
   png("graphique.png", width = 800, height = 600)
   plot(x, y)
   dev.off()
   
   # Plotly
   library(htmlwidgets)
   saveWidget(p, "graphique.html")

Conclusion
==========

Ce chapitre a couvert les aspects essentiels de la visualisation de données :

* Principes de design et choix approprié des graphiques
* Types de graphiques fondamentaux (distributions, relations, comparaisons)
* Techniques de personnalisation et d'annotation
* Graphiques interactifs pour l'exploration
* Export et partage des visualisations

La maîtrise de ces techniques permet de :
- Explorer efficacement les données
- Identifier des patterns et anomalies
- Communiquer des insights de manière claire
- Créer des rapports professionnels

Ces compétences seront essentielles pour le chapitre suivant sur les applications web interactives.
