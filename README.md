# Python — de zéro à l'analyse de données

Parcours d'apprentissage guidé, construit à partir de la roadmap [roadmap.sh — Python for Data Analysis](https://roadmap.sh/python-data-analysis), pour apprendre Python appliqué à l'analyse de données, de l'installation de l'environnement jusqu'aux dashboards et aux pipelines.

## 🖥️ Démarrage : préparer ta machine

1. [Setup Linux](00-setup/linux.md) ou [Setup Windows](00-setup/windows.md) : Python 3, pip, venv.
2. [Configuration de VSCodium](00-setup/vscodium.md) (IDE cible du parcours).
3. Installer les bibliothèques : `pip install -r requirements.txt` dans ton venv.

## 📚 Les leçons (dans l'ordre de la roadmap)

| Module | Contenu |
|---|---|
| [01 — Fondamentaux](01-fondamentaux/README.md) | types, opérateurs, structures de données, conditions, boucles, fonctions, compréhensions, chaînes |
| [02 — Gestion des packages](02-gestion-packages/README.md) | pip, venv, uv, conda |
| [03 — Lecture de fichiers](03-lecture-fichiers/README.md) | `pathlib`, CSV, JSON, Excel, Parquet |
| [04 — NumPy](04-numpy/README.md) | `ndarray`, opérations vectorisées, indexing/slicing, algèbre linéaire, random |
| [05 — Pandas](05-pandas/README.md) | Series/DataFrame, lecture, filtrage, groupby, merge/join, reshaping |
| [06 — Nettoyage de données](06-nettoyage/README.md) | valeurs manquantes, outliers (IQR, z-score), types/dates, texte, catégories |
| [07 — EDA](07-eda/README.md) | statistiques descriptives, distributions, relations entre variables |
| [08 — Visualisation](08-visualisation/README.md) | Matplotlib, Seaborn, Plotly |
| [09 — Web](09-web/README.md) | API avec `requests`, scraping avec BeautifulSoup, Scrapy (aperçu) |
| [10 — SQL](10-sql/README.md) | fondamentaux SQL, sqlite3/SQLAlchemy, DuckDB |
| [11 — Polars](11-polars/README.md) | DataFrame rapide en Rust, expressions, lazy |
| [12 — Dashboards](12-dashboards/README.md) | Streamlit, Dash, Power BI/Tableau (aperçu) |
| [13 — Big data & pipelines](13-big-data-pipelines/README.md) | Dask, PySpark, Airflow (aperçus) |
| [14 — Sujets avancés](14-sujets-avances/README.md) | POO, SciPy/scikit-learn, géospatial (GeoPandas) |

## 🛠️ Projets solo (à faire sans IA)

10 mini-projets progressifs, énoncés uniquement dans [`projets/`](projets/README.md) : dépenses personnelles, notes de classe, météo via API, scraping de livres, EDA du Titanic, benchmark pandas vs Polars, mini-ETL SQL, dashboard Streamlit, nettoyage d'un dataset sale, rapport automatisé.

## 📖 Ressources officielles

- [Documentation Python 3 (FR)](https://docs.python.org/fr/3/)
- [NumPy](https://numpy.org/doc/stable/) · [Pandas](https://pandas.pydata.org/docs/) · [Matplotlib](https://matplotlib.org/stable/) · [Seaborn](https://seaborn.pydata.org/) · [Plotly](https://plotly.com/python/)
- [Requests](https://requests.readthedocs.io/) · [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) · [SQLite](https://www.sqlitetutorial.net/) · [DuckDB](https://duckdb.org/docs/) · [Polars](https://docs.pola.rs/) · [Streamlit](https://docs.streamlit.io/)
- Roadmaps voisines : [Data Analyst](https://roadmap.sh/data-analyst), [SQL](https://roadmap.sh/sql), [Machine Learning](https://roadmap.sh/machine-learning), [AI & Data Scientist](https://roadmap.sh/ai-data-scientist)

## 📁 Organisation

Chaque module contient un `README.md` (index) et des leçons numérotées. Chaque leçon comporte : objectifs, théorie avec exemples, exercices à faire seul, liens vers la doc officielle. Aucun corrigé n'est fourni : c'est volontaire.
