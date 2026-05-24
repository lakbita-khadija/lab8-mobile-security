# RAPPORT D'ANALYSE — Posture et Exposition Mobile
**Application :** InsecureBankv2  
**Package :** com.android.insecurebankv2  
**Version :** 1.0  
**Analyste :** LAKBITA KHADIJA  
**Date :** 2026-05-24  
**Cours :** Sécurité des applications mobiles — LAB 8  
**Cadre :** Pédagogique uniquement  

---

## 1. Résumé exécutif

L'analyse statique de InsecureBankv2 a révélé **19 vulnérabilités**
dont **10 critiques** et **7 moyennes**.
Les risques majeurs concernent les communications non chiffrées (36 occurrences),
les permissions dangereuses, les composants Android exposés,
et le stockage non sécurisé de données sensibles.

**Score BeVigil : 7.4/10 — AVERAGE ⚠️**

---

## 2. Méthodologie

| Outil | Rôle | Type |
|-------|------|------|
| BeVigil (CloudSEK) | OSINT mobile en ligne | Passive / Black-box |
| Yaazhini (VegaBird) | Scanner statique local | Static / White-box |

---

## 3. Findings BeVigil

| # | Vulnérabilité | Sévérité | Impact |
|---|---------------|----------|--------|
| 1 | Shared Preferences sensibles | 🔴 LOW | 91% |
| 2 | Sensitive Information in Logs | 🟠 LOW | 7.2% |
| 3 | Exported Activity | 🟠 LOW | 1% |
| 4 | Possible Secret Detected | 🟠 LOW | 0.5% |
| 5 | Insecure HTTP Client | 🔴 LOW | 0.3% |

**Permissions :** Safe: 2 | Risky: 5 | Dangerous: 0  
**Trackers :** Google AdMob, Google Analytics, Google Tag Manager  
**Librairies tierces :** 15  

---

## 4. Findings Yaazhini

### Vulnérabilités
| Sévérité | Vulnérabilité | Occurrences |
|----------|---------------|-------------|
| 🔴 HIGH | Insecure Communication | 36 |
| 🟠 MEDIUM | Android Debuggable Enabled | 1 |
| 🟠 MEDIUM | Android Backup Vulnerability | 1 |
| 🟠 MEDIUM | Improper Export of Providers | 1 |
| 🟠 MEDIUM | Improper Export of Receivers | 1 |
| 🟠 MEDIUM | Use of Insufficiently Random Values | 3 |
| 🟠 MEDIUM | Insecure Signature SHA1withRSA | 1 |
| 🟠 MEDIUM | Weak Hash MD5 | 4 |
| 🟠 MEDIUM | Weak Hash SHA-1 | 1 |
| 🟡 LOW | Javascript Enabled in WebView | 3 |
| ⚠️ WARNING | Android External Storage | 13 |
| ℹ️ INFO | Missing Copy/Paste Protection | 9 |
| ℹ️ INFO | Missing Screenshot Protection | 10 |

### Permissions dangereuses
| Permission | Risque |
|------------|--------|
| SEND_SMS | 🔴 Critique |
| READ_CALL_LOG | 🔴 Critique |
| READ_PHONE_STATE | 🔴 Critique |
| READ_PROFILE | 🔴 Critique |
| READ_CONTACTS | 🟠 Moyen |
| ACCESS_COARSE_LOCATION | 🟠 Moyen |

### Composants exposés
| Composant | Type | Exported | Risque |
|-----------|------|----------|--------|
| MyBroadCastReceiver | Receiver | true | 🔴 Critique |
| LoginActivity | Activity | true | 🔴 Critique |
| DoTransfer | Activity | true | 🔴 Critique |
| ChangePassword | Activity | true | 🔴 Critique |

---

## 5. Corrélation OWASP Mobile Top 10

| OWASP ID | Catégorie | Nb Findings | Sévérité |
|----------|-----------|-------------|----------|
| M1 | Improper Credential Usage | 2 | 🔴 Critique |
| M2 | Inadequate Supply Chain | 2 | 🟠 Moyen |
| M3 | Insecure Authentication | 2 | 🔴 Critique |
| M5 | Insecure Communication | 3 | 🔴 Critique |
| M6 | Inadequate Privacy Controls | 4 | 🔴 Critique |
| M8 | Security Misconfiguration | 4 | 🔴 Critique |
| M9 | Insecure Data Storage | 2 | 🔴 Critique |

---

## 6. Recommandations

### 🔴 Priorité 1 — Critique
1. **Forcer HTTPS** sur toutes les communications + Certificate Pinning
2. **Désactiver android:debuggable** en production
3. **Protéger MyBroadCastReceiver** → exported=false
4. **Chiffrer les SharedPreferences** → EncryptedSharedPreferences
5. **Supprimer permissions inutiles** → SEND_SMS, READ_CALL_LOG

### 🟠 Priorité 2 — Moyen
6. **Remplacer MD5/SHA1** par SHA-256 minimum
7. **Désactiver android:allowBackup=false**
8. **Désactiver Javascript dans WebView** si non nécessaire

### 🟡 Priorité 3 — Low
9. **Ajouter protection copy/paste** sur les champs sensibles
10. **Bloquer les screenshots** sur les écrans sensibles

---

## 7. Conclusion

InsecureBankv2 présente une surface d'attaque très large avec
des vecteurs critiques facilement exploitables notamment
les 36 communications non chiffrées et les composants Android
exportés sans protection. L'application nécessite une refonte
sécuritaire complète avant tout déploiement en production.

---
*Rapport — LAB 8, MLIAEdu, 2026 — LAKBITA KHADIJA*
