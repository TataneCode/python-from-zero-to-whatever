# SQL 2 — sqlite3 (stdlib) et SQLAlchemy

## sqlite3 : base de données embarquée (aucun serveur)

```python
import sqlite3
import pandas as pd

con = sqlite3.connect("data/ma_base.db")   # crée le fichier s'il n'existe pas

# créer une table et insérer des données
con.execute("""
    CREATE TABLE IF NOT EXISTS clients (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        nom TEXT NOT NULL,
        ville TEXT,
        salaire REAL
    )
""")
con.execute("INSERT INTO clients (nom, ville, salaire) VALUES (?, ?, ?)", ("Alice", "Paris", 2500))
con.executemany("INSERT INTO clients (nom, ville, salaire) VALUES (?, ?, ?)",
                [("Bob", "Lyon", 3200), ("Chloe", "Paris", 2800)])
con.commit()   # valide les écritures

# interroger
for ligne in con.execute("SELECT * FROM clients WHERE ville = 'Paris'"):
    print(ligne)

# directement dans pandas
query = "SELECT ville, AVG(salaire) AS salaire_moyen, COUNT(*) AS nb FROM clients GROUP BY ville"
df = pd.read_sql_query(query, con)
print(df)

# écrire un DataFrame dans la base
df_ventes = pd.DataFrame({"id_client": [1, 1, 2], "montant": [120, 80, 200]})
df_ventes.to_sql("ventes", con, if_exists="replace", index=False)

con.close()
```

> Les `?` sont des **paramètres** : ils protègent des injections SQL (ne jamais construire une requête avec des f-strings sur des entrées utilisateur).

## SQLAlchemy : l'ORM professionnel

```bash
pip install sqlalchemy
```

```python
from sqlalchemy import create_engine, text

engine = create_engine("sqlite:///data/ma_base.db")     # même syntaxe pour PostgreSQL, MySQL...

with engine.connect() as conn:
    resultat = conn.execute(text("SELECT * FROM clients WHERE salaire > :seuil"), {"seuil": 2600})
    for ligne in resultat:
        print(ligne)

# avec pandas
df = pd.read_sql("SELECT * FROM ventes", engine)
```

SQLAlchemy sert aussi d'ORM (définir les tables comme des classes Python) pour les vraies applications.

## Exercices (à faire seul)

1. Crée une base `bibliotheque.db` avec tables `livres` et `auteurs`, insère des données, fais une jointure pour lister les livres avec le nom de l'auteur.
2. Charge un CSV avec pandas, écris-le dans une table sqlite avec `to_sql`, puis relis-le uniquement avec `pd.read_sql_query` et un `GROUP BY`.
3. Refais l'exercice 2 avec SQLAlchemy (`create_engine` + `text`).

## Pour aller plus loin

- [sqlite3 — doc Python](https://docs.python.org/fr/3/library/sqlite3.html)
- [SQLAlchemy](https://docs.sqlalchemy.org/)
