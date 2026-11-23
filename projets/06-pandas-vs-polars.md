# Projet 6 — Benchmark : pandas vs Polars

**Niveau :** ⭐⭐ · **Modules :** 04, 05, 11

## Énoncé

Génère toi-même un gros fichier de ventes (pas besoin de téléchargement) :

```python
import numpy as np, pandas as pd
rng = np.random.default_rng(42)
n = 2_000_000
df = pd.DataFrame({
    "date": pd.date_range("2023-01-01", periods=n, freq="s").astype(str),
    "produit": rng.choice(["A", "B", "C", "D", "E"], n),
    "categorie": rng.choice(["alim", "tech", "maison"], n),
    "ville": rng.choice(["Paris", "Lyon", "Lille", "Bordeaux"], n),
    "quantite": rng.integers(1, 10, n),
    "prix": np.round(rng.uniform(1, 500, n), 2),
})
df.to_csv("data/ventes_gros.csv", index=False)
```

Puis écris un script de benchmark qui mesure (avec `time.perf_counter()`) le temps de **la même analyse** avec pandas et avec Polars :

1. Lire le CSV.
2. Filtrer `prix > 50`.
3. `groupby(["categorie", "ville"])` + somme de `quantite * prix` (le CA), tri décroissant, top 10.

Affiche un tableau comparatif des temps. Réponds par écrit : quel outil gagne, et de combien ?

## Critères de réussite

- Même analyse des deux côtés (vérifie que les résultats sont identiques, ex. `pd.testing` ou `assert` sur les valeurs).
- Temps mesurés proprement (2-3 essais, moyenne).
- Fichier CSV généré avec une graine fixée (reproductible).

## Extensions possibles

- Tester aussi `pl.scan_csv` (lazy) vs `pl.read_csv`.
- Tester DuckDB (`duckdb.sql(...)`) comme troisième candidat.
- Mesurer la mémoire utilisée (`df.memory_usage(deep=True).sum()` côté pandas).
