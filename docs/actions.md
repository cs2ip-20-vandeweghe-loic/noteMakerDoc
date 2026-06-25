---
title: CI/CD
icon: lucide/infinity
---

# CI/CD avec GitHub Actions

> NoteMaker intègre des **tests automatisés** qui s'exécutent à chaque modification du code.

---

## Comment ça fonctionne ?

Le fichier **`.github/workflows/ci.yml`** définit le pipeline de tests automatiques.

### Déclenchement

Les tests se lancent automatiquement :
- À chaque **push** sur `main`
- À chaque **pull request**

---

## Tests exécutés

### Test 1 : Package Python

**Environnement** : Ubuntu + Python 3.12

**Étapes** :

1. Checkout du code
2. Installation de Python
3. Installation du package : `pip install -e .`
4. Vérification de l'aide : `note --help`

Test du workflow complet :

- `note add "github test"`
- `note list`
- `note delete all`

### Test 2 : Image Docker

**Étapes** :

1. Checkout du code
2. Construction de l'image : `docker build -f docker/Dockerfile -t note-cli .`

---

## Consulter les résultats

Sur GitHub, onglet **Actions** :

- Historique de tous les tests
- Statut : passing ou failing
- Logs détaillés pour chaque étape

---

## Résultat

Chaque modification est **automatiquement testée** avant d'être acceptée dans le projet.

Si les tests passent : le code est validé

Si les tests échouent : alerte pour corriger

---

Le projet est testé en continu pour garantir sa qualité.

---

## Prochaine étape

- [Dockerisation](docker.md)
- [Guide d'utilisation](utilisation.md)