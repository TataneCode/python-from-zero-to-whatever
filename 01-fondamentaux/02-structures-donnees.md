# Leçon 2 — Structures de données

## Objectifs

- Créer et manipuler **listes**, **tuples**, **sets** et **dictionnaires**.
- Choisir la bonne structure selon le besoin.
- Indexer et parcourir chaque structure.

## Listes — `list` (ordonnée, modifiable, avec doublons)

```python
notes = [12, 15, 9, 18]
notes.append(20)        # ajoute à la fin
notes.insert(0, 10)     # insère à l'index 0
notes.remove(9)         # supprime la première occurrence de 9
dernier = notes.pop()   # retire et renvoie le dernier élément
print(notes[0])         # 10  (index 0)
print(notes[-1])        # dernier élément
print(notes[1:3])       # sous-liste de l'index 1 à 2 inclus
print(len(notes))       # taille
```

## Tuples — `tuple` (ordonné, **non modifiable**)

```python
point = (3, 4)
x, y = point            # unpacking
# point[0] = 10         # ERREUR : un tuple ne se modifie pas
```

Utilise un tuple pour des données qui ne doivent pas changer (coordonnées, date, identifiant composé).

## Sets — `set` (non ordonné, **sans doublons**)

```python
villes = {"Paris", "Lyon", "Paris"}
print(villes)           # {'Lyon', 'Paris'}
villes.add("Marseille")
print("Lyon" in villes) # True  (test d'appartenance très rapide)
```

Opérations utiles : `a | b` (union), `a & b` (intersection), `a - b` (différence).

## Dictionnaires — `dict` (clé → valeur)

```python
personne = {"nom": "Alice", "age": 25, "ville": "Paris"}
print(personne["nom"])          # Alice
personne["age"] = 26            # modification
personne["email"] = "a@b.fr"    # ajout
print(personne.get("tel"))      # None (clé absente, sans erreur)
print(personne.keys())          # dict_keys(['nom', 'age', 'ville', 'email'])
print(personne.items())         # paires (clé, valeur), utile pour les boucles
```

Parcours :

```python
for cle, valeur in personne.items():
    print(f"{cle} = {valeur}")
```

## Quelle structure choisir ?

| Besoin | Structure |
|---|---|
| Collection ordonnée que je modifie souvent | `list` |
| Données fixes (ne doivent pas changer) | `tuple` |
| Savoir si un élément est présent / supprimer les doublons | `set` |
| Associer une valeur à une clé (fiche, enregistrement) | `dict` |

## Exercices (à faire seul)

1. Crée une liste de 5 prénoms, affiche le premier et le dernier, ajoute-en un sixième, trie la liste (`ma_liste.sort()`).
2. À partir d'une liste de nombres avec doublons, crée un `set` et affiche combien de valeurs uniques il contient.
3. Crée un dictionnaire représentant un livre (`titre`, `auteur`, `annee`, `prix`), affiche le prix, puis ajoute la clé `lu` (True/False).
4. Compte les occurrences de chaque lettre dans une phrase (indice : dictionnaire + boucle `for`).

## Pour aller plus loin

- [Tutoriel officiel — structures de données](https://docs.python.org/fr/3/tutorial/datastructures.html)
