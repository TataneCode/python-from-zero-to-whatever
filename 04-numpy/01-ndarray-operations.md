# NumPy 1 — Tableaux `ndarray` et opérations

## Créer des tableaux

```python
import numpy as np

a = np.array([1, 2, 3, 4])            # vecteur 1D
b = np.array([[1, 2, 3], [4, 5, 6]])  # matrice 2D (2 lignes, 3 colonnes)

print(a.shape)      # (4,)      -> dimensions
print(b.shape)      # (2, 3)
print(a.dtype)      # int64     -> type des éléments
print(b.ndim)       # 2         -> nombre de dimensions

zeros = np.zeros((3, 3))              # tableau de zéros
uns = np.ones((2, 4))                 # tableau de uns
plage = np.arange(0, 10, 2)           # [0 2 4 6 8]  (comme range)
lin = np.linspace(0, 1, 5)            # [0.  0.25 0.5  0.75 1. ]  (5 valeurs espacées)
```

## Opérations élément par élément (vectorisées)

```python
x = np.array([1, 2, 3, 4])
y = np.array([10, 20, 30, 40])

x + y        # array([11, 22, 33, 44])
x * 2        # array([2, 4, 6, 8])
x ** 2       # array([ 1,  4,  9, 16])
y / x        # array([10., 10., 10., 10.])
```

## Fonctions universelles (ufunc)

```python
np.sqrt(x)          # racine carrée de chaque élément
np.exp(x)           # exponentielle
np.log(x)           # logarithme naturel
np.abs(np.array([-3, 5]))   # valeur absolue -> [3 5]
np.sin(x)
```

## Agrégations

```python
x = np.array([1, 2, 3, 4])
x.sum()       # 10
x.mean()      # 2.5
x.min()       # 1
x.max()       # 4
x.std()       # écart-type
x.argmin()    # index du minimum

b = np.array([[1, 2, 3], [4, 5, 6]])
b.sum(axis=0)   # somme par colonne -> array([5, 7, 9])
b.sum(axis=1)   # somme par ligne   -> array([ 6, 15])
b.mean(axis=0)  # moyenne par colonne
```

## Broadcasting (diffusion)

NumPy étire automatiquement les dimensions compatibles :

```python
matrice = np.array([[1, 2, 3], [4, 5, 6]])
matrice + 10          # ajoute 10 à CHAQUE élément
vecteur = np.array([100, 200, 300])
matrice + vecteur     # ajoute le vecteur à chaque ligne
```

## Exercices (à faire seul)

1. Crée un tableau de 0 à 99 (`np.arange`) ; calcule la somme, la moyenne et l'écart-type.
2. Crée une matrice 3×3 de nombres aléatoires entiers entre 0 et 9 (`np.random.default_rng(0).integers(...)`) ; affiche la somme de chaque ligne et de chaque colonne.
3. Convertis une liste de températures en Celsius en Fahrenheit avec une seule opération vectorisée : `f = c * 9/5 + 32`.
4. Crée un vecteur de 1000 valeurs entre 0 et 1, compte combien sont supérieures à 0.5 (`np.sum(v > 0.5)`).

## Pour aller plus loin

- [NumPy : quickstart officiel](https://numpy.org/doc/stable/user/quickstart.html)
