# NumPy 3 — Algèbre linéaire et module random

## Algèbre linéaire (`np.linalg`)

```python
import numpy as np

A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

A @ B            # produit matriciel -> array([[19, 22], [43, 50]])
A.T              # transposée
np.linalg.inv(A) # inverse de A
np.linalg.det(A) # déterminant
np.linalg.norm(A)            # norme (de Frobenius par défaut)
np.linalg.norm(np.array([3, 4]))   # 5.0 (norme euclidienne d'un vecteur)

# Résoudre A x = b
b = np.array([1, 2])
x = np.linalg.solve(A, b)
```

Valeurs/vecteurs propres (utile en PCA, plus tard) :

```python
valeurs, vecteurs = np.linalg.eig(A)
```

## Module random (`np.random`)

Utilise toujours un **générateur** (`default_rng`) pour des résultats reproductibles :

```python
rng = np.random.default_rng(42)     # 42 = graine (seed) -> reproductible

rng.integers(0, 10, size=5)         # 5 entiers entre 0 et 9
rng.random(5)                       # 5 flottants dans [0, 1)
rng.normal(0, 1, size=1000)        # 1000 valeurs d'une loi normale centrée réduite
rng.choice(["a", "b", "c"], size=10)  # tirages avec remise
rng.shuffle(...)                    # mélange en place (sur un tableau)
```

Lois utiles en analyse : `normal`, `uniform`, `binomial`, `poisson`.

## Exercices (à faire seul)

1. Génère (avec graine 0) 10 000 valeurs d'une loi normale de moyenne 50 et d'écart-type 10 ; vérifie avec `.mean()` et `.std()` que tu retombes bien dessus (approximativement).
2. Crée deux matrices 3×3 aléatoires, calcule leur produit matriciel, et vérifie que `(A @ B).T == B.T @ A.T`.
3. Simule 1000 lancers de dé (`rng.integers(1, 7, size=1000)`) et compte la fréquence de chaque face.
4. Crée un vecteur aléatoire de taille 100, normalise-le pour que sa norme euclidienne fasse 1.

## Pour aller plus loin

- [numpy.linalg](https://numpy.org/doc/stable/reference/routines.linalg.html)
- [numpy.random Generator](https://numpy.org/doc/stable/reference/random/generator.html)

Module suivant : [05 — Pandas](../05-pandas/README.md).
