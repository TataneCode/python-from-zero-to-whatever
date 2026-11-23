# Projet 3 — Météo d'une ville sur 14 jours

**Niveau :** ⭐⭐ · **Modules :** 09 (API), 05 (pandas), 06 (dates), 08 (viz)

## Énoncé

Utilise l'[API Open-Meteo](https://open-meteo.com/en/docs) (gratuite, **sans clé**) pour récupérer les prévisions météo de ta ville sur 14 jours.

Le programme doit :

1. Demander le nom de la ville (ou hardcoder les coordonnées lat/lon) et appeler l'API avec `requests` (gère les erreurs HTTP).
2. Transformer le JSON reçu en DataFrame pandas avec colonnes : `date`, `tmax`, `tmin`, `precipitations`.
3. Convertir `date` en vraies dates (`pd.to_datetime`) et l'utiliser comme index.
4. Afficher : température max la plus haute et le jour correspondant, précipitations totales sur la période, écart moyen entre tmax et tmin.
5. Tracer un graphique matplotlib avec deux courbes (tmax, tmin) + barres de précipitations, sauvegardé en PNG.
6. Sauvegarder le DataFrame nettoyé en CSV.

## Critères de réussite

- Gestion propre des erreurs réseau (`try/except`, `timeout`).
- Un seul appel API récupère tout (paramètre `daily`).
- Le graphique a un titre, des légendes et des axes nommés.

## Extensions possibles

- Comparer la météo de 3 villes sur le même graphique.
- Corrélation : les jours de forte précipitation sont-ils les jours les plus frais ? (`df[["tmax","precipitations"]].corr()`)
- Alertes : afficher un message si une température dépasse un seuil que tu choisis.
