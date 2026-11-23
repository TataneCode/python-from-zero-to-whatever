# Pandas 6 — Reshaping (changer la forme des données)

## `pivot_table` : du long au large

```python
import pandas as pd

ventes = pd.DataFrame({
    "date":    ["2024-01", "2024-01", "2024-02", "2024-02"],
    "produit": ["A", "B", "A", "B"],
    "ca":      [100, 150, 120, 200],
})

pd.pivot_table(ventes, values="ca", index="date", columns="produit", aggfunc="sum")
#         produit    A    B
# date
# 2024-01          100  150
# 2024-02          120  200
```

## `melt` : du large au long (opération inverse)

```python
large = pd.DataFrame({"id": [1, 2], "jan": [10, 20], "fev": [30, 40]})
pd.melt(large, id_vars="id", var_name="mois", value_name="valeur")
#    id  mois  valeur
# 0   1   jan      10
# 1   2   jan      20
# 2   1   fev      30
# 3   2   fev      40
```

## `stack` / `unstack`

```python
df = pd.DataFrame({("A", "x"): [1, 2], ("A", "y"): [3, 4]}, index=["u", "v"])
df.columns = pd.MultiIndex.from_tuples(df.columns)
df.stack()      # passe les colonnes en index -> Series multi-index
df.unstack()    # opération inverse
```

## `crosstab` (rappel, version reshaping)

```python
pd.crosstab(ventes["date"], ventes["produit"], values=ventes["ca"], aggfunc="sum", fill_value=0)
```

## Quand utiliser quoi ?

| Situation | Fonction |
|---|---|
| Plusieurs colonnes de mêmes mesures (jan, fev, mar) → une colonne `mois` + une colonne `valeur` | `melt` |
| Une colonne catégorielle + des valeurs → tableau croisé lisible | `pivot_table` |
| Agréger avec effectifs par combinaison de catégories | `crosstab` |
| Colonnes à plusieurs niveaux ↔ index hiérarchique | `stack` / `unstack` |

## Exercices (à faire seul)

1. À partir d'un DataFrame large (client, jan, fev, mar, avr), produis un DataFrame long avec `melt`, puis un `pivot_table` qui revient au format de départ.
2. Construis un tableau croisé mois × catégorie avec le CA moyen, rempli de 0 quand il n'y a pas de vente.
3. Prends un DataFrame avec colonnes MultiIndex et aplatis-le avec `stack`.

## Pour aller plus loin

- [Pandas : reshaping and pivot tables](https://pandas.pydata.org/docs/user_guide/reshaping.html)

Module suivant : [06 — Nettoyage de données](../06-nettoyage/README.md).
