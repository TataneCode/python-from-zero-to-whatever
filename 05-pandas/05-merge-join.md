# Pandas 5 — Merging et joining (jointures)

Combiner plusieurs DataFrames est aussi fréquent que le groupby. `pd.merge` reproduit les jointures SQL.

```python
import pandas as pd

clients = pd.DataFrame({
    "id_client": [1, 2, 3, 4],
    "nom": ["Alice", "Bob", "Chloe", "David"],
    "ville": ["Paris", "Lyon", "Paris", "Marseille"],
})

commandes = pd.DataFrame({
    "id_commande": [101, 102, 103, 104],
    "id_client": [1, 2, 1, 5],          # le client 5 n'existe pas dans clients
    "montant": [120, 80, 200, 50],
    "date": ["2024-01-10", "2024-01-12", "2024-02-01", "2024-02-03"],
})
```

## Les 4 types de jointure (`how`)

```python
pd.merge(clients, commandes, on="id_client", how="inner")   # seulement les clients avec commandes (défaut)
pd.merge(clients, commandes, on="id_client", how="left")    # tous les clients, commandes si elles existent
pd.merge(clients, commandes, on="id_client", how="right")   # toutes les commandes
pd.merge(clients, commandes, on="id_client", how="outer")   # tout, des deux côtés (NaN si absent)
```

## Options utiles

```python
pd.merge(clients, commandes, left_on="id_client", right_on="id_client_ref")  # noms de clés différents
pd.merge(a, b, on="id", suffixes=("_gauche", "_droite"))   # colonnes en double : renomme
pd.merge(a, b, on=["ville", "annee"])                       # jointure sur plusieurs colonnes
# indicateurs : indicator=True ajoute une colonne _merge (left_only, right_only, both)
```

## `concat` : empiler des DataFrames

```python
janv = pd.read_csv("data/ventes_2024_01.csv")
fev  = pd.read_csv("data/ventes_2024_02.csv")
tout = pd.concat([janv, fev], ignore_index=True)      # empile verticalement (axis=0)

# horizontalement (axis=1) : côte à côte, même index
pd.concat([df_a, df_b], axis=1)
```

## `join` (raccourci sur l'index)

```python
df_a.join(df_b, on="id_client", lsuffix="_a", rsuffix="_b")
```

## Exercices (à faire seul)

1. Crée deux DataFrames : produits (id, nom, categorie) et ventes (id_produit, quantite, date). Fais une jointure pour obtenir les ventes avec le nom du produit.
2. Identifie les produits jamais vendus (`how="left"` + `isna()` sur la colonne de ventes, ou `indicator=True`).
3. Fusionne 3 CSV mensuels avec `concat`, ajoute une colonne `mois` avant chaque concat, puis fais un groupby par mois.
4. Deux DataFrames avec des clés nommées différemment : jointure avec `left_on`/`right_on`.

## Pour aller plus loin

- [Pandas : merge, join, concatenate](https://pandas.pydata.org/docs/user_guide/merging.html)

Leçon suivante : [Reshaping](06-reshape.md).
