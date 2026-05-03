# Audit rapide UX/UI — reconnaissance-p

## Constat projet
Le dépôt contient une application React (dans `import React.docx`) orientée mobile avec 3 vues principales :
- **Scanner** (caméra + reconnaissance IA),
- **Catalogue**,
- **Ajout produit**.

## 3 améliorations prioritaires

### 1) Ajouter un vrai flux d’onboarding caméra + états d’erreur actionnables
**Problème observé :** la caméra démarre directement et affiche un message d’erreur générique en cas d’échec. L’utilisateur n’est pas guidé (permissions refusées, appareil non compatible, connexion lente, etc.).

**Amélioration proposée :**
- Écran d’introduction avant activation caméra : “Pourquoi on demande l’accès ?” + bouton “Activer la caméra”.
- Messages d’erreurs contextualisés + actions :
  - permission refusée → “Ouvrir les réglages”,
  - caméra indisponible → “Réessayer”,
  - hors-ligne → “Passer en mode saisie manuelle”.
- État intermédiaire visuel pendant l’analyse (squelette + temps estimé).

**Impact UX attendu :** baisse de l’abandon au premier usage, sentiment de contrôle et réduction de la frustration.

---

### 2) Rendre le résultat de scan exploitable en 1 clic (au lieu d’un simple verdict)
**Problème observé :** le résultat est surtout binaire (reconnu / non reconnu). Peu d’actions immédiates sont proposées pour poursuivre le parcours.

**Amélioration proposée :**
- Sur succès : carte produit avec actions rapides (**Modifier prix**, **Ajuster stock**, **Voir historique**).
- Sur “non reconnu” : proposer directement **Créer ce produit** avec photo préremplie + nom suggéré.
- Ajouter une zone “Derniers scans” pour éviter de rescanner le même article.

**Impact UX attendu :** réduction du nombre d’étapes, gain de temps opérationnel, meilleure continuité du workflow de caisse.

---

### 3) Refonte visuelle légère pour lisibilité et hiérarchie mobile
**Problème observé :** l’interface est fonctionnelle mais manque de hiérarchie visuelle et de repères (couleurs d’état, densité d’info, feedback tactiles).

**Amélioration proposée :**
- Définir des tokens UI simples :
  - 1 couleur primaire, 1 couleur succès, 1 couleur erreur,
  - échelle d’espacement cohérente (8px),
  - tailles de typo standardisées.
- Renforcer la navigation basse : labels plus explicites, zone tactile plus large, état actif plus contrasté.
- Uniformiser les composants “cartes produit” (nom, prix, stock, statut) avec badges visuels.

**Impact UX attendu :** meilleure lisibilité en situation réelle (mouvement, lumière variable), perception plus professionnelle, apprentissage plus rapide de l’app.

## Ordre recommandé d’implémentation (2 semaines)
1. **Semaine 1** : onboarding caméra + gestion erreurs actionnables.
2. **Semaine 1-2** : écran résultat avec actions rapides.
3. **Semaine 2** : harmonisation design system mobile (tokens + composants).
