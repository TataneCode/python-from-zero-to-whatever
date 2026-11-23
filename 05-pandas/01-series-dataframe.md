# Pandas 1 — Series et DataFrame

## Series (une colonne)

```python
import pandas as pd

s = pd.Series([10, 20, 30], index=["a", "b", "c"], name="valeurs")
print(s["b"])        # 20
print(s.mean())      # 20.0
print(s + 5)         # opérations vectorisées comme NumPy
```

## DataFrame (le tableau central)

```python
df = pd.DataFrame({
    "nom": ["Alice", "Bob", "Chloe"],
    "age": [25, 30, 22],
    "ville": ["Paris", "Lyon", "Paris"],
    "salaire": [2500, 3200, 2800],
})

print(df.head(2))    # 2 premières lignes
print(df.tail(1))    # dernière ligne
print(df.shape)      # (3, 4)  -> (lignes, colonnes)
print(df.columns)    # Index(['nom', 'age', 'ville', 'salaire'])
print(df.dtypes)     # type de chaque colonne
print(df.index)      # index des lignes
```

## Inspection rapide (indispensable)

```python
df.info()            # types, valeurs non nulles, mémoire
print(df.describe()) # statistiques des colonnes numériques (count, mean, std, min, 25%, 50%, 75%, max)
print(df["ville"].value_counts())  # effectif par catégorie
```

## Accéder aux colonnes et lignes

```python
df["nom"]            # une colonne -> Series
df[["nom", "age"]]   # plusieurs colonnes -> DataFrame
print(df["age"].mean())
```

Pour les lignes, voir la leçon 3 (`loc` / `iloc`). Aperçu :

```python
df.loc[0]            # ligne d'index 0 (toutes colonnes)
df.iloc[0]           # première ligne (position)
```

## Exercices (à faire seul)

1. Crée un DataFrame de 5 élèves avec colonnes `nom`, `note_maths`, `note_francais` ; affiche `describe()`.
2. Crée une Series de températures journalières indexées par des dates (strings "2024-01-01"...) ; affiche la température max et le jour correspondant (`idxmax()`).
3. À partir du DataFrame élèves, crée une nouvelle colonne `moyenne` = moyenne des deux notes.

## Pour aller plus loin

- [Pandas : 10 minutes to pandas](https://pandas.pydata.org/docs/user_guide/10min.html)
- [DataFrame vs Series](https://pandas.pydata.org/docs/getting_started/basics.html)
