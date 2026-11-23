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
