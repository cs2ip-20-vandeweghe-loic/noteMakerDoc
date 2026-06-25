---
title: Architecture
icon: lucide/wrench
---

# Architecture technique

> Découvrez comment NoteMaker est construit et comment les différents composants interagissent entre eux.

---

## Vue d'ensemble

NoteMaker est une **application CLI Python** qui utilise une architecture modulaire simple et claire.

### Stack technologique

| Composant | Technologie | Rôle |
|-----------|-------------|------|
| **Langage** | Python 3.8+ (testé sur 3.12) | Développement de l'application |
| **CLI** | argparse | Gestion des arguments et commandes |
| **Stockage** | JSON | Persistance des données locales |
| **Distribution** | setuptools + pipx | Installation et packaging |
| **Conteneurisation** | Docker + Docker Compose | Déploiement portable |
| **CI/CD** | GitHub Actions | Tests automatisés |

---

## Structure du projet

Le projet suit le **src layout** moderne de Python :

```
noteMakerPy/
├── .github/
│ └── workflows/
│ └── ci.yml # CI/CD GitHub Actions
├── docker/
│ ├── Dockerfile # Image Docker
│ └── compose.yaml # Docker Compose
├── src/
│ └── note/ # Package principal
│ ├── __init__.py
│ ├── cli.py # Point d'entrée et parser
│ ├── database.py # Gestion du fichier JSON
│ └── function/ # Logique métier
│ ├── add.py # Ajout de notes
│ ├── list.py # Affichage des notes
│ ├── delete.py # Suppression de notes
│ └── export_markdown.py # Export Markdown
├── pyproject.toml # Configuration moderne du projet
├── LICENSE # Licence MIT
└── README.md # Documentation
```

## Modules principaux

| Module | Rôle |
|--------|------|
| **cli.py** | Point d'entrée, analyse les commandes via `argparse` |
| **database.py** | Gestion lecture/écriture des notes (JSON) |
| **function/add.py** | Création de notes avec métadonnées auto |
| **function/list.py** | Affichage des notes (toutes ou filtrées) |
| **function/delete.py** | Suppression de note(s) |
| **function/export_markdown.py** | Export vers fichiers Markdown |

Flux simplifié : `Utilisateur` → `cli.py` → `function/*.py` → `database.py` → fichier JSON

---

## Modèle de données

### Structure d'une note

Chaque note est un objet JSON avec les propriétés suivantes :

```json
{
  "id": 1,
  "content": "Acheter du lait",
  "date": "2026-06-25T10:30:00",
  "author": "johndoe",
  "category": "general"
}
```

---

## Principes de conception

### Modularité
Chaque commande est **indépendante** dans son propre fichier, facilitant maintenance et extension.

### Simplicité
- Aucune dépendance externe lourde n'est nécessaire
- Le stockage JSON est simple et lisible par l'humain
- La structure du projet est claire et intuitive

### Extensibilité
Vous souhaitez ajouter une nouvelle commande ? C'est simple en **3 étapes** :

1. Créer un nouveau fichier dans le dossier `function/`
2. Ajouter le parser correspondant dans `cli.py`
3. Importer et appeler la nouvelle fonction

---

## Technologies utilisées

NoteMaker repose **uniquement sur la bibliothèque standard Python** (aucune installation de dépendance externe).

### Modules Python utilisés

- **argparse** - Analyse et parsing des arguments de ligne de commande
- **json** - Lecture et écriture du fichier de données
- **pathlib** - Gestion moderne des chemins de fichiers
- **datetime** - Génération automatique des horodatages
- **getpass** - Récupération du nom d'utilisateur système
- **collections.defaultdict** - Groupement efficace des notes par catégorie
- **os** - Accès aux variables d'environnement

---

## Déploiement

### Distribution (Python)

Le projet utilise **`pyproject.toml`** moderne :
- Point d'entrée CLI : `note` → `note.cli:main`
- Installation via `pipx install -e .` crée la commande globale

### Conteneurisation (Docker)

- **Base** : `python:3.12-slim`
- **Volume** : `/data` pour persister les notes
- **Entrée** : `docker compose` simplifie l'utilisation

---

## Prochaine étape

- [Guide d'utilisation](utilisation.md)
- [Dockerisation](docker.md)
- [CI/CD & Tests](actions.md)