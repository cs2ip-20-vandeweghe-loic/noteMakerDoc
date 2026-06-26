---
title: Dockerisation
icon: lucide/server
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

!!! note "Installation dockerisée"

    Vous pouvez télécharger le container via la commande ci-dessous :

    ```
    docker pull ghcr.io/cs2ip-20-vandeweghe-loic/note-maker:main

    docker run note-maker
    ```

    Si vous préférez télécharger manuellement le dépot, veuillez suivre les étapes suivantes :

    ```
    1. git pull https://github.com/cs2ip-20-vandeweghe-loic/noteMakerPy/tree/main

    2. cd ./docker

    3. sudo docker compose up -d
    ```


---

## Configuration du script bash

Pour utiliser NoteMaker simplement avec la commande `note`, créez un script bash.

### Étape 1 - Créer le script

Créez un fichier `note` contenant :

```bash
#!/bin/sh

mkdir -p "$HOME/.note-maker"

docker run --rm \
    -v "$HOME/.note-maker:/data" \
    -e NOTES_DB=/data/.notes.json \
    -e NOTES_EXPORT_DIR=/data/notes \
    note-maker "$@"
```

### Étape 2 - Rendre le script exécutable

```
chmod +x note
```

### Étape 3 - Installer le script

```
mkdir -p ~/.local/bin
mv note ~/.local/bin/
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

Les données sont automatiquement sauvegardées dans **`~/.note-maker/`** :

- **Base de données** : `~/.note-maker/.notes.json`

- **Exports Markdown** : `~/.note-maker/notes/`

Vos notes persistent entre chaque utilisation grâce au volume Docker.

---

## Variables d'environnement

Le script bash définit automatiquement :

| Variable | Valeur | Description |
|----------|--------|-------------|
| `NOTES_DB` | `/data/.notes.json` | Fichier de base de données |
| `NOTES_EXPORT_DIR` | `/data/notes` | Dossier d'export Markdown |

Vous pouvez les modifier dans le script `~/.local/bin/note` si nécessaire.

---

## Workflow complet

### Configuration initiale (une fois)

Voir la section [Configuration du script bash](#configuration-du-script-bash) ci-dessus.

### Utilisation quotidienne

Voir la section [Commandes disponibles](#commandes-disponibles) ci-dessus.

**Aucune différence avec une installation classique.**

---

## Vérification

Pour tester que tout fonctionne :

**1. Créer une note de test**

`note add "Test Docker"`

**2. Vérifier qu'elle apparaît**

`note list`

**3. Consulter le fichier de données**

`cat ~/.note-maker/.notes.json`

Si vous voyez votre note en JSON, tout est opérationnel.

---

!!! info "Astuce : vérifier le script"
    Tapez : `which note`
    
    Résultat attendu :
    ```
    /home/<user>/.local/bin/note
    ```

---

## Commandes utiles

**Mettre à jour l'image**

`docker pull ghcr.io/cs2ip-20-vandeweghe-loic/note-maker:main`

**Supprimer l'image locale**

`docker rmi note-maker`

**Supprimer toutes les données**

`rm -rf ~/.note-maker`

!!! warning "Attention"
    La dernière commande **supprime définitivement toutes vos notes** : utilisez-la avec précaution.

---

## Conclusion

La dockerisation de NoteMaker est complète et opérationnelle.

---

## Prochaine étape

- [Guide d'utilisation](utilisation.md)
- [Architecture technique](architecture.md)
- [CI/CD & Tests](actions.md)