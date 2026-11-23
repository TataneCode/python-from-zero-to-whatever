# Visualisation 2 — Seaborn

```bash
pip install seaborn
```

Seaborn s'appuie sur Matplotlib et ajoute des graphiques statistiques prêts à l'emploi, avec des styles modernes par défaut.

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.set_theme()   # applique le thème par défaut (peut aussi être appelé dans chaque script)
```

## Charger un jeu de données d'exemple

```python
tips = sns.load_dataset("tips")      # pourboires au restaurant (chargé depuis le dépôt seaborn)
iris = sns.load_dataset("iris")
```

> `load_dataset` télécharge le fichier au premier appel puis le met en cache. Pour travailler hors ligne ensuite, sauvegarde-le : `tips.to_csv("data/tips.csv", index=False)`.

## Distribution plots

```python
sns.histplot(data=tips, x="total_bill", bins=20, kde=True)   # histogramme + densité
sns.kdeplot(data=tips, x="total_bill")                       # densité seule
sns.boxplot(data=tips, x="day", y="total_bill")               # boxplot par catégorie
sns.violinplot(data=tips, x="day", y="total_bill")            # violon (distribution + densité)
sns.stripplot(data=tips, x="day", y="total_bill", alpha=0.5)   # points individuels
```

## Categorical plots

```python
sns.barplot(data=tips, x="day", y="total_bill", estimator="mean")     # moyenne par défaut, barre = IC 95%
sns.countplot(data=tips, x="day")                                     # effectifs
sns.catplot(data=tips, x="day", y="total_bill", hue="sex", kind="bar") # kind: bar, box, violin, strip...
```

## Heatmaps

```python
corr = tips.select_dtypes("number").corr()
sns.heatmap(corr, annot=True, cmap="coolwarm", center=0, vmin=-1, vmax=1)
plt.show()
```

## Regression plots

```python
sns.regplot(data=tips, x="total_bill", y="tip")                    # nuage + droite de régression
sns.lmplot(data=tips, x="total_bill", y="tip", hue="smoker", col="time")  # facettes
```

## Pairplot (matrice de relations)

```python
sns.pairplot(iris, hue="species")
```

## Personnaliser et sauvegarder

```python
sns.set_style("whitegrid")          # darkgrid, white, whitegrid, dark, ticks
sns.set_palette("viridis")          # ou "deep", "muted", "Set2", ou une liste de couleurs

g = sns.scatterplot(data=tips, x="total_bill", y="tip")
g.figure.savefig("data/tip_vs_bill.png", dpi=150, bbox_inches="tight")
```

## Exercices (à faire seul)

1. Sur `tips` : distribution du `total_bill` par `day` (boxplot + violin côte à côte via `catplot`), sauvegarde en PNG.
2. Heatmap de corrélation des variables numériques de `iris`, annotée.
3. `regplot` de `tip` vs `total_bill`, coloré par `smoker` ; que remarques-tu ?
4. `pairplot` de `iris` ; quelles paires de variables semblent corrélées ?

## Pour aller plus loin

- [Seaborn : tutoriel officiel](https://seaborn.pydata.org/tutorial.html)
- [Galerie Seaborn](https://seaborn.pydata.org/examples/index.html)
