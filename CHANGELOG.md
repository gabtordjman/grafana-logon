# Changelog - Grafana Logon Monitor

## [Version 1.0] - 2025-12-09

### NXLog.conf
**v1.0** - Version stable
- Collecte des événements Windows Security (ID 4624, 4625, 4634, 4647)
- Ajout automatique des champs `service_name` et `logon_type`
- Envoi au format syslog IETF vers Alloy
- Compatibilité NXLog Community Edition

### Config.alloy
**v1.0** - Version stable
- Réception TCP sur port 514
- Forwarding simple vers Loki
- Configuration minimale sans parsing

### Query Grafana
**v1.0** - Version fonctionnelle pour : RECUPERATION DES CONNEXIONS ET AFFICHAGE DANS LE TABLEAU, CONNEXION REUSSIE UNIQUEMENT POUR L'INSTANT
- Extraction utilisateur depuis "Nouvelle ouverture de session"
- Capture station de travail depuis "Nom de la station de travail"
- Filtrage par domaine VMW10SYSLOG
- Affichage message "L'ouverture de session d'un compte s'est correctement déroulée"

---

## Évolution Développement

### NXLog.conf
- v0.1 : Configuration basique im_msvistalog
- v0.2 : Ajout pm_transformer pour logon_type/service_name
- v0.3 : Corrections syntaxe NXLog CE (Exec vs if)
- v0.4 : Passage format brut au lieu de JSON
- v0.5 : Correction erreurs Path et route
- **v1.0 : Version stable actuelle**

### Config.alloy
- v0.1 : Réception syslog basique
- v0.2 : Tentative parsing avec loki.process (abandonné)
- v0.3 : Corrections syntaxe Alloy (virgules)
- v0.4 : Simplification vers forward-only
- **v1.0 : Version stable actuelle**

### Query Grafana
- v0.1 : Extraction regex simple
- v0.2 : Découverte format tabulations (\t)
- v0.3 : Utilisation pattern `<time> <level> <message>`
- v0.4 : Différenciation succès/échecs/déconnexions
- v0.5 : Filtrage domaine VMW10SYSLOG
- **v1.0 : Version stable actuelle (connexion reussie seulement)**

---

## Statut Actuel
✅ **Fonctionnel** : Surveillance connexions utilisateurs réussies  
🔄 **En développement** : Échecs d'authentification et déconnexions  
📅 **Prochainement** : Alertes, tableaux avancés, export SIEM

---

*Développé sur une période de 7 heures avec tests intensifs de différentes approches d'extraction et parsing.*
