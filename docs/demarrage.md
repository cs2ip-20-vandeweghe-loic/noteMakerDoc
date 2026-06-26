---
title: Démarrage rapide
icon: lucide/zap
---

# Démarrage rapide

> Installez et utilisez NoteMaker rapidement.

---

## Prérequis

Avant d'installer NoteMaker, assurez-vous d'avoir les éléments suivants :

| Élément | Version minimale | Vérification |
|---------|------------------|--------------|
| **Python** | 3.8 ou supérieur | `python --version` |
| **pipx** | Dernière version | `pipx --version` |

!!! note "Installations Python et `pipx` :"
    - Pour installer Python, consultez la [documentation officielle de Python](https://www.python.org/downloads/).
    - Si `pipx` n'est pas installé, consultez la [documentation officielle](https://pipx.pypa.io/stable/installation/).

---

## Installation

### Avec pipx

`pipx install -e .`

### Avec Docker

Consultez l'onglet [Dockerisation](docker.md).

---

## Premières commandes

**Créer une note**

`note add [contenu] [catégorie]`

**Voir vos notes**

`note list`

**Supprimer une note**

`note delete 1`

**Exporter en Markdown**

`note export markdown`

---

## Où sont vos notes ?

- **pipx** : Stockées localement dans `~/.notes.json`
- **Docker** : Stockées dans `notes-data/.notes.json` (au niveau du projet)

---

## Prochaine étape

- [Installation complète](installation.md)
- [Guide d'utilisation](utilisation.md)
- [Docker](docker.md)
