# Dashboards 3 — Power BI, Tableau et outils BI (aperçu)

En entreprise, les dashboards sont souvent faits avec des outils dédiés, sans coder :

| Outil | Éditeur | Particularité |
|---|---|---|
| **Power BI** | Microsoft | intégré à l'écosystème Microsoft 365, langage DAX pour les mesures |
| **Tableau** | Salesforce | très visuel, glisser-déposer, calculs calculés puissants |
| **Looker Studio** | Google | gratuit, connecté à Google Sheets/BigQuery |
| **Metabase** | open source | dashboards SQL simples, auto-hébergeable |

## Ce qu'il faut retenir

- Ces outils se connectent aux mêmes sources (CSV, SQL, entrepôts de données) que Python.
- Python sert souvent **en amont** : nettoyer et préparer les données (pandas) avant de les charger dans Power BI/Tableau.
- Le métier de **BI Analyst** combine SQL + outil BI + un peu de modélisation ; c'est la [roadmap BI Analyst](https://roadmap.sh/ai-data-scientist) voisine.

## Exercice (à faire seul)

1. Télécharge la version gratuite de Power BI Desktop (Windows) ou essaie Metabase en local avec Docker, importe un de tes CSV nettoyés, et crée un dashboard avec 3 visualisations.

Module suivant : [13 — Big data et pipelines](../13-big-data-pipelines/README.md).
