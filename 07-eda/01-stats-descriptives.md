# EDA 1 — Statistiques descriptives

## Mesures de tendance centrale

```python
import pandas as pd
import numpy as np

s = pd.Series([12, 15, 9, 18, 15, 40])   # le 40 est un outlier

s.mean()     # 18.33  (moyenne, sensible aux outliers)
s.median()   # 15.0   (médiane, robuste)
s.mode()     # 15     (valeur la plus fréquente)
```

## Dispersion

```python
s.var()      # variance
s.std()      # écart-type (même unité que les données)
s.min(), s.max()
s.quantile(0.25), s.quantile(0.75)   # quartiles Q1, Q3
s.describe() # count, mean, std, min, 25%, 50%, 75%, max en un appel
```

## Sur un DataFrame entier

```python
df.describe()                          # toutes les colonnes numériques
df.describe(include="object")          # colonnes texte (count, unique, top, freq)
df.describe(include="all")
df["colonne"].nunique()                # nombre de valeurs distinctes
```

## Corrélation et covariance

```python
df[["taille", "poids", "age"]].corr()          # matrice de corrélation de Pearson (entre -1 et 1)
df[["taille", "poids"]].corr().iloc[0, 1]      # corrélation taille/poids

df["a"].cov(df["b"])                           # covariance
```

Interprétation de la corrélation : proche de 1 = lien fort positif, -1 = fort négatif, 0 = pas de lien **linéaire** (attention : corrélation ≠ causalité).

```python
df.corr(numeric_only=True)     # ignore les colonnes non numériques
```

## Exercices (à faire seul)

1. Sur un DataFrame de 100 lignes (taille, poids, âge générés aléatoirement), calcule moyenne/médiane/écart-type de chaque colonne ; compare moyenne vs médiane quand tu ajoutes un outlier.
2. Calcule la corrélation entre deux colonnes fortement liées (ex. `x` et `x*2 + bruit`) et entre deux colonnes indépendantes ; interprète.
3. Trouve la colonne la plus corrélée avec une colonne cible (ex. `prix`) dans un dataset.

## Pour aller plus loin

- [Pandas : describe](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html)
- [Pandas : correlation](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.corr.html)
