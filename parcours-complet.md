# Parcours complet — Python de zéro à l'analyse de données
> Concaténation de toutes les leçons du parcours, dans l'ordre de la roadmap (du setup jusqu'aux projets). Généré pour la lecture sur liseuse.


---

<!-- source : README.md -->

# Python — de zéro à l'analyse de données

Parcours d'apprentissage guidé, construit à partir de la roadmap [roadmap.sh — Python for Data Analysis](https://roadmap.sh/python-data-analysis), pour apprendre Python appliqué à l'analyse de données, de l'installation de l'environnement jusqu'aux dashboards et aux pipelines.

## 🖥️ Démarrage : préparer ta machine

1. [Setup Linux](00-setup/linux.md) ou [Setup Windows](00-setup/windows.md) : Python 3, pip, venv.
2. [Configuration de VSCodium](00-setup/vscodium.md) (IDE cible du parcours).
3. Installer les bibliothèques : `pip install -r requirements.txt` dans ton venv.

## 📚 Les leçons (dans l'ordre de la roadmap)

| Module | Contenu |
|---|---|
| [01 — Fondamentaux](01-fondamentaux/README.md) | types, opérateurs, structures de données, conditions, boucles, fonctions, compréhensions, chaînes |
| [02 — Gestion des packages](02-gestion-packages/README.md) | pip, venv, uv, conda |
| [03 — Lecture de fichiers](03-lecture-fichiers/README.md) | `pathlib`, CSV, JSON, Excel, Parquet |
| [04 — NumPy](04-numpy/README.md) | `ndarray`, opérations vectorisées, indexing/slicing, algèbre linéaire, random |
| [05 — Pandas](05-pandas/README.md) | Series/DataFrame, lecture, filtrage, groupby, merge/join, reshaping |
| [06 — Nettoyage de données](06-nettoyage/README.md) | valeurs manquantes, outliers (IQR, z-score), types/dates, texte, catégories |
| [07 — EDA](07-eda/README.md) | statistiques descriptives, distributions, relations entre variables |
| [08 — Visualisation](08-visualisation/README.md) | Matplotlib, Seaborn, Plotly |
| [09 — Web](09-web/README.md) | API avec `requests`, scraping avec BeautifulSoup, Scrapy (aperçu) |
| [10 — SQL](10-sql/README.md) | fondamentaux SQL, sqlite3/SQLAlchemy, DuckDB |
| [11 — Polars](11-polars/README.md) | DataFrame rapide en Rust, expressions, lazy |
| [12 — Dashboards](12-dashboards/README.md) | Streamlit, Dash, Power BI/Tableau (aperçu) |
| [13 — Big data & pipelines](13-big-data-pipelines/README.md) | Dask, PySpark, Airflow (aperçus) |
| [14 — Sujets avancés](14-sujets-avances/README.md) | POO, SciPy/scikit-learn, géospatial (GeoPandas) |

## 🛠️ Projets solo (à faire sans IA)

10 mini-projets progressifs, énoncés uniquement dans [`projets/`](projets/README.md) : dépenses personnelles, notes de classe, météo via API, scraping de livres, EDA du Titanic, benchmark pandas vs Polars, mini-ETL SQL, dashboard Streamlit, nettoyage d'un dataset sale, rapport automatisé.

## 📖 Ressources officielles

