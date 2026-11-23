# Big data 3 — Airflow : orchestrer des pipelines (aperçu)

```bash
pip install apache-airflow
```

**Apache Airflow** planifie et surveille des suites de tâches (un **DAG** = Directed Acyclic Graph) : « chaque nuit, récupérer les données → les nettoyer → les charger dans l'entrepôt → envoyer un rapport ».

## Concepts clés

- **DAG** : le graphe des tâches et de leurs dépendances.
- **Operator** : une tâche (PythonOperator pour exécuter une fonction, BashOperator...).
- **Scheduler** : déclenche les DAGs selon un planning (`@daily`, cron...).
- **Web UI** : visualise l'exécution, les logs, relance les tâches en échec.

## Exemple de DAG (Python)

```python
from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime

def nettoyer():
    import pandas as pd
    df = pd.read_csv("data/ventes_brut.csv")
    df = df.dropna()
    df.to_parquet("data/ventes_propre.parquet", index=False)

with DAG("pipeline_ventes", start_date=datetime(2024, 1, 1), schedule="@daily") as dag:
    t = PythonOperator(task_id="nettoyer", python_callable=nettoyer)
```

Lancement local : `airflow standalone` puis UI sur `http://localhost:8080`.

## Alternatives plus légères

- **cron** (Linux) / **Planificateur de tâches** (Windows) pour un simple script régulier.
- `schedule` (pip) en Python.
- Prefect / Dagster pour des orchestrateurs modernes plus simples qu'Airflow.

## Exercice (à faire seul)

1. Écris un script `pipeline.py` (récupérer API → nettoyer → sauvegarder) et planifie-le avec cron (`crontab -e`, ex. `0 2 * * * /chemin/.venv/bin/python /chemin/pipeline.py`) sur Linux, ou avec le Planificateur de tâches sur Windows.

## Pour aller plus loin

- [Documentation Airflow](https://airflow.apache.org/docs/)

Module suivant : [14 — Sujets avancés](../14-sujets-avances/README.md).
