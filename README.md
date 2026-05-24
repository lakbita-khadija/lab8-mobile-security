LAB 8 — Analyse de posture et exposition d'applications mobiles
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
<img width="947" height="690" alt="Capture d&#39;écran 2026-05-24 132530" src="https://github.com/user-attachments/assets/407930d8-2247-42f6-acb6-1eab4bef6d5e" />

<img width="1310" height="577" alt="Capture d&#39;écran 2026-05-24 132942" src="https://github.com/user-attachments/assets/daba49ce-2aa7-4b9c-9c75-36798567a710" />

<img width="1919" height="679" alt="Capture d&#39;écran 2026-05-24 132915" src="https://github.com/user-attachments/assets/5dafd1cc-dad3-4a2c-bd86-0fba8ea98346" />
<img width="1916" height="933" alt="Capture d&#39;écran 2026-05-24 132842" src="https://github.com/user-attachments/assets/00606354-885f-4f20-818b-828796b6365b" />

<img width="853" height="820" alt="Capture d&#39;écran 2026-05-24 134324" src="https://github.com/user-attachments/assets/63219bce-3cf2-4964-94a2-852c30ed8a44" />
<img width="1916" height="921" alt="Capture d&#39;écran 2026-05-24 134629" src="https://github.com/user-attachments/assets/0091f466-78fe-4d25-992e-088cb9607dda" />
<img width="1628" height="605" alt="Capture d&#39;écran 2026-05-24 134438" src="https://github.com/user-attachments/assets/57f9a5d7-65b8-4ce2-a711-288c4cf0712e" />

<img width="1919" height="577" alt="Capture d&#39;écran 2026-05-24 134542" src="https://github.com/user-attachments/assets/d175fe5e-5d28-4a7b-a705-96c29f9de913" />

## Recommandations prioritaires
1. Forcer HTTPS + Certificate Pinning
2. Désactiver android:debuggable en production
3. Protéger MyBroadCastReceiver (exported=false)
4. Chiffrer les SharedPreferences
5. Supprimer permissions inutiles (SEND_SMS, READ_CALL_LOG)
6. Remplacer MD5/SHA1 par SHA-256

---

*LAB 8 — MLIAEdu 2026 — Cadre pédagogique uniquement*
