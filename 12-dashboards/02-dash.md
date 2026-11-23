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
