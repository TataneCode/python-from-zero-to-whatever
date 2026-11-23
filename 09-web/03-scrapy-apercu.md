# Web 3 — Scrapy (aperçu)

```bash
pip install scrapy
```

**Scrapy** est un framework complet pour le scraping à grande échelle : requêtes asynchrones rapides, gestion automatique des erreurs, pipelines de nettoyage, export CSV/JSON, et `scrapy shell` pour tester ses sélecteurs.

## Quand passer de BeautifulSoup à Scrapy ?

- Des **centaines/milliers de pages** à crawler.
- Besoin de **vitesse** (requêtes parallèles).
- Projet structuré avec plusieurs « spiders » (robots d'exploration) et pipelines de traitement.

## Structure d'un projet Scrapy

```bash
scrapy startproject monsite
cd monsite
scrapy genspider livres books.toscrape.com
```

Un spider ressemble à :

```python
import scrapy

class LivresSpider(scrapy.Spider):
    name = "livres"
    start_urls = ["https://books.toscrape.com/"]

    def parse(self, response):
        for article in response.css("article.product_pod"):
            yield {
                "titre": article.css("h3 a::attr(title)").get(),
                "prix": article.css("p.price_color::text").get(),
            }
        # suivre la page suivante
        suivant = response.css("li.next a::attr(href)").get()
        if suivant:
            yield response.follow(suivant, callback=self.parse)
```

Lancement : `scrapy crawl livres -O livres.csv`

## `scrapy shell` : tester ses sélecteurs

```bash
scrapy shell "https://books.toscrape.com/"
>>> response.css("article.product_pod h3 a::attr(title)").getall()[:3]
```

## Exercices (à faire seul)

1. Installe scrapy, crée un projet, et réécris le scraping de books.toscrape.com en spider avec pagination sur 3 pages ; exporte en CSV.
2. Utilise `scrapy shell` pour trouver le sélecteur CSS qui isole les prix.

## Pour aller plus loin

- [Documentation Scrapy](https://docs.scrapy.org/)

Module suivant : [10 — SQL](../10-sql/README.md).
