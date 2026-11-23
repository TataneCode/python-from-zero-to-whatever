# Avancé 3 — Analyse géospatiale (aperçu)

```bash
pip install geopandas
```

**GeoPandas** ajoute la dimension géographique aux DataFrames : points, lignes, polygones, avec CRS (systèmes de coordonnées), jointures spatiales et cartes.

```python
import geopandas as gpd

# lire un fichier géo (GeoJSON, Shapefile...)
villes = gpd.read_file("data/villes.geojson")
print(villes.crs)            # EPSG:4326 (WGS84, lat/lon GPS)

# GeoDataFrame = DataFrame pandas + colonne "geometry"
villes.plot(column="population", legend=True, cmap="viridis")

# jointure spatiale : quels points tombent dans quel polygone ?
points = gpd.GeoDataFrame(..., geometry=gpd.points_from_xy(lons, lats), crs="EPSG:4326")
jointure = gpd.sjoin(points, regions, predicate="within")
```

## Ressources de données géo gratuites

- [Natural Earth](https://www.naturalearthdata.com/) : frontières de pays, villes.
- [data.gouv.fr](https://www.data.gouv.fr/) : données géo françaises (découpage administratif, etc.).
- OpenStreetMap via [Overpass API](https://overpass-turbo.eu/).

## Cartes interactives

```python
import plotly.express as px
fig = px.scatter_mapbox(df, lat="lat", lon="lon", size="population", hover_name="ville",
                        mapbox_style="open-street-map", zoom=4)
fig.show()
```

## Exercice (à faire seul)

1. Récupère le GeoJSON des pays (Natural Earth), charge avec GeoPandas, colore par continent, sauvegarde la carte en HTML avec Plotly choropleth.

## Pour aller plus loin

- [GeoPandas](https://geopandas.org/)
- [Roadmap GIS / géospatial](https://roadmap.sh/datastructures-and-algorithms) (section géo) — ou la roadmap Data Engineer.

Parcours terminé : place aux [projets solo](../projets/README.md) !
