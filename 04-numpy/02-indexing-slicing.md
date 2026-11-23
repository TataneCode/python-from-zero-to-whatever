# NumPy 2 — Indexing et slicing

## Accès élémentaire

```python
import numpy as np

a = np.array([10, 20, 30, 40, 50])
a[0]     # 10
a[-1]    # 50 (dernier)
a[1:4]   # array([20, 30, 40])   tranche [début:fin[ (fin exclu)
a[:3]    # array([10, 20, 30])
a[::2]   # array([10, 30, 50])   pas de 2
```

> Un slice renvoie une **vue** (view) : modifier le slice modifie le tableau d'origine. Utilise `.copy()` pour une copie indépendante.

## Matrices 2D

```python
m = np.array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]])
m[0, 0]      # 1   (ligne 0, colonne 0)
m[1, 2]      # 6
m[0]         # array([1, 2, 3])  (ligne entière)
m[:, 1]      # array([2, 5, 8])  (colonne entière)
m[:2, 1:]    # sous-matrice : lignes 0-1, colonnes 1-2 -> [[2,3],[5,6]]
```

## Masques booléens (sélection par condition)

```python
v = np.array([3, 12, 7, 20, 5])
masque = v > 10            # array([False, True, False, True, False])
v[masque]                  # array([12, 20])  <- valeurs qui passent le test
v[v % 2 == 0]              # array([12, 20])  <- nombres pairs

v[masque] = 0              # modifie les éléments sélectionnés
```

C'est le mécanisme central du filtrage en data analysis.

## Fancy indexing (indexation par liste d'indices)

```python
a = np.array([10, 20, 30, 40, 50])
a[[0, 2, 4]]        # array([10, 30, 50])

m = np.array([[1, 2], [3, 4], [5, 6]])
m[[0, 2]]           # lignes 0 et 2 -> [[1,2],[5,6]]
m[[0, 2], [1, 0]]   # éléments (0,1) et (2,0) -> [2, 5]
```

## Exercices (à faire seul)

1. Crée une matrice 4×4 d'entiers de 1 à 16 (`np.arange(1, 17).reshape(4, 4)`) ; extrais la diagonale, la dernière colonne, et la sous-matrice centrale 2×2.
2. Dans un vecteur de 100 nombres aléatoires entre 0 et 1, remplace par -1 toutes les valeurs < 0.1, puis compte combien de -1 il y a.
3. Trie un vecteur avec `np.sort`, et trouve les indices des 3 plus grandes valeurs (`np.argsort`).
4. À partir d'une matrice 5×3, sélectionne uniquement les lignes dont la moyenne dépasse la moyenne globale de la matrice.

## Pour aller plus loin

- [NumPy : indexing](https://numpy.org/doc/stable/user/basics.indexing.html)
