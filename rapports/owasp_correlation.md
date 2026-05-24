# Corrélation OWASP Mobile Top 10 — InsecureBankv2

| OWASP ID | Catégorie | Trouvaille | Outil | Sévérité |
|----------|-----------|------------|-------|----------|
| M1 | Improper Credential Usage | Shared Preferences sensibles | BeVigil | 🔴 Critique |
| M1 | Improper Credential Usage | Sensitive Info in Logs | BeVigil | 🟠 Moyen |
| M2 | Inadequate Supply Chain | Weak Hash MD5/SHA1 | Yaazhini | 🟠 Moyen |
| M2 | Inadequate Supply Chain | Insecure Signature SHA1withRSA | Yaazhini | 🟠 Moyen |
| M3 | Insecure Authentication | LoginActivity exportée | Yaazhini | 🔴 Critique |
| M3 | Insecure Authentication | DoLogin/DoTransfer exposés | Yaazhini | 🔴 Critique |
| M5 | Insecure Communication | Insecure Communication x36 | Yaazhini | 🔴 Critique |
| M5 | Insecure Communication | URLs HTTP non chiffrées | Yaazhini | 🔴 Critique |
| M5 | Insecure Communication | Insecure HTTP Client | BeVigil | 🔴 Critique |
| M6 | Inadequate Privacy Controls | SEND_SMS | Yaazhini | 🔴 Critique |
| M6 | Inadequate Privacy Controls | READ_CALL_LOG | Yaazhini | 🔴 Critique |
| M6 | Inadequate Privacy Controls | READ_PHONE_STATE | Yaazhini | 🔴 Critique |
| M6 | Inadequate Privacy Controls | READ_CONTACTS/READ_PROFILE | Yaazhini | 🟠 Moyen |
| M8 | Security Misconfiguration | Android Debuggable Enabled | Yaazhini | 🟠 Moyen |
| M8 | Security Misconfiguration | Android Backup Enabled | Yaazhini | 🟠 Moyen |
| M8 | Security Misconfiguration | MyBroadCastReceiver exported=true | Yaazhini | 🔴 Critique |
| M8 | Security Misconfiguration | Javascript enabled in WebView | Yaazhini | 🟡 Low |
| M9 | Insecure Data Storage | Android External Storage x13 | Yaazhini | 🟠 Moyen |
| M9 | Insecure Data Storage | Shared Preferences non chiffrées | BeVigil | 🔴 Critique |

## Résumé par catégorie OWASP
| OWASP ID | Nb Findings | Sévérité Max |
|----------|-------------|--------------|
| M1 | 2 | 🔴 Critique |
| M2 | 2 | 🟠 Moyen |
| M3 | 2 | 🔴 Critique |
| M5 | 3 | 🔴 Critique |
| M6 | 4 | 🔴 Critique |
| M8 | 4 | 🔴 Critique |
| M9 | 2 | 🔴 Critique |
