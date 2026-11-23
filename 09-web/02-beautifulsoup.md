# Web 2 — Scraper du HTML avec BeautifulSoup

```bash
pip install beautifulsoup4
```

Quand il n'y a pas d'API, on parse le HTML de la page.

## Récupérer et parser une page

```python
import requests
from bs4 import BeautifulSoup

url = "https://books.toscrape.com/"        # site d'entraînement au scraping (prévu pour ça)
html = requests.get(url, timeout=10).text
soup = BeautifulSoup(html, "html.parser")

soup.title.text          # titre de la page
soup.find("h1").text     # premier <h1>
```

## Sélectionner des éléments (CSS)

```python
# par balise
soup.find_all("h3")                       # tous les <h3>

# par classe CSS
soup.select("article.product_pod")       # tous les articles produits
soup.select("div.price_color")

# combinaison
soup.select("p.star-rating.Three")       # classe multiple
```

## Extraire le texte et les attributs

```python
livre = soup.select_one("article.product_pod")
titre = livre.h3.a["title"]              # attribut title du <a> dans le <h3>
prix = livre.select_one("p.price_color").text     # "£51.77"
disponibilite = livre.select_one("p.instock.availability").text.strip()
lien = livre.h3.a["href"]                 # URL relative
```

## Boucler sur tous les éléments

```python
livres = []
for article in soup.select("article.product_pod"):
    livres.append({
        "titre": article.h3.a["title"],
        "prix": article.select_one("p.price_color").text,
        "note": article.select_one("p.star-rating")["class"][1],  # "Three", "Four"...
    })

import pandas as pd
df = pd.DataFrame(livres)
df["prix"] = df["prix"].str.replace("£", "").astype(float)
print(df.head())
print(df["note"].value_counts())
```

## Pagination

```python
page = 1
while page <= 3:
    url = f"https://books.toscrape.com/catalogue/page-{page}.html"
    ...
    page += 1
```

## Exercices (à faire seul)

1. Scrape la page d'accueil de books.toscrape.com : récupère titre, prix et note des 20 livres, mets-les dans un DataFrame.
2. Convertis les notes ("One" à "Five") en entiers (mapping) et calcule le prix moyen par note.
3. Scrape 3 pages (pagination) et sauvegarde le résultat en CSV.
4. Récupère la liste des pays depuis `https://restcountries.com/v3.1/all?fields=name,capital,population` (API JSON) — puis fais la même chose en scrapant une page HTML simple de ton choix.

## Pour aller plus loin

- [Documentation BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- Inspecte le HTML d'une page : clic droit → « Inspecter » dans ton navigateur (outil développeur, onglet Éléments).
