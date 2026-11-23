# 10 — SQL avec Python

SQL reste **incontournable** pour interroger des bases de données. En Python, trois approches :

| Approche | Quand l'utiliser |
|---|---|
| `sqlite3` (stdlib) | petite base locale, embarquée, zéro installation |
| `SQLAlchemy` | projets professionnels, multi-SGBD (PostgreSQL, MySQL...) |
| `DuckDB` | analyser des **gros fichiers** (CSV/Parquet) directement en SQL, sans charger en mémoire |

```bash
pip install sqlalchemy duckdb
```

## Leçons

1. [Fondamentaux SQL](01-sql-fondamentaux.md) — SELECT, WHERE, ORDER BY, GROUP BY, JOIN, agrégations.
2. [sqlite3 et SQLAlchemy](02-sqlite3-sqlalchemy.md) — créer une base, insérer, interroger depuis Python, `pd.read_sql`.
3. [DuckDB](03-duckdb.md) — requêter des CSV/Parquet directement en SQL.

Ressource : la [roadmap SQL de roadmap.sh](https://roadmap.sh/sql) pour aller plus loin.

Module suivant : [11 — Polars](../11-polars/README.md).
