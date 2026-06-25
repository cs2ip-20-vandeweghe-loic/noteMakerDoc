---
title: Guide d'utilisation
icon: lucide/book-open
---

# Guide d'utilisation

> Découvrez toutes les commandes de NoteMaker et apprenez à gérer efficacement vos notes en ligne de commande.

---

## Ajouter une note

### Syntaxe

`note add [contenu] [catégorie]`

### Utilisation

**Mode interactif** : 

Exécutez simplement la commande sans ajouter de paramètres :

`note add`

L'application vous demandera d'entrer le contenu de votre note et la catégorie.

**Mode direct** : 

Ajoutez directement une note avec son contenu :

`note add "Acheter du pain"`

**Avec catégorie** : 

Organisez vos notes par catégorie :

`note add "Réunion projet à 14h" travail`

### Informations enregistrées

Chaque note enregistre automatiquement :

- Un **ID unique** (incrémenté)
- Un **auteur** (nom d'utilisateur système)
- Une **date de création** (horodatage)
- Une **catégorie** (par défaut : "general")

---

## Afficher les notes

### Syntaxe

`note list [id]`

### Utilisation

**Toutes les notes** : 

Affiche l'ensemble de vos notes groupées par catégorie :

`note list`

**Exemple de sortie** :

```bash
travail

\[1] Réunion projet à 14h
(johndoe - 2026-06-25T10:30:00)
\[3] Appeler le client
(johndoe - 2026-06-25T11:15:00)

general

\[2] Acheter du pain
(johndoe - 2026-06-25T10:45:00)
```

**Une note spécifique** : 

Consultez les détails d'une note par son ID :

`note list 2`

---

## Supprimer des notes

### Syntaxe

`note delete [id|all]`

### Utilisation

**Mode interactif** : 

La commande vous demande l'ID à supprimer :

`note delete`

**Supprimer une note précise** : 

Indiquez directement l'ID :

`note delete 3`

**Tout supprimer** : 

Effacez toutes vos notes d'un coup :

`note delete all`

!!! warning "Attention"
    La suppression est **définitive** et irréversible !

---

## Exporter les notes

### Syntaxe

`note export markdown`

### Utilisation

Exportez vos notes dans des fichiers Markdown organisés par catégorie :

`note export markdown`

---

## Récapitulatif des commandes

| Commande | Description | Exemple |
|----------|-------------|---------|
| `note add [texte] [cat]` | Ajouter une note | `note add "Rendez-vous 15h" perso` |
| `note list [id]` | Lister les notes | `note list` ou `note list 3` |
| `note delete [id/all]` | Supprimer des notes | `note delete 5` ou `note delete all` |
| `note export markdown` | Exporter en Markdown | `note export markdown` |

---

## Prochaine étape

Découvrez comment fonctionne NoteMaker en interne dans l'onglet [Architecture technique](architecture.md).