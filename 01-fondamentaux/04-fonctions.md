# Leçon 4 — Fonctions

## Objectifs

- Définir ses propres fonctions avec `def`.
- Utiliser les paramètres positionnels, `*args` et `**kwargs`.
- Écrire des fonctions courtes avec `lambda`.
- Connaître les fonctions intégrées essentielles.
- Distinguer **fonction** et **méthode**.

## Définir une fonction

```python
def aire_rectangle(longueur, largeur):
    """Renvoie l'aire d'un rectangle."""
    return longueur * largeur

aire = aire_rectangle(5, 3)   # 15
```

- `def` déclare la fonction, les `:` ouvrent le bloc (indenté).
- `return` renvoie une valeur et termine la fonction.
- La docstring (entre `"""`) documente la fonction.

Paramètre avec valeur par défaut :

```python
def salutation(nom, formule="Bonjour"):
    return f"{formule}, {nom} !"
```

## `*args` et `**kwargs`

```python
def somme(*nombres):              # nombre quelconque d'arguments positionnels
    return sum(nombres)

somme(1, 2, 3, 4)                 # 10

def presentation(**infos):         # nombre quelconque d'arguments nommés
    for cle, valeur in infos.items():
        print(f"{cle} : {valeur}")

presentation(nom="Alice", age=25, ville="Paris")
```

## Fonctions lambda

Fonction anonyme en une ligne, pratique pour un usage ponctuel :

```python
carre = lambda x: x ** 2
print(carre(4))                   # 16

notes = [12, 15, 9, 18]
doubles = list(map(lambda n: n * 2, notes))   # [24, 30, 18, 36]
triees = sorted(notes, key=lambda n: -n)      # tri décroissant
```

> Au-delà d'une ligne, préfère une `def` : plus lisible.

## Fonctions intégrées utiles en data analysis

| Fonction | Rôle | Exemple |
|---|---|---|
| `len(x)` | taille | `len([1, 2, 3])` → `3` |
| `sum(x)` | somme | `sum([1, 2, 3])` → `6` |
| `min(x)` / `max(x)` | extrême | `max([3, 9, 2])` → `9` |
| `abs(x)` | valeur absolue | `abs(-5)` → `5` |
| `round(x, n)` | arrondi à n décimales | `round(3.14159, 2)` → `3.14` |
| `sorted(x)` | liste triée | `sorted([3, 1, 2])` → `[1, 2, 3]` |
| `enumerate(x)` | (index, valeur) | voir leçon 3 |
| `zip(a, b)` | paires d'éléments | `list(zip([1,2],["a","b"]))` → `[(1,'a'), (2,'b')]` |
| `map(f, x)` | applique `f` à chaque élément | voir lambda |
| `input()` / `print()` | entrée / sortie | voir leçon 1 |

## Fonction vs méthode

- **Fonction** : appelée seule → `len(ma_liste)`, `print(x)`.
- **Méthode** : attachée à un objet, appelée avec un point → `ma_liste.append(1)`, `texte.upper()`.

```python
texte = "bonjour"
print(len(texte))        # fonction : 7
print(texte.upper())     # méthode : "BONJOUR"
```

## Exercices (à faire seul)

1. Écris `moyenne(notes)` qui renvoie la moyenne d'une liste (sans `sum` si tu veux t'entraîner, avec sinon).
2. Écris `statistiques(notes)` qui renvoie `(min, max, moyenne)` sous forme de tuple.
3. Écris `filtrer_pairs(*nombres)` qui renvoie la liste des nombres pairs passés en argument.
4. Utilise `sorted` avec une `lambda` pour trier une liste de dictionnaires de livres par prix croissant.
5. Écris une fonction `fibonacci(n)` qui renvoie les `n` premiers termes de la suite de Fibonacci.

## Pour aller plus loin

- [Tutoriel officiel — définir des fonctions](https://docs.python.org/fr/3/tutorial/controlflow.html#defining-functions)
- [Built-in functions](https://docs.python.org/fr/3/library/functions.html)
