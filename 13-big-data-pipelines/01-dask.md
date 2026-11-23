# Big data 1 — Dask (pandas en parallèle)

```bash
pip install "dask[dataframe]"
```

Dask découpe un gros DataFrame en **partitions** et les traite en parallèle sur tous les cœurs de ta machine, avec une API très proche de pandas.

```python
import dask.dataframe as dd

ddf = dd.read_csv("data/gros_*.csv")     # lit plusieurs CSV comme un seul DataFrame

# mêmes opérations que pandas, mais en "lazy" (rien n'est exécuté tout de suite)
resultat = (
    ddf[ddf["prix"] > 100]
    .groupby("categorie")["montant"]
    .sum()
)

resultat.compute()          # exécute le calcul et renvoie un pandas DataFrame
```

## Quand l'utiliser

- Fichier CSV/Parquet de quelques Go, trop lourd pour `pd.read_csv` en RAM.
- Beaucoup de calculs répétitifs à paralléliser.

```python
import dask.array as da
x = da.random.random((10000, 10000), chunks=(1000, 1000))   # comme numpy, par blocs
y = (x + x.T).mean(axis=0).compute()
```

## Exercice (à faire seul)

1. Génère 5 CSV de 200 000 lignes chacun, lis-les avec `dd.read_csv("data/part-*.csv")`, fais un groupby + agrégation, `compute()`, et compare le temps avec pandas.

## Pour aller plus loin

- [Documentation Dask](https://docs.dask.org/)
