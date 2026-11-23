# Setup sous Windows (Python + VSCodium)

## 1. Installer Python 3

**Option A — winget (recommandé, Windows 10/11) :**

```powershell
winget install Python.Python.3.12
```

**Option B — installateur officiel :** télécharge l'installeur sur [python.org/downloads](https://www.python.org/downloads/) et **coche impérativement « Add Python to PATH »** à la première étape.

Vérifie dans un terminal (PowerShell ou CMD) :

```powershell
python --version   # Python 3.10+ recommandé
pip --version
```

> Si `python` n'est pas reconnu, relance l'installeur et coche « Add Python to PATH », ou ajoute manuellement le dossier d'installation (ex. `C:\Users\<toi>\AppData\Local\Programs\Python\Python312`) à la variable d'environnement `Path`.

## 2. Installer VSCodium

**Option A — winget :**

```powershell
winget install VSCodium.VSCodium
```

**Option B — installateur :** télécharge le fichier `.exe` ou `.msi` sur [vscodium.com](https://vscodium.com/#install) et lance-le.

## 3. Créer le projet et son environnement virtuel

```powershell
mkdir $HOME\projets\python-data-analysis
cd $HOME\projets\python-data-analysis
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

- Si PowerShell bloque le script avec une erreur d'« execution policy », exécute une fois :

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
  ```

- Avec l'invite de commandes classique (cmd) : `.\.venv\Scripts\activate.bat`

Puis installe les bibliothèques :

```powershell
python -m pip install --upgrade pip
pip install -r C:\chemin\vers\le\depot\requirements.txt
```

L'activation est visible : le prompt est préfixé par `(.venv)`.
Pour quitter l'environnement : `deactivate`.

## 4. Ouvrir le projet dans VSCodium

Dans le terminal :

```powershell
codium $HOME\projets\python-data-analysis
```

Puis :

1. `Ctrl+Maj+P` → tape `Python: Select Interpreter` → choisis `.\.venv\Scripts\python.exe`.
2. Installe les extensions (voir [vscodium.md](vscodium.md)) : **Python**, **Pylance**, **Jupyter**.
3. Ouvre un fichier `.py` et lance-le avec `F5` ou via le bouton ▶, ou dans le terminal intégré : `python mon_script.py`.

## 5. (Optionnel) JupyterLab

```powershell
pip install jupyterlab
jupyter lab
```

Un onglet navigateur s'ouvre sur `http://localhost:8888`.

## Récapitulatif des commandes utiles

| Action | PowerShell | cmd |
|---|---|---|
| Activer l'environnement | `.\.venv\Scripts\Activate.ps1` | `.\.venv\Scripts\activate.bat` |
| Quitter l'environnement | `deactivate` | `deactivate` |
| Installer un paquet | `pip install <paquet>` | `pip install <paquet>` |
| Lister les paquets | `pip list` | `pip list` |
| Geler les dépendances | `pip freeze > requirements.txt` | `pip freeze > requirements.txt` |
| Lancer un script | `python script.py` | `python script.py` |
| Lancer Jupyter | `jupyter lab` | `jupyter lab` |
