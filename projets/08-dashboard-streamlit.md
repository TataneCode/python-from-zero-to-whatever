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
