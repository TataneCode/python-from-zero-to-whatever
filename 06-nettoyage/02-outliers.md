# Nettoyage 2 — Détection des outliers (valeurs aberrantes)

## Inspection visuelle d'abord

```python
df["colonne"].plot.box()          # boîte à moustaches (matplotlib, voir module 08)
df["colonne"].hist(bins=50)
```

## Méthode IQR (écart interquartile)

Un outlier est une valeur hors de `[Q1 - 1.5*IQR, Q3 + 1.5*IQR]`.

```python
Q1 = df["colonne"].quantile(0.25)
Q3 = df["colonne"].quantile(0.75)
IQR = Q3 - Q1

borne_inf = Q1 - 1.5 * IQR
borne_sup = Q3 + 1.5 * IQR

masque_outliers = (df["colonne"] < borne_inf) | (df["colonne"] > borne_sup)
print(masque_outliers.sum())
df[masque_outliers]          # voir les lignes concernées
```

Variante stricte (outliers extrêmes) : facteur 3 au lieu de 1.5.

## Méthode du z-score

Un outlier a un z-score |z| > 3 (écarts à la moyenne supérieurs à 3 écarts-types) :

```python
import numpy as np
z = (df["colonne"] - df["colonne"].mean()) / df["colonne"].std()
masque = z.abs() > 3
```

> Le z-score suppose une distribution à peu près normale ; l'IQR est plus robuste.

## Traiter les outliers

```python
# supprimer les lignes
df = df[~masque_outliers]

# ou écrêter (winsoriser) : remplacer par la borne
df.loc[df["colonne"] > borne_sup, "colonne"] = borne_sup
df.loc[df["colonne"] < borne_inf, "colonne"] = borne_inf
```

Ne supprime jamais un outlier sans l'avoir compris : c'est peut-être une vraie valeur importante.

## Exercices (à faire seul)

1. Génère 1000 salaires normaux (moyenne 3000, écart-type 500) + 5 valeurs aberrantes (ex. 50000) ; détecte-les avec IQR et avec z-score ; compare.
2. Sur un DataFrame de ventes, écrête les quantités négatives et les prix > Q3 + 3*IQR.
3. Compte les outliers par catégorie (`groupby` sur une colonne catégorielle, applique le masque IQR par groupe).

## Pour aller plus loin

- [Pandas : quantiles](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.quantile.html)
