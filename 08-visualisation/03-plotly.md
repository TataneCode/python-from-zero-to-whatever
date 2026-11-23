# Visualisation 3 — Plotly (interactif)

```bash
pip install plotly
```

Plotly produit des graphiques **interactifs** (zoom, survol avec valeurs, légende cliquable) affichés dans le navigateur ou dans un notebook Jupyter.

```python
import plotly.express as px
```

## Plotly Express : la façon rapide

```python
import plotly.express as px

df = px.data.iris()          # jeux de données d'exemple intégrés
fig = px.scatter(df, x="sepal_width", y="sepal_length", color="species", size="petal_length",
                 hover_data=["petal_width"], title="Iris : largeur vs longueur de sépale")
fig.show()                   # ouvre dans le navigateur
fig.write_html("data/iris.html")   # sauvegarde autonome (ouvrable sans serveur)
```

## Autres types rapides

```python
px.line(df, x="date", y="valeur")                 # courbe temporelle
px.bar(df, x="categorie", y="total", color="sous_categorie")
px.histogram(df, x="valeur", nbins=30)
px.box(df, x="categorie", y="valeur")
px.pie(df, names="categorie", values="total")
px.scatter_matrix(df, dimensions=["a", "b", "c"], color="categorie")   # pairplot interactif
px.imshow(corr_matrix, text_auto=True, color_continuous_scale="RdBu_r")  # heatmap
px.choropleth(...)    # cartes (module 14, géospatial)
```

## Personnaliser

```python
fig.update_layout(
    title="Titre du graphique",
    xaxis_title="Axe X (unité)",
    yaxis_title="Axe Y (unité)",
    template="plotly_dark",          # thèmes : plotly, plotly_white, plotly_dark, ggplot2, seaborn...
    width=900, height=500,
)
fig.update_traces(marker=dict(size=8, opacity=0.7))
```

## Export

```python
fig.write_html("data/rapport.html")       # HTML autonome
fig.write_image("data/fig.png")           # image statique (nécessite kaleido : pip install kaleido)
```

## Exercices (à faire seul)

1. Scatter interactif sur `px.data.gapminder()` : PIB par habitant vs espérance de vie, couleur par continent, taille par population, année en animation (`animation_frame="year"`).
2. Boxplot interactif d'une colonne par catégorie sur ton propre DataFrame ; sauvegarde en HTML.
3. Heatmap de corrélation interactive avec `px.imshow`.

## Pour aller plus loin

- [Plotly Express](https://plotly.com/python/plotly-express/)
- [Plotly : graphiques fondamentaux](https://plotly.com/python/)

Module suivant : [09 — Web scraping et API](../09-web/README.md).
