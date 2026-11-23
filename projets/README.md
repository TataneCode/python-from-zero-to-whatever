# Projets solo — à réaliser sans IA

Ces mini-projets sont conçus pour être faits **seul**, dans l'ordre, en t'appuyant uniquement sur les leçons du parcours et la documentation officielle. Ne demande pas la solution à une IA : le but est de chercher, tester, te tromper et trouver.

## Règles du jeu

1. Lis l'énoncé, écris ton code, teste, corrige. La documentation officielle est ton amie ([docs.python.org](https://docs.python.org/fr/3/), [pandas.pydata.org](https://pandas.pydata.org/docs/), etc.).
2. Versionne chaque projet avec git (un commit par étape qui marche).
3. Quand tu bloques plus de 30 min sur un point, note la question précise — puis cherche dans la doc avant toute autre aide.

## Progression proposée

| # | Projet | Niveau | Compétences visées |
|---|---|---|---|
| 1 | [Dépenses personnelles](01-depenses-personnelles.md) | ⭐ débutant | bases Python, fichiers CSV, pandas, matplotlib |
| 2 | [Notes de classe](02-notes-de-classe.md) | ⭐ débutant | fonctions, statistiques de base, numpy |
| 3 | [Météo d'une ville](03-meteo-open-meteo.md) | ⭐⭐ | API `requests`, JSON, nettoyage de dates, graphiques |
| 4 | [Scraping de livres](04-scraping-books.md) | ⭐⭐ | BeautifulSoup, parsing HTML, nettoyage de texte |
| 5 | [EDA du Titanic](05-titanic-eda.md) | ⭐⭐ | pandas, groupby, EDA complète, seaborn |
| 6 | [Pandas vs Polars](06-pandas-vs-polars.md) | ⭐⭐ | comparaison de perfs, benchmark |
| 7 | [Mini-ETL SQL](07-etl-sql.md) | ⭐⭐ | CSV → sqlite3/DuckDB → requêtes SQL → rapport |
| 8 | [Dashboard Streamlit](08-dashboard-streamlit.md) | ⭐⭐⭐ | app web interactive en pur Python |
| 9 | [Dataset volontairement sale](09-dataset-sale.md) | ⭐⭐⭐ | nettoyage complet, notebook documenté |
| 10 | [Rapport automatisé](10-rapport-automatise.md) | ⭐⭐⭐ | script + planification (cron), génération de PNG |

## Données utilisables sans clé API

- Tes propres données (dépenses, notes, livres lus...).
- [Open-Meteo](https://open-meteo.com/en/docs) (météo, sans clé), [REST Countries](https://restcountries.com/), [JSONPlaceholder](https://jsonplaceholder.com/), [PokeAPI](https://pokeapi.co/).
- [books.toscrape.com](https://books.toscrape.com/) (site d'entraînement au scraping).
- Jeux de données seaborn/plotly (`sns.load_dataset`, `px.data.*`).
- [data.gouv.fr](https://www.data.gouv.fr/) et [Kaggle](https://www.kaggle.com/datasets) (téléchargement manuel).
- Données générées toi-même avec `numpy.random`.
