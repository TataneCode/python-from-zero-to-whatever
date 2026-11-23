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
