# 08 — Visualisation de données

Trois bibliothèques complémentaires :

| Bibliothèque | Style | Quand l'utiliser |
|---|---|---|
| **Matplotlib** | bas niveau, contrôle total | base de tout, figures sur mesure, publications |
| **Seaborn** | haut niveau, statistique | distributions, catégories, heatmaps, regression plots (s'appuie sur Matplotlib) |
| **Plotly** | interactif (zoom, survol, filtres) | dashboards, explorations interactives, web |

```bash
pip install matplotlib seaborn plotly
```

## Leçons

1. [Matplotlib](01-matplotlib.md) — figures, subplots, personnalisation, sauvegarde.
2. [Seaborn](02-seaborn.md) — distribution plots, categorical plots, heatmaps, regression plots.
3. [Plotly](03-plotly.md) — graphiques interactifs (Express).

## Règle d'or

Un bon graphique répond à **une question**. Titre explicite, axes nommés avec unités, légende si besoin, et sauvegarde en PNG/PDF/SVG (`fig.savefig(...)`).

Module suivant : [09 — Web scraping et API](../09-web/README.md).
