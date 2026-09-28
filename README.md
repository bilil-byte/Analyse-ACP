# Analyse en Composantes Principales (ACP)

Projet d'analyse de données appliquant une Analyse en Composantes Principales (ACP) à un jeu de données de cours en ligne, afin d'en dégager les axes structurants (format du cours, niveau de difficulté/performance, mode d'évaluation, ancienneté d'inscription).

## Objectifs

- Réduire la dimensionnalité d'un jeu de données de cours (8 variables quantitatives) tout en conservant l'essentiel de l'information.
- Identifier les axes de variation principaux entre les cours et les interpréter en termes de profil (durée/format, difficulté/performance, mode d'évaluation).
- Valider l'implémentation de l'ACP scikit-learn par une décomposition SVD manuelle.

## Données

Le jeu de données (`my_courses.csv`) contient 19 cours décrits par les variables suivantes :

| Variable | Description |
|---|---|
| `inscription` | Nombre de jours écoulés depuis l'inscription au cours |
| `progression` | Progression sur le cours (%) |
| `moyenneDeClasse` | Moyenne de la classe aux évaluations (%) |
| `duree` | Durée estimée du cours (heures) |
| `difficulte` | Difficulté estimée (1 = facile, 3 = difficile) |
| `nbChapitres` | Nombre de chapitres |
| `nbEvaluations` | Nombre d'évaluations (quiz + activités) |
| `ratioQuizEvaluation` | Proportion de quiz parmi les évaluations |

Les colonnes `idCours` et `derniereMiseAJour` sont exclues de l'ACP (identifiant et date, non pertinents pour l'analyse de variance).

## Méthodologie

1. **Nettoyage** : traitement des valeurs manquantes (remplacement par la moyenne), vérification des doublons.
2. **Standardisation** : mise à l'échelle des variables (`StandardScaler`) avant ACP, les variables étant sur des échelles hétérogènes.
3. **ACP** : décomposition via `sklearn.decomposition.PCA`, choix de 6 composantes retenant 95,6 % de la variance totale.
4. **Validation croisée de méthode** : comparaison des projections obtenues par `sklearn` et par une décomposition SVD manuelle (`numpy.linalg.svd`), avec réalignement des signes (ambiguïté de signe inhérente à la SVD/ACP).
5. **Interprétation** : cercle des corrélations et lecture des variables les mieux représentées sur chaque axe.



## Technologies utilisées

Python · Pandas · NumPy · Scikit-learn · Matplotlib

## Pistes d'amélioration

- Ajouter un biplot combinant individus et variables sur un même graphique.

## Auteur

Lilian Nkwemfo
