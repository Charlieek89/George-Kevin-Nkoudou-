# Product Requirements Document (PRD) — Application de tontine

## 1. Vision

Construire une plateforme fiable de tontine digitale qui permet d’organiser des cycles d’épargne communautaire avec traçabilité complète des contributions et distributions.

## 2. Personae

- **Membre** : cotise périodiquement et reçoit la cagnotte à son tour.
- **Responsable de tontine** : crée la tontine et gère les paramètres.
- **Administrateur plateforme** : supervise la conformité, les paiements, les incidents.

## 3. Exigences fonctionnelles principales

1. Authentification sécurisée (email/téléphone + OTP + 2FA optionnelle).
2. KYC (niveau configurable selon plafond et réglementation locale).
3. Création de tontine :
   - nom, devise, fréquence (hebdo/mensuelle),
   - montant de cotisation,
   - nombre de membres,
   - mode d’attribution du tour (tirage, manuel, enchère optionnelle).
4. Gestion des cycles : ouverture, clôture, reporting.
5. Paiement cotisation :
   - WAVE Mobile Money,
   - carte bancaire (PSP partenaire),
   - suivi des callbacks/webhooks de paiement.
6. Distribution/payout au bénéficiaire du tour.
7. Gestion des retards : pénalité, grâce, exclusion.
8. Litiges : ouverture ticket, médiation admin, preuves.
9. Notifications push/SMS/email.
10. Rapports : journal, export CSV/PDF, rapprochement comptable.

## 4. Exigences non fonctionnelles

- Disponibilité cible : 99,9%.
- Performances API : p95 < 500 ms sur endpoints critiques hors PSP.
- Auditabilité : chaque action critique est journalisée (acteur, horodatage, contexte).
- Sécurité : chiffrement au repos et en transit, RBAC strict, secrets vaultés.
- Scalabilité : architecture modulaire supportant montée en charge multi-pays.

## 5. Critères MVP

- Onboarding complet membre.
- Création + adhésion tontine.
- Cotisation via WAVE + carte.
- Attribution d’un tour et distribution simulée/réelle.
- Dashboard de suivi admin.
- Journal d’audit exploitable.
