# 11 — Polars : l'alternative rapide à pandas

[Polars](https://pola-rs.github.io/polars-book/) est une bibliothèque DataFrame écrite en Rust, pensée pour la **performance** sur les gros volumes (lecture par morceaux, exécution parallèle, requêtes optimisées « lazy »).

```bash
pip install polars
```

```python
import polars as pl
```

## DataFrame et lecture

```python
df = pl.read_csv("data/ventes.csv")
df = pl.read_parquet("data/ventes.parquet")

df.head()
df.shape          # (lignes, colonnes)
df.schema         # types des colonnes
df.describe()
```

## Expressions (le cœur de Polars)

Polars exprime les calculs avec des **expressions** (`pl.col(...)`), évaluées en parallèle :

```python
df.select(
    pl.col("prix") * pl.col("quantite"),                     # nouvelle colonne calculée
    (pl.col("prix") * 1.2).alias("prix_ttc"),
)

df.filter(pl.col("ville") == "Paris")
df.filter((pl.col("prix") > 100) & (pl.col("quantite") >= 2))

# groupby + agrégation
df.group_by("ville").agg(
    pl.col("prix").mean().alias("prix_moyen"),
    pl.col("quantite").sum().alias("qte_totale"),
    pl.len().alias("nb_ventes"),        # pl.len() = COUNT(*)
).sort("prix_moyen", descending=True)
```

## Lazy : optimiser avant d'exécuter

```python
lazy = (
    pl.scan_csv("data/gros_fichier.csv")        # scan = lecture différée, ne charge rien encore
    .filter(pl.col("prix") > 50)
    .group_by("categorie")
    .agg(pl.col("montant").sum())
    .sort("montant", descending=True)
)
resultat = lazy.collect()     # exécute la requête optimisée
```

`scan_csv` + `collect` laissent Polars optimiser (filtrer avant de lire les colonnes inutiles, etc.) : c'est ce qui le rend rapide sur les gros fichiers.

## Conversion pandas ↔ Polars

```python
import pandas as pd
df_pd = pd.read_csv("data/ventes.csv")
df_pl = pl.from_pandas(df_pd)
df_pd = df_pl.to_pandas()
```

## Polars vs pandas : quand choisir ?

| pandas | Polars |
|---|---|
| écosystème immense (viz, ML, tutos) | fichiers > quelques Go, besoins de vitesse |
| API très connue | syntaxe « expressions » à apprendre |
| manipulación fine ligne par ligne | traitements vectorisés parallèles |

## Exercices (à faire seul)

1. Génère un CSV de 1M de lignes (numpy), lis-le avec `pl.scan_csv`, filtre et agrège en lazy, compare le temps avec `pd.read_csv` + filtre pandas.
2. Refais l'analyse du module 05 (groupby + tri) en Polars et compare la lisibilité.
3. Convertis un DataFrame pandas en Polars, fais un `group_by().agg()`, reconvertis en pandas.

## Pour aller plus loin

- [Polars : user guide](https://docs.pola.rs/)
- [Polars vs pandas](https://docs.pola.rs/user-guide/migration/pandas/)

Module suivant : [12 — Dashboards](../12-dashboards/README.md).
