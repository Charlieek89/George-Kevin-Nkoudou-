# Application de tontine (mobile + dashboard web)

Ce dépôt contient une base de conception pour une **application de tontine sécurisée**, avec :

- une application mobile (Android/iOS) pour les membres ;
- un dashboard web pour les administrateurs/superviseurs ;
- l’intégration des paiements **WAVE Mobile Money** et **carte bancaire** ;
- une architecture orientée sécurité, auditabilité et conformité.

## Objectifs produit

- Créer et gérer des tontines (groupes, règles, cycles, montants, tours).
- Permettre les cotisations, retraits/payouts et suivis de pénalités.
- Offrir la transparence : journal d’événements, historiques, preuves de paiement.
- Réduire les risques de fraude grâce à la sécurité applicative et opérationnelle.

## Portée fonctionnelle

### Côté mobile (membre)

- Inscription/connexion sécurisée + KYC.
- Création et adhésion à une tontine.
- Paiement des cotisations (WAVE, carte bancaire).
- Notifications (rappels, retards, attribution du tour).
- Historique personnel et statut en temps réel.

### Côté dashboard web (admin/super admin)

- Gestion des utilisateurs et niveaux de rôles.
- Paramétrage des tontines (fréquence, ordre des tours, pénalités, plafond).
- Vue consolidée des paiements, incidents et rapprochements.
- Validation/gestion des litiges et export des rapports.

## Documents de référence du projet

- [PRD / Spécification fonctionnelle](docs/PRODUCT_REQUIREMENTS.md)
- [Architecture technique](docs/ARCHITECTURE.md)
- [Sécurité & conformité](docs/SECURITY.md)
- [Plan d’implémentation](docs/IMPLEMENTATION_PLAN.md)

## Proposition de stack

- **Mobile** : Flutter (ou React Native).
- **Web dashboard** : Next.js + TypeScript.
- **Backend API** : NestJS (TypeScript).
- **Base de données** : PostgreSQL.
- **Cache/queue** : Redis + BullMQ.
- **Stockage** : S3-compatible pour pièces KYC et justificatifs.
- **Observabilité** : OpenTelemetry + Grafana/Loki/Prometheus.
- **CI/CD** : GitHub Actions.

## Prochaines étapes

1. Valider les exigences métier (règles tontine par pays/zone).
2. Valider les partenariats paiement (WAVE + PSP carte bancaire).
3. Lancer un MVP avec parcours complet : création de tontine, cotisation, attribution, audit.
4. Effectuer des tests de sécurité (SAST/DAST/pentest) avant production.
