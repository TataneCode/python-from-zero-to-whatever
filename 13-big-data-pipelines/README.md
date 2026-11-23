# 13 — Big data et pipelines de données (aperçu)

Quand les données ne tiennent plus sur une machine ou doivent être traitées automatiquement à intervalles réguliers.

```bash
pip install dask            # pandas parallèle sur une machine
# pyspark : pip install pyspark   (nécessite Java)
# airflow : pip install apache-airflow
```

## Leçons

1. [Dask : pandas en parallèle](01-dask.md) — même API que pandas, mais distribué sur les cœurs/plusieurs machines.
2. [PySpark : le standard du big data](02-pyspark.md) — cluster, DataFrames Spark, lecture de Parquet distribué.
3. [Airflow : orchestrer des pipelines](03-airflow.md) — planifier et surveiller des tâches (ex. « chaque nuit à 2h : récupérer → nettoyer → charger »).

## Idée générale

- **Dask** = « pandas qui scale » sur une grosse machine.
- **PySpark** = « pandas sur un cluster de machines » (standard industriel, ex. Databricks).
- **Airflow** = le chef d'orchestre qui enchaîne les étapes et gère les échecs.

Module suivant : [14 — Sujets avancés](../14-sujets-avances/README.md).
