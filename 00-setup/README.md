# 00 — Mise en place de l'environnement

Avant toute leçon, prépare ta machine. L'ordre recommandé :

1. [Installation sous Linux](linux.md) ou [sous Windows](windows.md) : Python 3 + pip + venv.
2. [Configuration de VSCodium](vscodium.md) : l'IDE cible pour tout le parcours.
3. Crée un dossier de projet dédié, par exemple `~/projets/python-data-analysis/`, et un environnement virtuel à l'intérieur (voir les guides OS).
4. Installe les bibliothèques du parcours : `pip install -r requirements.txt` (fichier à la racine du dépôt).

## Vérification rapide

Dans un terminal, avec l'environnement virtuel activé :

```bash
python --version        # doit afficher Python 3.10 ou plus récent
pip --version
python -c "import numpy, pandas; print(numpy.__version__, pandas.__version__)"
```

## Alternatives si tu ne veux rien installer

- **JupyterLab** en local : `pip install jupyterlab` puis `jupyter lab` (interface notebook dans le navigateur).
- **Google Colab** : notebooks en ligne gratuits avec GPU, rien à installer (compte Google requis).

Passe ensuite au [module 01 — les fondamentaux de Python](../01-fondamentaux/README.md).
