# Projet : Analyse Exploratoire pour une Campagne Marketing Bancaire

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Status](https://img.shields.io/badge/Status-Terminé-success.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

##  Description

Analyse exploratoire de données et modélisation prédictive pour optimiser les campagnes de télémarketing d'une banque portugaise. L'objectif est d'identifier les clients les plus susceptibles de souscrire à un dépôt à terme.

**Contexte :** Campagnes de télémarketing (Mai 2008 - Novembre 2010)  
**Dataset :** 40,858 clients × 20 variables  
**Défi :** Déséquilibre des classes (11.27% "yes")

---

##  Objectifs

- Explorer et analyser les données pour extraire des insights stratégiques
- Identifier les segments de clients à cibler en priorité
- Appliquer des méthodes statistiques avancées (Chi², ANOVA, MANOVA)
- Construire un modèle prédictif performant (KNN, Random Forest, XGBoost)
- Fournir des recommandations actionnables pour maximiser le ROI

---

##  Résultats Clés

### Performances du Modèle (Random Forest)

| Métrique | Valeur | Amélioration vs Baseline |
|----------|--------|--------------------------|
| **F1-Score** | 0.4920 | +34.8% |
| **Recall** | 57.00% | +104% |
| **Precision** | 43.28% | -18% |
| **AUC-ROC** | 0.7990 | +10% |
| **Faux Négatifs** | 396 | -40.4% |

**Impact Business :** 268 opportunités commerciales supplémentaires récupérées

### Insights Stratégiques (Top 3)

1. **Poutcome (Historique)** : Clients "success" : 65.58% de souscription (+56.74 pts)
2. **Month (Timing)** : Mars : 50.74% vs Mai : 6.47% (+44.27 pts)
3. **Age (Démographie)** : 65+ ans : 46.63% vs 35-45 ans : 8.52% (+38.12 pts)

### Recommandations

- Concentrer 80% du budget sur 3 mois : **Mars, Septembre, Décembre**
- Cibler en priorité : Anciens "success" + Seniors 65+ + Étudiants
- Limiter à **2-3 contacts maximum** par client (éviter fatigue)
- ROI estimé : **+337%** vs approche actuelle

---

## 🗂️ Structure du Projet
```
projet-analyse-exploiratoire/
│
├── 📁 data/                           # Données (disponibles sur Google Drive)
│   ├── bank-additional-full.csv      # Dataset original (41,188 lignes)
│   ├── bank-additional-full-cleaned.csv  # Dataset nettoyé (40,858 lignes)
│   └── bank-additional-names.txt     # Documentation des variables
│
├── 📁 notebooks/                      # Notebooks Jupyter (5)
│   ├── 01_comprehension_donnees.ipynb
│   ├── 02_preparation_nettoyage.ipynb
│   ├── 03_analyse_statistique.ipynb
│   ├── 04_modelisation.ipynb
│   └── 05_resultats_recommandations.ipynb
│
├── 📁 results/                        # Résultats
│   └── figures/                       # 30+ graphiques (PNG)
│
├── 📄 Rapport complet ecrit.pdf      # Rapport final (15+ pages)
├── 📄 MiniProjet_analyse_exploiratoire.pdf  # Énoncé du projet
├── 📄 README.md                       # Ce fichier
└── 📄 requirements.txt                # Dépendances Python
```

---

## 📂 Données

**Les fichiers de données sont volumineux (>100 MB) et ne sont pas inclus dans ce repository.**

**Téléchargement :**
- **Google Drive :** [Lien vers les données](https://drive.google.com/drive/folders/1lcI1TGrw2V8DZQijPIXB_YB4Wz2KyHAM?usp=sharing)
- **UCI Repository :** [Bank Marketing Dataset](https://archive.ics.uci.edu/dataset/222/bank+marketing)

**Instructions :**
1. Téléchargez les fichiers depuis Google Drive
2. Placez-les dans le dossier `data/` à la racine du projet
3. Les notebooks pourront alors accéder aux données

---

##  Installation

### Prérequis

- Python 3.8+
- Jupyter Notebook ou JupyterLab
- Git

### Installation des dépendances
```bash
# Cloner le repository
git clone https://github.com/[VOTRE_USERNAME]/projet-analyse-exploiratoire.git
cd projet-analyse-exploiratoire

# Créer un environnement virtuel (optionnel mais recommandé)
python -m venv .venv
source .venv/bin/activate  # Sur Windows: .venv\Scripts\activate

# Installer les dépendances
pip install -r requirements.txt
```

### Lancer les notebooks
```bash
jupyter notebook
# Ou
jupyter lab
```

---

##  Méthodologie

Le projet suit la méthodologie **CRISP-DM** :

### 1. Compréhension des Données (Notebook 1)
- Exploration initiale (41,188 clients × 21 variables)
- Identification des valeurs manquantes et outliers
- Analyse du déséquilibre des classes (11.27% "yes")

### 2. Préparation des Données (Notebook 2)
- Traitement des "unknown" (5 variables gardées, 1 supprimée)
- Gestion des outliers (13,288 détectés, tous conservés)
- Exclusion de "duration" (data leakage)
- Dataset final : 40,858 lignes × 20 variables

### 3. Analyses Statistiques (Notebook 3)
- **9 analyses univariées** (distribution, histogrammes, boxplots)
- **8 analyses bivariées** (toutes variables vs y)
- **Tests statistiques** : Chi² (8 tests), ANOVA, t-test, MANOVA
- **Identification des 3 variables les plus discriminantes**

### 4. Modélisation (Notebook 4)
- **Baseline :** KNN k=5 sans SMOTE (F1=0.3651)
- **Modèle 1 :** KNN k=19 avec SMOTE (F1=0.4242)
- **Modèle 2 :** Random Forest (F1=0.4920)  **Retenu**
- **Modèle 3 :** XGBoost (F1=0.4934)

**Techniques utilisées :**
- SMOTE pour rééquilibrage (50-50 sur train)
- GridSearchCV pour optimisation hyperparamètres
- Validation croisée 5-fold

### 5. Résultats et Recommandations (Notebook 5)
- Synthèse des 4 notebooks précédents
- 6 recommandations stratégiques détaillées
- Estimation d'impact business (ROI +337%)
- KPI à suivre

---

##  Graphiques Clés

Le projet contient **30+ visualisations professionnelles** :

- Distributions univariées (9 graphiques)
- Analyses bivariées (8 graphiques)
- Heatmaps de corrélations
- Matrices de confusion (baseline vs optimisé)
- Courbes ROC comparées (4 modèles)
- Feature Importance (Random Forest + XGBoost)
- Comparaisons de performances

**Tous les graphiques sont sauvegardés en haute résolution (300 DPI) dans `results/figures/`**

---

##  Technologies Utilisées

### Langages et Environnement
- **Python 3.8+**
- **Jupyter Notebook**

### Librairies Principales
```python
# Manipulation de données
pandas==2.0.0
numpy==1.24.0

# Visualisation
matplotlib==3.7.0
seaborn==0.12.0

# Machine Learning
scikit-learn==1.3.0
xgboost==2.0.0
imbalanced-learn==0.11.0

# Utilitaires
scipy==1.10.0
```

---

##  Variables du Dataset

### Variables Démographiques
- `age` : Âge du client (numérique)
- `job` : Type d'emploi (12 catégories)
- `marital` : Statut matrimonial (married, single, divorced)
- `education` : Niveau d'éducation (8 catégories)

### Variables Financières
- `default` : Crédit en défaut ? (yes, no, unknown)
- `balance` : Solde moyen annuel en euros
- `housing` : Prêt immobilier ? (yes, no, unknown)
- `loan` : Prêt personnel ? (yes, no, unknown)

### Variables de Contact
- `contact` : Type de communication (cellular, telephone)
- `month` : Mois du dernier contact (12 mois)
- `day_of_week` : Jour de la semaine (lun-ven)
- `campaign` : Nombre de contacts durant la campagne

### Variables Historiques
- `pdays` : Jours depuis dernier contact (999 = jamais contacté)
- `previous` : Nombre de contacts avant cette campagne
- `poutcome` : Résultat campagne précédente (success, failure, nonexistent)

### Variables Socio-économiques
- `emp.var.rate` : Taux de variation de l'emploi
- `cons.price.idx` : Indice des prix à la consommation
- `cons.conf.idx` : Indice de confiance des consommateurs
- `euribor3m` : Taux Euribor 3 mois
- `nr.employed` : Nombre d'employés

### Variable Cible
- `y` : Souscription au dépôt à terme ? (yes, no)

---

## 🎓 Compétences Développées

- Analyse exploratoire de données (EDA)
- Nettoyage et préparation de données
- Tests statistiques (Chi², ANOVA, MANOVA)
- Gestion du déséquilibre de classes (SMOTE)
- Modélisation supervisée (KNN, Random Forest, XGBoost)
- Optimisation d'hyperparamètres (GridSearchCV)
- Évaluation de modèles (F1, Recall, Precision, AUC-ROC)
- Visualisation de données (Matplotlib, Seaborn)
- Communication de résultats techniques
- Prise de décision basée sur les données

---


## 👤 Auteur

**[Votre Nom]**

- GitHub: Adjakim (https://github.com/Adjakim)
- Email: adjakimfatima@gmail.com

---

##  Date de Réalisation

**13-Fevrier2026/27-Février 2026**

---

** Si ce projet vous a été utile, n'hésitez pas à lui donner une étoile !**