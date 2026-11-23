# Projet 10 — Rapport automatisé (script + planification)

**Niveau :** ⭐⭐⭐ · **Modules :** 05-08, 13 (aperçu Airflow/cron)

## Énoncé

Automatise la production d'un **rapport hebdomadaire** :

1. Un script `rapport.py` qui :
   - récupère les données (API Open-Meteo pour ta ville, ou lit le CSV du jour),
   - calcule les indicateurs (ex. : température moyenne/max de la semaine, précipitations totales, évolution vs semaine précédente si tu archives les rapports),
   - génère **2 graphiques PNG** (matplotlib) dans un dossier `rapports/YYYY-MM-DD/`,
   - écrit un petit fichier `resume.txt` (ou markdown) avec les chiffres clés.
2. Planifie l'exécution automatique :
   - **Linux** : `crontab -e` → ex. `0 8 * * 1 /chemin/.venv/bin/python /chemin/rapport.py` (tous les lundis à 8h),
   - **Windows** : Planificateur de tâches → nouvelle tâche, déclencheur hebdomadaire, action : lancer le script avec le python du venv.
3. Teste en lançant le script manuellement plusieurs fois : chaque exécution crée un dossier daté sans écraser les précédents.

## Critères de réussite

- Le script fonctionne depuis n'importe quel dossier (chemins relatifs au script via `pathlib.Path(__file__).parent`).
- Les rapports s'accumulent dans `rapports/` avec la date du jour.
- La planification est en place (montre la commande `crontab -l` ou la tâche planifiée).

## Extensions possibles

- Envoyer le rapport par email (`smtplib`) — ou simplement l'ouvrir dans un dashboard Streamlit qui liste les rapports archivés.
- Version « pro » : remplacer cron par un DAG Airflow minimal (module 13).
- Historique : un graphique de l'évolution des températures moyennes semaine après semaine.
