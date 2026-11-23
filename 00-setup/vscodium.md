# VSCodium : configuration pour la data analysis

VSCodium est la version 100 % open source de VS Code, sans télémétrie Microsoft. C'est l'IDE cible de ce parcours.

## 1. Extensions à installer

Ouvre le panneau Extensions (`Ctrl+Maj+X`) et installe :

| Extension | Éditeur | Rôle |
|---|---|---|
| **Python** | Microsoft | coloration, linting de base, débogage, sélection d'interpréteur |
| **Pylance** | Microsoft | autocomplétion intelligente et vérification de types |
| **Jupyter** | Microsoft | exécution de notebooks `.ipynb` directement dans VSCodium |

> VSCodium utilise le registre **Open VSX** (et non le marketplace Microsoft). Les extensions Microsoft ci-dessus y sont disponibles ; si une extension manque, cherche une alternative open source équivalente.

Extensions utiles ensuite : **Error Lens** (erreurs visibles en ligne), **autoDocstring** (génère les docstrings), **Rainbow CSV** (aperçu des CSV).

## 2. Sélectionner l'interpréteur Python du projet

1. Ouvre le dossier de ton projet : `Fichier > Ouvrir le dossier...`
2. `Ctrl+Maj+P` → `Python: Select Interpreter`
3. Choisis l'interpréteur de ton venv : `./.venv/bin/python` (Linux) ou `.\.venv\Scripts\python.exe` (Windows).

Vérification : la barre d'état en bas à gauche affiche `Python 3.x.x ('.venv')`.

## 3. Exécuter un script

- Bouton ▶ en haut à droite du fichier, ou `F5` (débogage), ou clic droit → **Run Python File in Terminal**.
- Le terminal intégré s'ouvre en bas ; assure-toi que le venv est actif (`(.venv)` dans le prompt). Sinon active-le manuellement (voir les guides Linux/Windows).

## 4. Travailler avec les notebooks (Jupyter)

1. Crée un fichier `notebook.ipynb` (ou `Nouveau fichier...` → sélectionne le type Notebook).
2. En haut à droite, clique sur **Select Kernel** → choisis l'interpréteur du venv.
3. Exécute les cellules avec `Maj+Entrée`.

## 5. Quelques raccourcis utiles

| Raccourci | Action |
|---|---|
| `Ctrl+Maj+P` | palette de commandes |
| `Ctrl+`` ` (backtick) | ouvrir/fermer le terminal |
| `Ctrl+Maj+X` | panneau extensions |
| `Ctrl+P` | ouvrir un fichier rapidement |
| `F5` / `Ctrl+F5` | déboguer / exécuter sans débogage |
| `Maj+Entrée` | exécuter la cellule (notebook) |
| `Ctrl+Shift+P` puis `Format Document` | formater le code |

## 6. Réglages recommandés (settings.json)

`Ctrl+Maj+P` → `Preferences: Open User Settings (JSON)` et ajoute :

```json
{
  "python.defaultInterpreterPath": ".venv/bin/python",
  "python.terminal.activateEnvironment": true,
  "editor.formatOnSave": true,
  "jupyter.askForKernelRestart": false
}
```

> Sur Windows, remplace `python.defaultInterpreterPath` par `.\.venv\Scripts\python.exe` (chemin relatif au dossier ouvert).

Tu es prêt·e : passe au [module 01 — fondamentaux de Python](../01-fondamentaux/README.md).
