# Projet 4 — Scraper et analyser un catalogue de livres

**Niveau :** ⭐⭐ · **Modules :** 09 (BeautifulSoup), 05, 06 (nettoyage texte)

## Énoncé

[books.toscrape.com](https://books.toscrape.com/) est un site **conçu pour s'entraîner au scraping**. Ta mission :

1. Scraper la page d'accueil : pour chaque livre, extraire **titre, prix, note (étoiles), disponibilité**.
2. Convertir le prix (`"£51.77"`) en `float` et la note (`"Three"`) en entier 1-5 (mapping).
3. Stocker le tout dans un DataFrame pandas.
4. Analyser : prix moyen, prix min/max, livre le plus cher, répartition des notes (`value_counts`), nombre de livres disponibles vs indisponibles.
5. Graphiques : histogramme des prix, barplot du prix moyen par note.
6. Bonus : scraper les **3 premières pages** (pagination `catalogue/page-2.html`, ...) et sauvegarder le résultat complet en CSV.

## Critères de réussite

- `User-Agent` personnalisé dans les requêtes + `time.sleep(1)` entre les pages.
- Les prix sont bien des `float` (vérifie avec `dtypes`).
- Le CSV exporté se relit correctement.

## Extensions possibles

- Extraire aussi la catégorie de chaque livre (page détail) et calculer le prix moyen par catégorie.
- Trouver les livres "Five stars" au prix inférieur à la moyenne.
