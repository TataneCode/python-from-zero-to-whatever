# 06 — Nettoyage de données (Data Cleaning)

> « 80 % du travail d'un data analyst, c'est nettoyer les données. »

Avant toute analyse fiable, il faut traiter les valeurs manquantes, les outliers, les mauvais types, le texte sale et les catégories incohérentes.

## Leçons

1. [Valeurs manquantes](01-valeurs-manquantes.md) — `isna`/`isnull`, `dropna`, imputation, `ffill`/`bfill`.
2. [Détection des outliers](02-outliers.md) — IQR, z-score, visualisation.
3. [Conversion de types et parsing de dates](03-types-dates.md) — `astype`, `to_datetime`, `to_numeric`.
4. [Nettoyage de texte](04-texte.md) — `strip`, `replace`, `split`, expressions régulières (`re`), méthodes `.str` de pandas.
5. [Encodage des catégories](05-categories.md) — `astype("category")`, encodage one-hot (`get_dummies`).

## Ordre de travail conseillé

1. Charger → 2. Inspecter (`info`, `describe`, `isna().sum()`) → 3. Types et dates → 4. Texte → 5. Valeurs manquantes → 6. Outliers → 7. Catégories → 8. Sauvegarder la version propre.

Module suivant : [07 — Analyse exploratoire (EDA)](../07-eda/README.md).
