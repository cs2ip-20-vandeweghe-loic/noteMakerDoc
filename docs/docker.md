---
title: Dockerisation
icon: lucide/container
---

# Dockerisation

> Utilisez NoteMaker via Docker sans installer Python sur votre machine.

---

## Principe

Docker permet d'**exécuter NoteMaker depuis votre poste de travail** sans installer Python ni pipx.

**Avantages** :

- Aucune installation Python nécessaire
- Environnement isolé et reproductible
- Données persistantes via volumes
- Configuration via variables d'environnement

---

## Prérequis

**Docker** doit être installé sur votre poste : [Documentation officielle](https://docs.docker.com/get-docker/)

**Vérification** : `docker --version`

---

## Utilisation avec Docker Compose

Le projet inclut un fichier **`docker/compose.yaml`** prêt à l'emploi.

### Configuration de l'alias

Pour simplifier l'utilisation, créez un **alias** dans votre shell.

**Bash** - Ajoutez dans `~/.bashrc` :

```bash
echo 'alias note="docker compose -f docker/compose.yaml run --rm note-maker"' >> ~/.bashrc
source ~/.bashrc
```

**Zsh** - Ajoutez dans `~/.zshrc` :

```bash
echo 'alias note="docker compose -f docker/compose.yaml run --rm note-maker"' >> ~/.zshrc
source ~/.zshrc
```

---

## Commandes disponibles

Une fois l'alias configuré, utilisez NoteMaker normalement :

### Ajouter une note

`note add "Acheter du lait"`

Avec catégorie : `note add "Réunion 14h" travail`

### Lister les notes

Toutes : `note list`

Une seule : `note list 1`

### Supprimer des notes

Une note : `note delete 1`

Toutes : `note delete all`

### Exporter en Markdown

`note export markdown`

---

## Où sont stockées vos notes ?

Les données sont automatiquement sauvegardées dans le dossier **`notes-data/`** à la racine du projet :

- **Base de données** : `notes-data/.notes.json`

- **Exports Markdown** : `notes-data/notes/`

Vos notes persistent entre chaque utilisation grâce au volume Docker.

---

## Variables d'environnement

Le fichier `docker/compose.yaml` définit automatiquement :

| Variable | Valeur | Description |
|----------|--------|-------------|
| `NOTES_DB` | `/data/.notes.json` | Fichier de base de données |
| `NOTES_EXPORT_DIR` | `/data/notes` | Dossier d'export Markdown |
| `PYTHONUNBUFFERED` | `1` | Logs en temps réel |

Vous pouvez les modifier dans le fichier `docker/compose.yaml` si nécessaire.

---

## Workflow complet

### Configuration initiale (une fois)

**Étape 1** - Créer l'alias

Pour Bash : 

`echo 'alias note="docker compose -f docker/compose.yaml run --rm note-maker"' >> ~/.bashrc`

Pour Zsh : 

`echo 'alias note="docker compose -f docker/compose.yaml run --rm note-maker"' >> ~/.zshrc`

**Étape 2** - Activer l'alias

`source ~/.bashrc` ou `source ~/.zshrc`

**Étape 3** - Construire l'image

`docker compose -f docker/compose.yaml build`

### Utilisation quotidienne

Ensuite, utilisez simplement :

- `note add "Ma tâche"`
- `note list`
- `note delete 1`
- `note export markdown`

**Aucune différence avec une installation classique.**

---

## Vérification

Pour tester que tout fonctionne :

**1. Créer une note de test**

`note add "Test Docker"`

**2. Vérifier qu'elle apparaît**

`note list`

**3. Consulter le fichier de données**

`cat notes-data/.notes.json`

Si vous voyez votre note en JSON, tout est opérationnel.

---

!!! info "Astuce : vérifier l'alias"
    Tapez : `type note`
    
    Résultat attendu :
    ```
    note is aliased to 'docker compose -f docker/compose.yaml run --rm note-maker'
    ```

---

## Commandes utiles

### Construction et nettoyage

**Construire l'image manuellement**

`docker compose -f docker/compose.yaml build`

**Supprimer le conteneur**

`docker compose -f docker/compose.yaml down`

**Nettoyer tout**

`docker compose -f docker/compose.yaml down --volumes`

!!! warning "Attention"
    La dernière commande **supprime vos notes** : utilisez cette commande avec précaution.

---

## Conclusion

La dockerisation de NoteMaker est complète et opérationnelle.

---

## Prochaine étape

- [Guide d'utilisation](utilisation.md)
- [Architecture technique](architecture.md)
- [CI/CD & Tests](actions.md)