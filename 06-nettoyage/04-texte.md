# Nettoyage 4 — Nettoyage de texte

## Méthodes `.str` de pandas (vectorisées)

```python
import pandas as pd

s = pd.Series(["  Alice  ", "BOB", "chloé Martin"])

s.str.strip()            # supprime espaces début/fin -> ["Alice", "BOB", "chloé Martin"]
s.str.lower()            # minuscules
s.str.upper()            # majuscules
s.str.capitalize()       # première lettre en majuscule
s.str.replace("a", "@")  # remplace (texte simple)
s.str.split(" ")         # découpe -> liste de mots (ex. "chloé Martin" -> ["chloé", "Martin"])
s.str.len()              # longueur de chaque chaîne
s.str.contains("ali", case=False)   # masque booléen
s.str.startswith("A")
s.str.slice(0, 3)        # 3 premiers caractères
```

Extraire avec des groupes nommés :

```python
s.str.extract(r"(\w+)\s+(\w+)")          # deux groupes : prénom + nom -> DataFrame 2 colonnes
```

## Expressions régulières avec `re` (module standard)

```python
import re

re.search(r"\d+", "prix: 123 €")            # trouve le premier groupe de chiffres
re.findall(r"\d+", "a1 b22 c333")           # ['1', '22', '333']
re.sub(r"\s+", " ", "trop   d'espaces")     # normalise les espaces -> "trop d'espaces"
```

En pandas, préférez les méthodes `.str` vectorisées ; `re` sert pour la logique ponctuelle.

```python
df["email_propre"] = df["email"].str.strip().str.lower()
df["domaine"] = df["email"].str.extract(r"@(.+)$")[0]
df["tel_nettoye"] = df["tel"].str.replace(r"[^0-9]", "", regex=True)   # garde uniquement les chiffres
```

## Tables de correspondance (mapping)

```python
mapping = {"fr": "France", "FR": "France", "fra": "France", "usa": "États-Unis"}
df["pays"] = df["code_pays"].str.lower().map(mapping)
```

## Exercices (à faire seul)

1. Colonne `nom` sale : espaces en trop, casse aléatoire, parfois "NOM Prénom" inversé → nettoie (strip, title) et sépare en deux colonnes avec `str.split` + `str.extract`.
2. Colonne `prix` du type "1 234,56 €" → enlève le symbole et les espaces, remplace la virgule par un point, convertis en float.
3. Colonne `code` du type "A-12-B" → extrais la partie numérique avec une regex.

## Pour aller plus loin

- [Pandas : working with text data](https://pandas.pydata.org/docs/user_guide/text.html)
- [regex101.com](https://regex101.com/) pour tester tes expressions régulières
- [Documentation `re`](https://docs.python.org/fr/3/library/re.html)
