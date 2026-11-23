# Visualisation 1 — Matplotlib

```bash
pip install matplotlib
```

```python
import matplotlib.pyplot as plt
```

## Premier graphique

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 1, 5, 3]

plt.plot(x, y, marker="o")       # ligne avec points
plt.title("Mon premier graphique")
plt.xlabel("Axe X")
plt.ylabel("Axe Y")
plt.grid(True)
plt.show()
```

## Types de graphiques de base

```python
plt.plot(x, y)              # courbe
plt.scatter(x, y)           # nuage de points
plt.bar(categories, valeurs)        # barres verticales
plt.barh(categories, valeurs)       # barres horizontales
plt.hist(valeurs, bins=20)          # histogramme
plt.boxplot([serie1, serie2])       # boxplots
plt.pie(parts, labels=categories, autopct="%1.1f%%")  # camembert (à utiliser avec parcimonie)
```

## Figure et subplots (plusieurs graphiques côte à côte)

```python
fig, axes = plt.subplots(2, 2, figsize=(10, 8))   # grille 2x2
axes[0, 0].plot(x, y)
axes[0, 0].set_title("Courbe")
axes[0, 1].bar(categories, valeurs)
axes[1, 0].hist(valeurs, bins=15)
axes[1, 1].scatter(x, y)
fig.suptitle("Tableau de bord")
fig.tight_layout()      # ajuste les espacements
plt.show()
```

Ou la version orientée objet complète :

```python
fig = plt.figure(figsize=(8, 5))
ax = fig.add_subplot(111)
ax.plot(x, y, color="red", linestyle="--", linewidth=2, marker="o")
ax.set_xlabel("X (unité)")
ax.set_ylabel("Y (unité)")
ax.set_title("Titre")
```

## Personnaliser

```python
plt.plot(x, y, color="#1f77b4", linestyle="--", marker="s", markersize=8, label="Série 1")
plt.plot(x, [v*2 for v in y], label="Série 2")
plt.legend()
plt.xlim(0, 6)
plt.ylim(0, 12)
plt.xticks([1, 2, 3, 4, 5], ["un", "deux", "trois", "quatre", "cinq"])
plt.style.use("seaborn-v0_8")   # thème parmi plt.style.available
```

## Sauvegarder une figure

```python
fig.savefig("data/graphique.png", dpi=150, bbox_inches="tight")
fig.savefig("data/graphique.pdf")           # vectoriel
fig.savefig("data/graphique.svg")
plt.close(fig)   # libère la mémoire (important dans les boucles)
```

## Travailler avec pandas

```python
df["age"].hist(bins=20)                       # raccourci pandas (appelle matplotlib)
df.plot(x="date", y="ca", kind="line")       # df.plot(kind=...) : line, bar, barh, hist, box, scatter, pie, area...
df.plot.scatter(x="taille", y="poids", c="age", colormap="viridis")
```

## Exercices (à faire seul)

1. Trace la courbe de `sin(x)` pour x de 0 à 2π (utilise `numpy.linspace` et `numpy.sin`), avec titre et labels.
2. Crée une figure 1×3 : courbe, barres, histogramme sur des données aléatoires (graine fixée).
3. Personnalise un scatterplot : couleur selon une catégorie, taille des points selon une valeur, légende, et sauvegarde en PNG à 200 dpi.

## Pour aller plus loin

- [Matplotlib : tutoriel officiel](https://matplotlib.org/stable/tutorials/index.html)
- [Galerie d'exemples](https://matplotlib.org/stable/gallery/index.html)
