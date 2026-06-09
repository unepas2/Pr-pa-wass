# Carnet d'éveil — Bilan développemental indicatif (3–12 mois)

Application web autonome (un seul `index.html`, sans dépendance) pour **estimer et
suivre le développement de bébé** entre 3 et 12 mois.

## Fonctionnement

### Le bilan, en deux phases
1. **Estimation « à l'aveugle »** — un questionnaire adaptatif (motricité globale,
   motricité fine, langage & communication, compréhension & exploration,
   interactions sociales & émotionnelles) estime l'âge développemental probable
   **sans connaître l'âge réel** : âge estimé, fourchette, score de confiance,
   profil par domaine.
2. **Comparaison avec l'âge réel** — saisie de l'âge réel (+ prématurité et âge
   corrigé). L'application produit un **bilan personnalisé** : indice de cohérence,
   classification du profil, conclusion en langage naturel, forces, points à
   observer, activités conseillées et recommandation.

### Le carnet de suivi
- **Profils enfants** (prénom ou pseudo, avatar, plusieurs enfants possibles).
- **Date de naissance optionnelle** : l'âge est calculé automatiquement à chaque bilan.
- **Historique** des bilans, consultables à tout moment.
- **Courbes d'évolution** lissées (âge estimé vs âge de référence, et par domaine).
- **Commentaires automatiques de progrès** : ce qui s'améliore, ce qui reste
  stable, ce qui est à surveiller, d'un bilan à l'autre.
- **Reprise automatique** : un bilan interrompu se reprend là où on s'était arrêté.
- **Écran de vérification** avant le résultat (préciser les « je ne sais pas »).

### Comptes et synchronisation (optionnel)
- Par défaut : **mode local**, tout reste sur l'appareil (aucun envoi sur Internet).
- En option : **connexion Google + synchronisation cloud** via Firebase, pour
  retrouver son historique sur tous ses appareils. Voir **[SETUP-FIREBASE.md](SETUP-FIREBASE.md)**.

## Utilisation
Ouvrez `index.html` dans un navigateur, ou publiez le dépôt via **GitHub Pages**.
Le fichier est entièrement autonome (aucun serveur requis en mode local).

## Design & accessibilité
- Interface moderne mobile-first : barre supérieure « verre dépoli », dégradés
  doux, animations légères, **mode sombre automatique** (selon le réglage du
  téléphone), retour visuel au toucher.
- Navigation au clavier, éléments interactifs natifs (`<button>`), focus visible,
  respect de `prefers-reduced-motion`.

## Avertissement
Outil **indicatif et non médical**. Il ne pose **aucun diagnostic** et ne conclut
jamais à une pathologie. En cas de doute, parlez-en à un pédiatre, un médecin ou
une PMI.
