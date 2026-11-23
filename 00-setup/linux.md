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
