# Projet 9 — Nettoyer un dataset volontairement sale

**Niveau :** ⭐⭐⭐ · **Modules :** 06 (tout le nettoyage), 07

## Énoncé

Génère toi-même un dataset de 500 lignes « réaliste et sale » (clients d'une boutique en ligne) avec au moins :

- des **valeurs manquantes** (âge, email, ville),
- des **dates** dans 3 formats différents (`"2024-01-15"`, `"15/01/2024"`, `"15 janv. 2024"`),
- du **texte sale** : `"  alice@EXEMPLE.fr  "`, noms avec espaces/casse aléatoires,
- des **outliers** : âges = -5 ou 250, montants négatifs ou énormes,
- des **catégories incohérentes** : `"H"`, `"homme"`, `"M"`, `"Femme"`, `"femme "` pour le sexe,
- des **types erronés** : âge en chaîne `"vingt-cinq"`, prix `"12,50 €"`.

Puis, dans un **notebook Jupyter documenté**, applique le nettoyage étape par étape (une cellule + explication markdown par étape) et termine par un mini-rapport EDA (3 stats + 2 graphiques).

## Critères de réussite

- Chaque étape de nettoyage est justifiée dans le notebook (pourquoi cette imputation, pourquoi cette règle d'outlier...).
- Un DataFrame « avant/après » comparatif (shape, % de manquants, dtypes).
- Le notebook se rejoue entièrement sans erreur.

## Extensions possibles

- Écris les règles de nettoyage dans une fonction `nettoyer(df)` réutilisable, testée sur un deuxième fichier sale.
- Encadre le tout dans une classe `NettoyeurDonnees` (module 14, POO).
