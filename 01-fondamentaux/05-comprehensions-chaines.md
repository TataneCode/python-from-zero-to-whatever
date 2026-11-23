# Leçon 5 — Compréhensions de listes et manipulation de chaînes

## Objectifs

- Écrire des listes en une ligne avec les **list comprehensions**.
- Manipuler les chaînes : casse, découpage, recherche, remplacement, jointure.
- Utiliser les f-strings pour formater proprement.

## List comprehensions

Syntaxe : `[expression for élément in itérable if condition]`

```python
nombres = [1, 2, 3, 4, 5, 6]
carres = [n ** 2 for n in nombres]                    # [1, 4, 9, 16, 25, 36]
pairs = [n for n in nombres if n % 2 == 0]            # [2, 4, 6]
carres_pairs = [n ** 2 for n in nombres if n % 2 == 0]  # [4, 16, 36]
```

Autres exemples :

```python
mots = ["Bonjour", "LE", "monde"]
minuscules = [m.lower() for m in mots]
longueurs = {m: len(m) for m in mots}                 # dict comprehension
```

## Chaînes de caractères (rappels et compléments)

```python
texte = "  Bonjour le Monde  "
texte.strip()          # "Bonjour le Monde"  (supprime espaces début/fin)
texte.lower()          # "bonjour le monde"
texte.upper()          # "BONJOUR LE MONDE"
texte.replace("Monde", "monde!")   # remplace une sous-chaîne
"a-b-c".split("-")     # ['a', 'b', 'c']  (découpe)
" ".join(["a", "b", "c"])  # "a b c"  (jointure)
"Bonjour".startswith("Bon")  # True
"monde" in texte.lower()     # True (recherche de sous-chaîne)
len(texte)             # longueur
texte[0]               # ' '  (les chaînes sont indexables comme les listes)
```

## F-strings (affichage formaté)

```python
nom = "Alice"
note = 15.5
print(f"{nom} a eu {note}")            # Alice a eu 15.5
print(f"{nom} a eu {note:.1f}")        # Alice a eu 15.5 (1 décimale)
print(f"{note:.2f}")                   # 15.50
print(f"{1234567:,}")                  # 1,234,567 (séparateur de milliers, selon locale)
print(f"{0.95:.0%}")                   # 95% (pourcentage)
```

## Exercices (à faire seul)

1. À partir d'une liste de températures en Celsius, crée deux listes par comprehension : une en Fahrenheit, et une ne contenant que celles au-dessus de 25 °C.
2. Demande une phrase à l'utilisateur, compte combien de voyelles elle contient (comprehension + `in "aeiouy"`).
3. Transforme une liste de noms propres en une seule chaîne séparée par des virgules, en mettant la première lettre en majuscule (`str.capitalize()`).
4. À partir d'une liste de phrases, crée un dictionnaire `{phrase: nombre_de_mots}` par dict comprehension.

## Pour aller plus loin

- [Tutoriel officiel — comprehensions](https://docs.python.org/fr/3/tutorial/datastructures.html#list-comprehensions)
- [Méthodes des chaînes](https://docs.python.org/fr/3/library/stdtypes.html#string-methods)

Module suivant : [02 — Gestion des packages](../02-gestion-packages/README.md).
