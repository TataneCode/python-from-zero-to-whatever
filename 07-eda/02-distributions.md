# EDA 2 — Analyse des distributions

## Histogramme (répartition d'une variable numérique)

```python
import matplotlib.pyplot as plt

df["age"].hist(bins=20)
plt.title("Distribution des âges")
plt.xlabel("Âge")
plt.ylabel("Effectif")
plt.show()
```

Lire un histogramme : forme (symétrique, asymétrique à droite/gauche), pics (modes), étalement, valeurs isolées.

## Boxplot (boîte à moustaches)

```python
df.boxplot(column="salaire", by="ville")   # un boxplot par ville
# ou df["salaire"].plot.box()
plt.show()
```

Un boxplot montre : médiane (trait central), Q1/Q3 (boîte), moustaches (généralement 1.5×IQR), points isolés = outliers potentiels.

## Autres indicateurs de forme

```python
df["salaire"].skew()     # asymétrie (skewness) : 0 = symétrique, > 0 = étalée à droite
df["salaire"].kurt()     # aplatissement (kurtosis)
```

## Distribution par catégorie

```python
df["ville"].value_counts().plot.bar()
df.groupby("ville")["salaire"].mean().plot.bar()
```

## Exercices (à faire seul)

1. Génère 1000 valeurs d'une loi normale (moyenne 100, écart-type 15) et trace l'histogramme ; superpose la courbe théorique avec `scipy.stats.norm.pdf` (module 14) ou simplement compare moyenne/écart-type empiriques.
2. Trace le boxplot d'une colonne par catégorie et identifie dans quelle catégorie la médiane est la plus haute.
3. Compare l'histogramme d'une distribution normale et d'une distribution uniforme (`np.random.default_rng(0).uniform(...)`).

## Pour aller plus loin

- [Pandas : plotting](https://pandas.pydata.org/docs/user_guide/visualization.html)
- Le module suivant ([08 — Visualisation](../08-visualisation/README.md)) détaille Matplotlib, Seaborn et Plotly.
