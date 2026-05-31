# Nom du Projet

> Courte description du projet (1-2 lignes).

---

## Prérequis

- Python **3.10+**
- [uv](https://docs.astral.sh/uv/getting-started/installation/)

### Installer uv

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# Via pip
pip install uv
```

---

## Installation

```bash
# 1. Cloner le dépôt
git clone https://github.com/mdidech/ml-challenges-template.git <new-project-name>
cd <new-project-name>

# 2. Créer l'environnement virtuel
uv venv

# 3. Installer les dépendances
uv sync
```

---

## Utilisation

```bash
# Ou activer l'environnement
source .venv/bin/activate      # macOS / Linux
.venv/Scripts/activate.bat     # Windows (cmd)
.venv/Scripts/Activate.ps1     # Windows (PowerShell)
```

---

## Gestion des dépendances

```bash
# Ajouter un paquet
uv add NOM_PACKAGE

# Ajouter une dépendance de développement
uv add --dev NOM_PACKAGE

# Ajouter une version précise
uv add "PACKAGE>=x.x"

# Supprimer un paquet
uv remove NOM_PACKAGE

# Mettre à jour toutes les dépendances
uv sync --upgrade
```

---

## Structure

```
.
├── <à compléter selon le projet>
├── pyproject.toml     # Dépendances et métadonnées
├── uv.lock            # Versions verrouillées (à committer)
└── README.md
```

---

## Commandes rapides

| Action | Commande |
|---|---|
| Créer l'env virtuel | `uv venv` |
| Installer les dépendances | `uv sync` |
| Ajouter un paquet | `uv add NOM_PACKAGE` |
| Supprimer un paquet | `uv remove NOM_PACKAGE` |
| Lancer un script | `uv run python script.py` |
| Mettre à jour uv | `uv self update` |

---

## Bonnes pratiques

- **Committer `uv.lock`** — garantit les mêmes versions pour tous les contributeurs.
- **Ne pas committer `.venv/`** — l'ajouter au `.gitignore`.
- **Utiliser `uv run`** ou activer le `.venv` pour éviter d'utiliser le Python système.
- **Lancer `uv sync` après un `git pull`** — resynchronise l'env si les dépendances ont changé.

---

## Dépannage

**`uv` introuvable après installation**
→ Redémarre le terminal ou recharge ton shell (`source ~/.bashrc` / `source ~/.zshrc`).

**`uv sync` échoue**
→ Vérifie la version Python : `uv python list`. Installe si besoin : `uv python install 3.11`.

**Un script ne trouve pas ses paquets**
→ S'assurer de lancer via `uv run` ou depuis le `.venv` activé.

---

## ML Mentor — Parcours d'apprentissage guidé

Ce projet embarque le skill **`ml-mentor`** : un mentor pédagogique intégré à Claude Code qui guide l'apprenant de bout en bout à travers un parcours de Machine Learning structuré, en s'appuyant sur le dataset de `data/` et les objectifs de `specs/cahier_des_charges.md`.

### Objectif du skill

Le skill a **deux objectifs simultanés** :
- faire progresser l'apprenant du niveau **débutant vers avancé** (pandas, numpy, matplotlib → supervisé → non supervisé → pipelines, évaluation) ;
- s'assurer que **tout le challenge du cahier des charges est résolu** à la fin — chaque exercice est mappé à une exigence des specs, et le parcours ne se termine que quand toutes les cases sont cochées.

### Déroulement du parcours

```
Démarrage
│
├── Claude lit CLAUDE.md + specs/ + data/
├── Extrait la checklist des exigences du cahier des charges
├── Dresse le plan complet (8 modules) adapté au dataset
└── Crée progress.md — le fichier de suivi persistant

    Pour chaque exercice :
    │
    ├── 1. Claude crée exercises/NN_nom.md  ← énoncé, objectif, hints, critères
    ├── 2. L'apprenant code dans exercises/NN_nom.ipynb
    ├── 3. L'apprenant demande la revue ("j'ai fini")
    ├── 4. Claude EXÉCUTE le notebook + fait la code review
    │        ✅ Points forts
    │        ⚠️ Points faibles (data leakage, random_state, mauvaise métrique…)
    │        🎯 Axes d'amélioration
    │        Verdict : réussi ou à corriger
    │
    ├── Si incorrect → choix de l'apprenant :
    │        (a) Être guidé — hint ciblé, on réessaie
    │        (b) Voir la correction — solution expliquée
    │
    └── Si réussi → progress.md mis à jour → exercice suivant

Fin du parcours
│
├── Toutes les exigences du cahier des charges cochées ✅
└── Bilan final :
        - Challenge résolu (exigence par exigence)
        - Compétences acquises par thème
        - Niveau de maîtrise (Découverte / En cours / Maîtrisé / Solide)
        - Axes d'amélioration globaux
```

### Les 8 modules du parcours

| Module | Thème | Contenu |
|--------|-------|---------|
| 0 | Fondations Python | NumPy, pandas, matplotlib |
| 1 | EDA | Statistiques descriptives, distributions, corrélations |
| 2 | Prétraitement | Imputation, outliers, encodage, split, scaling |
| 3 | Apprentissage supervisé | Régression / Classification, premiers modèles |
| 4 | Évaluation | Métriques, validation croisée, comparaison |
| 5 | Pipelines | Pipeline, ColumnTransformer, GridSearchCV |
| 6 | Non supervisé | Clustering, réduction de dimension (PCA, t-SNE) |
| 7 | Projet de synthèse | Solution bout-en-bout conforme aux specs |

### Structure des fichiers générés par le skill

```
exercises/
├── 00_numpy_basics.md        ← énoncé (écrit par le mentor)
├── 00_numpy_basics.ipynb     ← réponse (écrit par l'apprenant)
├── 01_pandas_load.md
├── 01_pandas_load.ipynb
└── ...

progress.md                   ← suivi persistant (reprise entre sessions)
```

### Comment démarrer

1. S'assurer que le skill `ml-mentor` est installé dans Claude Code (`.claude/`).
2. Placer le dataset dans `data/` et remplir `specs/cahier_des_charges.md`.
3. Ouvrir Claude Code à la racine du projet et écrire :

```
je veux commencer mon parcours ML
```

Pour reprendre une session interrompue :

```
où j'en suis ?
```

Pour demander une revue après avoir codé un exercice :

```
j'ai fini l'exercice 03, revois mon code
```
