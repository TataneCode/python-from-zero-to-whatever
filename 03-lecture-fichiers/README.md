# 03 — Lecture et écriture de fichiers (formats de données)

## Objectifs

- Naviguer dans les chemins de fichiers avec `pathlib` (compatible Linux/Windows).
- Lire et écrire les formats de la roadmap : **CSV**, **JSON**, **Excel**, **Parquet**.
- Comprendre le contexte `with open(...)` pour les fichiers texte.

## Chemins de fichiers : `pathlib`

```python
from pathlib import Path

dossier = Path("data")              # chemin relatif, portable
fichier = dossier / "ventes.csv"    # concaténation propre avec "/"
print(fichier.exists())             # True si le fichier existe
print(fichier.suffix)               # ".csv"
dossier.mkdir(exist_ok=True)        # crée le dossier s'il n'existe pas
```

## Fichiers texte et `with open(...)`

```python
with open("data/notes.txt", "r", encoding="utf-8") as f:
    contenu = f.read()              # tout le fichier
    # ou f.readlines() pour une liste de lignes

with open("data/sortie.txt", "w", encoding="utf-8") as f:
    f.write("Bonjour\n")
```

Le `with` ferme le fichier automatiquement, même en cas d'erreur.

## CSV (valeurs séparées par des virgules)

```python
import csv

with open("data/ventes.csv", newline="", encoding="utf-8") as f:
    lecteur = csv.DictReader(f)     # chaque ligne devient un dict
    for ligne in lecteur:
        print(ligne["produit"], ligne["prix"])
```

> Pour l'analyse de données, on utilisera surtout **pandas** (`pd.read_csv`), plus puissant — ce module sert à comprendre le format. `csv` reste utile pour des fichiers simples sans installer pandas.

## JSON

```python
import json

with open("data/config.json", encoding="utf-8") as f:
    data = json.load(f)             # JSON -> dict/list Python

with open("data/sortie.json", "w", encoding="utf-8") as f:
    json.dump(data, f, indent=2, ensure_ascii=False)
```

## Excel (.xlsx)

Nécessite `openpyxl` (`pip install openpyxl`) :

```python
import pandas as pd

df = pd.read_excel("data/ventes.xlsx", sheet_name="Feuil1")
df.to_excel("data/export.xlsx", index=False)
```

## Parquet (format colonne binaire, rapide et compressé)

Nécessite `pyarrow` (`pip install pyarrow`) :

```python
import pandas as pd

df = pd.read_parquet("data/ventes.parquet")
df.to_parquet("data/export.parquet", index=False)
```

> Parquet est le format à privilégier pour les **gros volumes** de données.

## Récapitulatif

| Format | Lecture (stdlib) | Lecture (data) | Usage typique |
|---|---|---|---|
| Texte brut | `open()` | — | logs, notes |
| CSV | `csv` | `pd.read_csv` | exports, données tabulaires |
| JSON | `json` | `pd.read_json` | API, configuration |
| Excel | — | `pd.read_excel` | fichiers bureautique |
| Parquet | — | `pd.read_parquet` | gros volumes, data lakes |

## Exercices (à faire seul)

1. Crée un dossier `data/` et un fichier `data/produits.csv` à la main (5 lignes : produit, prix, quantité), puis lis-le avec `csv.DictReader` et affiche le prix total de chaque ligne.
2. Écris un programme qui convertit ce CSV en JSON (liste de dictionnaires) avec `json.dump`.
3. Avec pandas (module 05), lis le même CSV avec `pd.read_csv` et compare.

Module suivant : [04 — NumPy](../04-numpy/README.md).
