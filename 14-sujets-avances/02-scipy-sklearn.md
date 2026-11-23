# Avancé 2 — SciPy et scikit-learn (aperçu)

```bash
pip install scipy scikit-learn
```

## SciPy : calcul scientifique

```python
import numpy as np
from scipy import stats

# lois de probabilité
data = np.random.default_rng(0).normal(100, 15, 1000)
stats.describe(data)                       # stats descriptives avancées
stats.normaltest(data)                     # test de normalité
stats.ttest_ind(groupe_a, groupe_b)        # test t de Student (2 groupes)
stats.pearsonr(x, y)                       # corrélation + p-value
stats.linregress(x, y)                     # régression linéaire (pente, ordonnée, r²)

# optimisation, intégration, traitement du signal...
from scipy import optimize
f = lambda x: (x - 3) ** 2
optimize.minimize(f, x0=0)                 # trouve le minimum
```

## scikit-learn : premier modèle de machine learning

Le pattern universel : `fit` (entraînement) puis `predict` (prédiction).

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

df = pd.read_csv("data/logements.csv")     # colonnes : surface, chambres, prix
X = df[["surface", "chambres"]]            # features (entrées)
y = df["prix"]                             # cible

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

modele = LinearRegression()
modele.fit(X_train, y_train)               # entraînement

predictions = modele.predict(X_test)
print("R² :", r2_score(y_test, predictions))
print("RMSE :", mean_squared_error(y_test, predictions) ** 0.5)

print("Coefficients :", modele.coef_, "Intercept :", modele.intercept_)
```

Autres modèles courants : `RandomForestRegressor`, `LogisticRegression` (classification), `KMeans` (clustering)... avec toujours la même API `fit`/`predict`.

## Exercices (à faire seul)

1. Test t : deux groupes de notes (2 classes) — y a-t-il une différence significative de moyenne ? (`stats.ttest_ind`)
2. Régression linéaire simple avec `stats.linregress` : prix d'un logement en fonction de la surface.
3. Premier modèle sklearn : prédis le pourboire (`tip`) à partir du montant (`total_bill`) sur le dataset `tips` de seaborn ; affiche R².

## Pour aller plus loin

- [SciPy](https://docs.scipy.org/doc/scipy/tutorial/index.html)
- [scikit-learn : getting started](https://scikit-learn.org/stable/getting_started.html)
- [Roadmap Machine Learning](https://roadmap.sh/machine-learning)
