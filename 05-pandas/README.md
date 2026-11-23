# 05 — Pandas : la manipulation de données tabulaires

[Pandas](https://pandas.pydata.org/docs/) est **la** bibliothèque de référence pour lire, transformer et analyser des données structurées (CSV, Excel, SQL...) en Python.

```bash
pip install pandas
```

```python
import pandas as pd
```

## Leçons

1. [Series et DataFrame](01-series-dataframe.md) — créer, inspecter (`head`, `info`, `describe`, `shape`, `dtypes`).
2. [Lire et écrire des données](02-lecture-ecriture.md) — CSV, Excel, JSON, Parquet, SQL.
3. [Indexing, slicing et filtrage](03-indexing-filtrage.md) — `loc`, `iloc`, masques booléens, `query`.
4. [GroupBy et agrégation](04-groupby-agregation.md) — `groupby`, `agg`, `value_counts`, tableaux croisés.
5. [Merging et joining](05-merge-join.md) — `merge`, `concat`, jointures type SQL.
6. [Reshaping](06-reshape.md) — `pivot_table`, `melt`, `stack`/`unstack`, `crosstab`.

## À retenir

- Un **DataFrame** = tableau 2D avec des étiquettes de lignes (index) et de colonnes.
- Une **Series** = une seule colonne (ou ligne) avec un index.
- Pandas s'appuie sur NumPy : même logique de vectorisation.

Module suivant : [06 — Nettoyage de données](../06-nettoyage/README.md).
