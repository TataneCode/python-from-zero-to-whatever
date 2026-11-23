# Pandas 4 — GroupBy et agrégation

Le pattern fondamental de l'analyse : **split → apply → combine**.

```python
import pandas as pd

df = pd.DataFrame({
    "ville":    ["Paris", "Lyon", "Paris", "Lyon", "Paris", "Lyon"],
    "produit":  ["A", "A", "B", "B", "A", "B"],
    "quantite": [10, 5, 8, 12, 7, 3],
    "prix":     [100, 50, 80, 120, 70, 30],
})
```

## `groupby` + agrégation

```python
df.groupby("ville")["quantite"].sum()          # total par ville
df.groupby("ville")["prix"].mean()             # prix moyen par ville

df.groupby("ville").agg(                       # plusieurs agrégations d'un coup
    total_quantite=("quantite", "sum"),
    prix_moyen=("prix", "mean"),
    nb_ventes=("prix", "count"),
)

df.groupby(["ville", "produit"])[["quantite", "prix"]].sum()   # double groupement
```

Autres agrégations : `min`, `max`, `median`, `std`, `var`, `first`, `last`, `nunique` (nombre de valeurs uniques).

## `value_counts` et `crosstab`

```python
df["ville"].value_counts()                       # effectifs par valeur
df["ville"].value_counts(normalize=True)        # en proportion (somme = 1)
pd.crosstab(df["ville"], df["produit"])         # tableau croisé (effectifs)
pd.crosstab(df["ville"], df["produit"], values=df["prix"], aggfunc="sum")  # avec agrégation
```

## `transform` (garder la taille du DataFrame)

```python
df["ecart_a_la_moyenne_ville"] = df["prix"] - df.groupby("ville")["prix"].transform("mean")
```

## Exercices (à faire seul)

1. Sur un DataFrame de ventes (mois, vendeur, montant) : calcule le chiffre d'affaires total par vendeur, puis le vendeur avec le plus gros CA.
2. Groupe par catégorie et affiche pour chaque groupe : nombre d'articles, prix min, prix max, prix moyen.
3. Avec `crosstab`, fais un tableau ville × produit avec la somme des quantités, et ajoute les marges (`margins=True`).
4. Calcule, par ville, la part de chaque produit dans le CA total de la ville (indice : `groupby` + `transform("sum")` puis division).

## Pour aller plus loin

- [Pandas : group by (split-apply-combine)](https://pandas.pydata.org/docs/user_guide/groupby.html)
