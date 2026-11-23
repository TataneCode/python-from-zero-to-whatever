# Pandas 2 — Lire et écrire des données

## Lire des fichiers locaux

```python
import pandas as pd

df = pd.read_csv("data/ventes.csv")                    # CSV (séparateur virgule par défaut)
df = pd.read_csv("data/ventes.csv", sep=";")           # point-virgule (export Excel FR)
df = pd.read_csv("data/ventes.csv", sep=";", decimal=",")  # virgule comme séparateur décimal
df = pd.read_excel("data/ventes.xlsx", sheet_name="Feuil1")   # nécessite openpyxl
df = pd.read_json("data/donnees.json")                 # JSON
df = pd.read_parquet("data/ventes.parquet")             # Parquet (nécessite pyarrow)
```

Options utiles de `read_csv` : `header=0`, `names=[...]`, `skiprows=n`, `encoding="utf-8"` ou `"latin-1"`, `na_values=["N/A", "-"]`, `parse_dates=["date"]`, `dayfirst=True`.

## Lire depuis une URL

```python
df = pd.read_csv("https://raw.githubusercontent.com/.../fichier.csv")
```

## Lire depuis une base SQL

```python
import sqlite3
con = sqlite3.connect("data/ma_base.db")
df = pd.read_sql_query("SELECT * FROM clients WHERE ville = 'Paris'", con)
```

(Voir le [module 10 — SQL](../10-sql/README.md) pour aller plus loin.)

## Écrire

```python
df.to_csv("data/sortie.csv", index=False)          # index=False : ne pas écrire l'index comme colonne
df.to_csv("data/sortie.csv", sep=";", index=False, encoding="utf-8-sig")  # lisible par Excel FR
df.to_excel("data/sortie.xlsx", index=False)       # nécessite openpyxl
df.to_json("data/sortie.json", orient="records", force_ascii=False, indent=2)
df.to_parquet("data/sortie.parquet", index=False)  # nécessite pyarrow
df.to_sql("table_resultat", con, if_exists="replace", index=False)
```

## Exercices (à faire seul)

1. Crée un CSV à la main (ou exporte un tableur) avec 10 lignes et 4 colonnes, lis-le avec `pd.read_csv`, affiche `info()` et `describe()`.
2. Re-lis le même fichier en forçant la colonne date avec `parse_dates` et vérifie le `dtype`.
3. Écris le DataFrame filtré (lignes où une colonne numérique > seuil) dans un nouveau CSV **et** un Parquet ; compare les tailles de fichiers.

## Pour aller plus loin

- [Pandas : IO tools (lecture/écriture)](https://pandas.pydata.org/docs/user_guide/io.html)
