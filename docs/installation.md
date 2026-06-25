---
title: Guide d'installation
icon: lucide/arrow-down-to-line
---

# Guide d'installation

> Installez NoteMaker en quelques minutes et commencez à gérer vos notes directement depuis votre terminal.

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

### Étape 1 : Cloner le projet

Téléchargez ou clonez le dépôt NoteMaker sur votre machine locale.

```bash
git clone <url-du-repo>
cd noteMakerPy
```

### Étape 2 : Installer avec pipx

Exécutez la commande suivante dans le répertoire du projet :

`pipx install -e .`

**Que fait cette commande ?**

- L'option `-e` installe le projet en mode **éditable**
- L'application devient disponible **globalement** via la commande `note`

### Étape 3 : Vérifier l'installation

Testez que l'installation a fonctionné en affichant l'aide :

`note --help`

Vous devriez voir la liste des commandes disponibles s'afficher.

---

## Mise à jour

Si vous modifiez le code source, mettez à jour l'installation avec :

`pipx upgrade note`

---

## Premier test

Créez votre première note pour vérifier le bon fonctionnement :

1. **Ajouter une note** : `note add "Ma première note"`
2. **Afficher vos notes** : `note list`

Si vous voyez votre note s'afficher, votre NoteMaker est correctement installé.

---

## Emplacement des données

Les notes sont automatiquement stockées dans le fichier :

**`~/.notes.json`**

Ce fichier JSON est créé lors de l'ajout de votre première note.

---

## Alternative : Installation Docker

Si vous préférez utiliser Docker, consultez l'onglet [Dockerisation](docker.md) pour une installation sans Python.

---

## Prochaine étape

Découvrez toutes les commandes dans le [Guide d'utilisation](utilisation.md).