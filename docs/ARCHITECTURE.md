# Architecture technique cible

## 1. Vue d’ensemble

Architecture en services modulaires :

- **clients** : app mobile + dashboard web ;
- **API Gateway** : routage, auth, rate limiting ;
- **services métier** : users, tontines, payments, notifications, reporting ;
- **données** : PostgreSQL, Redis, stockage objet ;
- **intégrations externes** : WAVE API, PSP carte bancaire, service SMS/email.

## 2. Domaines backend recommandés

1. **Identity Service** : auth, sessions, MFA, gestion des rôles.
2. **KYC Service** : collecte pièces, statut validation, scoring risque.
3. **Tontine Service** : logique métier (groupes, cycles, tours, règles).
4. **Payment Service** : orchestration WAVE/carte, webhooks, rapprochement.
5. **Ledger Service** : grand livre immuable (double entrée simplifiée).
6. **Notification Service** : push, SMS, email, templates.
7. **Admin Service** : supervision, litiges, flags anti-fraude.

## 3. Principes techniques

- API REST pour exposition client, événements asynchrones pour traitements lents.
- Idempotence sur toutes opérations de paiement.
- Transaction atomique entre validation de paiement et écriture ledger.
- Horodatage normalisé UTC et identifiants corrélés pour traçage.

## 4. Modèle de données (noyau)

- `users`
- `kyc_profiles`
- `tontines`
- `tontine_members`
- `contribution_schedules`
- `payments`
- `payouts`
- `ledger_entries`
- `audit_events`
- `disputes`

## 5. Flux paiement (résumé)

1. Le client initie un paiement de cotisation.
2. `Payment Service` crée une transaction `PENDING` avec clé idempotente.
3. Redirection/confirmation PSP (WAVE ou carte).
4. Réception webhook signé.
5. Vérification signature + montant + devise + état transaction.
6. Passage `SUCCESS`, écriture ledger, mise à jour cycle tontine.
7. Émission d’événements (notification, reporting, anti-fraude).

## 6. Déploiement

- Conteneurs (Docker) orchestrés (Kubernetes managé recommandé).
- Environnements séparés : dev / staging / prod.
- Stratégie blue-green ou canary pour les services critiques.
