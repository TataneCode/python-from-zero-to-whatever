# Nettoyage 1 — Valeurs manquantes

## Détecter

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({"a": [1, np.nan, 3], "b": [4, 5, None]})

df.isna()               # masque booléen (isnull = alias)
df.isna().sum()         # nombre de manquants par colonne
df.isna().mean() * 100  # pourcentage de manquants par colonne
df.isna().any(axis=1)   # True pour les lignes qui ont au moins un manquant
```

## Supprimer (`dropna`) vs imputer

```python
df.dropna()                  # supprime les lignes avec au moins un NaN
df.dropna(subset=["a"])      # seulement si la colonne "a" est manquante
df.dropna(thresh=2)          # garde les lignes avec au moins 2 valeurs non nulles
df.dropna(axis=1)            # supprime les COLONNES avec des NaN (how="all" pour tout-NaN)

# supprimer une colonne entière si trop de manquants
df = df.drop(columns=["b"]) if df["b"].isna().mean() > 0.5 else df
```

## Imputer (remplacer)

```python
df["a"].fillna(df["a"].mean())     # par la moyenne
df["a"].fillna(df["a"].median())   # par la médiane (robuste aux outliers)
df["a"].fillna(0)                  # par une constante
df["a"].fillna(df["a"].mode()[0])  # par le mode (colonne catégorielle)
df["ville"].fillna("Inconnu")
```

## Propagation avant/arrière (`ffill` / `bfill`)

Idéal pour les séries temporelles :

```python
s = pd.Series([1, np.nan, np.nan, 4, np.nan])
s.ffill()   # forward fill  : [1, 1, 1, 4, 4]  (propage la dernière valeur connue)
s.bfill()   # backward fill : [1, 4, 4, 4, NaN] (propage la suivante)
df.ffill()  # fonctionne aussi sur DataFrame, colonne par colonne
```

## Interpolation (pour les séries temporelles)

```python
df["temperature"].interpolate(method="linear")          # interpolation linéaire
df["temperature"].interpolate(method="time")            # pondérée par le temps (index = dates)
```

## Règle de décision

| Situation | Choix |
|---|---|
| Peu de manquants (< 5 %) et aléatoires | supprimer ou imputer par moyenne/médiane |
| Colonne > 50 % de manquants | souvent la supprimer |
| Série temporelle | `ffill`/`bfill` ou `interpolate` |
| Le manquant a un sens métier (« aucun achat » = 0) | remplacer par une valeur explicite |

## Exercices (à faire seul)

1. Crée un DataFrame avec 20 % de valeurs manquantes aléatoires ; affiche le % de manquants par colonne, supprime les colonnes à plus de 50 %, impute le reste par la médiane.
2. Sur une série temporelle de températures avec des trous, compare `ffill`, `bfill` et `interpolate`.
3. Impute une colonne catégorielle par son mode.

## Pour aller plus loin

- [Pandas : missing data](https://pandas.pydata.org/docs/user_guide/missing_data.html)
