# Projet 7 — Mini-ETL : CSV → base SQL → rapport

**Niveau :** ⭐⭐ · **Modules :** 05, 06, 10

## Énoncé

Construis un petit pipeline **ETL** (Extract → Transform → Load) :

1. **Extract** : génère (ou télécharge) un CSV de ventes avec des données volontairement imparfaites (quelques valeurs manquantes, dates au format `"03/01/2024"`, prix avec virgule).
2. **Transform** : avec pandas, nettoie (dates → `datetime`, prix → `float`, manquants traités) et calcule `montant = quantite * prix`.
3. **Load** : charge le DataFrame propre dans une base **sqlite3** (tables `clients` et `ventes` avec clé étrangère), via `to_sql`.
4. **Analyse en SQL** : écris et exécutes des requêtes SQL (via `pd.read_sql_query`) :
   - CA total et par mois (`strftime('%Y-%m', date)`),
   - top 5 clients par CA (JOIN),
   - panier moyen (montant moyen par commande).
5. **Bonus** : refais les mêmes requêtes directement sur le CSV avec **DuckDB** (`duckdb.sql("SELECT ... FROM 'data/ventes.csv' ...")`) et compare.
6. Exporte le rapport (résultats des requêtes) en CSV.

## Critères de réussite

- Les tables sqlite contiennent bien les données nettoyées (vérifie avec `SELECT COUNT(*)`).
- Au moins 3 requêtes SQL avec JOIN/GROUP BY.
- Rapport CSV généré automatiquement.

## Extensions possibles

- Ajoute une table `produits` et des contraintes de clé étrangère (`PRAGMA foreign_keys = ON`).
- Fais le même pipeline avec SQLAlchemy (`create_engine`).