- [Documentation Python 3 (FR)](https://docs.python.org/fr/3/)
- [NumPy](https://numpy.org/doc/stable/) · [Pandas](https://pandas.pydata.org/docs/) · [Matplotlib](https://matplotlib.org/stable/) · [Seaborn](https://seaborn.pydata.org/) · [Plotly](https://plotly.com/python/)
- [Requests](https://requests.readthedocs.io/) · [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) · [SQLite](https://www.sqlitetutorial.net/) · [DuckDB](https://duckdb.org/docs/) · [Polars](https://docs.pola.rs/) · [Streamlit](https://docs.streamlit.io/)
- Roadmaps voisines : [Data Analyst](https://roadmap.sh/data-analyst), [SQL](https://roadmap.sh/sql), [Machine Learning](https://roadmap.sh/machine-learning), [AI & Data Scientist](https://roadmap.sh/ai-data-scientist)

## 📁 Organisation

Chaque module contient un `README.md` (index) et des leçons numérotées. Chaque leçon comporte : objectifs, théorie avec exemples, exercices à faire seul, liens vers la doc officielle. Aucun corrigé n'est fourni : c'est volontaire.


---

<!-- source : 00-setup/README.md -->

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


---

<!-- source : 00-setup/linux.md -->

# Setup sous Linux (Python + VSCodium)

Ce guide couvre les distributions basées sur Debian/Ubuntu ; des variantes pour Fedora et Arch sont indiquées entre parenthèses.

## 1. Installer Python 3, pip et venv

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

- Fedora : `sudo dnf install python3 python3-pip`
- Arch : `sudo pacman -S python python-pip`

Vérifie :

```bash
python3 --version   # Python 3.10+ recommandé
pip3 --version
```

> Astuce : sur certaines distributions, `python` n'existe pas, utilise toujours `python3`.

## 2. Installer VSCodium

**Option A — Flatpak (simple, fonctionne partout) :**

```bash
flatpak install flathub com.vscodium.codium
flatpak run com.vscodium.codium
```

**Option B — dépôt officiel (paquet `.deb`) :**

```bash
wget -qO - https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg \
  | gpg --dearmor | sudo dd of=/usr/share/keyrings/vscodium-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/vscodium-archive-keyring.gpg] https://download.vscodium.com/debs vscodium main" \
  | sudo tee /etc/apt/sources.list.d/vscodium.list
sudo apt update && sudo apt install codium
```

Lance ensuite `codium` depuis le menu ou le terminal.

**Option C — Arch :** `yay -S vscodium` (ou `vscodium-bin` depuis l'AUR).

## 3. Créer le projet et son environnement virtuel

```bash
mkdir -p ~/projets/python-data-analysis
cd ~/projets/python-data-analysis
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r /chemin/vers/le/depot/requirements.txt
```

L'activation est visible dans le terminal : le prompt est préfixé par `(.venv)`.
Pour quitter l'environnement : `deactivate`.

## 4. Ouvrir le projet dans VSCodium

```bash
codium ~/projets/python-data-analysis
```

Puis :

1. `Ctrl+Maj+P` → tape `Python: Select Interpreter` → choisis `./.venv/bin/python`.
2. Installe les extensions (voir [vscodium.md](vscodium.md)) : **Python**, **Pylance**, **Jupyter**.
3. Ouvre un fichier `.py` et lance-le avec `F5` ou via le bouton ▶, ou dans le terminal intégré : `python mon_script.py`.

## 5. (Optionnel) JupyterLab

```bash
pip install jupyterlab
jupyter lab
```

Un onglet navigateur s'ouvre sur `http://localhost:8888`.

## Récapitulatif des commandes utiles

| Action | Commande |
|---|---|
| Activer l'environnement | `source .venv/bin/activate` |
| Quitter l'environnement | `deactivate` |
| Installer un paquet | `pip install <paquet>` |
| Lister les paquets | `pip list` |
| Geler les dépendances | `pip freeze > requirements.txt` |
| Lancer un script | `python script.py` |
| Lancer Jupyter | `jupyter lab` |


---

<!-- source : 00-setup/vscodium.md -->

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


---

<!-- source : 00-setup/windows.md -->

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


---

<!-- source : 01-fondamentaux/README.md -->

# 01 — Fondamentaux de Python

Avant d'analyser des données, il faut maîtriser les bases du langage. Ce module couvre la partie « Python » de la roadmap.

## Leçons

1. [Types de données et opérateurs](01-types-operateurs.md) — entiers, flottants, booléens, chaînes, conversion de types, opérateurs arithmétiques/comparaison/logiques.
2. [Structures de données](02-structures-donnees.md) — listes, tuples, sets, dictionnaires.
3. [Contrôle de flux](03-controle-flux.md) — conditions `if/elif/else`, boucles `for`/`while`, `break`/`continue`.
4. [Fonctions](04-fonctions.md) — définition, `*args`/`**kwargs`, fonctions lambda, fonctions intégrées utiles, fonctions vs méthodes.
5. [Compréhensions et manipulation de chaînes](05-comprehensions-chaines.md) — list comprehensions, `print`, opérations courantes sur les strings.

## À la fin du module tu sauras

- Écrire un script Python qui lit des données saisies par l'utilisateur et applique des règles métier simples.
- Manipuler des listes et dictionnaires sans chercher la syntaxe à chaque fois.
- Structurer un programme en fonctions réutilisables.

Ressource officielle : [documentation Python 3 (tutoriel)](https://docs.python.org/fr/3/tutorial/).

Module suivant : [02 — Gestion des packages](../02-gestion-packages/README.md).


---

<!-- source : 01-fondamentaux/01-types-operateurs.md -->

# Leçon 1 — Types de données et opérateurs

## Objectifs

- Connaître les 4 types de base : `int`, `float`, `bool`, `str`.
- Savoir convertir un type en un autre (`int()`, `float()`, `str()`, `bool()`).
- Utiliser les opérateurs arithmétiques, de comparaison et logiques.

## Les types de base

```python
age = 25                 # int (entier)
prix = 19.99             # float (décimal)
est_actif = True         # bool (True / False)
nom = "Alice"            # str (chaîne de caractères)

print(type(age))         # <class 'int'>
```

## Conversion de types (type casting)

```python
entier = int("42")       # "42" -> 42
decimal = float("3.14")  # "3.14" -> 3.14
texte = str(42)          # 42 -> "42"
vrai = bool(1)           # 1 -> True  (0 -> False)
```

Attention : `int("3.14")` provoque une erreur ; passe par `float` d'abord : `int(float("3.14"))` → `3`.

## Opérateurs arithmétiques

| Opérateur | Signification | Exemple |
|---|---|---|
| `+` `-` `*` | addition, soustraction, multiplication | `7 + 2` → `9` |
| `/` | division (toujours un `float`) | `7 / 2` → `3.5` |
| `//` | division entière | `7 // 2` → `3` |
| `%` | reste (modulo) | `7 % 2` → `1` |
| `**` | puissance | `2 ** 10` → `1024` |

## Opérateurs de comparaison

`==` `!=` `<` `<=` `>` `>=` → renvoient un `bool`.

```python
5 > 3    # True
"a" == "A"  # False (sensible à la casse)
```

## Opérateurs logiques

- `and` : les deux conditions doivent être vraies.
- `or` : au moins une doit être vraie.
- `not` : inverse la condition.

```python
age = 20
majeur = age >= 18 and age <= 120   # True
note = 15
recu = note >= 10 or note == 9.5    # True
```

## Afficher des variables

```python
nom = "Alice"
age = 25
print("Bonjour", nom, "tu as", age, "ans")
print(f"Bonjour {nom}, tu as {age} ans")   # f-string (recommandé)
print("L'année prochaine tu auras", age + 1, "ans")
```

## Exercices (à faire seul)

1. Demande à l'utilisateur son année de naissance (`input()`), calcule et affiche son âge approximatif.
2. Demande un prix HT et un taux de TVA (ex. 20), affiche le prix TTC.
3. Écris une fonction `est_pair(n)` qui renvoie `True` si `n` est pair (utilise `%`).
4. Demande trois notes, affiche la moyenne avec 2 décimales (`print(f"{moyenne:.2f}")`).

## Pour aller plus loin

- [Tutoriel officiel — nombres](https://docs.python.org/fr/3/tutorial/introduction.html#numbers)
- `input()` renvoie toujours une `str` : pense à convertir.


---

<!-- source : 01-fondamentaux/02-structures-donnees.md -->

# Leçon 2 — Structures de données

## Objectifs

- Créer et manipuler **listes**, **tuples**, **sets** et **dictionnaires**.
- Choisir la bonne structure selon le besoin.
- Indexer et parcourir chaque structure.

## Listes — `list` (ordonnée, modifiable, avec doublons)

```python
notes = [12, 15, 9, 18]
notes.append(20)        # ajoute à la fin
notes.insert(0, 10)     # insère à l'index 0
notes.remove(9)         # supprime la première occurrence de 9
dernier = notes.pop()   # retire et renvoie le dernier élément
print(notes[0])         # 10  (index 0)
print(notes[-1])        # dernier élément
print(notes[1:3])       # sous-liste de l'index 1 à 2 inclus
print(len(notes))       # taille
```

## Tuples — `tuple` (ordonné, **non modifiable**)

```python
point = (3, 4)
x, y = point            # unpacking
# point[0] = 10         # ERREUR : un tuple ne se modifie pas
```

Utilise un tuple pour des données qui ne doivent pas changer (coordonnées, date, identifiant composé).

## Sets — `set` (non ordonné, **sans doublons**)

```python
villes = {"Paris", "Lyon", "Paris"}
print(villes)           # {'Lyon', 'Paris'}
villes.add("Marseille")
print("Lyon" in villes) # True  (test d'appartenance très rapide)
```

Opérations utiles : `a | b` (union), `a & b` (intersection), `a - b` (différence).

## Dictionnaires — `dict` (clé → valeur)

```python
personne = {"nom": "Alice", "age": 25, "ville": "Paris"}
print(personne["nom"])          # Alice
personne["age"] = 26            # modification
personne["email"] = "a@b.fr"    # ajout
print(personne.get("tel"))      # None (clé absente, sans erreur)
print(personne.keys())          # dict_keys(['nom', 'age', 'ville', 'email'])
print(personne.items())         # paires (clé, valeur), utile pour les boucles
```

Parcours :

```python
for cle, valeur in personne.items():
    print(f"{cle} = {valeur}")
```

## Quelle structure choisir ?

| Besoin | Structure |
|---|---|
| Collection ordonnée que je modifie souvent | `list` |
| Données fixes (ne doivent pas changer) | `tuple` |
| Savoir si un élément est présent / supprimer les doublons | `set` |
| Associer une valeur à une clé (fiche, enregistrement) | `dict` |

## Exercices (à faire seul)

1. Crée une liste de 5 prénoms, affiche le premier et le dernier, ajoute-en un sixième, trie la liste (`ma_liste.sort()`).
2. À partir d'une liste de nombres avec doublons, crée un `set` et affiche combien de valeurs uniques il contient.
3. Crée un dictionnaire représentant un livre (`titre`, `auteur`, `annee`, `prix`), affiche le prix, puis ajoute la clé `lu` (True/False).
4. Compte les occurrences de chaque lettre dans une phrase (indice : dictionnaire + boucle `for`).

## Pour aller plus loin

- [Tutoriel officiel — structures de données](https://docs.python.org/fr/3/tutorial/datastructures.html)


---

<!-- source : 01-fondamentaux/03-controle-flux.md -->

# Leçon 3 — Contrôle de flux (conditions et boucles)

## Objectifs

- Écrire des conditions avec `if / elif / else`.
- Parcourir des collections avec `for`.
- Répéter avec `while`, sortir avec `break`, sauter une itération avec `continue`.

## Conditions

```python
note = 15
if note >= 16:
    mention = "Très bien"
elif note >= 14:
    mention = "Bien"
elif note >= 12:
    mention = "Assez bien"
elif note >= 10:
    mention = "Passable"
else:
    mention = "Insuffisant"
```

> L'indentation (4 espaces) **fait partie de la syntaxe** en Python : c'est elle qui délimite les blocs.

Opérateurs logiques combinés : `and`, `or`, `not` (voir leçon 1).

## Boucle `for` — parcourir une séquence

```python
notes = [12, 15, 9, 18]
total = 0
for note in notes:
    total += note
print(total / len(notes))

for i in range(5):        # 0, 1, 2, 3, 4
    print(i)

for i, note in enumerate(notes):   # index + valeur
    print(f"Note {i + 1} : {note}")
```

`range(n)`, `range(debut, fin)`, `range(debut, fin, pas)`.

## Boucle `while` — répéter tant qu'une condition est vraie

```python
compteur = 0
while compteur < 5:
    print(compteur)
    compteur += 1        # indispensable pour sortir un jour !
```

## `break` et `continue`

```python
for n in range(10):
    if n == 3:
        continue        # saute l'itération 3
    if n == 7:
        break           # sort complètement de la boucle
    print(n)            # affiche 0,1,2,4,5,6
```

## Exercices (à faire seul)

1. Demande un nombre, affiche s'il est positif, négatif ou nul.
2. Affiche la table de multiplication de 7 (de 1 à 10) avec une boucle.
3. Parcours une liste de notes et compte combien sont >= 10 (sans utiliser `sum`).
4. Trouve le plus grand nombre d'une liste avec une boucle (indice : variable `max` initialisée au premier élément).
5. Boucle infinie contrôlée : demande un mot de passe jusqu'à ce qu'il soit correct (`while True` + `break`).

## Pour aller plus loin

- [Tutoriel officiel — contrôle de flux](https://docs.python.org/fr/3/tutorial/controlflow.html)


---

<!-- source : 01-fondamentaux/04-fonctions.md -->

# Leçon 4 — Fonctions

## Objectifs

- Définir ses propres fonctions avec `def`.
- Utiliser les paramètres positionnels, `*args` et `**kwargs`.
- Écrire des fonctions courtes avec `lambda`.
- Connaître les fonctions intégrées essentielles.
- Distinguer **fonction** et **méthode**.

## Définir une fonction

```python
def aire_rectangle(longueur, largeur):
    """Renvoie l'aire d'un rectangle."""
    return longueur * largeur

aire = aire_rectangle(5, 3)   # 15
```

- `def` déclare la fonction, les `:` ouvrent le bloc (indenté).
- `return` renvoie une valeur et termine la fonction.
- La docstring (entre `"""`) documente la fonction.

Paramètre avec valeur par défaut :

```python
def salutation(nom, formule="Bonjour"):
    return f"{formule}, {nom} !"
```

## `*args` et `**kwargs`

```python
def somme(*nombres):              # nombre quelconque d'arguments positionnels
    return sum(nombres)

somme(1, 2, 3, 4)                 # 10

def presentation(**infos):         # nombre quelconque d'arguments nommés
    for cle, valeur in infos.items():
        print(f"{cle} : {valeur}")

presentation(nom="Alice", age=25, ville="Paris")
```

## Fonctions lambda

Fonction anonyme en une ligne, pratique pour un usage ponctuel :

```python
carre = lambda x: x ** 2
print(carre(4))                   # 16

notes = [12, 15, 9, 18]
doubles = list(map(lambda n: n * 2, notes))   # [24, 30, 18, 36]
triees = sorted(notes, key=lambda n: -n)      # tri décroissant
```

> Au-delà d'une ligne, préfère une `def` : plus lisible.

## Fonctions intégrées utiles en data analysis

| Fonction | Rôle | Exemple |
|---|---|---|
| `len(x)` | taille | `len([1, 2, 3])` → `3` |
| `sum(x)` | somme | `sum([1, 2, 3])` → `6` |
| `min(x)` / `max(x)` | extrême | `max([3, 9, 2])` → `9` |
| `abs(x)` | valeur absolue | `abs(-5)` → `5` |
| `round(x, n)` | arrondi à n décimales | `round(3.14159, 2)` → `3.14` |
| `sorted(x)` | liste triée | `sorted([3, 1, 2])` → `[1, 2, 3]` |
| `enumerate(x)` | (index, valeur) | voir leçon 3 |
| `zip(a, b)` | paires d'éléments | `list(zip([1,2],["a","b"]))` → `[(1,'a'), (2,'b')]` |
| `map(f, x)` | applique `f` à chaque élément | voir lambda |
| `input()` / `print()` | entrée / sortie | voir leçon 1 |

## Fonction vs méthode

- **Fonction** : appelée seule → `len(ma_liste)`, `print(x)`.
- **Méthode** : attachée à un objet, appelée avec un point → `ma_liste.append(1)`, `texte.upper()`.

```python
texte = "bonjour"
print(len(texte))        # fonction : 7
print(texte.upper())     # méthode : "BONJOUR"
```

## Exercices (à faire seul)

1. Écris `moyenne(notes)` qui renvoie la moyenne d'une liste (sans `sum` si tu veux t'entraîner, avec sinon).
2. Écris `statistiques(notes)` qui renvoie `(min, max, moyenne)` sous forme de tuple.
3. Écris `filtrer_pairs(*nombres)` qui renvoie la liste des nombres pairs passés en argument.
4. Utilise `sorted` avec une `lambda` pour trier une liste de dictionnaires de livres par prix croissant.
5. Écris une fonction `fibonacci(n)` qui renvoie les `n` premiers termes de la suite de Fibonacci.

## Pour aller plus loin

- [Tutoriel officiel — définir des fonctions](https://docs.python.org/fr/3/tutorial/controlflow.html#defining-functions)
- [Built-in functions](https://docs.python.org/fr/3/library/functions.html)


---

<!-- source : 01-fondamentaux/05-comprehensions-chaines.md -->

# Leçon 5 — Compréhensions de listes et manipulation de chaînes

## Objectifs

- Écrire des listes en une ligne avec les **list comprehensions**.
- Manipuler les chaînes : casse, découpage, recherche, remplacement, jointure.
- Utiliser les f-strings pour formater proprement.

## List comprehensions

Syntaxe : `[expression for élément in itérable if condition]`

```python
nombres = [1, 2, 3, 4, 5, 6]
carres = [n ** 2 for n in nombres]                    # [1, 4, 9, 16, 25, 36]
pairs = [n for n in nombres if n % 2 == 0]            # [2, 4, 6]
carres_pairs = [n ** 2 for n in nombres if n % 2 == 0]  # [4, 16, 36]
```

Autres exemples :

```python
mots = ["Bonjour", "LE", "monde"]
minuscules = [m.lower() for m in mots]
longueurs = {m: len(m) for m in mots}                 # dict comprehension
```

## Chaînes de caractères (rappels et compléments)

```python
texte = "  Bonjour le Monde  "
texte.strip()          # "Bonjour le Monde"  (supprime espaces début/fin)
texte.lower()          # "bonjour le monde"
texte.upper()          # "BONJOUR LE MONDE"
texte.replace("Monde", "monde!")   # remplace une sous-chaîne
"a-b-c".split("-")     # ['a', 'b', 'c']  (découpe)
" ".join(["a", "b", "c"])  # "a b c"  (jointure)
"Bonjour".startswith("Bon")  # True
"monde" in texte.lower()     # True (recherche de sous-chaîne)
len(texte)             # longueur
texte[0]               # ' '  (les chaînes sont indexables comme les listes)
```

## F-strings (affichage formaté)

```python
nom = "Alice"
note = 15.5
print(f"{nom} a eu {note}")            # Alice a eu 15.5
print(f"{nom} a eu {note:.1f}")        # Alice a eu 15.5 (1 décimale)
print(f"{note:.2f}")                   # 15.50
print(f"{1234567:,}")                  # 1,234,567 (séparateur de milliers, selon locale)
print(f"{0.95:.0%}")                   # 95% (pourcentage)
```

## Exercices (à faire seul)

1. À partir d'une liste de températures en Celsius, crée deux listes par comprehension : une en Fahrenheit, et une ne contenant que celles au-dessus de 25 °C.
2. Demande une phrase à l'utilisateur, compte combien de voyelles elle contient (comprehension + `in "aeiouy"`).
3. Transforme une liste de noms propres en une seule chaîne séparée par des virgules, en mettant la première lettre en majuscule (`str.capitalize()`).
4. À partir d'une liste de phrases, crée un dictionnaire `{phrase: nombre_de_mots}` par dict comprehension.

## Pour aller plus loin

- [Tutoriel officiel — comprehensions](https://docs.python.org/fr/3/tutorial/datastructures.html#list-comprehensions)
- [Méthodes des chaînes](https://docs.python.org/fr/3/library/stdtypes.html#string-methods)

Module suivant : [02 — Gestion des packages](../02-gestion-packages/README.md).


---

<!-- source : 02-gestion-packages/README.md -->

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


---

<!-- source : 03-lecture-fichiers/README.md -->

# 03 — Lecture et écriture de fichiers (formats de données)

## Objectifs

- Naviguer dans les chemins de fichiers avec `pathlib` (compatible Linux/Windows).
- Lire et écrire les formats de la roadmap : **CSV**, **JSON**, **Excel**, **Parquet**.
- Comprendre le contexte `with open(...)` pour les fichiers texte.

## Chemins de fichiers : `pathlib`

```python
from pathlib import Path

dossier = Path("data")              # chemin relatif, portable
fichier = dossier / "ventes.csv"    # concaténation propre avec "/"
print(fichier.exists())             # True si le fichier existe
print(fichier.suffix)               # ".csv"
dossier.mkdir(exist_ok=True)        # crée le dossier s'il n'existe pas
```

## Fichiers texte et `with open(...)`

```python
with open("data/notes.txt", "r", encoding="utf-8") as f:
    contenu = f.read()              # tout le fichier
    # ou f.readlines() pour une liste de lignes

with open("data/sortie.txt", "w", encoding="utf-8") as f:
    f.write("Bonjour\n")
```

Le `with` ferme le fichier automatiquement, même en cas d'erreur.

## CSV (valeurs séparées par des virgules)

```python
import csv

with open("data/ventes.csv", newline="", encoding="utf-8") as f:
    lecteur = csv.DictReader(f)     # chaque ligne devient un dict
    for ligne in lecteur:
        print(ligne["produit"], ligne["prix"])
```

> Pour l'analyse de données, on utilisera surtout **pandas** (`pd.read_csv`), plus puissant — ce module sert à comprendre le format. `csv` reste utile pour des fichiers simples sans installer pandas.

## JSON

```python
import json

with open("data/config.json", encoding="utf-8") as f:
    data = json.load(f)             # JSON -> dict/list Python

with open("data/sortie.json", "w", encoding="utf-8") as f:
    json.dump(data, f, indent=2, ensure_ascii=False)
```

## Excel (.xlsx)

Nécessite `openpyxl` (`pip install openpyxl`) :

```python
import pandas as pd

df = pd.read_excel("data/ventes.xlsx", sheet_name="Feuil1")
df.to_excel("data/export.xlsx", index=False)
```

## Parquet (format colonne binaire, rapide et compressé)

Nécessite `pyarrow` (`pip install pyarrow`) :

```python
import pandas as pd

df = pd.read_parquet("data/ventes.parquet")
df.to_parquet("data/export.parquet", index=False)
```

> Parquet est le format à privilégier pour les **gros volumes** de données.

## Récapitulatif

| Format | Lecture (stdlib) | Lecture (data) | Usage typique |
|---|---|---|---|
| Texte brut | `open()` | — | logs, notes |
| CSV | `csv` | `pd.read_csv` | exports, données tabulaires |
| JSON | `json` | `pd.read_json` | API, configuration |
| Excel | — | `pd.read_excel` | fichiers bureautique |
| Parquet | — | `pd.read_parquet` | gros volumes, data lakes |

## Exercices (à faire seul)

1. Crée un dossier `data/` et un fichier `data/produits.csv` à la main (5 lignes : produit, prix, quantité), puis lis-le avec `csv.DictReader` et affiche le prix total de chaque ligne.
2. Écris un programme qui convertit ce CSV en JSON (liste de dictionnaires) avec `json.dump`.
3. Avec pandas (module 05), lis le même CSV avec `pd.read_csv` et compare.

Module suivant : [04 — NumPy](../04-numpy/README.md).


---

<!-- source : 04-numpy/README.md -->

# 04 — NumPy : le calcul numérique vectorisé

[NumPy](https://numpy.org/doc/stable/) est la brique de base de toute la data science en Python : tableaux multidimensionnels (`ndarray`) et opérations vectorisées ultra-rapides (écrites en C).

```bash
pip install numpy
```

```python
import numpy as np
```

## Leçons

1. [Tableaux `ndarray` et opérations](01-ndarray-operations.md) — création, formes, opérations élément par élément, fonctions universelles, agrégations.
2. [Indexing et slicing](02-indexing-slicing.md) — accès, tranches, masques booléens, fancy indexing.
3. [Algèbre linéaire et module random](03-algebre-lineaire-random.md) — produits matriciels, normes, génération de nombres aléatoires reproductibles.

## À retenir

- Un `ndarray` a un **seul type** de données (souvent `float64`).
- Les opérations s'appliquent **à tout le tableau d'un coup** : pas de boucle `for`.
- `np.array([...])` crée un tableau à partir d'une liste Python.

Module suivant : [05 — Pandas](../05-pandas/README.md).


---

<!-- source : 04-numpy/01-ndarray-operations.md -->

# NumPy 1 — Tableaux `ndarray` et opérations

## Créer des tableaux

```python
import numpy as np

a = np.array([1, 2, 3, 4])            # vecteur 1D
b = np.array([[1, 2, 3], [4, 5, 6]])  # matrice 2D (2 lignes, 3 colonnes)

print(a.shape)      # (4,)      -> dimensions
print(b.shape)      # (2, 3)
print(a.dtype)      # int64     -> type des éléments
print(b.ndim)       # 2         -> nombre de dimensions

zeros = np.zeros((3, 3))              # tableau de zéros
uns = np.ones((2, 4))                 # tableau de uns
plage = np.arange(0, 10, 2)           # [0 2 4 6 8]  (comme range)
lin = np.linspace(0, 1, 5)            # [0.  0.25 0.5  0.75 1. ]  (5 valeurs espacées)
```

## Opérations élément par élément (vectorisées)

```python
x = np.array([1, 2, 3, 4])
y = np.array([10, 20, 30, 40])

x + y        # array([11, 22, 33, 44])
x * 2        # array([2, 4, 6, 8])
x ** 2       # array([ 1,  4,  9, 16])
y / x        # array([10., 10., 10., 10.])
```

## Fonctions universelles (ufunc)

```python
np.sqrt(x)          # racine carrée de chaque élément
np.exp(x)           # exponentielle
np.log(x)           # logarithme naturel
np.abs(np.array([-3, 5]))   # valeur absolue -> [3 5]
np.sin(x)
```

## Agrégations

```python
x = np.array([1, 2, 3, 4])
x.sum()       # 10
x.mean()      # 2.5
x.min()       # 1
x.max()       # 4
x.std()       # écart-type
x.argmin()    # index du minimum

b = np.array([[1, 2, 3], [4, 5, 6]])
b.sum(axis=0)   # somme par colonne -> array([5, 7, 9])
b.sum(axis=1)   # somme par ligne   -> array([ 6, 15])
b.mean(axis=0)  # moyenne par colonne
```

## Broadcasting (diffusion)

NumPy étire automatiquement les dimensions compatibles :

```python
matrice = np.array([[1, 2, 3], [4, 5, 6]])
matrice + 10          # ajoute 10 à CHAQUE élément
vecteur = np.array([100, 200, 300])
matrice + vecteur     # ajoute le vecteur à chaque ligne
```

## Exercices (à faire seul)

1. Crée un tableau de 0 à 99 (`np.arange`) ; calcule la somme, la moyenne et l'écart-type.
2. Crée une matrice 3×3 de nombres aléatoires entiers entre 0 et 9 (`np.random.default_rng(0).integers(...)`) ; affiche la somme de chaque ligne et de chaque colonne.
3. Convertis une liste de températures en Celsius en Fahrenheit avec une seule opération vectorisée : `f = c * 9/5 + 32`.
4. Crée un vecteur de 1000 valeurs entre 0 et 1, compte combien sont supérieures à 0.5 (`np.sum(v > 0.5)`).

## Pour aller plus loin

- [NumPy : quickstart officiel](https://numpy.org/doc/stable/user/quickstart.html)


---

<!-- source : 04-numpy/02-indexing-slicing.md -->

# NumPy 2 — Indexing et slicing

## Accès élémentaire

```python
import numpy as np

a = np.array([10, 20, 30, 40, 50])
a[0]     # 10
a[-1]    # 50 (dernier)
a[1:4]   # array([20, 30, 40])   tranche [début:fin[ (fin exclu)
a[:3]    # array([10, 20, 30])
a[::2]   # array([10, 30, 50])   pas de 2
```

> Un slice renvoie une **vue** (view) : modifier le slice modifie le tableau d'origine. Utilise `.copy()` pour une copie indépendante.

## Matrices 2D

```python
m = np.array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]])
m[0, 0]      # 1   (ligne 0, colonne 0)
m[1, 2]      # 6
m[0]         # array([1, 2, 3])  (ligne entière)
m[:, 1]      # array([2, 5, 8])  (colonne entière)
m[:2, 1:]    # sous-matrice : lignes 0-1, colonnes 1-2 -> [[2,3],[5,6]]
```

## Masques booléens (sélection par condition)

```python
v = np.array([3, 12, 7, 20, 5])
masque = v > 10            # array([False, True, False, True, False])
v[masque]                  # array([12, 20])  <- valeurs qui passent le test
v[v % 2 == 0]              # array([12, 20])  <- nombres pairs

v[masque] = 0              # modifie les éléments sélectionnés
```

C'est le mécanisme central du filtrage en data analysis.

## Fancy indexing (indexation par liste d'indices)

```python
a = np.array([10, 20, 30, 40, 50])
a[[0, 2, 4]]        # array([10, 30, 50])

m = np.array([[1, 2], [3, 4], [5, 6]])
m[[0, 2]]           # lignes 0 et 2 -> [[1,2],[5,6]]
m[[0, 2], [1, 0]]   # éléments (0,1) et (2,0) -> [2, 5]
```

## Exercices (à faire seul)

1. Crée une matrice 4×4 d'entiers de 1 à 16 (`np.arange(1, 17).reshape(4, 4)`) ; extrais la diagonale, la dernière colonne, et la sous-matrice centrale 2×2.
2. Dans un vecteur de 100 nombres aléatoires entre 0 et 1, remplace par -1 toutes les valeurs < 0.1, puis compte combien de -1 il y a.
3. Trie un vecteur avec `np.sort`, et trouve les indices des 3 plus grandes valeurs (`np.argsort`).
4. À partir d'une matrice 5×3, sélectionne uniquement les lignes dont la moyenne dépasse la moyenne globale de la matrice.

## Pour aller plus loin

- [NumPy : indexing](https://numpy.org/doc/stable/user/basics.indexing.html)


---

<!-- source : 04-numpy/03-algebre-lineaire-random.md -->

# NumPy 3 — Algèbre linéaire et module random

## Algèbre linéaire (`np.linalg`)

```python
import numpy as np

A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

A @ B            # produit matriciel -> array([[19, 22], [43, 50]])
A.T              # transposée
np.linalg.inv(A) # inverse de A
np.linalg.det(A) # déterminant
np.linalg.norm(A)            # norme (de Frobenius par défaut)
np.linalg.norm(np.array([3, 4]))   # 5.0 (norme euclidienne d'un vecteur)

# Résoudre A x = b
b = np.array([1, 2])
x = np.linalg.solve(A, b)
```

Valeurs/vecteurs propres (utile en PCA, plus tard) :

```python
valeurs, vecteurs = np.linalg.eig(A)
```

## Module random (`np.random`)

Utilise toujours un **générateur** (`default_rng`) pour des résultats reproductibles :

```python
rng = np.random.default_rng(42)     # 42 = graine (seed) -> reproductible

rng.integers(0, 10, size=5)         # 5 entiers entre 0 et 9
rng.random(5)                       # 5 flottants dans [0, 1)
rng.normal(0, 1, size=1000)        # 1000 valeurs d'une loi normale centrée réduite
rng.choice(["a", "b", "c"], size=10)  # tirages avec remise
rng.shuffle(...)                    # mélange en place (sur un tableau)
```

Lois utiles en analyse : `normal`, `uniform`, `binomial`, `poisson`.

## Exercices (à faire seul)

1. Génère (avec graine 0) 10 000 valeurs d'une loi normale de moyenne 50 et d'écart-type 10 ; vérifie avec `.mean()` et `.std()` que tu retombes bien dessus (approximativement).
2. Crée deux matrices 3×3 aléatoires, calcule leur produit matriciel, et vérifie que `(A @ B).T == B.T @ A.T`.
3. Simule 1000 lancers de dé (`rng.integers(1, 7, size=1000)`) et compte la fréquence de chaque face.
4. Crée un vecteur aléatoire de taille 100, normalise-le pour que sa norme euclidienne fasse 1.

## Pour aller plus loin

- [numpy.linalg](https://numpy.org/doc/stable/reference/routines.linalg.html)
- [numpy.random Generator](https://numpy.org/doc/stable/reference/random/generator.html)

Module suivant : [05 — Pandas](../05-pandas/README.md).


---

<!-- source : 05-pandas/README.md -->

# 05 — Pandas : la manipulation de données tabulaires

[Pandas](https://pandas.pydata.org/docs/) est **la** bibliothèque de référence pour lire, transformer et analyser des données structurées (CSV, Excel, SQL...) en Python.

```bash
pip install pandas
```

```python
import pandas as pd
```

## Leçons

1. [Series et DataFrame](01-series-dataframe.md) — créer, inspecter (`head`, `info`, `describe`, `shape`, `dtypes`).
2. [Lire et écrire des données](02-lecture-ecriture.md) — CSV, Excel, JSON, Parquet, SQL.
3. [Indexing, slicing et filtrage](03-indexing-filtrage.md) — `loc`, `iloc`, masques booléens, `query`.
4. [GroupBy et agrégation](04-groupby-agregation.md) — `groupby`, `agg`, `value_counts`, tableaux croisés.
5. [Merging et joining](05-merge-join.md) — `merge`, `concat`, jointures type SQL.
6. [Reshaping](06-reshape.md) — `pivot_table`, `melt`, `stack`/`unstack`, `crosstab`.

## À retenir

- Un **DataFrame** = tableau 2D avec des étiquettes de lignes (index) et de colonnes.
- Une **Series** = une seule colonne (ou ligne) avec un index.
- Pandas s'appuie sur NumPy : même logique de vectorisation.

Module suivant : [06 — Nettoyage de données](../06-nettoyage/README.md).


---

<!-- source : 05-pandas/01-series-dataframe.md -->

# Pandas 1 — Series et DataFrame

## Series (une colonne)

```python
import pandas as pd

s = pd.Series([10, 20, 30], index=["a", "b", "c"], name="valeurs")
print(s["b"])        # 20
print(s.mean())      # 20.0
print(s + 5)         # opérations vectorisées comme NumPy
```

## DataFrame (le tableau central)

```python
df = pd.DataFrame({
    "nom": ["Alice", "Bob", "Chloe"],
    "age": [25, 30, 22],
    "ville": ["Paris", "Lyon", "Paris"],
    "salaire": [2500, 3200, 2800],
})

print(df.head(2))    # 2 premières lignes
print(df.tail(1))    # dernière ligne
print(df.shape)      # (3, 4)  -> (lignes, colonnes)
print(df.columns)    # Index(['nom', 'age', 'ville', 'salaire'])
print(df.dtypes)     # type de chaque colonne
print(df.index)      # index des lignes
```

## Inspection rapide (indispensable)

```python
df.info()            # types, valeurs non nulles, mémoire
print(df.describe()) # statistiques des colonnes numériques (count, mean, std, min, 25%, 50%, 75%, max)
print(df["ville"].value_counts())  # effectif par catégorie
```

## Accéder aux colonnes et lignes

```python
df["nom"]            # une colonne -> Series
df[["nom", "age"]]   # plusieurs colonnes -> DataFrame
print(df["age"].mean())
```

Pour les lignes, voir la leçon 3 (`loc` / `iloc`). Aperçu :

```python
df.loc[0]            # ligne d'index 0 (toutes colonnes)
df.iloc[0]           # première ligne (position)
```

## Exercices (à faire seul)

1. Crée un DataFrame de 5 élèves avec colonnes `nom`, `note_maths`, `note_francais` ; affiche `describe()`.
2. Crée une Series de températures journalières indexées par des dates (strings "2024-01-01"...) ; affiche la température max et le jour correspondant (`idxmax()`).
3. À partir du DataFrame élèves, crée une nouvelle colonne `moyenne` = moyenne des deux notes.

## Pour aller plus loin

- [Pandas : 10 minutes to pandas](https://pandas.pydata.org/docs/user_guide/10min.html)
- [DataFrame vs Series](https://pandas.pydata.org/docs/getting_started/basics.html)


---

<!-- source : 05-pandas/02-lecture-ecriture.md -->

# Pandas 2 — Lire et écrire des données

## Lire des fichiers locaux

```python
import pandas as pd

df = pd.read_csv("data/ventes.csv")                    # CSV (séparateur virgule par défaut)
df = pd.read_csv("data/ventes.csv", sep=";")           # point-virgule (export Excel FR)
df = pd.read_csv("data/ventes.csv", sep=";", decimal=",")  # virgule comme séparateur décimal
df = pd.read_excel("data/ventes.xlsx", sheet_name="Feuil1")   # nécessite openpyxl
df = pd.read_json("data/donnees.json")                 # JSON
df = pd.read_parquet("data/ventes.parquet")             # Parquet (nécessite pyarrow)
```

Options utiles de `read_csv` : `header=0`, `names=[...]`, `skiprows=n`, `encoding="utf-8"` ou `"latin-1"`, `na_values=["N/A", "-"]`, `parse_dates=["date"]`, `dayfirst=True`.

## Lire depuis une URL

```python
df = pd.read_csv("https://raw.githubusercontent.com/.../fichier.csv")
```

## Lire depuis une base SQL

```python
import sqlite3
con = sqlite3.connect("data/ma_base.db")
df = pd.read_sql_query("SELECT * FROM clients WHERE ville = 'Paris'", con)
```

(Voir le [module 10 — SQL](../10-sql/README.md) pour aller plus loin.)

## Écrire

```python
df.to_csv("data/sortie.csv", index=False)          # index=False : ne pas écrire l'index comme colonne
df.to_csv("data/sortie.csv", sep=";", index=False, encoding="utf-8-sig")  # lisible par Excel FR
df.to_excel("data/sortie.xlsx", index=False)       # nécessite openpyxl
df.to_json("data/sortie.json", orient="records", force_ascii=False, indent=2)
df.to_parquet("data/sortie.parquet", index=False)  # nécessite pyarrow
df.to_sql("table_resultat", con, if_exists="replace", index=False)
```

## Exercices (à faire seul)

1. Crée un CSV à la main (ou exporte un tableur) avec 10 lignes et 4 colonnes, lis-le avec `pd.read_csv`, affiche `info()` et `describe()`.
2. Re-lis le même fichier en forçant la colonne date avec `parse_dates` et vérifie le `dtype`.
3. Écris le DataFrame filtré (lignes où une colonne numérique > seuil) dans un nouveau CSV **et** un Parquet ; compare les tailles de fichiers.

## Pour aller plus loin

- [Pandas : IO tools (lecture/écriture)](https://pandas.pydata.org/docs/user_guide/io.html)


---

<!-- source : 05-pandas/03-indexing-filtrage.md -->

# Pandas 3 — Indexing, slicing et filtrage

## `loc` (par étiquette) et `iloc` (par position)

```python
import pandas as pd

df = pd.DataFrame({
    "nom": ["Alice", "Bob", "Chloe", "David"],
    "age": [25, 30, 22, 35],
    "ville": ["Paris", "Lyon", "Paris", "Lyon"],
    "salaire": [2500, 3200, 2800, 4100],
})

df.loc[0, "nom"]        # "Alice"      (étiquette de ligne, nom de colonne)
df.loc[0:2, "nom"]      # lignes 0 à 2 incluses (loc inclut la borne !)
df.iloc[0:2]            # 2 premières lignes (borne exclue, comme les slices Python)
df.iloc[:, 1:3]         # toutes les lignes, colonnes 1 et 2
```

## Filtrage par conditions (masques booléens)

```python
# une condition
df[df["age"] > 25]

# plusieurs conditions : & (et), | (ou), ~ (non) — chaque condition entre parenthèses
adultes_parisiens = df[(df["age"] >= 18) & (df["ville"] == "Paris")]
haut_salaire = df[(df["salaire"] > 3000) | (df["ville"] == "Paris")]
pas_lyon = df[~(df["ville"] == "Lyon")]

# méthode isin : appartenance à une liste
df[df["ville"].isin(["Paris", "Marseille"])]

# chaînes : méthodes .str
df[df["nom"].str.startswith("A")]
df[df["nom"].str.contains("a", case=False)]
```

## `query()` : filtrer avec une expression textuelle

```python
df.query("age > 25 and ville == 'Lyon'")
df.query("salaire > @seuil")   # @seuil fait référence à une variable Python du scope
```

## Sélectionner + modifier

```python
df.loc[df["ville"] == "Paris", "salaire"] = df["salaire"] * 1.1   # augmentation de 10 % à Paris
df.loc[df["age"] < 18, "age"] = None                               # valeurs manquantes (voir module 06)
```

## Trier

```python
df.sort_values("salaire")                        # croissant
df.sort_values(["ville", "salaire"], ascending=[True, False])  # par ville puis salaire décroissant
df.sort_index()
```

## Exercices (à faire seul)

1. Sur un DataFrame de ventes (date, produit, quantité, prix), sélectionne les ventes de janvier 2024 pour le produit "X".
2. Compte combien de lignes ont au moins une valeur manquante (`df.isna().any(axis=1).sum()`).
3. Remplace les salaires inférieurs à 2000 par la médiane des salaires (`df["salaire"].median()`).
4. Trie par catégorie puis par montant décroissant, et garde les 10 premières lignes (`head(10)`).

## Pour aller plus loin

- [Pandas : indexing and selecting data](https://pandas.pydata.org/docs/user_guide/indexing.html)


---

<!-- source : 05-pandas/04-groupby-agregation.md -->

# Pandas 4 — GroupBy et agrégation

Le pattern fondamental de l'analyse : **split → apply → combine**.

```python
import pandas as pd

df = pd.DataFrame({
    "ville":    ["Paris", "Lyon", "Paris", "Lyon", "Paris", "Lyon"],
    "produit":  ["A", "A", "B", "B", "A", "B"],
    "quantite": [10, 5, 8, 12, 7, 3],
    "prix":     [100, 50, 80, 120, 70, 30],
})
```

## `groupby` + agrégation

```python
df.groupby("ville")["quantite"].sum()          # total par ville
df.groupby("ville")["prix"].mean()             # prix moyen par ville

df.groupby("ville").agg(                       # plusieurs agrégations d'un coup
    total_quantite=("quantite", "sum"),
    prix_moyen=("prix", "mean"),
    nb_ventes=("prix", "count"),
)

df.groupby(["ville", "produit"])[["quantite", "prix"]].sum()   # double groupement
```

Autres agrégations : `min`, `max`, `median`, `std`, `var`, `first`, `last`, `nunique` (nombre de valeurs uniques).

## `value_counts` et `crosstab`

```python
df["ville"].value_counts()                       # effectifs par valeur
df["ville"].value_counts(normalize=True)        # en proportion (somme = 1)
pd.crosstab(df["ville"], df["produit"])         # tableau croisé (effectifs)
pd.crosstab(df["ville"], df["produit"], values=df["prix"], aggfunc="sum")  # avec agrégation
```

## `transform` (garder la taille du DataFrame)

```python
df["ecart_a_la_moyenne_ville"] = df["prix"] - df.groupby("ville")["prix"].transform("mean")
```

## Exercices (à faire seul)

1. Sur un DataFrame de ventes (mois, vendeur, montant) : calcule le chiffre d'affaires total par vendeur, puis le vendeur avec le plus gros CA.
2. Groupe par catégorie et affiche pour chaque groupe : nombre d'articles, prix min, prix max, prix moyen.
3. Avec `crosstab`, fais un tableau ville × produit avec la somme des quantités, et ajoute les marges (`margins=True`).
4. Calcule, par ville, la part de chaque produit dans le CA total de la ville (indice : `groupby` + `transform("sum")` puis division).

## Pour aller plus loin

- [Pandas : group by (split-apply-combine)](https://pandas.pydata.org/docs/user_guide/groupby.html)


---

<!-- source : 05-pandas/05-merge-join.md -->

# Pandas 5 — Merging et joining (jointures)

Combiner plusieurs DataFrames est aussi fréquent que le groupby. `pd.merge` reproduit les jointures SQL.

```python
import pandas as pd

clients = pd.DataFrame({
    "id_client": [1, 2, 3, 4],
    "nom": ["Alice", "Bob", "Chloe", "David"],
    "ville": ["Paris", "Lyon", "Paris", "Marseille"],
})

commandes = pd.DataFrame({
    "id_commande": [101, 102, 103, 104],
    "id_client": [1, 2, 1, 5],          # le client 5 n'existe pas dans clients
    "montant": [120, 80, 200, 50],
    "date": ["2024-01-10", "2024-01-12", "2024-02-01", "2024-02-03"],
})
```

## Les 4 types de jointure (`how`)

```python
pd.merge(clients, commandes, on="id_client", how="inner")   # seulement les clients avec commandes (défaut)
pd.merge(clients, commandes, on="id_client", how="left")    # tous les clients, commandes si elles existent
pd.merge(clients, commandes, on="id_client", how="right")   # toutes les commandes
pd.merge(clients, commandes, on="id_client", how="outer")   # tout, des deux côtés (NaN si absent)
```

## Options utiles

```python
pd.merge(clients, commandes, left_on="id_client", right_on="id_client_ref")  # noms de clés différents
pd.merge(a, b, on="id", suffixes=("_gauche", "_droite"))   # colonnes en double : renomme
pd.merge(a, b, on=["ville", "annee"])                       # jointure sur plusieurs colonnes
# indicateurs : indicator=True ajoute une colonne _merge (left_only, right_only, both)
```

## `concat` : empiler des DataFrames

```python
janv = pd.read_csv("data/ventes_2024_01.csv")
fev  = pd.read_csv("data/ventes_2024_02.csv")
tout = pd.concat([janv, fev], ignore_index=True)      # empile verticalement (axis=0)

# horizontalement (axis=1) : côte à côte, même index
pd.concat([df_a, df_b], axis=1)
```

## `join` (raccourci sur l'index)

```python
df_a.join(df_b, on="id_client", lsuffix="_a", rsuffix="_b")
```

## Exercices (à faire seul)

1. Crée deux DataFrames : produits (id, nom, categorie) et ventes (id_produit, quantite, date). Fais une jointure pour obtenir les ventes avec le nom du produit.
2. Identifie les produits jamais vendus (`how="left"` + `isna()` sur la colonne de ventes, ou `indicator=True`).
3. Fusionne 3 CSV mensuels avec `concat`, ajoute une colonne `mois` avant chaque concat, puis fais un groupby par mois.
4. Deux DataFrames avec des clés nommées différemment : jointure avec `left_on`/`right_on`.

## Pour aller plus loin

- [Pandas : merge, join, concatenate](https://pandas.pydata.org/docs/user_guide/merging.html)

Leçon suivante : [Reshaping](06-reshape.md).


---

<!-- source : 05-pandas/06-reshape.md -->

# Pandas 6 — Reshaping (changer la forme des données)

## `pivot_table` : du long au large

```python
import pandas as pd

ventes = pd.DataFrame({
    "date":    ["2024-01", "2024-01", "2024-02", "2024-02"],
    "produit": ["A", "B", "A", "B"],
    "ca":      [100, 150, 120, 200],
})

pd.pivot_table(ventes, values="ca", index="date", columns="produit", aggfunc="sum")
#         produit    A    B
# date
# 2024-01          100  150
# 2024-02          120  200
```

## `melt` : du large au long (opération inverse)

```python
large = pd.DataFrame({"id": [1, 2], "jan": [10, 20], "fev": [30, 40]})
pd.melt(large, id_vars="id", var_name="mois", value_name="valeur")
#    id  mois  valeur
# 0   1   jan      10
# 1   2   jan      20
# 2   1   fev      30
# 3   2   fev      40
```

## `stack` / `unstack`

```python
df = pd.DataFrame({("A", "x"): [1, 2], ("A", "y"): [3, 4]}, index=["u", "v"])
df.columns = pd.MultiIndex.from_tuples(df.columns)
df.stack()      # passe les colonnes en index -> Series multi-index
df.unstack()    # opération inverse
```

## `crosstab` (rappel, version reshaping)

```python
pd.crosstab(ventes["date"], ventes["produit"], values=ventes["ca"], aggfunc="sum", fill_value=0)
```

## Quand utiliser quoi ?

| Situation | Fonction |
|---|---|
| Plusieurs colonnes de mêmes mesures (jan, fev, mar) → une colonne `mois` + une colonne `valeur` | `melt` |
| Une colonne catégorielle + des valeurs → tableau croisé lisible | `pivot_table` |
| Agréger avec effectifs par combinaison de catégories | `crosstab` |
| Colonnes à plusieurs niveaux ↔ index hiérarchique | `stack` / `unstack` |

## Exercices (à faire seul)

1. À partir d'un DataFrame large (client, jan, fev, mar, avr), produis un DataFrame long avec `melt`, puis un `pivot_table` qui revient au format de départ.
2. Construis un tableau croisé mois × catégorie avec le CA moyen, rempli de 0 quand il n'y a pas de vente.
3. Prends un DataFrame avec colonnes MultiIndex et aplatis-le avec `stack`.

## Pour aller plus loin

- [Pandas : reshaping and pivot tables](https://pandas.pydata.org/docs/user_guide/reshaping.html)

Module suivant : [06 — Nettoyage de données](../06-nettoyage/README.md).


---

<!-- source : 06-nettoyage/README.md -->

# 06 — Nettoyage de données (Data Cleaning)

> « 80 % du travail d'un data analyst, c'est nettoyer les données. »

Avant toute analyse fiable, il faut traiter les valeurs manquantes, les outliers, les mauvais types, le texte sale et les catégories incohérentes.

## Leçons

1. [Valeurs manquantes](01-valeurs-manquantes.md) — `isna`/`isnull`, `dropna`, imputation, `ffill`/`bfill`.
2. [Détection des outliers](02-outliers.md) — IQR, z-score, visualisation.
3. [Conversion de types et parsing de dates](03-types-dates.md) — `astype`, `to_datetime`, `to_numeric`.
4. [Nettoyage de texte](04-texte.md) — `strip`, `replace`, `split`, expressions régulières (`re`), méthodes `.str` de pandas.
5. [Encodage des catégories](05-categories.md) — `astype("category")`, encodage one-hot (`get_dummies`).

## Ordre de travail conseillé

1. Charger → 2. Inspecter (`info`, `describe`, `isna().sum()`) → 3. Types et dates → 4. Texte → 5. Valeurs manquantes → 6. Outliers → 7. Catégories → 8. Sauvegarder la version propre.

Module suivant : [07 — Analyse exploratoire (EDA)](../07-eda/README.md).


---

<!-- source : 06-nettoyage/01-valeurs-manquantes.md -->

# Nettoyage 1 — Valeurs manquantes

## Détecter

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({"a": [1, np.nan, 3], "b": [4, 5, None]})

df.isna()               # masque booléen (isnull = alias)
df.isna().sum()         # nombre de manquants par colonne
df.isna().mean() * 100  # pourcentage de manquants par colonne
df.isna().any(axis=1)   # True pour les lignes qui ont au moins un manquant
```

## Supprimer (`dropna`) vs imputer

```python
df.dropna()                  # supprime les lignes avec au moins un NaN
df.dropna(subset=["a"])      # seulement si la colonne "a" est manquante
df.dropna(thresh=2)          # garde les lignes avec au moins 2 valeurs non nulles
df.dropna(axis=1)            # supprime les COLONNES avec des NaN (how="all" pour tout-NaN)

# supprimer une colonne entière si trop de manquants
df = df.drop(columns=["b"]) if df["b"].isna().mean() > 0.5 else df
```

## Imputer (remplacer)

```python
df["a"].fillna(df["a"].mean())     # par la moyenne
df["a"].fillna(df["a"].median())   # par la médiane (robuste aux outliers)
df["a"].fillna(0)                  # par une constante
df["a"].fillna(df["a"].mode()[0])  # par le mode (colonne catégorielle)
df["ville"].fillna("Inconnu")
```

## Propagation avant/arrière (`ffill` / `bfill`)

Idéal pour les séries temporelles :

```python
s = pd.Series([1, np.nan, np.nan, 4, np.nan])
s.ffill()   # forward fill  : [1, 1, 1, 4, 4]  (propage la dernière valeur connue)
s.bfill()   # backward fill : [1, 4, 4, 4, NaN] (propage la suivante)
df.ffill()  # fonctionne aussi sur DataFrame, colonne par colonne
```

## Interpolation (pour les séries temporelles)

```python
df["temperature"].interpolate(method="linear")          # interpolation linéaire
df["temperature"].interpolate(method="time")            # pondérée par le temps (index = dates)
```

## Règle de décision

| Situation | Choix |
|---|---|
| Peu de manquants (< 5 %) et aléatoires | supprimer ou imputer par moyenne/médiane |
| Colonne > 50 % de manquants | souvent la supprimer |
| Série temporelle | `ffill`/`bfill` ou `interpolate` |
| Le manquant a un sens métier (« aucun achat » = 0) | remplacer par une valeur explicite |

## Exercices (à faire seul)

1. Crée un DataFrame avec 20 % de valeurs manquantes aléatoires ; affiche le % de manquants par colonne, supprime les colonnes à plus de 50 %, impute le reste par la médiane.
2. Sur une série temporelle de températures avec des trous, compare `ffill`, `bfill` et `interpolate`.
3. Impute une colonne catégorielle par son mode.

## Pour aller plus loin

- [Pandas : missing data](https://pandas.pydata.org/docs/user_guide/missing_data.html)


---

<!-- source : 06-nettoyage/02-outliers.md -->

# Nettoyage 2 — Détection des outliers (valeurs aberrantes)

## Inspection visuelle d'abord

```python
df["colonne"].plot.box()          # boîte à moustaches (matplotlib, voir module 08)
df["colonne"].hist(bins=50)
```

## Méthode IQR (écart interquartile)

Un outlier est une valeur hors de `[Q1 - 1.5*IQR, Q3 + 1.5*IQR]`.

```python
Q1 = df["colonne"].quantile(0.25)
Q3 = df["colonne"].quantile(0.75)
IQR = Q3 - Q1

borne_inf = Q1 - 1.5 * IQR
borne_sup = Q3 + 1.5 * IQR

masque_outliers = (df["colonne"] < borne_inf) | (df["colonne"] > borne_sup)
print(masque_outliers.sum())
df[masque_outliers]          # voir les lignes concernées
```

Variante stricte (outliers extrêmes) : facteur 3 au lieu de 1.5.

## Méthode du z-score

Un outlier a un z-score |z| > 3 (écarts à la moyenne supérieurs à 3 écarts-types) :

```python
import numpy as np
z = (df["colonne"] - df["colonne"].mean()) / df["colonne"].std()
masque = z.abs() > 3
```

> Le z-score suppose une distribution à peu près normale ; l'IQR est plus robuste.

## Traiter les outliers

```python
# supprimer les lignes
df = df[~masque_outliers]

# ou écrêter (winsoriser) : remplacer par la borne
df.loc[df["colonne"] > borne_sup, "colonne"] = borne_sup
df.loc[df["colonne"] < borne_inf, "colonne"] = borne_inf
```

Ne supprime jamais un outlier sans l'avoir compris : c'est peut-être une vraie valeur importante.

## Exercices (à faire seul)

1. Génère 1000 salaires normaux (moyenne 3000, écart-type 500) + 5 valeurs aberrantes (ex. 50000) ; détecte-les avec IQR et avec z-score ; compare.
2. Sur un DataFrame de ventes, écrête les quantités négatives et les prix > Q3 + 3*IQR.
3. Compte les outliers par catégorie (`groupby` sur une colonne catégorielle, applique le masque IQR par groupe).

## Pour aller plus loin

- [Pandas : quantiles](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.quantile.html)


---

<!-- source : 06-nettoyage/03-types-dates.md -->

# Nettoyage 3 — Conversion de types et parsing de dates

## Vérifier et convertir les types

```python
df.dtypes
df["quantite"].astype(int)          # entier
df["prix"].astype(float)            # décimal
df["nom"].astype(str)
df["est_actif"].astype(bool)
df["categorie"].astype("category") # catégorie (économe en mémoire, utile pour groupby)
```

Conversion « sûre » (les valeurs non convertibles deviennent NaN) :

```python
pd.to_numeric(df["prix"], errors="coerce")     # "12,50" -> NaN (à cause de la virgule)
pd.to_numeric(df["prix"].str.replace(",", "."), errors="coerce")  # d'abord nettoyer, puis convertir
```

## Dates : `pd.to_datetime`

```python
df["date"] = pd.to_datetime(df["date"], format="%d/%m/%Y")          # format explicite (rapide)
df["date"] = pd.to_datetime(df["date"], dayfirst=True)             # infère, jour en premier
df["date"] = pd.to_datetime(df["date"], errors="coerce")           # dates invalides -> NaT
```

Une fois en `datetime64` :

```python
df["date"].dt.year          # année
df["date"].dt.month         # mois (1-12)
df["date"].dt.day           # jour du mois
df["date"].dt.dayofweek     # jour de la semaine (0=lundi)
df["date"].dt.day_name()    # "Monday"...
df["date"].dt.quarter       # trimestre
df["date"].dt.is_month_end  # booléen

# créer des périodes
df["mois"] = df["date"].dt.to_period("M")   # 2024-01
```

## Trier et filtrer sur les dates

```python
df = df.sort_values("date")
janvier = df[(df["date"] >= "2024-01-01") & (df["date"] < "2024-02-01")]
recent = df[df["date"] >= pd.Timestamp("2024-06-01")]
```

## Durées (`Timedelta`)

```python
df["duree"] = df["date_fin"] - df["date_debut"]
df["duree"].dt.days
df["date_fin"] = df["date_debut"] + pd.Timedelta(days=7)
```

## Exercices (à faire seul)

1. Un CSV avec une colonne `date` au format "13/02/2024" et une colonne `prix` au format "1 234,56 €" : convertis-les proprement (`str.replace` + `to_datetime`/`to_numeric`).
2. Extraie année, mois et jour de la semaine d'une colonne date, puis groupe les ventes par jour de la semaine.
3. Calcule l'ancienneté en jours entre une colonne `date_inscription` et aujourd'hui (`pd.Timestamp.now()`).

## Pour aller plus loin

- [Pandas : timeseries / dates](https://pandas.pydata.org/docs/user_guide/timeseries.html)
- [Formats de date (strftime)](https://docs.python.org/fr/3/library/datetime.html#strftime-and-strptime-format-codes)


---

<!-- source : 06-nettoyage/04-texte.md -->

# Nettoyage 4 — Nettoyage de texte

## Méthodes `.str` de pandas (vectorisées)

```python
import pandas as pd

s = pd.Series(["  Alice  ", "BOB", "chloé Martin"])

s.str.strip()            # supprime espaces début/fin -> ["Alice", "BOB", "chloé Martin"]
s.str.lower()            # minuscules
s.str.upper()            # majuscules
s.str.capitalize()       # première lettre en majuscule
s.str.replace("a", "@")  # remplace (texte simple)
s.str.split(" ")         # découpe -> liste de mots (ex. "chloé Martin" -> ["chloé", "Martin"])
s.str.len()              # longueur de chaque chaîne
s.str.contains("ali", case=False)   # masque booléen
s.str.startswith("A")
s.str.slice(0, 3)        # 3 premiers caractères
```

Extraire avec des groupes nommés :

```python
s.str.extract(r"(\w+)\s+(\w+)")          # deux groupes : prénom + nom -> DataFrame 2 colonnes
```

## Expressions régulières avec `re` (module standard)

```python
import re

re.search(r"\d+", "prix: 123 €")            # trouve le premier groupe de chiffres
re.findall(r"\d+", "a1 b22 c333")           # ['1', '22', '333']
re.sub(r"\s+", " ", "trop   d'espaces")     # normalise les espaces -> "trop d'espaces"
```

En pandas, préférez les méthodes `.str` vectorisées ; `re` sert pour la logique ponctuelle.

```python
df["email_propre"] = df["email"].str.strip().str.lower()
df["domaine"] = df["email"].str.extract(r"@(.+)$")[0]
df["tel_nettoye"] = df["tel"].str.replace(r"[^0-9]", "", regex=True)   # garde uniquement les chiffres
```

## Tables de correspondance (mapping)

```python
mapping = {"fr": "France", "FR": "France", "fra": "France", "usa": "États-Unis"}
df["pays"] = df["code_pays"].str.lower().map(mapping)
```

## Exercices (à faire seul)

1. Colonne `nom` sale : espaces en trop, casse aléatoire, parfois "NOM Prénom" inversé → nettoie (strip, title) et sépare en deux colonnes avec `str.split` + `str.extract`.
2. Colonne `prix` du type "1 234,56 €" → enlève le symbole et les espaces, remplace la virgule par un point, convertis en float.
3. Colonne `code` du type "A-12-B" → extrais la partie numérique avec une regex.

## Pour aller plus loin

- [Pandas : working with text data](https://pandas.pydata.org/docs/user_guide/text.html)
- [regex101.com](https://regex101.com/) pour tester tes expressions régulières
- [Documentation `re`](https://docs.python.org/fr/3/library/re.html)


---

<!-- source : 06-nettoyage/05-categories.md -->

# Nettoyage 5 — Encodage des catégories

## Type `category`

```python
df["ville"] = df["ville"].astype("category")
```

Avantages : moins de mémoire, tris/groupby plus rapides, ordre des catégories contrôlable.

```python
df["ville"].cat.categories          # liste des catégories
df["taille"] = df["taille"].astype("category")
df["taille"] = df["taille"].cat.set_categories(["S", "M", "L", "XL"], ordered=True)  # ordre logique
df["taille"] > "M"                  # comparaison selon l'ordre défini
```

## Normaliser les catégories (fautes, variantes)

```python
df["ville"] = df["ville"].str.strip().str.title()      # "paris " -> "Paris"
df["ville"] = df["ville"].replace({"St Denis": "Saint-Denis", "St-denis": "Saint-Denis"})
```

## Encodage one-hot (`pd.get_dummies`)

Transforme une colonne catégorielle en colonnes 0/1 (utile pour le machine learning, module 14) :

```python
pd.get_dummies(df["ville"], prefix="ville", dtype=int)
#   ville_Lyon  ville_Marseille  ville_Paris
# 0           0                0            1
```

Options : `drop_first=True` (évite la colinéarité), `dummy_na=True` (ajoute une colonne pour les NaN).

## Label encoding (catégorie → entier)

```python
df["ville_code"] = df["ville"].cat.codes     # chaque catégorie -> entier (ordre alphabétique ou défini)
```

## Exercices (à faire seul)

1. Colonne `couleur` avec valeurs "Rouge", "rouge ", "ROUGE", "Bleu" → normalise puis convertis en `category`.
2. Colonne `taille` avec S/M/L/XL mélangés à des "s", " m " → nettoie, définis un ordre, vérifie que "L" > "M".
3. Fais un one-hot encoding d'une colonne `departement` avec `get_dummies`, puis reconstitue la colonne d'origine à partir des dummies (somme des lignes = 1).

## Pour aller plus loin

- [Pandas : categorical data](https://pandas.pydata.org/docs/user_guide/categorical.html)


---

<!-- source : 07-eda/README.md -->

# 07 — Analyse exploratoire des données (EDA)

L'**Exploratory Data Analysis** consiste à comprendre un jeu de données avant de modéliser : statistiques descriptives, distributions, relations entre variables, inspection visuelle.

## Leçons

1. [Statistiques descriptives](01-stats-descriptives.md) — moyenne, médiane, mode, variance, écart-type, corrélation, covariance.
2. [Analyse des distributions](02-distributions.md) — histogrammes, boxplots, asymétrie.
3. [Analyse des relations](03-relations.md) — scatterplots, matrice de corrélation, tableaux croisés.

## Routine EDA type

```python
df.info()
df.describe()
df.isna().sum()
df.hist()                 # aperçu de toutes les distributions
# puis les relations : df.corr(numeric_only=True), scatterplots...
```

Module suivant : [08 — Visualisation](../08-visualisation/README.md).


---

<!-- source : 07-eda/01-stats-descriptives.md -->

# EDA 1 — Statistiques descriptives

## Mesures de tendance centrale

```python
import pandas as pd
import numpy as np

s = pd.Series([12, 15, 9, 18, 15, 40])   # le 40 est un outlier

s.mean()     # 18.33  (moyenne, sensible aux outliers)
s.median()   # 15.0   (médiane, robuste)
s.mode()     # 15     (valeur la plus fréquente)
```

## Dispersion

```python
s.var()      # variance
s.std()      # écart-type (même unité que les données)
s.min(), s.max()
s.quantile(0.25), s.quantile(0.75)   # quartiles Q1, Q3
s.describe() # count, mean, std, min, 25%, 50%, 75%, max en un appel
```

## Sur un DataFrame entier

```python
df.describe()                          # toutes les colonnes numériques
df.describe(include="object")          # colonnes texte (count, unique, top, freq)
df.describe(include="all")
df["colonne"].nunique()                # nombre de valeurs distinctes
```

## Corrélation et covariance

```python
df[["taille", "poids", "age"]].corr()          # matrice de corrélation de Pearson (entre -1 et 1)
df[["taille", "poids"]].corr().iloc[0, 1]      # corrélation taille/poids

df["a"].cov(df["b"])                           # covariance
```

Interprétation de la corrélation : proche de 1 = lien fort positif, -1 = fort négatif, 0 = pas de lien **linéaire** (attention : corrélation ≠ causalité).

```python
df.corr(numeric_only=True)     # ignore les colonnes non numériques
```

## Exercices (à faire seul)

1. Sur un DataFrame de 100 lignes (taille, poids, âge générés aléatoirement), calcule moyenne/médiane/écart-type de chaque colonne ; compare moyenne vs médiane quand tu ajoutes un outlier.
2. Calcule la corrélation entre deux colonnes fortement liées (ex. `x` et `x*2 + bruit`) et entre deux colonnes indépendantes ; interprète.
3. Trouve la colonne la plus corrélée avec une colonne cible (ex. `prix`) dans un dataset.

## Pour aller plus loin

- [Pandas : describe](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html)
- [Pandas : correlation](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.corr.html)


---

<!-- source : 07-eda/02-distributions.md -->

# EDA 2 — Analyse des distributions

## Histogramme (répartition d'une variable numérique)

```python
import matplotlib.pyplot as plt

df["age"].hist(bins=20)
plt.title("Distribution des âges")
plt.xlabel("Âge")
plt.ylabel("Effectif")
plt.show()
```

Lire un histogramme : forme (symétrique, asymétrique à droite/gauche), pics (modes), étalement, valeurs isolées.

## Boxplot (boîte à moustaches)

```python
df.boxplot(column="salaire", by="ville")   # un boxplot par ville
# ou df["salaire"].plot.box()
plt.show()
```

Un boxplot montre : médiane (trait central), Q1/Q3 (boîte), moustaches (généralement 1.5×IQR), points isolés = outliers potentiels.

## Autres indicateurs de forme

```python
df["salaire"].skew()     # asymétrie (skewness) : 0 = symétrique, > 0 = étalée à droite
df["salaire"].kurt()     # aplatissement (kurtosis)
```

## Distribution par catégorie

```python
df["ville"].value_counts().plot.bar()
df.groupby("ville")["salaire"].mean().plot.bar()
```

## Exercices (à faire seul)

1. Génère 1000 valeurs d'une loi normale (moyenne 100, écart-type 15) et trace l'histogramme ; superpose la courbe théorique avec `scipy.stats.norm.pdf` (module 14) ou simplement compare moyenne/écart-type empiriques.
2. Trace le boxplot d'une colonne par catégorie et identifie dans quelle catégorie la médiane est la plus haute.
3. Compare l'histogramme d'une distribution normale et d'une distribution uniforme (`np.random.default_rng(0).uniform(...)`).

## Pour aller plus loin

- [Pandas : plotting](https://pandas.pydata.org/docs/user_guide/visualization.html)
- Le module suivant ([08 — Visualisation](../08-visualisation/README.md)) détaille Matplotlib, Seaborn et Plotly.


---

<!-- source : 07-eda/03-relations.md -->

# EDA 3 — Analyse des relations entre variables

## Nuage de points (scatterplot)

```python
import matplotlib.pyplot as plt

plt.scatter(df["taille"], df["poids"])
plt.xlabel("Taille (cm)")
plt.ylabel("Poids (kg)")
plt.show()

# avec une couleur par catégorie
for ville, groupe in df.groupby("ville"):
    plt.scatter(groupe["taille"], groupe["poids"], label=ville)
plt.legend()
plt.show()
```

## Matrice de corrélation

```python
corr = df.corr(numeric_only=True)
print(corr.round(2))

# heatmap avec seaborn (module 08)
import seaborn as sns
sns.heatmap(corr, annot=True, cmap="coolwarm", vmin=-1, vmax=1)
```

## Deux variables catégorielles : tableau croisé

```python
pd.crosstab(df["ville"], df["sexe"], normalize="index")   # proportions en ligne
pd.crosstab(df["ville"], df["sexe"], values=df["salaire"], aggfunc="mean")
```

## Une catégorielle, une numérique

```python
df.groupby("ville")["salaire"].agg(["mean", "median", "std"])
df.boxplot(column="salaire", by="ville")
```

## Matrice de nuages de points (pairplot) avec seaborn

```python
import seaborn as sns
sns.pairplot(df[["taille", "poids", "age", "sexe"]], hue="sexe")
```

## Exercices (à faire seul)

1. Sur un dataset avec plusieurs colonnes numériques, trouve la paire de variables la plus corrélée (|corr| max) et trace leur scatterplot.
2. Trace la heatmap de corrélation et identifie les corrélations fortes (> 0.7 ou < -0.7).
3. Compare le salaire moyen par catégorie avec un barplot et un boxplot ; quelle visualisation te parle le plus ?
4. Fais un `crosstab` normalisé entre deux colonnes catégorielles et interprète.

## Pour aller plus loin

- [Seaborn : relational plots](https://seaborn.pydata.org/tutorial/relational.html)

Module suivant : [08 — Visualisation](../08-visualisation/README.md).


---

<!-- source : 08-visualisation/README.md -->

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


---

<!-- source : 08-visualisation/01-matplotlib.md -->

# Visualisation 1 — Matplotlib

```bash
pip install matplotlib
```

```python
import matplotlib.pyplot as plt
```

## Premier graphique

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 1, 5, 3]

plt.plot(x, y, marker="o")       # ligne avec points
plt.title("Mon premier graphique")
plt.xlabel("Axe X")
plt.ylabel("Axe Y")
plt.grid(True)
plt.show()
```

## Types de graphiques de base

```python
plt.plot(x, y)              # courbe
plt.scatter(x, y)           # nuage de points
plt.bar(categories, valeurs)        # barres verticales
plt.barh(categories, valeurs)       # barres horizontales
plt.hist(valeurs, bins=20)          # histogramme
plt.boxplot([serie1, serie2])       # boxplots
plt.pie(parts, labels=categories, autopct="%1.1f%%")  # camembert (à utiliser avec parcimonie)
```

## Figure et subplots (plusieurs graphiques côte à côte)

```python
fig, axes = plt.subplots(2, 2, figsize=(10, 8))   # grille 2x2
axes[0, 0].plot(x, y)
axes[0, 0].set_title("Courbe")
axes[0, 1].bar(categories, valeurs)
axes[1, 0].hist(valeurs, bins=15)
axes[1, 1].scatter(x, y)
fig.suptitle("Tableau de bord")
fig.tight_layout()      # ajuste les espacements
plt.show()
```

Ou la version orientée objet complète :

```python
fig = plt.figure(figsize=(8, 5))
ax = fig.add_subplot(111)
ax.plot(x, y, color="red", linestyle="--", linewidth=2, marker="o")
ax.set_xlabel("X (unité)")
ax.set_ylabel("Y (unité)")
ax.set_title("Titre")
```

## Personnaliser

```python
plt.plot(x, y, color="#1f77b4", linestyle="--", marker="s", markersize=8, label="Série 1")
plt.plot(x, [v*2 for v in y], label="Série 2")
plt.legend()
plt.xlim(0, 6)
plt.ylim(0, 12)
plt.xticks([1, 2, 3, 4, 5], ["un", "deux", "trois", "quatre", "cinq"])
plt.style.use("seaborn-v0_8")   # thème parmi plt.style.available
```

## Sauvegarder une figure

```python
fig.savefig("data/graphique.png", dpi=150, bbox_inches="tight")
fig.savefig("data/graphique.pdf")           # vectoriel
fig.savefig("data/graphique.svg")
plt.close(fig)   # libère la mémoire (important dans les boucles)
```

## Travailler avec pandas

```python
df["age"].hist(bins=20)                       # raccourci pandas (appelle matplotlib)
df.plot(x="date", y="ca", kind="line")       # df.plot(kind=...) : line, bar, barh, hist, box, scatter, pie, area...
df.plot.scatter(x="taille", y="poids", c="age", colormap="viridis")
```

## Exercices (à faire seul)

1. Trace la courbe de `sin(x)` pour x de 0 à 2π (utilise `numpy.linspace` et `numpy.sin`), avec titre et labels.
2. Crée une figure 1×3 : courbe, barres, histogramme sur des données aléatoires (graine fixée).
3. Personnalise un scatterplot : couleur selon une catégorie, taille des points selon une valeur, légende, et sauvegarde en PNG à 200 dpi.

## Pour aller plus loin

- [Matplotlib : tutoriel officiel](https://matplotlib.org/stable/tutorials/index.html)
- [Galerie d'exemples](https://matplotlib.org/stable/gallery/index.html)


---

<!-- source : 08-visualisation/02-seaborn.md -->

# Visualisation 2 — Seaborn

```bash
pip install seaborn
```

Seaborn s'appuie sur Matplotlib et ajoute des graphiques statistiques prêts à l'emploi, avec des styles modernes par défaut.

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.set_theme()   # applique le thème par défaut (peut aussi être appelé dans chaque script)
```

## Charger un jeu de données d'exemple

```python
tips = sns.load_dataset("tips")      # pourboires au restaurant (chargé depuis le dépôt seaborn)
iris = sns.load_dataset("iris")
```

> `load_dataset` télécharge le fichier au premier appel puis le met en cache. Pour travailler hors ligne ensuite, sauvegarde-le : `tips.to_csv("data/tips.csv", index=False)`.

## Distribution plots

```python
sns.histplot(data=tips, x="total_bill", bins=20, kde=True)   # histogramme + densité
sns.kdeplot(data=tips, x="total_bill")                       # densité seule
sns.boxplot(data=tips, x="day", y="total_bill")               # boxplot par catégorie
sns.violinplot(data=tips, x="day", y="total_bill")            # violon (distribution + densité)
sns.stripplot(data=tips, x="day", y="total_bill", alpha=0.5)   # points individuels
```

## Categorical plots

```python
sns.barplot(data=tips, x="day", y="total_bill", estimator="mean")     # moyenne par défaut, barre = IC 95%
sns.countplot(data=tips, x="day")                                     # effectifs
sns.catplot(data=tips, x="day", y="total_bill", hue="sex", kind="bar") # kind: bar, box, violin, strip...
```

## Heatmaps

```python
corr = tips.select_dtypes("number").corr()
sns.heatmap(corr, annot=True, cmap="coolwarm", center=0, vmin=-1, vmax=1)
plt.show()
```

## Regression plots

```python
sns.regplot(data=tips, x="total_bill", y="tip")                    # nuage + droite de régression
sns.lmplot(data=tips, x="total_bill", y="tip", hue="smoker", col="time")  # facettes
```

## Pairplot (matrice de relations)

```python
sns.pairplot(iris, hue="species")
```

## Personnaliser et sauvegarder

```python
sns.set_style("whitegrid")          # darkgrid, white, whitegrid, dark, ticks
sns.set_palette("viridis")          # ou "deep", "muted", "Set2", ou une liste de couleurs

g = sns.scatterplot(data=tips, x="total_bill", y="tip")
g.figure.savefig("data/tip_vs_bill.png", dpi=150, bbox_inches="tight")
```

## Exercices (à faire seul)

1. Sur `tips` : distribution du `total_bill` par `day` (boxplot + violin côte à côte via `catplot`), sauvegarde en PNG.
2. Heatmap de corrélation des variables numériques de `iris`, annotée.
3. `regplot` de `tip` vs `total_bill`, coloré par `smoker` ; que remarques-tu ?
4. `pairplot` de `iris` ; quelles paires de variables semblent corrélées ?

## Pour aller plus loin

- [Seaborn : tutoriel officiel](https://seaborn.pydata.org/tutorial.html)
- [Galerie Seaborn](https://seaborn.pydata.org/examples/index.html)


---

<!-- source : 08-visualisation/03-plotly.md -->

# Visualisation 3 — Plotly (interactif)

```bash
pip install plotly
```

Plotly produit des graphiques **interactifs** (zoom, survol avec valeurs, légende cliquable) affichés dans le navigateur ou dans un notebook Jupyter.

```python
import plotly.express as px
```

## Plotly Express : la façon rapide

```python
import plotly.express as px

df = px.data.iris()          # jeux de données d'exemple intégrés
fig = px.scatter(df, x="sepal_width", y="sepal_length", color="species", size="petal_length",
                 hover_data=["petal_width"], title="Iris : largeur vs longueur de sépale")
fig.show()                   # ouvre dans le navigateur
fig.write_html("data/iris.html")   # sauvegarde autonome (ouvrable sans serveur)
```

## Autres types rapides

```python
px.line(df, x="date", y="valeur")                 # courbe temporelle
px.bar(df, x="categorie", y="total", color="sous_categorie")
px.histogram(df, x="valeur", nbins=30)
px.box(df, x="categorie", y="valeur")
px.pie(df, names="categorie", values="total")
px.scatter_matrix(df, dimensions=["a", "b", "c"], color="categorie")   # pairplot interactif
px.imshow(corr_matrix, text_auto=True, color_continuous_scale="RdBu_r")  # heatmap
px.choropleth(...)    # cartes (module 14, géospatial)
```

## Personnaliser

```python
fig.update_layout(
    title="Titre du graphique",
    xaxis_title="Axe X (unité)",
    yaxis_title="Axe Y (unité)",
    template="plotly_dark",          # thèmes : plotly, plotly_white, plotly_dark, ggplot2, seaborn...
    width=900, height=500,
)
fig.update_traces(marker=dict(size=8, opacity=0.7))
```

## Export

```python
fig.write_html("data/rapport.html")       # HTML autonome
fig.write_image("data/fig.png")           # image statique (nécessite kaleido : pip install kaleido)
```

## Exercices (à faire seul)

1. Scatter interactif sur `px.data.gapminder()` : PIB par habitant vs espérance de vie, couleur par continent, taille par population, année en animation (`animation_frame="year"`).
2. Boxplot interactif d'une colonne par catégorie sur ton propre DataFrame ; sauvegarde en HTML.
3. Heatmap de corrélation interactive avec `px.imshow`.

## Pour aller plus loin

- [Plotly Express](https://plotly.com/python/plotly-express/)
- [Plotly : graphiques fondamentaux](https://plotly.com/python/)

Module suivant : [09 — Web scraping et API](../09-web/README.md).


---

<!-- source : 09-web/README.md -->

# 09 — Récupérer des données sur le web (API et scraping)

Deux approches complémentaires :

- **API** avec `requests` : le site fournit des données structurées (JSON) — c'est la méthode propre et fiable.
- **Scraping HTML** avec `BeautifulSoup` (ou `scrapy` pour les gros projets) : on extrait les données des pages web elles-mêmes.

```bash
pip install requests beautifulsoup4
# scrapy (optionnel, projets de scraping avancés) : pip install scrapy
```

⚠️ Bonnes pratiques : respecte le `robots.txt` du site, les conditions d'utilisation, espace tes requêtes (`time.sleep(1)` entre deux appels), et n'extraie jamais de données personnelles.

## Leçons

1. [Appeler des API avec `requests`](01-apis-requests.md)
2. [Scraper du HTML avec `BeautifulSoup`](02-beautifulsoup.md)
3. [Scrapy en aperçu](03-scrapy-apercu.md)

Module suivant : [10 — SQL](../10-sql/README.md).


---

<!-- source : 09-web/01-apis-requests.md -->

# Web 1 — Appeler des API avec `requests`

```bash
pip install requests
```

## GET : récupérer des données

```python
import requests

r = requests.get("https://api.open-meteo.com/v1/forecast",
                 params={"latitude": 48.85, "longitude": 2.35,
                         "daily": "temperature_2m_max,temperature_2m_min,precipitation_sum",
                         "timezone": "Europe/Paris",
                         "forecast_days": 7})
print(r.status_code)        # 200 = OK
print(r.ok)                 # True si status < 400

data = r.json()             # JSON -> dict Python
print(data["daily"]["time"])
print(data["daily"]["temperature_2m_max"])
```

## Gérer les erreurs

```python
try:
    r = requests.get("https://api.exemple.com/donnees", timeout=10)  # timeout obligatoire en pratique
    r.raise_for_status()    # lève une exception si 4xx/5xx
except requests.exceptions.HTTPError as e:
    print("Erreur HTTP :", e)
except requests.exceptions.ConnectionError:
    print("Connexion impossible")
except requests.exceptions.Timeout:
    print("La requête a expiré")
```

## API publiques sans clé (pour t'entraîner)

| API | Données | Exemple d'URL |
|---|---|---|
| Open-Meteo | météo mondiale, sans clé | `https://api.open-meteo.com/v1/forecast?latitude=48.85&longitude=2.35&current=temperature_2m` |
| REST Countries | pays du monde | `https://restcountries.com/v3.1/name/france` |
| JSONPlaceholder | données de test (posts, users...) | `https://jsonplaceholder.com/posts/1` |
| PokeAPI | Pokémon | `https://pokeapi.co/api/v2/pokemon/ditto` |
| Open Library | livres | `https://openlibrary.org/search.json?q=python` |

## POST : envoyer des données

```python
r = requests.post("https://httpbin.org/post",
                  json={"nom": "Alice", "age": 25},   # sérialisé en JSON automatiquement
                  headers={"Authorization": "Bearer <token>"})
print(r.json())
```

## En-têtes et authentification

```python
headers = {"User-Agent": "mon-projet-python/1.0", "Accept": "application/json"}
r = requests.get(url, headers=headers)
```

Certaines API exigent une clé : `params={"appid": "TA_CLE"}` ou en-tête `Authorization`. Ne committe **jamais** ta clé : utilise une variable d'environnement (`os.environ["MA_CLE"]` + fichier `.env` non versionné).

## Transformer la réponse en DataFrame

```python
import pandas as pd

meteo = requests.get("https://api.open-meteo.com/v1/forecast",
                     params={"latitude": 48.85, "longitude": 2.35,
                             "daily": "temperature_2m_max,precipitation_sum",
                             "forecast_days": 14, "timezone": "Europe/Paris"}).json()
df = pd.DataFrame(meteo["daily"])
df["time"] = pd.to_datetime(df["time"])
print(df.head())
```

## Exercices (à faire seul)

1. Récupère la météo actuelle de 3 villes avec Open-Meteo et affiche température + vent.
2. Interroge REST Countries pour obtenir capitale, population et superficie de la France ; mets-les dans un DataFrame.
3. Récupère les 10 premiers posts de JSONPlaceholder, eksttrais `userId` et `title`, compte les posts par utilisateur.
4. Ajoute un `time.sleep(1)` entre les appels d'une boucle de 5 requêtes (bonne pratique).

## Pour aller plus loin

- [Documentation requests](https://requests.readthedocs.io/)
- [Open-Meteo : documentation API](https://open-meteo.com/en/docs)


---

<!-- source : 09-web/02-beautifulsoup.md -->

# Web 2 — Scraper du HTML avec BeautifulSoup

```bash
pip install beautifulsoup4
```

Quand il n'y a pas d'API, on parse le HTML de la page.

## Récupérer et parser une page

```python
import requests
from bs4 import BeautifulSoup

url = "https://books.toscrape.com/"        # site d'entraînement au scraping (prévu pour ça)
html = requests.get(url, timeout=10).text
soup = BeautifulSoup(html, "html.parser")

soup.title.text          # titre de la page
soup.find("h1").text     # premier <h1>
```

## Sélectionner des éléments (CSS)

```python
# par balise
soup.find_all("h3")                       # tous les <h3>

# par classe CSS
soup.select("article.product_pod")       # tous les articles produits
soup.select("div.price_color")

# combinaison
soup.select("p.star-rating.Three")       # classe multiple
```

## Extraire le texte et les attributs

```python
livre = soup.select_one("article.product_pod")
titre = livre.h3.a["title"]              # attribut title du <a> dans le <h3>
prix = livre.select_one("p.price_color").text     # "£51.77"
disponibilite = livre.select_one("p.instock.availability").text.strip()
lien = livre.h3.a["href"]                 # URL relative
```

## Boucler sur tous les éléments

```python
livres = []
for article in soup.select("article.product_pod"):
    livres.append({
        "titre": article.h3.a["title"],
        "prix": article.select_one("p.price_color").text,
        "note": article.select_one("p.star-rating")["class"][1],  # "Three", "Four"...
    })

import pandas as pd
df = pd.DataFrame(livres)
df["prix"] = df["prix"].str.replace("£", "").astype(float)
print(df.head())
print(df["note"].value_counts())
```

## Pagination

```python
page = 1
while page <= 3:
    url = f"https://books.toscrape.com/catalogue/page-{page}.html"
    ...
    page += 1
```

## Exercices (à faire seul)

1. Scrape la page d'accueil de books.toscrape.com : récupère titre, prix et note des 20 livres, mets-les dans un DataFrame.
2. Convertis les notes ("One" à "Five") en entiers (mapping) et calcule le prix moyen par note.
3. Scrape 3 pages (pagination) et sauvegarde le résultat en CSV.
4. Récupère la liste des pays depuis `https://restcountries.com/v3.1/all?fields=name,capital,population` (API JSON) — puis fais la même chose en scrapant une page HTML simple de ton choix.

## Pour aller plus loin

- [Documentation BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- Inspecte le HTML d'une page : clic droit → « Inspecter » dans ton navigateur (outil développeur, onglet Éléments).


---

<!-- source : 09-web/03-scrapy-apercu.md -->

# Web 3 — Scrapy (aperçu)

```bash
pip install scrapy
```

**Scrapy** est un framework complet pour le scraping à grande échelle : requêtes asynchrones rapides, gestion automatique des erreurs, pipelines de nettoyage, export CSV/JSON, et `scrapy shell` pour tester ses sélecteurs.

## Quand passer de BeautifulSoup à Scrapy ?

- Des **centaines/milliers de pages** à crawler.
- Besoin de **vitesse** (requêtes parallèles).
- Projet structuré avec plusieurs « spiders » (robots d'exploration) et pipelines de traitement.

## Structure d'un projet Scrapy

```bash
scrapy startproject monsite
cd monsite
scrapy genspider livres books.toscrape.com
```

Un spider ressemble à :

```python
import scrapy

class LivresSpider(scrapy.Spider):
    name = "livres"
    start_urls = ["https://books.toscrape.com/"]

    def parse(self, response):
        for article in response.css("article.product_pod"):
            yield {
                "titre": article.css("h3 a::attr(title)").get(),
                "prix": article.css("p.price_color::text").get(),
            }
        # suivre la page suivante
        suivant = response.css("li.next a::attr(href)").get()
        if suivant:
            yield response.follow(suivant, callback=self.parse)
```

Lancement : `scrapy crawl livres -O livres.csv`

## `scrapy shell` : tester ses sélecteurs

```bash
scrapy shell "https://books.toscrape.com/"
>>> response.css("article.product_pod h3 a::attr(title)").getall()[:3]
```

## Exercices (à faire seul)

1. Installe scrapy, crée un projet, et réécris le scraping de books.toscrape.com en spider avec pagination sur 3 pages ; exporte en CSV.
2. Utilise `scrapy shell` pour trouver le sélecteur CSS qui isole les prix.

## Pour aller plus loin

- [Documentation Scrapy](https://docs.scrapy.org/)

Module suivant : [10 — SQL](../10-sql/README.md).


---

<!-- source : 10-sql/README.md -->

# 10 — SQL avec Python

SQL reste **incontournable** pour interroger des bases de données. En Python, trois approches :

| Approche | Quand l'utiliser |
|---|---|
| `sqlite3` (stdlib) | petite base locale, embarquée, zéro installation |
| `SQLAlchemy` | projets professionnels, multi-SGBD (PostgreSQL, MySQL...) |
| `DuckDB` | analyser des **gros fichiers** (CSV/Parquet) directement en SQL, sans charger en mémoire |

```bash
pip install sqlalchemy duckdb
```

## Leçons

1. [Fondamentaux SQL](01-sql-fondamentaux.md) — SELECT, WHERE, ORDER BY, GROUP BY, JOIN, agrégations.
2. [sqlite3 et SQLAlchemy](02-sqlite3-sqlalchemy.md) — créer une base, insérer, interroger depuis Python, `pd.read_sql`.
3. [DuckDB](03-duckdb.md) — requêter des CSV/Parquet directement en SQL.

Ressource : la [roadmap SQL de roadmap.sh](https://roadmap.sh/sql) pour aller plus loin.

Module suivant : [11 — Polars](../11-polars/README.md).


---

<!-- source : 10-sql/01-sql-fondamentaux.md -->

# SQL 1 — Fondamentaux

SQL (Structured Query Language) interroge des bases relationnelles. Syntaxe essentielle :

```sql
SELECT colonne1, colonne2, COUNT(*) AS nb
FROM ma_table
WHERE colonne1 > 100 AND ville = 'Paris'
GROUP BY colonne2
HAVING COUNT(*) > 5
ORDER BY nb DESC
LIMIT 10;
```

## Les commandes essentielles

| Commande | Rôle | Exemple |
|---|---|---|
| `SELECT` | choisir les colonnes (`*` = toutes) | `SELECT nom, age FROM clients` |
| `FROM` | la table | |
| `WHERE` | filtrer les lignes | `WHERE age >= 18 AND ville = 'Lyon'` |
| `ORDER BY` | trier | `ORDER BY age DESC` (ou `ASC`) |
| `LIMIT n` | limiter le nombre de résultats | `LIMIT 10` |
| `DISTINCT` | valeurs uniques | `SELECT DISTINCT ville FROM clients` |
| `GROUP BY` | grouper | `GROUP BY ville` |
| `HAVING` | filtrer APRÈS groupement | `HAVING COUNT(*) > 5` (WHERE filtre avant) |
| `JOIN` | joindre des tables | `JOIN commandes ON clients.id = commandes.id_client` |

## Agrégations

```sql
SELECT ville, COUNT(*) AS nb, AVG(salaire) AS salaire_moyen,
       MIN(salaire), MAX(salaire), SUM(salaire)
FROM employes
GROUP BY ville;
```

Fonctions : `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`.

## Jointures

```sql
-- INNER JOIN : uniquement les correspondances
SELECT c.nom, co.montant
FROM clients c
INNER JOIN commandes co ON c.id = co.id_client;

-- LEFT JOIN : tous les clients, même sans commande
SELECT c.nom, co.montant
FROM clients c
LEFT JOIN commandes co ON c.id = co.id_client;
```

## Autres opérations utiles

```sql
INSERT INTO clients (nom, ville) VALUES ('Alice', 'Paris');
UPDATE clients SET ville = 'Lyon' WHERE nom = 'Alice';
DELETE FROM clients WHERE id = 42;

CREATE TABLE clients (
    id INTEGER PRIMARY KEY,
    nom TEXT NOT NULL,
    ville TEXT,
    salaire REAL
);

-- fonctions sur les chaînes et dates
SELECT UPPER(nom), LENGTH(nom) FROM clients;
SELECT * FROM ventes WHERE date >= '2024-01-01';
SELECT strftime('%Y-%m', date) AS mois, SUM(montant) FROM ventes GROUP BY mois;  -- SQLite
```

## Exercices (à faire seul)

Pratique sur [SQLite Online](https://sqliteonline.com/) ou avec le module suivant (`sqlite3`) :

1. Crée une table `produits` (id, nom, categorie, prix) et insère 10 lignes.
2. Affiche les produits de la catégorie "Électronique" triés par prix décroissant, limités à 5.
3. Calcule le prix moyen et le nombre de produits par catégorie (GROUP BY + HAVING pour ne garder que les catégories avec plus de 2 produits).
4. Crée une table `ventes` et fais une jointure avec `produits` pour obtenir le nom du produit de chaque vente.

## Pour aller plus loin

- [SQLite : tutoriel SQL](https://www.sqlitetutorial.net/)
- [W3Schools SQL](https://www.w3schools.com/sql/)


---

<!-- source : 10-sql/02-sqlite3-sqlalchemy.md -->

# SQL 2 — sqlite3 (stdlib) et SQLAlchemy

## sqlite3 : base de données embarquée (aucun serveur)

```python
import sqlite3
import pandas as pd

con = sqlite3.connect("data/ma_base.db")   # crée le fichier s'il n'existe pas

# créer une table et insérer des données
con.execute("""
    CREATE TABLE IF NOT EXISTS clients (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        nom TEXT NOT NULL,
        ville TEXT,
        salaire REAL
    )
""")
con.execute("INSERT INTO clients (nom, ville, salaire) VALUES (?, ?, ?)", ("Alice", "Paris", 2500))
con.executemany("INSERT INTO clients (nom, ville, salaire) VALUES (?, ?, ?)",
                [("Bob", "Lyon", 3200), ("Chloe", "Paris", 2800)])
con.commit()   # valide les écritures

# interroger
for ligne in con.execute("SELECT * FROM clients WHERE ville = 'Paris'"):
    print(ligne)

# directement dans pandas
query = "SELECT ville, AVG(salaire) AS salaire_moyen, COUNT(*) AS nb FROM clients GROUP BY ville"
df = pd.read_sql_query(query, con)
print(df)

# écrire un DataFrame dans la base
df_ventes = pd.DataFrame({"id_client": [1, 1, 2], "montant": [120, 80, 200]})
df_ventes.to_sql("ventes", con, if_exists="replace", index=False)

con.close()
```

> Les `?` sont des **paramètres** : ils protègent des injections SQL (ne jamais construire une requête avec des f-strings sur des entrées utilisateur).

## SQLAlchemy : l'ORM professionnel

```bash
pip install sqlalchemy
```

```python
from sqlalchemy import create_engine, text

engine = create_engine("sqlite:///data/ma_base.db")     # même syntaxe pour PostgreSQL, MySQL...

with engine.connect() as conn:
    resultat = conn.execute(text("SELECT * FROM clients WHERE salaire > :seuil"), {"seuil": 2600})
    for ligne in resultat:
        print(ligne)

# avec pandas
df = pd.read_sql("SELECT * FROM ventes", engine)
```

SQLAlchemy sert aussi d'ORM (définir les tables comme des classes Python) pour les vraies applications.

## Exercices (à faire seul)

1. Crée une base `bibliotheque.db` avec tables `livres` et `auteurs`, insère des données, fais une jointure pour lister les livres avec le nom de l'auteur.
2. Charge un CSV avec pandas, écris-le dans une table sqlite avec `to_sql`, puis relis-le uniquement avec `pd.read_sql_query` et un `GROUP BY`.
3. Refais l'exercice 2 avec SQLAlchemy (`create_engine` + `text`).

## Pour aller plus loin

- [sqlite3 — doc Python](https://docs.python.org/fr/3/library/sqlite3.html)
- [SQLAlchemy](https://docs.sqlalchemy.org/)


---

<!-- source : 10-sql/03-duckdb.md -->

# SQL 3 — DuckDB : du SQL sur des fichiers

[DuckDB](https://duckdb.org/) est une base de données **analytique embarquée** : on exécute du SQL directement sur des fichiers CSV/Parquet/JSON, sans serveur ni import en mémoire complet. Idéal pour les fichiers trop gros pour Excel mais gérables sur disque.

```bash
pip install duckdb
```

## Requêter un CSV directement

```python
import duckdb

resultat = duckdb.sql("""
    SELECT ville, AVG(prix) AS prix_moyen, COUNT(*) AS nb
    FROM 'data/ventes.csv'
    WHERE date >= '2024-01-01'
    GROUP BY ville
    ORDER BY prix_moyen DESC
""").df()          # .df() -> DataFrame pandas
print(resultat)
```

## Depuis pandas

```python
import duckdb
import pandas as pd

df = pd.read_csv("data/ventes.csv")

# duckdb voit la variable `df` du scope automatiquement
duckdb.sql("SELECT produit, SUM(quantite * prix) AS ca FROM df GROUP BY produit ORDER BY ca DESC LIMIT 5").df()
```

## Lire plusieurs formats

```python
duckdb.sql("SELECT * FROM 'data/ventes.parquet' LIMIT 5").df()
duckdb.sql("SELECT * FROM read_json_auto('data/donnees.json')").df()
duckdb.sql("SELECT * FROM read_csv_auto('data/ventes.csv')").df()

# joindre un CSV et un Parquet en une requête
duckdb.sql("""
    SELECT c.nom, v.montant
    FROM 'data/clients.csv' c
    JOIN 'data/ventes.parquet' v ON c.id = v.id_client
""").df()
```

## Créer une vraie base DuckDB

```python
con = duckdb.connect("data/analytics.duckdb")
con.execute("CREATE TABLE ventes AS SELECT * FROM 'data/ventes.csv'")
con.execute("INSERT INTO ventes VALUES (...)").df()
con.close()
```

## Pourquoi DuckDB ?

| Critère | pandas | DuckDB |
|---|---|---|
| Fichier de 10 Go | lent / mémoire | rapide, lecture par morceaux |
| Requête SQL complexe (joins, agrégations) | verbeux | naturel |
| Écrire le résultat | `to_parquet` | `COPY ... TO 'sortie.parquet'` |

## Exercices (à faire seul)

1. Sur un CSV de ventes que tu génères (1M de lignes avec numpy), calcule avec DuckDB le CA par mois et par catégorie ; compare le temps d'exécution avec pandas (`%time` en notebook ou `time.perf_counter()`).
2. Jointure entre un CSV clients et un Parquet commandes directement en SQL DuckDB.
3. Exporte le résultat d'une requête en Parquet avec `COPY (SELECT ...) TO 'data/rapport.parquet' (FORMAT PARQUET)`.

## Pour aller plus loin

- [DuckDB : documentation](https://duckdb.org/docs/)
- [DuckDB + pandas](https://duckdb.org/docs/guides/python/pandas.html)

Module suivant : [11 — Polars](../11-polars/README.md).


---

<!-- source : 11-polars/README.md -->

# 11 — Polars : l'alternative rapide à pandas

[Polars](https://pola-rs.github.io/polars-book/) est une bibliothèque DataFrame écrite en Rust, pensée pour la **performance** sur les gros volumes (lecture par morceaux, exécution parallèle, requêtes optimisées « lazy »).

```bash
pip install polars
```

```python
import polars as pl
```

## DataFrame et lecture

```python
df = pl.read_csv("data/ventes.csv")
df = pl.read_parquet("data/ventes.parquet")

df.head()
df.shape          # (lignes, colonnes)
df.schema         # types des colonnes
df.describe()
```

## Expressions (le cœur de Polars)

Polars exprime les calculs avec des **expressions** (`pl.col(...)`), évaluées en parallèle :

```python
df.select(
    pl.col("prix") * pl.col("quantite"),                     # nouvelle colonne calculée
    (pl.col("prix") * 1.2).alias("prix_ttc"),
)

df.filter(pl.col("ville") == "Paris")
df.filter((pl.col("prix") > 100) & (pl.col("quantite") >= 2))

# groupby + agrégation
df.group_by("ville").agg(
    pl.col("prix").mean().alias("prix_moyen"),
    pl.col("quantite").sum().alias("qte_totale"),
    pl.len().alias("nb_ventes"),        # pl.len() = COUNT(*)
).sort("prix_moyen", descending=True)
```

## Lazy : optimiser avant d'exécuter

```python
lazy = (
    pl.scan_csv("data/gros_fichier.csv")        # scan = lecture différée, ne charge rien encore
    .filter(pl.col("prix") > 50)
    .group_by("categorie")
    .agg(pl.col("montant").sum())
    .sort("montant", descending=True)
)
resultat = lazy.collect()     # exécute la requête optimisée
```

`scan_csv` + `collect` laissent Polars optimiser (filtrer avant de lire les colonnes inutiles, etc.) : c'est ce qui le rend rapide sur les gros fichiers.

## Conversion pandas ↔ Polars

```python
import pandas as pd
df_pd = pd.read_csv("data/ventes.csv")
df_pl = pl.from_pandas(df_pd)
df_pd = df_pl.to_pandas()
```

## Polars vs pandas : quand choisir ?

| pandas | Polars |
|---|---|
| écosystème immense (viz, ML, tutos) | fichiers > quelques Go, besoins de vitesse |
| API très connue | syntaxe « expressions » à apprendre |
| manipulación fine ligne par ligne | traitements vectorisés parallèles |

## Exercices (à faire seul)

1. Génère un CSV de 1M de lignes (numpy), lis-le avec `pl.scan_csv`, filtre et agrège en lazy, compare le temps avec `pd.read_csv` + filtre pandas.
2. Refais l'analyse du module 05 (groupby + tri) en Polars et compare la lisibilité.
3. Convertis un DataFrame pandas en Polars, fais un `group_by().agg()`, reconvertis en pandas.

## Pour aller plus loin

- [Polars : user guide](https://docs.pola.rs/)
- [Polars vs pandas](https://docs.pola.rs/user-guide/migration/pandas/)

Module suivant : [12 — Dashboards](../12-dashboards/README.md).


---

<!-- source : 12-dashboards/README.md -->

# 12 — Dashboards et outils BI

## Leçons

1. [Streamlit : un dashboard en pur Python](01-streamlit.md) — recommandé pour démarrer.
2. [Dash (Plotly) — aperçu](02-dash.md).
3. [Power BI / Tableau — aperçu](03-outils-bi.md) : outils BI professionnels (hors Python, à connaître).

## Streamlit en deux mots

```bash
pip install streamlit
streamlit run app.py     # ouvre un dashboard dans le navigateur, mis à jour à chaque modification
```

Module suivant : [13 — Big data et pipelines](../13-big-data-pipelines/README.md).


---

<!-- source : 12-dashboards/01-streamlit.md -->

# Dashboards 1 — Streamlit

[Streamlit](https://streamlit.io/) transforme un script Python en application web interactive, sans HTML/CSS/JS.

```bash
pip install streamlit
```

## Premier app (`app.py`)

```python
import streamlit as st
import pandas as pd
import plotly.express as px

st.title("Mon premier dashboard")
st.write("Analyse des ventes")

df = pd.read_csv("data/ventes.csv")

st.dataframe(df.head(20))               # table interactive (triable, scrollable)

ville = st.selectbox("Choisir une ville", df["ville"].unique())
st.write(f"Ville sélectionnée : {ville}")

filtre = df[df["ville"] == ville]
st.metric("Chiffre d'affaires", f"{filtre['montant'].sum():,.0f} €")

fig = px.bar(filtre.groupby("produit")["montant"].sum().reset_index(),
             x="produit", y="montant")
st.plotly_chart(fig)
```

Lancement : `streamlit run app.py` → l'app s'ouvre sur `http://localhost:8501` et se **recharge automatiquement** à chaque sauvegarde du fichier.

## Composants utiles

```python
st.sidebar.title("Filtres")                       # barre latérale
periode = st.sidebar.date_input("Date de début")
options = st.sidebar.multiselect("Produits", df["produit"].unique(), default=df["produit"].unique()[:2])

col1, col2 = st.columns(2)                        # mise en page en colonnes
col1.metric("CA", "12 000 €")
col2.metric("Commandes", 340)

st.line_chart(df.set_index("date")["montant"])    # graphique rapide intégré
st.map(df.dropna(subset=["lat", "lon"]))          # carte

upload = st.file_uploader("Charger un CSV", type="csv")   # upload de fichier
if upload:
    df_upload = pd.read_csv(upload)
```

## Caching (éviter de tout recalculer)

```python
@st.cache_data
def charger_donnees(chemin):
    return pd.read_csv(chemin)

df = charger_donnees("data/ventes.csv")
```

## Exercices (à faire seul)

1. Dashboard météo : récupère 14 jours de prévisions Open-Meteo pour une ville choisie dans un `selectbox`, affiche métriques (T° max/min moyenne) + graphique Plotly des températures.
2. Dashboard sur ton propre CSV : filtres par catégorie/date, tableau filtré, 2 graphiques, métriques clés en haut.
3. Ajoute un `file_uploader` pour charger n'importe quel CSV et afficher ses stats automatiquement.

## Pour aller plus loin

- [Documentation Streamlit](https://docs.streamlit.io/)
- Déploiement gratuit : Streamlit Community Cloud (à connecter à ton compte GitHub).


---

<!-- source : 12-dashboards/02-dash.md -->

# Dashboards 2 — Dash (Plotly), aperçu

```bash
pip install dash
```

**Dash** (par les créateurs de Plotly) construit des dashboards analytiques en Python pur, avec des callbacks réactifs (`@app.callback`). Plus verbeux que Streamlit, mais plus personnalisable (layout HTML flexible).

```python
from dash import Dash, html, dcc, Input, Output
import plotly.express as px
import pandas as pd

app = Dash(__name__)
df = pd.read_csv("data/ventes.csv")

app.layout = html.Div([
    html.H1("Ventes"),
    dcc.Dropdown(options=df["ville"].unique(), id="ville"),
    dcc.Graph(id="graph"),
])

@app.callback(Output("graph", "figure"), Input("ville", "value"))
def maj(ville):
    if ville is None:
        ville = df["ville"].unique()[0]
    d = df[df["ville"] == ville]
    return px.bar(d.groupby("produit")["montant"].sum().reset_index(), x="produit", y="montant")

if __name__ == "__main__":
    app.run(debug=True)     # http://localhost:8050
```

## Streamlit vs Dash

| Streamlit | Dash |
|---|---|
| quelques lignes, très rapide à prendre en main | layout + callbacks, plus de code |
| idéal pour prototyper / partager vite | idéal pour des dashboards complexes et personnalisés |
| composants prêts à l'emploi | contrôle total du HTML/CSS |

## Exercice (à faire seul)

1. Reprends le dashboard Streamlit de la leçon précédente et réécris-le en Dash avec le même selectbox et le même graphique.

## Pour aller plus loin

- [Documentation Dash](https://dash.plotly.com/)


---

<!-- source : 12-dashboards/03-outils-bi.md -->

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


---

<!-- source : 13-big-data-pipelines/README.md -->

# 13 — Big data et pipelines de données (aperçu)

Quand les données ne tiennent plus sur une machine ou doivent être traitées automatiquement à intervalles réguliers.

```bash
pip install dask            # pandas parallèle sur une machine
# pyspark : pip install pyspark   (nécessite Java)
# airflow : pip install apache-airflow
```

## Leçons

1. [Dask : pandas en parallèle](01-dask.md) — même API que pandas, mais distribué sur les cœurs/plusieurs machines.
2. [PySpark : le standard du big data](02-pyspark.md) — cluster, DataFrames Spark, lecture de Parquet distribué.
3. [Airflow : orchestrer des pipelines](03-airflow.md) — planifier et surveiller des tâches (ex. « chaque nuit à 2h : récupérer → nettoyer → charger »).

## Idée générale

- **Dask** = « pandas qui scale » sur une grosse machine.
- **PySpark** = « pandas sur un cluster de machines » (standard industriel, ex. Databricks).
- **Airflow** = le chef d'orchestre qui enchaîne les étapes et gère les échecs.

Module suivant : [14 — Sujets avancés](../14-sujets-avances/README.md).


---

<!-- source : 13-big-data-pipelines/01-dask.md -->

# Big data 1 — Dask (pandas en parallèle)

```bash
pip install "dask[dataframe]"
```

Dask découpe un gros DataFrame en **partitions** et les traite en parallèle sur tous les cœurs de ta machine, avec une API très proche de pandas.

```python
import dask.dataframe as dd

ddf = dd.read_csv("data/gros_*.csv")     # lit plusieurs CSV comme un seul DataFrame

# mêmes opérations que pandas, mais en "lazy" (rien n'est exécuté tout de suite)
resultat = (
    ddf[ddf["prix"] > 100]
    .groupby("categorie")["montant"]
    .sum()
)

resultat.compute()          # exécute le calcul et renvoie un pandas DataFrame
```

## Quand l'utiliser

- Fichier CSV/Parquet de quelques Go, trop lourd pour `pd.read_csv` en RAM.
- Beaucoup de calculs répétitifs à paralléliser.

```python
import dask.array as da
x = da.random.random((10000, 10000), chunks=(1000, 1000))   # comme numpy, par blocs
y = (x + x.T).mean(axis=0).compute()
```

## Exercice (à faire seul)

1. Génère 5 CSV de 200 000 lignes chacun, lis-les avec `dd.read_csv("data/part-*.csv")`, fais un groupby + agrégation, `compute()`, et compare le temps avec pandas.

## Pour aller plus loin

- [Documentation Dask](https://docs.dask.org/)


---

<!-- source : 13-big-data-pipelines/02-pyspark.md -->

# Big data 2 — PySpark (aperçu)

```bash
pip install pyspark    # nécessite Java installé sur la machine
```

**Apache Spark** est le standard industriel du traitement distribué : des DataFrames manipulés sur un **cluster** de machines, lus depuis des data lakes (Parquet sur S3/HDFS...).

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("demo").getOrCreate()

df = spark.read.parquet("data/ventes.parquet")     # lecture distribuée
df = df.filter(df.prix > 100).groupBy("categorie").sum("montant")
df.show(10)
df.write.parquet("data/resultat.parquet")

spark.stop()
```

## Spark vs pandas/Polars/Dask

| Outil | Échelle | Quand |
|---|---|---|
| pandas | < quelques Go, 1 machine | analyse interactive |
| Polars | jusqu'à la RAM dispo, 1 machine | gros fichiers rapides |
| Dask | RAM × cœurs, 1 grosse machine | paralléliser pandas |
| PySpark | To/Po, cluster de machines | vrai big data industriel |

## Exercice (à faire seul)

1. Installe pyspark (avec Java), crée une `SparkSession`, lis un Parquet que tu as généré, filtre + groupBy + `show()`.
2. Compare le temps de lecture d'un gros CSV avec pandas, Polars et Spark.

## Pour aller plus loin

- [PySpark : getting started](https://spark.apache.org/docs/latest/api/python/getting_started/index.html)


---

<!-- source : 13-big-data-pipelines/03-airflow.md -->

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


---

<!-- source : 14-sujets-avances/README.md -->

# 14 — Sujets avancés (aperçus)

Ces sujets complètent la roadmap « Python for Data Analysis » et mènent vers la data science / le ML (voir la [roadmap ML](https://roadmap.sh/machine-learning) et la [roadmap AI & Data Scientist](https://roadmap.sh/ai-data-scientist)).

## Leçons

1. [POO pour l'analyse de données](01-poo.md) — classes, encapsulation : structurer un projet d'analyse réutilisable.
2. [SciPy et scikit-learn](02-scipy-sklearn.md) — statistiques avancées et premier modèle de ML.
3. [Analyse géospatiale](03-geo.md) — GeoPandas, cartes de données.

```bash
pip install scipy scikit-learn geopandas
```

Tu as terminé le parcours principal : direction les [projets solo](../projets/README.md) !


---

<!-- source : 14-sujets-avances/01-poo.md -->

# Avancé 1 — POO pour l'analyse de données

La **programmation orientée objet** structure un projet d'analyse en objets cohérents (ex. une classe `Rapport` qui charge, nettoie, analyse et exporte).

## Classe de base

```python
class AnalyseVentes:
    def __init__(self, chemin_csv):
        import pandas as pd
        self.df = pd.read_csv(chemin_csv)
        self.propre = False

    def nettoyer(self):
        self.df = self.df.dropna()
        self.propre = True
        return self          # permet le chaînage

    def ca_par_categorie(self):
        return self.df.groupby("categorie")["montant"].sum().sort_values(ascending=False)

    def exporter(self, chemin):
        self.df.to_csv(chemin, index=False)

# utilisation
a = AnalyseVentes("data/ventes.csv").nettoyer()   # chaînage
print(a.ca_par_categorie())
a.exporter("data/ventes_propre.csv")
```

## Concepts clés

- `__init__` : constructeur (état initial de l'objet).
- `self` : l'objet lui-même.
- Méthodes = fonctions attachées à la classe.
- Héritage : `class AnalyseClients(AnalyseVentes)` réutilise tout et redéfinit ce qui change.
- `@property` : accède à un attribut comme à une propriété calculée.
- `__repr__` : représentation lisible (`print(objet)`).

## Quand faire de la POO en data analysis ?

- Projet réutilisable (plusieurs rapports sur les mêmes données).
- Plusieurs jeux de données avec la même logique de traitement.
- Équipe : clarifie les responsabilités.

Pour un script ponctuel, des fonctions suffisent (module 01).

## Exercices (à faire seul)

1. Crée une classe `Dataset` avec méthodes `charger`, `nb_lignes`, `colonnes`, `stats` (retourne `describe()`), `sauvegarder`.
2. Crée `DatasetCSV(Dataset)` et `DatasetAPI(Dataset)` qui héritent de `Dataset` et implémentent `charger` différemment.

## Pour aller plus loin

- [Tutoriel officiel — classes](https://docs.python.org/fr/3/tutorial/classes.html)


---

<!-- source : 14-sujets-avances/02-scipy-sklearn.md -->

# Avancé 2 — SciPy et scikit-learn (aperçu)

```bash
pip install scipy scikit-learn
```

## SciPy : calcul scientifique

```python
import numpy as np
from scipy import stats

# lois de probabilité
data = np.random.default_rng(0).normal(100, 15, 1000)
stats.describe(data)                       # stats descriptives avancées
stats.normaltest(data)                     # test de normalité
stats.ttest_ind(groupe_a, groupe_b)        # test t de Student (2 groupes)
stats.pearsonr(x, y)                       # corrélation + p-value
stats.linregress(x, y)                     # régression linéaire (pente, ordonnée, r²)

# optimisation, intégration, traitement du signal...
from scipy import optimize
f = lambda x: (x - 3) ** 2
optimize.minimize(f, x0=0)                 # trouve le minimum
```

## scikit-learn : premier modèle de machine learning

Le pattern universel : `fit` (entraînement) puis `predict` (prédiction).

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

df = pd.read_csv("data/logements.csv")     # colonnes : surface, chambres, prix
X = df[["surface", "chambres"]]            # features (entrées)
y = df["prix"]                             # cible

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

modele = LinearRegression()
modele.fit(X_train, y_train)               # entraînement

predictions = modele.predict(X_test)
print("R² :", r2_score(y_test, predictions))
print("RMSE :", mean_squared_error(y_test, predictions) ** 0.5)

print("Coefficients :", modele.coef_, "Intercept :", modele.intercept_)
```

Autres modèles courants : `RandomForestRegressor`, `LogisticRegression` (classification), `KMeans` (clustering)... avec toujours la même API `fit`/`predict`.

## Exercices (à faire seul)

1. Test t : deux groupes de notes (2 classes) — y a-t-il une différence significative de moyenne ? (`stats.ttest_ind`)
2. Régression linéaire simple avec `stats.linregress` : prix d'un logement en fonction de la surface.
3. Premier modèle sklearn : prédis le pourboire (`tip`) à partir du montant (`total_bill`) sur le dataset `tips` de seaborn ; affiche R².

## Pour aller plus loin

- [SciPy](https://docs.scipy.org/doc/scipy/tutorial/index.html)
- [scikit-learn : getting started](https://scikit-learn.org/stable/getting_started.html)
- [Roadmap Machine Learning](https://roadmap.sh/machine-learning)


---

<!-- source : 14-sujets-avances/03-geo.md -->

# Avancé 3 — Analyse géospatiale (aperçu)

```bash
pip install geopandas
```

**GeoPandas** ajoute la dimension géographique aux DataFrames : points, lignes, polygones, avec CRS (systèmes de coordonnées), jointures spatiales et cartes.

```python
import geopandas as gpd

# lire un fichier géo (GeoJSON, Shapefile...)
villes = gpd.read_file("data/villes.geojson")
print(villes.crs)            # EPSG:4326 (WGS84, lat/lon GPS)

# GeoDataFrame = DataFrame pandas + colonne "geometry"
villes.plot(column="population", legend=True, cmap="viridis")

# jointure spatiale : quels points tombent dans quel polygone ?
points = gpd.GeoDataFrame(..., geometry=gpd.points_from_xy(lons, lats), crs="EPSG:4326")
jointure = gpd.sjoin(points, regions, predicate="within")
```

## Ressources de données géo gratuites

- [Natural Earth](https://www.naturalearthdata.com/) : frontières de pays, villes.
- [data.gouv.fr](https://www.data.gouv.fr/) : données géo françaises (découpage administratif, etc.).
- OpenStreetMap via [Overpass API](https://overpass-turbo.eu/).

## Cartes interactives

```python
import plotly.express as px
fig = px.scatter_mapbox(df, lat="lat", lon="lon", size="population", hover_name="ville",
                        mapbox_style="open-street-map", zoom=4)
fig.show()
```

## Exercice (à faire seul)

1. Récupère le GeoJSON des pays (Natural Earth), charge avec GeoPandas, colore par continent, sauvegarde la carte en HTML avec Plotly choropleth.

## Pour aller plus loin

- [GeoPandas](https://geopandas.org/)
- [Roadmap GIS / géospatial](https://roadmap.sh/datastructures-and-algorithms) (section géo) — ou la roadmap Data Engineer.

Parcours terminé : place aux [projets solo](../projets/README.md) !


---

<!-- source : projets/README.md -->

# Projets solo — à réaliser sans IA

Ces mini-projets sont conçus pour être faits **seul**, dans l'ordre, en t'appuyant uniquement sur les leçons du parcours et la documentation officielle. Ne demande pas la solution à une IA : le but est de chercher, tester, te tromper et trouver.

## Règles du jeu

1. Lis l'énoncé, écris ton code, teste, corrige. La documentation officielle est ton amie ([docs.python.org](https://docs.python.org/fr/3/), [pandas.pydata.org](https://pandas.pydata.org/docs/), etc.).
2. Versionne chaque projet avec git (un commit par étape qui marche).
3. Quand tu bloques plus de 30 min sur un point, note la question précise — puis cherche dans la doc avant toute autre aide.

## Progression proposée

| # | Projet | Niveau | Compétences visées |
|---|---|---|---|
| 1 | [Dépenses personnelles](01-depenses-personnelles.md) | ⭐ débutant | bases Python, fichiers CSV, pandas, matplotlib |
| 2 | [Notes de classe](02-notes-de-classe.md) | ⭐ débutant | fonctions, statistiques de base, numpy |
| 3 | [Météo d'une ville](03-meteo-open-meteo.md) | ⭐⭐ | API `requests`, JSON, nettoyage de dates, graphiques |
| 4 | [Scraping de livres](04-scraping-books.md) | ⭐⭐ | BeautifulSoup, parsing HTML, nettoyage de texte |
| 5 | [EDA du Titanic](05-titanic-eda.md) | ⭐⭐ | pandas, groupby, EDA complète, seaborn |
| 6 | [Pandas vs Polars](06-pandas-vs-polars.md) | ⭐⭐ | comparaison de perfs, benchmark |
| 7 | [Mini-ETL SQL](07-etl-sql.md) | ⭐⭐ | CSV → sqlite3/DuckDB → requêtes SQL → rapport |
| 8 | [Dashboard Streamlit](08-dashboard-streamlit.md) | ⭐⭐⭐ | app web interactive en pur Python |
| 9 | [Dataset volontairement sale](09-dataset-sale.md) | ⭐⭐⭐ | nettoyage complet, notebook documenté |
| 10 | [Rapport automatisé](10-rapport-automatise.md) | ⭐⭐⭐ | script + planification (cron), génération de PNG |

## Données utilisables sans clé API

- Tes propres données (dépenses, notes, livres lus...).
- [Open-Meteo](https://open-meteo.com/en/docs) (météo, sans clé), [REST Countries](https://restcountries.com/), [JSONPlaceholder](https://jsonplaceholder.com/), [PokeAPI](https://pokeapi.co/).
- [books.toscrape.com](https://books.toscrape.com/) (site d'entraînement au scraping).
- Jeux de données seaborn/plotly (`sns.load_dataset`, `px.data.*`).
- [data.gouv.fr](https://www.data.gouv.fr/) et [Kaggle](https://www.kaggle.com/datasets) (téléchargement manuel).
- Données générées toi-même avec `numpy.random`.


---

<!-- source : projets/01-depenses-personnelles.md -->

# Projet 1 — Analyse de tes dépenses personnelles

**Niveau :** ⭐ débutant · **Modules :** 01, 02, 03, 05 (bases), 08 (matplotlib)

## Énoncé

Pendant un mois, note toutes tes dépenses dans un fichier CSV que tu crées toi-même :

```csv
date,categorie,libelle,montant
2024-01-03,alimentation,courses supermarché,42.50
2024-01-05,transport,essence,55.00
...
```

Puis écris un programme Python qui :

1. Lit le CSV avec `csv` (stdlib) ou `pandas`.
2. Affiche le **total dépensé** et le **nombre de dépenses**.
3. Calcule le **total par catégorie** et affiche-le trié du plus grand au plus petit.
4. Calcule la **dépense moyenne par jour** sur la période.
5. Produit un **graphique en barres** des dépenses par catégorie (matplotlib) et le sauvegarde en PNG.
6. Bonus : affiche la catégorie qui représente la plus grande part du total (en %).

## Critères de réussite

- Le programme tourne sans erreur sur ton CSV réel.
- Le PNG est généré et lisible (titre, axes nommés).
- Le code est découpé en fonctions (une par étape).

## Extensions possibles

- Lire le CSV exporté par ta banque (souvent en `;` avec des virgules décimales) : gérer `sep=";"` et `decimal=","`.
- Ajouter une colonne `mois` et comparer deux mois.
- Version interactive : demander la catégorie en `input()` et n'afficher que celle-là.


---

<!-- source : projets/02-notes-de-classe.md -->

# Projet 2 — Statistiques de notes de classe

**Niveau :** ⭐ débutant · **Modules :** 01 (fonctions), 04 (numpy)

## Énoncé

Tu es délégué·e de classe. Le professeur te donne les notes de ta classe en maths dans un fichier texte, une note par ligne :

```text
14
12
8
17
...
```

Écris un programme qui :

1. Lit le fichier et convertit chaque ligne en nombre (gère les lignes vides).
2. Affiche : nombre d'élèves, note max, note min, moyenne, médiane.
3. Compte combien d'élèves ont la moyenne (>= 10), et le pourcentage.
4. Affiche la **répartition par mention** (insuffisant < 10, passable 10-12, assez bien 12-14, bien 14-16, très bien >= 16) avec un histogramme matplotlib.
5. Bonus : avec numpy, calcule l'écart-type et trace la distribution avec `np.histogram`.

## Critères de réussite

- Fonctions réutilisables (`lire_notes`, `statistiques`, `mentions`...).
- Le programme gère un fichier vide ou inexistant sans planter (message clair).
- Résultats affichés avec des textes explicites.

## Extensions possibles

- Plusieurs matières dans le CSV (`eleve,maths,francais,anglais`) : moyenne par élève et par matière.
- Génère toi-même un fichier de 30 notes aléatoires avec `numpy.random.default_rng(42).integers(0, 21, 30)` pour tester.


---

<!-- source : projets/03-meteo-open-meteo.md -->

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


---

<!-- source : projets/04-scraping-books.md -->

# Projet 4 — Scraper et analyser un catalogue de livres

**Niveau :** ⭐⭐ · **Modules :** 09 (BeautifulSoup), 05, 06 (nettoyage texte)

## Énoncé

[books.toscrape.com](https://books.toscrape.com/) est un site **conçu pour s'entraîner au scraping**. Ta mission :

1. Scraper la page d'accueil : pour chaque livre, extraire **titre, prix, note (étoiles), disponibilité**.
2. Convertir le prix (`"£51.77"`) en `float` et la note (`"Three"`) en entier 1-5 (mapping).
3. Stocker le tout dans un DataFrame pandas.
4. Analyser : prix moyen, prix min/max, livre le plus cher, répartition des notes (`value_counts`), nombre de livres disponibles vs indisponibles.
5. Graphiques : histogramme des prix, barplot du prix moyen par note.
6. Bonus : scraper les **3 premières pages** (pagination `catalogue/page-2.html`, ...) et sauvegarder le résultat complet en CSV.

## Critères de réussite

- `User-Agent` personnalisé dans les requêtes + `time.sleep(1)` entre les pages.
- Les prix sont bien des `float` (vérifie avec `dtypes`).
- Le CSV exporté se relit correctement.

## Extensions possibles

- Extraire aussi la catégorie de chaque livre (page détail) et calculer le prix moyen par catégorie.
- Trouver les livres "Five stars" au prix inférieur à la moyenne.


---

<!-- source : projets/05-titanic-eda.md -->

# Projet 5 — EDA complète du Titanic

**Niveau :** ⭐⭐ · **Modules :** 05, 06, 07, 08

## Énoncé

Le dataset du Titanic (passagers, survie ou non) est le classique de l'EDA. Récupère le CSV `titanic.csv` (Kaggle « Titanic - Machine Learning from Disaster », téléchargement manuel) ou utilise `sns.load_dataset("titanic")`.

Réalise une **analyse exploratoire complète** dans un notebook Jupyter, avec au minimum :

1. **Inspection** : `info()`, `describe()`, % de valeurs manquantes par colonne.
2. **Nettoyage** : impute l'âge manquant (par la médiane par sexe/classe), gère `embarked` manquant, supprime ou transforme les colonnes inutiles (`deck` trop vide...).
3. **Stats** : taux de survie global, survie par sexe, par classe, par tranche d'âge (crée une colonne `tranche_age` avec `pd.cut`).
4. **Visualisations** (seaborn) : countplot survie, survie par sexe, distribution de l'âge des survivants vs non-survivants, heatmap de corrélation.
5. **3 questions métier** avec leurs réponses chiffrées, ex. : « Quelle classe a le meilleur taux de survie ? », « Les femmes ont-elles survécu plus que les hommes ? À quel point ? », « Le prix du billet (fare) est-il lié à la survie ? ».
6. Un **résumé écrit** en markdown dans le notebook (3-5 conclusions).

## Critères de réussite

- Notebook exécutable de haut en bas sans erreur (`Kernel > Restart & Run All`).
- Chaque graphique a un titre et une phrase d'interprétation en markdown.
- Les questions métier ont des réponses **chiffrées**.

## Extensions possibles

- Tableau croisé classe × sexe avec `crosstab(normalize="index")`.
- Compare survie des passagers seuls vs accompagnés (colonnes `sibsp` + `parch`).


---

<!-- source : projets/06-pandas-vs-polars.md -->

# Projet 6 — Benchmark : pandas vs Polars

**Niveau :** ⭐⭐ · **Modules :** 04, 05, 11

## Énoncé

Génère toi-même un gros fichier de ventes (pas besoin de téléchargement) :

```python
import numpy as np, pandas as pd
rng = np.random.default_rng(42)
n = 2_000_000
df = pd.DataFrame({
    "date": pd.date_range("2023-01-01", periods=n, freq="s").astype(str),
    "produit": rng.choice(["A", "B", "C", "D", "E"], n),
    "categorie": rng.choice(["alim", "tech", "maison"], n),
    "ville": rng.choice(["Paris", "Lyon", "Lille", "Bordeaux"], n),
    "quantite": rng.integers(1, 10, n),
    "prix": np.round(rng.uniform(1, 500, n), 2),
})
df.to_csv("data/ventes_gros.csv", index=False)
```

Puis écris un script de benchmark qui mesure (avec `time.perf_counter()`) le temps de **la même analyse** avec pandas et avec Polars :

1. Lire le CSV.
2. Filtrer `prix > 50`.
3. `groupby(["categorie", "ville"])` + somme de `quantite * prix` (le CA), tri décroissant, top 10.

Affiche un tableau comparatif des temps. Réponds par écrit : quel outil gagne, et de combien ?

## Critères de réussite

- Même analyse des deux côtés (vérifie que les résultats sont identiques, ex. `pd.testing` ou `assert` sur les valeurs).
- Temps mesurés proprement (2-3 essais, moyenne).
- Fichier CSV généré avec une graine fixée (reproductible).

## Extensions possibles

- Tester aussi `pl.scan_csv` (lazy) vs `pl.read_csv`.
- Tester DuckDB (`duckdb.sql(...)`) comme troisième candidat.
- Mesurer la mémoire utilisée (`df.memory_usage(deep=True).sum()` côté pandas).


---

<!-- source : projets/07-etl-sql.md -->

# Projet 7 — Mini-ETL : CSV → base SQL → rapport

**Niveau :** ⭐⭐ · **Modules :** 05, 06, 10

## Énoncé

Construis un petit pipeline **ETL** (Extract → Transform → Load) :

1. **Extract** : génère (ou télécharge) un CSV de ventes avec des données volontairement imparfaites (quelques valeurs manquantes, dates au format `"03/01/2024"`, prix avec virgule).
2. **Transform** : avec pandas, nettoie (dates → `datetime`, prix → `float`, manquants traités) et calcule `montant = quantite * prix`.
3. **Load** : charge le DataFrame propre dans une base **sqlite3** (tables `clients` et `ventes` avec clé étrangère), via `to_sql`.
4. **Analyse en SQL** : écris et exécutes des requêtes SQL (via `pd.read_sql_query`) :
   - CA total et par mois (`strftime('%Y-%m', date)`),
   - top 5 clients par CA (JOIN),
   - panier moyen (montant moyen par commande).
5. **Bonus** : refais les mêmes requêtes directement sur le CSV avec **DuckDB** (`duckdb.sql("SELECT ... FROM 'data/ventes.csv' ...")`) et compare.
6. Exporte le rapport (résultats des requêtes) en CSV.

## Critères de réussite

- Les tables sqlite contiennent bien les données nettoyées (vérifie avec `SELECT COUNT(*)`).
- Au moins 3 requêtes SQL avec JOIN/GROUP BY.
- Rapport CSV généré automatiquement.

## Extensions possibles

- Ajoute une table `produits` et des contraintes de clé étrangère (`PRAGMA foreign_keys = ON`).
- Fais le même pipeline avec SQLAlchemy (`create_engine`).


---

<!-- source : projets/08-dashboard-streamlit.md -->

# Projet 8 — Dashboard interactif avec Streamlit

**Niveau :** ⭐⭐⭐ · **Modules :** 08 (plotly), 12 (streamlit)

## Énoncé

Transforme une de tes analyses précédentes (météo, livres scrapés, Titanic...) en **application web interactive** :

1. Crée `app.py` avec `streamlit run app.py`.
2. Barre latérale (`st.sidebar`) avec au moins 2 filtres (ex. : ville, catégorie, plage de dates, note min...).
3. En haut : 2-3 **métriques clés** (`st.metric`) calculées sur les données filtrées.
4. Au moins **2 graphiques** (Plotly via `st.plotly_chart`, ou natifs `st.line_chart`/`st.bar_chart`).
5. Un tableau des données filtrées (`st.dataframe`).
6. Bonus : `st.file_uploader` pour charger n'importe quel CSV et voir ses stats instantanément.

## Critères de réussite

- L'app se lance sans erreur et se met à jour quand on change un filtre.
- `@st.cache_data` sur le chargement des données.
- Capture d'écran du dashboard jointe à ton commit (PNG dans le dossier du projet).

## Extensions possibles

- Carte (`st.map`) si tes données ont lat/lon.
- Déploiement sur Streamlit Community Cloud (gratuit, lié à ton dépôt GitHub).


---

<!-- source : projets/09-dataset-sale.md -->

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


---

<!-- source : projets/10-rapport-automatise.md -->

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
