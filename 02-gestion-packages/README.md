# 02 — Gestion des packages et des environnements

## Objectifs

- Comprendre le rôle de **pip**, **venv**, **conda** et **uv**.
- Savoir créer un environnement virtuel isolé par projet.
- Installer, mettre à jour et figer les dépendances.

## Pourquoi des environnements virtuels ?

Chaque projet a besoin de versions précises de bibliothèques. Un **environnement virtuel** (venv) isole les packages d'un projet du reste du système, évitant les conflits.

```bash
python -m venv .venv            # crée l'environnement
source .venv/bin/activate       # l'active (Linux/macOS)
.\.venv\Scripts\Activate.ps1   # l'active (Windows PowerShell)
deactivate                      # le quitte
```

## pip : le gestionnaire de packages officiel

```bash
pip install pandas              # installe
pip install "pandas>=2.0"      # avec contrainte de version
pip install --upgrade pip       # met à jour pip lui-même
pip list                        # liste les packages installés
pip show pandas                 # infos sur un package
pip freeze > requirements.txt   # fige les versions du projet
pip install -r requirements.txt # réinstalle tout (sur une autre machine)
```

## uv : l'outil moderne et rapide (recommandé en complément)

[uv](https://docs.astral.sh/uv/) remplace pip + venv par une seule commande rapide (écrit en Rust) :

```bash
pip install uv                  # ou via le script officiel sur docs.astral.sh
uv venv                         # crée .venv
uv pip install pandas           # installe dans le venv actif
uv pip install -r requirements.txt
uv run python mon_script.py     # exécute avec le bon environnement automatiquement
```

## conda : l'incontournable en data science / ML

[Conda](https://docs.conda.io/) gère des environnements **et** des paquets binaires (y compris des bibliothèques non-Python comme CUDA). Très utilisé avec **Anaconda** ou **Miniforge** (version communautaire légère, recommandée) :

```bash
conda create -n data python=3.12
conda activate data
conda install pandas numpy matplotlib
conda list
conda deactivate
```

> Pour ce parcours, `venv + pip` (ou `uv`) suffisent largement. Conda devient utile quand tu touches au machine learning avec des dépendances système (GPU, etc.).

## Bonnes pratiques

- Un venv **par projet**, jamais de `pip install` dans l'environnement système (sauf paquets système via `apt`, ex. `python3-venv`).
- Toujours versionner un `requirements.txt` (ou `pyproject.toml` avec uv) avec ton code.
- Ne jamais committer le dossier `.venv/` (voir `.gitignore` à la racine).

## Exercices (à faire seul)

1. Crée un nouveau venv dans un dossier de test, active-le, installe `requests`, vérifie avec `pip show requests`, puis gèle dans un `requirements.txt`.
2. Recrée le même environnement sur un autre dossier uniquement à partir du `requirements.txt`.
3. Essaie `uv venv` + `uv pip install` et compare la vitesse avec pip.

Module suivant : [03 — Lecture de fichiers](../03-lecture-fichiers/README.md).
