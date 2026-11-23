# Projet 5 — EDA complète du Titanic

**Niveau :** ⭐⭐ · **Modules :** 05, 06, 07, 08

## Énoncé

Le dataset du Titanic (passagers, survie ou non) est le classique de l'EDA. Récupère le CSV `titanic.csv` (Kaggle « Titanic - Machine Learning from Disaster », téléchargement manuel) ou utilise `sns.load_dataset("titanic")`.

Réalise une **analyse exploratoire complète** dans un notebook Jupyter, avec au minimum :

1. **Inspection** : `info()`, `describe()`, % de valeurs manquantes par colonne.
2. **Nettoyage** : impute l'âge manquant (par la médiane par sexe/classe), gère `embarked` manquant, supprime ou transforme les colonnes inutiles (`deck` trop vide...).
3. **Stats** : taux de survie global, survie par sexe, par classe, par tranche d'âge (crée une colonne `tranche_age` avec `pd.cut`).
4. **Visualisations** (seaborn) : countplot survie, survie par sexe, distribution de l'âge des survivants vs non-survivants, heatmap de corrélation.
5. **3 questions métier** avec leurs réponses chiffrées, ex. : « Quelle classe a le meilleur taux de survie ? », « Les femmes ont-elles survécu plus que les hommes ? À quel point ? », « Le prix du billet (fare) est-il lié à la survie ? ».
6. Un **résumé écrit** en markdown dans le notebook (3-5 conclusions).

## Critères de réussite

- Notebook exécutable de haut en bas sans erreur (`Kernel > Restart & Run All`).
- Chaque graphique a un titre et une phrase d'interprétation en markdown.
- Les questions métier ont des réponses **chiffrées**.

## Extensions possibles

- Tableau croisé classe × sexe avec `crosstab(normalize="index")`.
- Compare survie des passagers seuls vs accompagnés (colonnes `sibsp` + `parch`).
