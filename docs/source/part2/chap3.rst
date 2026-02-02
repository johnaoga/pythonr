.. _part2_chap3:

*************************************************
Chapitre 3 : Web Viewers et Dashboarding
*************************************************

Introduction
============

Les applications web interactives permettent de transformer des analyses statiques en outils dynamiques 
d'exploration et de communication. Ce chapitre présente Streamlit pour Python et Shiny pour R.

Vue d'ensemble
==============

Comparaison des frameworks
--------------------------

.. list-table:: Streamlit vs Shiny
   :header-rows: 1
   :widths: 30 35 35

   * - Aspect
     - Streamlit (Python)
     - Shiny (R)
   * - Architecture
     - Script Python linéaire
     - Structure UI/Server séparée
   * - Courbe d'apprentissage
     - Très facile, intuitif
     - Plus complexe, plus flexible
   * - Déploiement
     - Streamlit Cloud gratuit
     - Shinyapps.io (limité gratuit)
   * - Réactivité
     - Automatique (top-down)
     - Explicite (reactive programming)
   * - Performance
     - Bon pour petites/moyennes apps
     - Excellent, scalable

Streamlit (Python)
==================

Installation
------------

.. code-block:: bash

   pip install streamlit pandas numpy matplotlib seaborn plotly

Structure de base
-----------------

.. code-block:: python

   # app.py
   import streamlit as st
   import pandas as pd
   import numpy as np
   
   # Configuration de la page
   st.set_page_config(
       page_title="Mon Dashboard",
       page_icon="📊",
       layout="wide"
   )
   
   # Titre principal
   st.title("📊 Mon Dashboard")
   
   # Sidebar
   st.sidebar.header("Paramètres")
   
   # Contenu principal
   st.write("Bienvenue!")
   
   # Lancer : streamlit run app.py

Composants essentiels
---------------------

**Texte et affichage** :

.. code-block:: python

   import streamlit as st
   
   # Titres et texte
   st.title("Titre principal")
   st.header("En-tête")
   st.subheader("Sous-titre")
   st.text("Texte simple")
   st.markdown("**Markdown** *supporté*")
   st.latex(r"\sum_{i=1}^{n} x_i")
   
   # Messages
   st.success("Succès!")
   st.info("Information")
   st.warning("Attention!")
   st.error("Erreur!")

**Widgets d'entrée** :

.. code-block:: python

   # Inputs basiques
   bouton = st.button("Cliquer")
   checkbox = st.checkbox("Cocher")
   radio = st.radio("Choisir", ["A", "B", "C"])
   select = st.selectbox("Sélectionner", ["Option 1", "Option 2"])
   multiselect = st.multiselect("Multiple", ["A", "B", "C", "D"])
   
   # Inputs numériques
   slider = st.slider("Valeur", 0, 100, 50)
   number = st.number_input("Nombre", min_value=0, max_value=100)
   
   # Inputs texte
   text = st.text_input("Texte")
   area = st.text_area("Zone de texte")
   
   # Date et fichier
   date = st.date_input("Date")
   file = st.file_uploader("Fichier", type=['csv', 'xlsx'])

**Affichage de données** :

.. code-block:: python

   import pandas as pd
   
   df = pd.DataFrame({
       'A': [1, 2, 3],
       'B': [4, 5, 6]
   })
   
   # Tableaux
   st.dataframe(df)  # Interactif
   st.table(df)      # Statique
   
   # Métriques
   st.metric("Température", "25°C", "2°C")
   
   # Colonnes pour layout
   col1, col2, col3 = st.columns(3)
   with col1:
       st.metric("Métrique 1", "100")
   with col2:
       st.metric("Métrique 2", "200")
   with col3:
       st.metric("Métrique 3", "300")

**Graphiques** :

.. code-block:: python

   import matplotlib.pyplot as plt
   import plotly.express as px
   
   # Matplotlib
   fig, ax = plt.subplots()
   ax.plot([1, 2, 3], [1, 4, 9])
   st.pyplot(fig)
   
   # Plotly (interactif)
   fig = px.scatter(df, x='A', y='B')
   st.plotly_chart(fig)
   
   # Graphiques natifs
   st.line_chart(df)
   st.bar_chart(df)
   st.area_chart(df)

Exemple d'application Streamlit
--------------------------------

