# LAB 8 — Analyse de posture et exposition d'applications mobiles
**Analyste :** LAKBITA KHADIJA  
**Date :** 2026-05-24  
**Cours :** Sécurité des applications mobiles — MLIAEdu  

---

## Objectif
Analyser la posture de sécurité de l'application InsecureBankv2
en utilisant BeVigil (OSINT en ligne) et Yaazhini (analyse statique locale).

---

## Outils utilisés
| Outil | Rôle |
|-------|------|
| BeVigil (CloudSEK) | OSINT mobile — score, endpoints, trackers |
| Yaazhini (VegaBird) | Scanner statique — vulnérabilités, permissions |

---

## Application analysée
| Champ | Valeur |
|-------|--------|
| Nom | InsecureBankv2 |
| Package | com.android.insecurebankv2 |
| Version | 1.0 |
| SHA256 | b18af2a0e44d7634bbcdf93664d9c78a2695e050393fcfbb5e8b91f902d194a4 |
| Score BeVigil | 7.4/10 AVERAGE |

---

## Résultats clés
- 🔴 36 communications non chiffrées (HTTP)
- 🔴 MyBroadCastReceiver exporté sans protection
- 🔴 Permissions dangereuses : SEND_SMS, READ_CALL_LOG, READ_PHONE_STATE
- 🟠 Android Debuggable activé en production
- 🟠 Weak Hash MD5/SHA1 utilisés
- 🟠 SharedPreferences non chiffrées

---

## Structure du projet
lab8/
├── README.md
├── artefacts/
│   └── cible.apk.sha256
├── bevigil/
│   └── bevigil_results.md
├── yaazhini/
│   └── yaazhini_results.md
├── rapports/
│   ├── normalized_20260524.csv
│   ├── owasp_correlation.md
│   └── rapport_final.md
└── logs/
└── journal.md

---

## Corrélation OWASP Mobile Top 10
| OWASP | Catégorie | Sévérité |
|-------|-----------|----------|
| M1 | Improper Credential Usage | 🔴 Critique |
| M3 | Insecure Authentication | 🔴 Critique |
| M5 | Insecure Communication | 🔴 Critique |
| M6 | Inadequate Privacy Controls | 🔴 Critique |
| M8 | Security Misconfiguration | 🔴 Critique |
| M9 | Insecure Data Storage | 🔴 Critique |

---

## Recommandations prioritaires
1. Forcer HTTPS + Certificate Pinning
2. Désactiver android:debuggable en production
3. Protéger MyBroadCastReceiver (exported=false)
4. Chiffrer les SharedPreferences
5. Supprimer permissions inutiles (SEND_SMS, READ_CALL_LOG)
6. Remplacer MD5/SHA1 par SHA-256

---

*LAB 8 — MLIAEdu 2026 — Cadre pédagogique uniquement*
