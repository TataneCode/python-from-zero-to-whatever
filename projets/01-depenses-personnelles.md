# Projet 1 — Analyse de tes dépenses personnelles

**Niveau :** ⭐ débutant · **Modules :** 01, 02, 03, 05 (bases), 08 (matplotlib)

## Énoncé

Pendant un mois, note toutes tes dépenses dans un fichier CSV que tu crées toi-même :

```csv
date,categorie,libelle,montant
2024-01-03,alimentation,courses supermarché,42.50
2024-01-05,transport,essence,55.00
...
```

Puis écris un programme Python qui :

1. Lit le CSV avec `csv` (stdlib) ou `pandas`.
2. Affiche le **total dépensé** et le **nombre de dépenses**.
3. Calcule le **total par catégorie** et affiche-le trié du plus grand au plus petit.
4. Calcule la **dépense moyenne par jour** sur la période.
5. Produit un **graphique en barres** des dépenses par catégorie (matplotlib) et le sauvegarde en PNG.
6. Bonus : affiche la catégorie qui représente la plus grande part du total (en %).

## Critères de réussite

- Le programme tourne sans erreur sur ton CSV réel.
- Le PNG est généré et lisible (titre, axes nommés).
- Le code est découpé en fonctions (une par étape).

## Extensions possibles

- Lire le CSV exporté par ta banque (souvent en `;` avec des virgules décimales) : gérer `sep=";"` et `decimal=","`.
- Ajouter une colonne `mois` et comparer deux mois.
- Version interactive : demander la catégorie en `input()` et n'afficher que celle-là.