.. code-block:: python

   import streamlit as st
   import pandas as pd
   import numpy as np
   import plotly.express as px
   
   st.set_page_config(page_title="Dashboard Ventes", layout="wide")
   
   # Données simulées
   @st.cache_data
   def load_data():
       dates = pd.date_range('2023-01-01', periods=365, freq='D')
       df = pd.DataFrame({
           'date': dates,
           'ventes': np.random.randint(100, 1000, 365),
           'region': np.random.choice(['Nord', 'Sud', 'Est', 'Ouest'], 365),
           'produit': np.random.choice(['A', 'B', 'C'], 365)
       })
       return df
   
   df = load_data()
   
   # Sidebar - Filtres
   st.sidebar.header("Filtres")
   regions = st.sidebar.multiselect(
       "Régions", 
       options=df['region'].unique(),
       default=df['region'].unique()
   )
   
   produits = st.sidebar.multiselect(
       "Produits",
       options=df['produit'].unique(),
       default=df['produit'].unique()
   )
   
   # Filtrer les données
   df_filtered = df[
       (df['region'].isin(regions)) & 
       (df['produit'].isin(produits))
   ]
   
   # Titre
   st.title("📊 Dashboard des Ventes")
   
   # KPIs
   col1, col2, col3 = st.columns(3)
   
   with col1:
       st.metric("Total Ventes", f"{df_filtered['ventes'].sum():,}")
   with col2:
       st.metric("Moyenne", f"{df_filtered['ventes'].mean():.0f}")
   with col3:
       st.metric("Transactions", len(df_filtered))
   
   # Graphiques
   st.subheader("Evolution temporelle")
   fig_line = px.line(
       df_filtered.groupby('date')['ventes'].sum().reset_index(),
       x='date', y='ventes'
   )
   st.plotly_chart(fig_line, use_container_width=True)
   
   # Comparaisons
   col1, col2 = st.columns(2)
   
   with col1:
       st.subheader("Par région")
       fig_bar = px.bar(
           df_filtered.groupby('region')['ventes'].sum().reset_index(),
           x='region', y='ventes', color='region'
       )
       st.plotly_chart(fig_bar, use_container_width=True)
   
   with col2:
       st.subheader("Par produit")
       fig_pie = px.pie(
           df_filtered.groupby('produit')['ventes'].sum().reset_index(),
           values='ventes', names='produit'
       )
       st.plotly_chart(fig_pie, use_container_width=True)
   
   # Données brutes
   with st.expander("Voir les données"):
       st.dataframe(df_filtered)
       
       # Télécharger
       csv = df_filtered.to_csv(index=False)
       st.download_button(
           "📥 Télécharger CSV",
           data=csv,
           file_name='ventes.csv',
           mime='text/csv'
       )

Shiny (R)
=========

Installation
------------

.. code-block:: r

   install.packages(c("shiny", "shinydashboard", "ggplot2", "plotly", "DT"))

Structure de base
-----------------

.. code-block:: r

   # app.R
   library(shiny)
   
   # Interface utilisateur
   ui <- fluidPage(
     titlePanel("Mon Application Shiny"),
     
     sidebarLayout(
       sidebarPanel(
         sliderInput("bins", "Nombre de bins:",
                     min = 1, max = 50, value = 30)
       ),
       
       mainPanel(
         plotOutput("distPlot")
       )
     )
   )
   
   # Serveur
   server <- function(input, output) {
     output$distPlot <- renderPlot({
       x <- faithful[, 2]
       bins <- seq(min(x), max(x), length.out = input$bins + 1)
       hist(x, breaks = bins, col = 'darkgray')
     })
   }
   
   # Lancer l'app
   shinyApp(ui = ui, server = server)

Composants UI
-------------

.. code-block:: r

   # Widgets d'entrée
   ui <- fluidPage(
     # Inputs basiques
     actionButton("button", "Cliquer"),
     checkboxInput("checkbox", "Cocher", TRUE),
     radioButtons("radio", "Choisir:", c("A", "B", "C")),
     selectInput("select", "Sélectionner:", c("Opt1", "Opt2")),
     
     # Inputs numériques
     sliderInput("slider", "Valeur:", 0, 100, 50),
     numericInput("number", "Nombre:", 10, min = 1, max = 100),
     
     # Inputs texte
     textInput("text", "Texte:"),
     textAreaInput("area", "Zone:", rows = 5),
     
     # Date et fichier
     dateInput("date", "Date:"),
     fileInput("file", "Fichier:", accept = c(".csv", ".xlsx")),
     
     # Outputs
     plotOutput("plot"),
     tableOutput("table"),
     textOutput("text"),
     DT::dataTableOutput("datatable")
   )

Exemple d'application Shiny
---------------------------

