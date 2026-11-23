# SQL 3 — DuckDB : du SQL sur des fichiers

[DuckDB](https://duckdb.org/) est une base de données **analytique embarquée** : on exécute du SQL directement sur des fichiers CSV/Parquet/JSON, sans serveur ni import en mémoire complet. Idéal pour les fichiers trop gros pour Excel mais gérables sur disque.

```bash
pip install duckdb
```

## Requêter un CSV directement

```python
import duckdb

resultat = duckdb.sql("""
    SELECT ville, AVG(prix) AS prix_moyen, COUNT(*) AS nb
    FROM 'data/ventes.csv'
    WHERE date >= '2024-01-01'
    GROUP BY ville
    ORDER BY prix_moyen DESC
""").df()          # .df() -> DataFrame pandas
print(resultat)
```

## Depuis pandas

```python
import duckdb
import pandas as pd

df = pd.read_csv("data/ventes.csv")

# duckdb voit la variable `df` du scope automatiquement
duckdb.sql("SELECT produit, SUM(quantite * prix) AS ca FROM df GROUP BY produit ORDER BY ca DESC LIMIT 5").df()
```

## Lire plusieurs formats

```python
duckdb.sql("SELECT * FROM 'data/ventes.parquet' LIMIT 5").df()
duckdb.sql("SELECT * FROM read_json_auto('data/donnees.json')").df()
duckdb.sql("SELECT * FROM read_csv_auto('data/ventes.csv')").df()

# joindre un CSV et un Parquet en une requête
duckdb.sql("""
    SELECT c.nom, v.montant
    FROM 'data/clients.csv' c
    JOIN 'data/ventes.parquet' v ON c.id = v.id_client
""").df()
```

## Créer une vraie base DuckDB

```python
con = duckdb.connect("data/analytics.duckdb")
con.execute("CREATE TABLE ventes AS SELECT * FROM 'data/ventes.csv'")
con.execute("INSERT INTO ventes VALUES (...)").df()
con.close()
```

## Pourquoi DuckDB ?

| Critère | pandas | DuckDB |
|---|---|---|
| Fichier de 10 Go | lent / mémoire | rapide, lecture par morceaux |
| Requête SQL complexe (joins, agrégations) | verbeux | naturel |
| Écrire le résultat | `to_parquet` | `COPY ... TO 'sortie.parquet'` |

## Exercices (à faire seul)

1. Sur un CSV de ventes que tu génères (1M de lignes avec numpy), calcule avec DuckDB le CA par mois et par catégorie ; compare le temps d'exécution avec pandas (`%time` en notebook ou `time.perf_counter()`).
2. Jointure entre un CSV clients et un Parquet commandes directement en SQL DuckDB.
3. Exporte le résultat d'une requête en Parquet avec `COPY (SELECT ...) TO 'data/rapport.parquet' (FORMAT PARQUET)`.

## Pour aller plus loin

- [DuckDB : documentation](https://duckdb.org/docs/)
- [DuckDB + pandas](https://duckdb.org/docs/guides/python/pandas.html)

Module suivant : [11 — Polars](../11-polars/README.md).
