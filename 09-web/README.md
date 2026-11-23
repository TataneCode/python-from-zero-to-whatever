# 09 — Récupérer des données sur le web (API et scraping)

Deux approches complémentaires :

- **API** avec `requests` : le site fournit des données structurées (JSON) — c'est la méthode propre et fiable.
- **Scraping HTML** avec `BeautifulSoup` (ou `scrapy` pour les gros projets) : on extrait les données des pages web elles-mêmes.

```bash
pip install requests beautifulsoup4
# scrapy (optionnel, projets de scraping avancés) : pip install scrapy
```

⚠️ Bonnes pratiques : respecte le `robots.txt` du site, les conditions d'utilisation, espace tes requêtes (`time.sleep(1)` entre deux appels), et n'extraie jamais de données personnelles.

## Leçons

1. [Appeler des API avec `requests`](01-apis-requests.md)
2. [Scraper du HTML avec `BeautifulSoup`](02-beautifulsoup.md)
3. [Scrapy en aperçu](03-scrapy-apercu.md)

Module suivant : [10 — SQL](../10-sql/README.md).
