---
title: Démarrage rapide
icon: lucide/zap
---

# Démarrage rapide

> Installez et utilisez NoteMaker rapidement.

---

## Installation

### Avec pipx

`pipx install -e .`

### Avec Docker

`echo 'alias note="docker compose -f docker/compose.yaml run --rm note-maker"' >> ~/.bashrc && source ~/.bashrc`

Pour une configuration complète (Bash/Zsh/détails), voir [Dockerisation](docker.md).

---

## Premières commandes

**Créer une note**

`note add "Ma première note"`

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
