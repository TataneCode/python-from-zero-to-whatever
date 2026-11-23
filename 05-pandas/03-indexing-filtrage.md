# Pandas 3 — Indexing, slicing et filtrage

## `loc` (par étiquette) et `iloc` (par position)

```python
import pandas as pd

df = pd.DataFrame({
    "nom": ["Alice", "Bob", "Chloe", "David"],
    "age": [25, 30, 22, 35],
    "ville": ["Paris", "Lyon", "Paris", "Lyon"],
    "salaire": [2500, 3200, 2800, 4100],
})

df.loc[0, "nom"]        # "Alice"      (étiquette de ligne, nom de colonne)
df.loc[0:2, "nom"]      # lignes 0 à 2 incluses (loc inclut la borne !)
df.iloc[0:2]            # 2 premières lignes (borne exclue, comme les slices Python)
df.iloc[:, 1:3]         # toutes les lignes, colonnes 1 et 2
```

## Filtrage par conditions (masques booléens)

```python
# une condition
df[df["age"] > 25]

# plusieurs conditions : & (et), | (ou), ~ (non) — chaque condition entre parenthèses
adultes_parisiens = df[(df["age"] >= 18) & (df["ville"] == "Paris")]
haut_salaire = df[(df["salaire"] > 3000) | (df["ville"] == "Paris")]
pas_lyon = df[~(df["ville"] == "Lyon")]

# méthode isin : appartenance à une liste
df[df["ville"].isin(["Paris", "Marseille"])]

# chaînes : méthodes .str
df[df["nom"].str.startswith("A")]
df[df["nom"].str.contains("a", case=False)]
```

## `query()` : filtrer avec une expression textuelle

```python
df.query("age > 25 and ville == 'Lyon'")
df.query("salaire > @seuil")   # @seuil fait référence à une variable Python du scope
```

## Sélectionner + modifier

```python
df.loc[df["ville"] == "Paris", "salaire"] = df["salaire"] * 1.1   # augmentation de 10 % à Paris
df.loc[df["age"] < 18, "age"] = None                               # valeurs manquantes (voir module 06)
```

## Trier

```python
df.sort_values("salaire")                        # croissant
df.sort_values(["ville", "salaire"], ascending=[True, False])  # par ville puis salaire décroissant
df.sort_index()
```

## Exercices (à faire seul)

1. Sur un DataFrame de ventes (date, produit, quantité, prix), sélectionne les ventes de janvier 2024 pour le produit "X".
2. Compte combien de lignes ont au moins une valeur manquante (`df.isna().any(axis=1).sum()`).
3. Remplace les salaires inférieurs à 2000 par la médiane des salaires (`df["salaire"].median()`).
4. Trie par catégorie puis par montant décroissant, et garde les 10 premières lignes (`head(10)`).

## Pour aller plus loin

- [Pandas : indexing and selecting data](https://pandas.pydata.org/docs/user_guide/indexing.html)
