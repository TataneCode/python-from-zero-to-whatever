# 07 — Analyse exploratoire des données (EDA)

L'**Exploratory Data Analysis** consiste à comprendre un jeu de données avant de modéliser : statistiques descriptives, distributions, relations entre variables, inspection visuelle.

## Leçons

1. [Statistiques descriptives](01-stats-descriptives.md) — moyenne, médiane, mode, variance, écart-type, corrélation, covariance.
2. [Analyse des distributions](02-distributions.md) — histogrammes, boxplots, asymétrie.
3. [Analyse des relations](03-relations.md) — scatterplots, matrice de corrélation, tableaux croisés.

## Routine EDA type

```python
df.info()
df.describe()
df.isna().sum()
df.hist()                 # aperçu de toutes les distributions
# puis les relations : df.corr(numeric_only=True), scatterplots...
```

Module suivant : [08 — Visualisation](../08-visualisation/README.md).
