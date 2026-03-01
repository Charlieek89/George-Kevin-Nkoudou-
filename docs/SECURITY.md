# Sécurité & conformité

## 1. Contrôles essentiels

- Chiffrement TLS 1.2+ en transit.
- Chiffrement AES-256 au repos (DB + sauvegardes + stockage objet).
- Hash de mots de passe Argon2id.
- Rotation des secrets via coffre (Vault/Secrets Manager).
- RBAC avec principe du moindre privilège.
- 2FA recommandé pour rôles à privilèges.

## 2. Sécurité paiements

- Vérification stricte des signatures webhook (WAVE/PSP).
- Idempotence (clé unique par tentative logique).
- Anti-rejeu (nonce/timestamp + fenêtre de validité).
- Ledger immuable pour audit financier.
- Règles anti-fraude (seuils, vitesse, incohérences device/IP).

## 3. Sécurité applicative

- Validation forte des entrées (schémas DTO).
- Protection CSRF (web), protections XSS/SQLi via frameworks et ORM.
- Limitation de débit (rate limiting) par utilisateur/IP.
- Journalisation sécurisée sans données sensibles en clair.
- Revue de dépendances (SCA) et patching régulier.

## 4. Gouvernance et conformité

- Politique de conservation des données et droit à l’effacement.
- Traçabilité des consentements utilisateurs.
- Procédure de réponse à incident (runbook + SLA).
- Sauvegardes testées avec simulations de restauration.

## 5. Validation avant production

- SAST + DAST en CI.
- Pentest externe.
- Revue d’architecture de sécurité.
- Exercices PRA/PCA.
