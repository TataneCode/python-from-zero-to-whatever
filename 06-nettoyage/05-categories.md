# Nettoyage 5 — Encodage des catégories

## Type `category`

```python
df["ville"] = df["ville"].astype("category")
```

Avantages : moins de mémoire, tris/groupby plus rapides, ordre des catégories contrôlable.

```python
df["ville"].cat.categories          # liste des catégories
df["taille"] = df["taille"].astype("category")
df["taille"] = df["taille"].cat.set_categories(["S", "M", "L", "XL"], ordered=True)  # ordre logique
df["taille"] > "M"                  # comparaison selon l'ordre défini
```

## Normaliser les catégories (fautes, variantes)

```python
df["ville"] = df["ville"].str.strip().str.title()      # "paris " -> "Paris"
df["ville"] = df["ville"].replace({"St Denis": "Saint-Denis", "St-denis": "Saint-Denis"})
```

## Encodage one-hot (`pd.get_dummies`)

Transforme une colonne catégorielle en colonnes 0/1 (utile pour le machine learning, module 14) :

```python
pd.get_dummies(df["ville"], prefix="ville", dtype=int)
#   ville_Lyon  ville_Marseille  ville_Paris
# 0           0                0            1
```

Options : `drop_first=True` (évite la colinéarité), `dummy_na=True` (ajoute une colonne pour les NaN).

## Label encoding (catégorie → entier)

```python
df["ville_code"] = df["ville"].cat.codes     # chaque catégorie -> entier (ordre alphabétique ou défini)
```

## Exercices (à faire seul)

1. Colonne `couleur` avec valeurs "Rouge", "rouge ", "ROUGE", "Bleu" → normalise puis convertis en `category`.
2. Colonne `taille` avec S/M/L/XL mélangés à des "s", " m " → nettoie, définis un ordre, vérifie que "L" > "M".
3. Fais un one-hot encoding d'une colonne `departement` avec `get_dummies`, puis reconstitue la colonne d'origine à partir des dummies (somme des lignes = 1).

## Pour aller plus loin

- [Pandas : categorical data](https://pandas.pydata.org/docs/user_guide/categorical.html)
