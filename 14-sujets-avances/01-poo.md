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
