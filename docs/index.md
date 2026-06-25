---
title: Introduction
icon: lucide/rocket
---

# Bienvenue sur NoteMaker ! 

> Une application CLI simple et efficace pour gérer vos notes en ligne de commande.

## Qu'est-ce que NoteMaker ?

NoteMaker est un outil en ligne de commande développé en **Python** qui permet de créer, consulter et supprimer des notes rapidement directement depuis un terminal.

---

## Les fonctionnalités principales 

| Commande | Description | Exemple |
|----------|-------------|---------|
| `note add` | Ajouter une nouvelle note | `note add "Acheter du lait"` |
| `note list` | Afficher toutes vos notes | `note list` |
| `note delete` | Supprimer une note | `note delete 1` |
| `note export` | Exporter les notes en Markdown | `note export markdown` |

---

## Pourquoi NoteMaker ?

- **Rapidité** : vous pouvez ajouter une note en une seule commande
- **Légèreté** : aucune dépendance externe complexe n'est nécessaire
- **Simplicité** : le stockage est local en JSON
- **CLI** : les commandes en CLI sont parfaites pour l'utilisation dans le terminal
- **Portablilité** : NoteMaker est disponible via Docker ou installation classique

--- 

## Technologies

- **Python 3.8+** - Langage de développement
- **argparse** - Gestion des commandes CLI
- **JSON** - Stockage des données
- **Docker** - Déploiement conteneurisé
- **GitHub Actions** - CI/CD automatisé

---

## Prêt à commencer ?

Choisissez votre mode d'installation :

| **Démarrage rapide** | **Installation classique** | **Docker (Rapide)** |
|-----|-----|-----|
| Découvrez les commandes essentielles | Installez Python et pipx, puis démarrez localement | Utilisez Docker sans installation Python |
| [Démarrage rapide](demarrage.md) | [Guide d'installation](installation.md) | [Guide Docker](docker.md) |