# EDA 3 — Analyse des relations entre variables

## Nuage de points (scatterplot)

```python
import matplotlib.pyplot as plt

plt.scatter(df["taille"], df["poids"])
plt.xlabel("Taille (cm)")
plt.ylabel("Poids (kg)")
plt.show()

# avec une couleur par catégorie
for ville, groupe in df.groupby("ville"):
    plt.scatter(groupe["taille"], groupe["poids"], label=ville)
plt.legend()
plt.show()
```

## Matrice de corrélation

```python
corr = df.corr(numeric_only=True)
print(corr.round(2))

# heatmap avec seaborn (module 08)
import seaborn as sns
sns.heatmap(corr, annot=True, cmap="coolwarm", vmin=-1, vmax=1)
```

## Deux variables catégorielles : tableau croisé

```python
pd.crosstab(df["ville"], df["sexe"], normalize="index")   # proportions en ligne
pd.crosstab(df["ville"], df["sexe"], values=df["salaire"], aggfunc="mean")
```

## Une catégorielle, une numérique

```python
df.groupby("ville")["salaire"].agg(["mean", "median", "std"])
df.boxplot(column="salaire", by="ville")
```

## Matrice de nuages de points (pairplot) avec seaborn

```python
import seaborn as sns
sns.pairplot(df[["taille", "poids", "age", "sexe"]], hue="sexe")
```

## Exercices (à faire seul)

1. Sur un dataset avec plusieurs colonnes numériques, trouve la paire de variables la plus corrélée (|corr| max) et trace leur scatterplot.
2. Trace la heatmap de corrélation et identifie les corrélations fortes (> 0.7 ou < -0.7).
3. Compare le salaire moyen par catégorie avec un barplot et un boxplot ; quelle visualisation te parle le plus ?
4. Fais un `crosstab` normalisé entre deux colonnes catégorielles et interprète.

## Pour aller plus loin

- [Seaborn : relational plots](https://seaborn.pydata.org/tutorial/relational.html)

Module suivant : [08 — Visualisation](../08-visualisation/README.md).
