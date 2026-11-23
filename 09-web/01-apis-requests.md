# Web 1 — Appeler des API avec `requests`

```bash
pip install requests
```

## GET : récupérer des données

```python
import requests

r = requests.get("https://api.open-meteo.com/v1/forecast",
                 params={"latitude": 48.85, "longitude": 2.35,
                         "daily": "temperature_2m_max,temperature_2m_min,precipitation_sum",
                         "timezone": "Europe/Paris",
                         "forecast_days": 7})
print(r.status_code)        # 200 = OK
print(r.ok)                 # True si status < 400

data = r.json()             # JSON -> dict Python
print(data["daily"]["time"])
print(data["daily"]["temperature_2m_max"])
```

## Gérer les erreurs

```python
try:
    r = requests.get("https://api.exemple.com/donnees", timeout=10)  # timeout obligatoire en pratique
    r.raise_for_status()    # lève une exception si 4xx/5xx
except requests.exceptions.HTTPError as e:
    print("Erreur HTTP :", e)
except requests.exceptions.ConnectionError:
    print("Connexion impossible")
except requests.exceptions.Timeout:
    print("La requête a expiré")
```

## API publiques sans clé (pour t'entraîner)

| API | Données | Exemple d'URL |
|---|---|---|
| Open-Meteo | météo mondiale, sans clé | `https://api.open-meteo.com/v1/forecast?latitude=48.85&longitude=2.35&current=temperature_2m` |
| REST Countries | pays du monde | `https://restcountries.com/v3.1/name/france` |
| JSONPlaceholder | données de test (posts, users...) | `https://jsonplaceholder.com/posts/1` |
| PokeAPI | Pokémon | `https://pokeapi.co/api/v2/pokemon/ditto` |
| Open Library | livres | `https://openlibrary.org/search.json?q=python` |

## POST : envoyer des données

```python
r = requests.post("https://httpbin.org/post",
                  json={"nom": "Alice", "age": 25},   # sérialisé en JSON automatiquement
                  headers={"Authorization": "Bearer <token>"})
print(r.json())
```

## En-têtes et authentification

```python
headers = {"User-Agent": "mon-projet-python/1.0", "Accept": "application/json"}
r = requests.get(url, headers=headers)
```

Certaines API exigent une clé : `params={"appid": "TA_CLE"}` ou en-tête `Authorization`. Ne committe **jamais** ta clé : utilise une variable d'environnement (`os.environ["MA_CLE"]` + fichier `.env` non versionné).

## Transformer la réponse en DataFrame

```python
import pandas as pd

meteo = requests.get("https://api.open-meteo.com/v1/forecast",
                     params={"latitude": 48.85, "longitude": 2.35,
                             "daily": "temperature_2m_max,precipitation_sum",
                             "forecast_days": 14, "timezone": "Europe/Paris"}).json()
df = pd.DataFrame(meteo["daily"])
df["time"] = pd.to_datetime(df["time"])
print(df.head())
```

## Exercices (à faire seul)

1. Récupère la météo actuelle de 3 villes avec Open-Meteo et affiche température + vent.
2. Interroge REST Countries pour obtenir capitale, population et superficie de la France ; mets-les dans un DataFrame.
3. Récupère les 10 premiers posts de JSONPlaceholder, eksttrais `userId` et `title`, compte les posts par utilisateur.
4. Ajoute un `time.sleep(1)` entre les appels d'une boucle de 5 requêtes (bonne pratique).

## Pour aller plus loin

- [Documentation requests](https://requests.readthedocs.io/)
- [Open-Meteo : documentation API](https://open-meteo.com/en/docs)