.. code-block:: r

   library(shiny)
   library(shinydashboard)
   library(ggplot2)
   library(dplyr)
   
   # Interface
   ui <- dashboardPage(
     dashboardHeader(title = "Dashboard Ventes"),
     
     dashboardSidebar(
       sidebarMenu(
         menuItem("Vue d'ensemble", tabName = "overview", 
                  icon = icon("dashboard")),
         menuItem("Données", tabName = "data", 
                  icon = icon("table"))
       ),
       
       # Filtres
       selectInput("region", "Région:",
                   choices = c("Toutes", "Nord", "Sud", "Est", "Ouest"),
                   selected = "Toutes"),
       
       selectInput("produit", "Produit:",
                   choices = c("Tous", "A", "B", "C"),
                   selected = "Tous")
     ),
     
     dashboardBody(
       tabItems(
         tabItem(tabName = "overview",
           # KPIs
           fluidRow(
             valueBoxOutput("totalBox"),
             valueBoxOutput("avgBox"),
             valueBoxOutput("countBox")
           ),
           
           # Graphiques
           fluidRow(
             box(title = "Evolution", width = 12,
                 plotOutput("timePlot"))
           ),
           
           fluidRow(
             box(title = "Par région", width = 6,
                 plotOutput("regionPlot")),
             box(title = "Par produit", width = 6,
                 plotOutput("productPlot"))
           )
         ),
         
         tabItem(tabName = "data",
           h2("Données brutes"),
           DT::dataTableOutput("dataTable"),
           
           downloadButton("downloadData", "Télécharger CSV")
         )
       )
     )
   )
   
   # Serveur
   server <- function(input, output) {
     # Données simulées
     data <- reactive({
       df <- data.frame(
         date = seq.Date(as.Date("2023-01-01"), 
                        by = "day", length.out = 365),
         ventes = sample(100:1000, 365, replace = TRUE),
         region = sample(c("Nord", "Sud", "Est", "Ouest"), 
                        365, replace = TRUE),
         produit = sample(c("A", "B", "C"), 365, replace = TRUE)
       )
       
       # Appliquer les filtres
       if(input$region != "Toutes") {
         df <- df %>% filter(region == input$region)
       }
       if(input$produit != "Tous") {
         df <- df %>% filter(produit == input$produit)
       }
       
       df
     })
     
     # KPIs
     output$totalBox <- renderValueBox({
       valueBox(
         value = formatC(sum(data()$ventes), format = "d", big.mark = ","),
         subtitle = "Total Ventes",
         icon = icon("euro"),
         color = "blue"
       )
     })
     
     output$avgBox <- renderValueBox({
       valueBox(
         value = round(mean(data()$ventes)),
         subtitle = "Moyenne",
         icon = icon("chart-line"),
         color = "green"
       )
     })
     
     output$countBox <- renderValueBox({
       valueBox(
         value = nrow(data()),
         subtitle = "Transactions",
         icon = icon("shopping-cart"),
         color = "yellow"
       )
     })
     
     # Graphiques
     output$timePlot <- renderPlot({
       data() %>%
         group_by(date) %>%
         summarise(total = sum(ventes)) %>%
         ggplot(aes(x = date, y = total)) +
         geom_line(color = "steelblue", size = 1) +
         theme_minimal() +
         labs(title = "Evolution des ventes", x = "Date", y = "Ventes")
     })
     
     output$regionPlot <- renderPlot({
       data() %>%
         group_by(region) %>%
         summarise(total = sum(ventes)) %>%
         ggplot(aes(x = region, y = total, fill = region)) +
         geom_bar(stat = "identity") +
         theme_minimal() +
         theme(legend.position = "none") +
         labs(x = "Région", y = "Ventes")
     })
     
     output$productPlot <- renderPlot({
       data() %>%
         group_by(produit) %>%
         summarise(total = sum(ventes)) %>%
         ggplot(aes(x = "", y = total, fill = produit)) +
         geom_bar(stat = "identity", width = 1) +
         coord_polar("y") +
         theme_void() +
         labs(fill = "Produit")
     })
     
     # Table
     output$dataTable <- DT::renderDataTable({
       data()
     })
     
     # Téléchargement
     output$downloadData <- downloadHandler(
       filename = function() {
         paste("ventes-", Sys.Date(), ".csv", sep = "")
       },
       content = function(file) {
         write.csv(data(), file, row.names = FALSE)
       }
     )
   }
   
   shinyApp(ui = ui, server = server)

Bonnes pratiques
================

Performance
-----------

**Streamlit** :

* Utiliser ``@st.cache_data`` pour les données
* Utiliser ``@st.cache_resource`` pour les modèles
* Minimiser les rechargements avec ``st.form``

**Shiny** :

* Utiliser ``reactive()`` pour les calculs réutilisés
* Utiliser ``isolate()`` pour éviter les dépendances inutiles
* Utiliser ``observeEvent()`` plutôt que ``observe()``

Design
------

* Organiser l'interface de manière logique
* Utiliser des titres et sections clairs
* Fournir des instructions et aide contextuelle
* Implémenter des messages d'erreur utiles
* Permettre le téléchargement des résultats

Déploiement
-----------

**Streamlit** :

.. code-block:: bash

   # Streamlit Cloud (gratuit)
   # 1. Push sur GitHub
   # 2. Connecter à streamlit.io
   # 3. Déployer
   
   # Local
   streamlit run app.py --server.port 8080

**Shiny** :

.. code-block:: r

   # shinyapps.io
   library(rsconnect)
   deployApp()
   
   # Shiny Server (open source)
   # Installer Shiny Server
   # Placer l'app dans /srv/shiny-server/

Conclusion
==========

Ce chapitre a présenté les frameworks de création d'applications web interactives :

* **Streamlit** : Simple et rapide pour Python
* **Shiny** : Puissant et flexible pour R

Ces outils permettent de :
- Créer des dashboards interactifs
- Partager des analyses avec des non-techniciens
- Explorer les données de manière dynamique
- Automatiser les rapports

Les compétences acquises dans ce chapitre sont essentielles pour la communication 
moderne des résultats d'analyse de données.
