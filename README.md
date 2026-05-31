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
git clone <url-du-repo>
cd <nom-du-repo>

# 2. Créer l'environnement virtuel
uv venv

# 3. Installer les dépendances
uv sync
```

---

## Utilisation

```bash
# Lancer un script
uv run python <script.py>

# Ou activer l'environnement
source .venv/bin/activate   # macOS / Linux
.venv\Scripts\activate      # Windows
```

---

## Gestion des dépendances

```bash
# Ajouter un paquet
uv add <paquet>

# Ajouter une dépendance de développement
uv add --dev <paquet>

# Ajouter une version précise
uv add "<paquet>>=x.x"

# Supprimer un paquet
uv remove <paquet>

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
| Ajouter un paquet | `uv add <paquet>` |
| Supprimer un paquet | `uv remove <paquet>` |
| Lancer un script | `uv run python <script.py>` |
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