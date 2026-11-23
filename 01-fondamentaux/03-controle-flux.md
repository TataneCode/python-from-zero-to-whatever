# Leçon 3 — Contrôle de flux (conditions et boucles)

## Objectifs

- Écrire des conditions avec `if / elif / else`.
- Parcourir des collections avec `for`.
- Répéter avec `while`, sortir avec `break`, sauter une itération avec `continue`.

## Conditions

```python
note = 15
if note >= 16:
    mention = "Très bien"
elif note >= 14:
    mention = "Bien"
elif note >= 12:
    mention = "Assez bien"
elif note >= 10:
    mention = "Passable"
else:
    mention = "Insuffisant"
```

> L'indentation (4 espaces) **fait partie de la syntaxe** en Python : c'est elle qui délimite les blocs.

Opérateurs logiques combinés : `and`, `or`, `not` (voir leçon 1).

## Boucle `for` — parcourir une séquence

```python
notes = [12, 15, 9, 18]
total = 0
for note in notes:
    total += note
print(total / len(notes))

for i in range(5):        # 0, 1, 2, 3, 4
    print(i)

for i, note in enumerate(notes):   # index + valeur
    print(f"Note {i + 1} : {note}")
```

`range(n)`, `range(debut, fin)`, `range(debut, fin, pas)`.

## Boucle `while` — répéter tant qu'une condition est vraie

```python
compteur = 0
while compteur < 5:
    print(compteur)
    compteur += 1        # indispensable pour sortir un jour !
```

## `break` et `continue`

```python
for n in range(10):
    if n == 3:
        continue        # saute l'itération 3
    if n == 7:
        break           # sort complètement de la boucle
    print(n)            # affiche 0,1,2,4,5,6
```

## Exercices (à faire seul)

1. Demande un nombre, affiche s'il est positif, négatif ou nul.
2. Affiche la table de multiplication de 7 (de 1 à 10) avec une boucle.
3. Parcours une liste de notes et compte combien sont >= 10 (sans utiliser `sum`).
4. Trouve le plus grand nombre d'une liste avec une boucle (indice : variable `max` initialisée au premier élément).
5. Boucle infinie contrôlée : demande un mot de passe jusqu'à ce qu'il soit correct (`while True` + `break`).

## Pour aller plus loin

- [Tutoriel officiel — contrôle de flux](https://docs.python.org/fr/3/tutorial/controlflow.html)
