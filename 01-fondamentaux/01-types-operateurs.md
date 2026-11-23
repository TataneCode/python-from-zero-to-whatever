# Leçon 1 — Types de données et opérateurs

## Objectifs

- Connaître les 4 types de base : `int`, `float`, `bool`, `str`.
- Savoir convertir un type en un autre (`int()`, `float()`, `str()`, `bool()`).
- Utiliser les opérateurs arithmétiques, de comparaison et logiques.

## Les types de base

```python
age = 25                 # int (entier)
prix = 19.99             # float (décimal)
est_actif = True         # bool (True / False)
nom = "Alice"            # str (chaîne de caractères)

print(type(age))         # <class 'int'>
```

## Conversion de types (type casting)

```python
entier = int("42")       # "42" -> 42
decimal = float("3.14")  # "3.14" -> 3.14
texte = str(42)          # 42 -> "42"
vrai = bool(1)           # 1 -> True  (0 -> False)
```

Attention : `int("3.14")` provoque une erreur ; passe par `float` d'abord : `int(float("3.14"))` → `3`.

## Opérateurs arithmétiques

| Opérateur | Signification | Exemple |
|---|---|---|
| `+` `-` `*` | addition, soustraction, multiplication | `7 + 2` → `9` |
| `/` | division (toujours un `float`) | `7 / 2` → `3.5` |
| `//` | division entière | `7 // 2` → `3` |
| `%` | reste (modulo) | `7 % 2` → `1` |
| `**` | puissance | `2 ** 10` → `1024` |

## Opérateurs de comparaison

`==` `!=` `<` `<=` `>` `>=` → renvoient un `bool`.

```python
5 > 3    # True
"a" == "A"  # False (sensible à la casse)
```

## Opérateurs logiques

- `and` : les deux conditions doivent être vraies.
- `or` : au moins une doit être vraie.
- `not` : inverse la condition.

```python
age = 20
majeur = age >= 18 and age <= 120   # True
note = 15
recu = note >= 10 or note == 9.5    # True
```

## Afficher des variables

```python
nom = "Alice"
age = 25
print("Bonjour", nom, "tu as", age, "ans")
print(f"Bonjour {nom}, tu as {age} ans")   # f-string (recommandé)
print("L'année prochaine tu auras", age + 1, "ans")
```

## Exercices (à faire seul)

1. Demande à l'utilisateur son année de naissance (`input()`), calcule et affiche son âge approximatif.
2. Demande un prix HT et un taux de TVA (ex. 20), affiche le prix TTC.
3. Écris une fonction `est_pair(n)` qui renvoie `True` si `n` est pair (utilise `%`).
4. Demande trois notes, affiche la moyenne avec 2 décimales (`print(f"{moyenne:.2f}")`).

## Pour aller plus loin

- [Tutoriel officiel — nombres](https://docs.python.org/fr/3/tutorial/introduction.html#numbers)
- `input()` renvoie toujours une `str` : pense à convertir.
