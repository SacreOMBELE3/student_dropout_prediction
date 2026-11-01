<<<<<<< HEAD
# Prédiction du devenir académique des étudiants

> Projet de data science visant à estimer le devenir académique d’un étudiant afin d’aider les équipes pédagogiques à repérer plus tôt les besoins d’accompagnement.

## Présentation

Le projet consiste à concevoir une solution de bout en bout combinant analyse de données, apprentissage automatique, stockage des prédictions et visualisation. La cible comporte trois catégories :

| Classe | Signification |
|---|---|
| `Dropout` | L’étudiant a abandonné ses études. |
| `Enrolled` | L’étudiant est toujours inscrit. |
| `Graduate` | L’étudiant a obtenu son diplôme. |

Une prédiction est une estimation destinée à éclairer l’accompagnement pédagogique. Elle ne doit pas être utilisée seule pour prendre une décision défavorable envers un étudiant.

## Objectifs

- Auditer, comprendre et préparer les données.
- Explorer les facteurs associés aux trois résultats académiques, sans confondre association et causalité.
- Entraîner et comparer plusieurs modèles de classification.
- Évaluer les performances par classe, notamment le rappel de la classe `Dropout`, ainsi qu’à l’aide de la matrice de confusion.
- À terme, enregistrer les données nécessaires et les prédictions dans SQL Server.
- À terme, proposer une application web de saisie et de consultation des prédictions, puis des tableaux de bord Power BI.

## Jeu de données

Le fichier fourni est `data/bronze/data.csv`. Il s’agit du jeu de données « Predict Students' Dropout and Academic Success », qui regroupe des informations sur le parcours antérieur, la formation, certaines caractéristiques démographiques et socioéconomiques, ainsi que les résultats semestriels.

L’audit du fichier présent dans le dépôt relève **4 424 observations et 37 colonnes au total**, dont la variable cible `Target` (soit 36 variables explicatives et une cible). La répartition observée est la suivante :

| Résultat (`Target`) | Nombre | Part |
|---|---:|---:|
| `Graduate` | 2 209 | 49,9 % |
| `Dropout` | 1 421 | 32,1 % |
| `Enrolled` | 794 | 17,9 % |

Le CSV est séparé par des points-virgules. Le fichier original doit rester intact dans le dossier `bronze` ; les transformations et données préparées seront conservées dans `silver` et `gold`.

### Point de vigilance : moment de la prédiction

Pour prédire le risque dès l’inscription, seules les informations disponibles à ce moment doivent être utilisées. Les résultats des semestres futurs doivent être exclus afin d’éviter la fuite de données. Le cahier des charges prévoit de commencer par ce scénario, puis de comparer éventuellement un modèle intégrant les résultats du premier semestre.

## État actuel du projet

Le dépôt contient actuellement le fichier de données et un premier notebook d’audit. Les autres composants décrits dans le cahier des charges (modèles, scripts, application Flask, base SQL Server et rapports Power BI) restent à réaliser.

```text
.
├── data/
│   └── bronze/
│       └── data.csv
├── notebooks/
│   └── 01_data_audit.ipynb.ipynb
├── Cahier de charge_Projet_Prediction_Abandon_Etudiant.pdf
└── README.md
```

Le notebook `notebooks/01_data_audit.ipynb.ipynb` examine la structure du jeu de données, ses types, les valeurs manquantes, les doublons et les catégories de la cible. Il contient également une première documentation des variables.

## Environnement et démarrage

Le projet est prévu pour un travail local sous Windows avec Python et Jupyter. Créez un environnement virtuel depuis la racine du dépôt :

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install pandas numpy jupyter
jupyter lab
```

Ouvrez ensuite le notebook d’audit depuis Jupyter. Son paramètre `DATA_PATH` utilise actuellement un chemin Windows propre à l’environnement d’origine ; adaptez-le au chemin local du fichier `data/bronze/data.csv` avant l’exécution.

## Feuille de route

Les étapes ci-dessous reprennent le cahier des charges ; elles ne signifient pas que les livrables sont déjà implémentés.

1. **Audit des données** — notebook `01_data_audit.ipynb`.
2. **Analyse exploratoire** — graphiques et constats documentés.
3. **Préparation des données** — jeux de données nettoyés et prêts pour la modélisation.
4. **Entraînement et évaluation** — pipelines de classification comparés et validés.
5. **Stockage SQL Server** — conception de la base et des tables nécessaires.
6. **Application Flask** — formulaire, résultat prédit et, si possible, probabilités estimées.
7. **Power BI** — vues générales, analyses et indicateurs du modèle.
8. **Tests et documentation** — vérification et documentation des composants livrés.

## Pistes de visualisation Power BI

- **Vue générale :** effectif, répartition des résultats, taux d’abandon observé et comparaison par formation.
- **Analyse :** comparaison des catégories selon les caractéristiques disponibles, sans interpréter une association comme une preuve de causalité.
- **Modèle :** accuracy, précision, rappel, F1-score, matrice de confusion et volume des prédictions.

## Technologies prévues

| Domaine | Technologies |
|---|---|
| Analyse et préparation | Python, Pandas, NumPy |
| Visualisation exploratoire | Matplotlib, Seaborn |
| Machine learning | Scikit-learn, Joblib |
| Application web | Flask, HTML, CSS |
| Stockage | SQL Server, SSMS |
| Tableaux de bord | Power BI Desktop |
| Versionnement | Git, GitHub |

## Organisation cible

À mesure que les étapes seront réalisées, le dépôt pourra évoluer vers l’organisation suivante :

```text
student_dropout_prediction/
├── data/
│   ├── bronze/       # données originales, non modifiées
│   ├── silver/       # données nettoyées
│   └── gold/         # données prêtes pour l’analyse et la modélisation
├── notebooks/        # audit, exploration, préparation, entraînement, évaluation
├── src/              # préparation, entraînement et prédiction
├── models/           # modèles ou pipelines sérialisés
├── app/              # application Flask, templates et fichiers statiques
├── sql/              # scripts et objets SQL Server
├── powerbi/          # rapports Power BI
└── tests/            # tests du projet

=======
# student_dropout_prediction
construire une solution capable d’estimer si un étudiant est susceptible d’abandonner ses études, de rester inscrit ou d’obtenir son diplôme, afin d’aider les équipes pédagogiques à mieux accompagner les étudiants.
>>>>>>> 4222fb332fc121d4e1a0767b1019d2525e6817f4
