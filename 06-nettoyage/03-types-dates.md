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
