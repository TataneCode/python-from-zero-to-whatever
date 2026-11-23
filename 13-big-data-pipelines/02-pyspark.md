# Big data 2 — PySpark (aperçu)

```bash
pip install pyspark    # nécessite Java installé sur la machine
```

**Apache Spark** est le standard industriel du traitement distribué : des DataFrames manipulés sur un **cluster** de machines, lus depuis des data lakes (Parquet sur S3/HDFS...).

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("demo").getOrCreate()

df = spark.read.parquet("data/ventes.parquet")     # lecture distribuée
df = df.filter(df.prix > 100).groupBy("categorie").sum("montant")
df.show(10)
df.write.parquet("data/resultat.parquet")

spark.stop()
```

## Spark vs pandas/Polars/Dask

| Outil | Échelle | Quand |
|---|---|---|
| pandas | < quelques Go, 1 machine | analyse interactive |
| Polars | jusqu'à la RAM dispo, 1 machine | gros fichiers rapides |
| Dask | RAM × cœurs, 1 grosse machine | paralléliser pandas |
| PySpark | To/Po, cluster de machines | vrai big data industriel |

## Exercice (à faire seul)

1. Installe pyspark (avec Java), crée une `SparkSession`, lis un Parquet que tu as généré, filtre + groupBy + `show()`.
2. Compare le temps de lecture d'un gros CSV avec pandas, Polars et Spark.

## Pour aller plus loin

- [PySpark : getting started](https://spark.apache.org/docs/latest/api/python/getting_started/index.html)
