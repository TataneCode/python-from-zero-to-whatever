# 04 — NumPy : le calcul numérique vectorisé

[NumPy](https://numpy.org/doc/stable/) est la brique de base de toute la data science en Python : tableaux multidimensionnels (`ndarray`) et opérations vectorisées ultra-rapides (écrites en C).

```bash
pip install numpy
```

```python
import numpy as np
```

## Leçons

1. [Tableaux `ndarray` et opérations](01-ndarray-operations.md) — création, formes, opérations élément par élément, fonctions universelles, agrégations.
2. [Indexing et slicing](02-indexing-slicing.md) — accès, tranches, masques booléens, fancy indexing.
3. [Algèbre linéaire et module random](03-algebre-lineaire-random.md) — produits matriciels, normes, génération de nombres aléatoires reproductibles.

## À retenir

- Un `ndarray` a un **seul type** de données (souvent `float64`).
- Les opérations s'appliquent **à tout le tableau d'un coup** : pas de boucle `for`.
- `np.array([...])` crée un tableau à partir d'une liste Python.

Module suivant : [05 — Pandas](../05-pandas/README.md).
