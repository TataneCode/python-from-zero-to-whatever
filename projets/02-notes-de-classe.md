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
