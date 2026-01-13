# 📊 Étude et Mise en Œuvre d'Outils de Monitoring Réseau
> **Projet Tutoré** : Analyse comparative et déploiement d'une solution de supervision proactive.

---

## 🎯 1. Introduction et Contexte
Dans une infrastructure moderne, la supervision réseau est un pilier fondamental pour garantir la **stabilité**, la **performance** et la **sécurité** des systèmes. Ce projet s'inscrit dans le cadre de la formation en **Administration et Sécurité des Réseaux (ASR)** et répond à la problématique du choix et de la configuration d'outils adaptés pour une surveillance proactive.

### Objectifs principaux :
*   Comparer les solutions de monitoring (Open Source vs Commerciales).
*   Déployer une solution capable de surveiller la disponibilité et d'anticiper les pannes.
*   Mettre en place des alertes en temps réel et des tableaux de bord dynamiques.

---

## ⚖️ 2. Étude Comparative des Solutions
Sept outils majeurs ont été rigoureusement évalués selon des critères techniques, ergonomiques et économiques.

| Critères | **Zabbix** | **Nagios** | **Centreon** | **PRTG (Free)** |
| :--- | :--- | :--- | :--- | :--- |
| **Interface** | Moderne, intuitive | Basique, vieillissante | Intuitive (français) | Très conviviale |
| **Apprentissage** | Moyenne | Élevée (config manuelle) | Faible à moyenne | Faible (très rapide) |
| **Fonctionnalités** | Très riches, tout-en-un | Essentielles via plugins | Riches (dépendant Nagios) | Riches (limité 100 capteurs) |
| **Performance** | Excellente, scalable | Robuste | Bonne | Bonne (petits réseaux) |
| **Coût** | **Gratuit, Open Source** | Gratuit | Gratuit (édition de base) | Version complète payante |

> **🏆 Choix retenu : Zabbix.** Il se démarque par son interface moderne, sa scalabilité (architecture distribuée) et sa communauté très active.

---

## ⚙️ 3. Zoom sur la Solution : Zabbix
Zabbix est une plateforme centralisée permettant de surveiller en temps réel la disponibilité et l'intégrité des équipements.

### Architecture Technique :
*   **Zabbix Server** : Le cœur du système qui traite les données et gère les alertes.
*   **Zabbix Agent** : Installé sur les hôtes pour collecter les indicateurs locaux (CPU, RAM, Disque).
*   **Zabbix Proxy** : Pour la supervision décentralisée sur des sites distants.
*   **Base de Données** : Stockage des configurations et de l'historique (PostgreSQL utilisé ici).

**Ports essentiels :** TCP 10050 (Agent) et TCP 10051 (Serveur/Proxy).

---

## 🛠️ 4. Mise en Œuvre et Environnement de Test
Le déploiement a été réalisé dans un environnement virtualisé sous **VMware Workstation**.

### Topologie du Laboratoire :
*   **Serveur Zabbix** : Ubuntu 22.04 (IP: 192.168.81.132).
*   **Client Ubuntu Server** : Supervision du service Apache et SSH.
*   **Client Kali Linux** : Machine cliente supervisée.
*   **Client Windows 10** : Supervision du service Spooler.

---

## 🚀 5. Scénarios de Test et Alerting (Telegram)
Pour assurer une réactivité maximale, nous avons intégré un **bot Telegram** pour la réception des alertes.

### Simulations réalisées :
1.  **Indisponibilité de Service** : L'arrêt d'Apache sur Ubuntu déclenche immédiatement un trigger et une notification Telegram.
2.  **Saturation d'Espace Disque** : Création d'un fichier de 15 Go pour simuler un dépassement du seuil critique (80%).
3.  **Panne Windows** : Détection de l'arrêt du service "Spooler" sur la VM Windows 10.

---

## 📈 6. Visualisation (Dashboards)
Le tableau de bord mis en place offre une vue synthétique incluant :
*   **Current problems** : Suivi des alertes actives par sévérité.
*   **Map** : Représentation visuelle de la topologie réseau en direct.
*   **CPU Usage** : Graphique d'évolution temporelle comparatif.
*   **Host Availability** : État global (Disponible / Indisponible).

---

## 🏁 Conclusion
Ce projet démontre que Zabbix est une solution de référence capable de fournir une supervision complète et proactive. L'implémentation a prouvé l'efficacité de l'outil pour collecter des données, analyser les performances et générer des alertes en temps réel, garantissant ainsi une haute disponibilité des infrastructures.

---
### 📂 Documents du Projet
*   [📁 Rapport Complet (PDF)](./docs/Projet_Tutoré_Groupe11.pdf)
  
---
**Analogie finale :**
Mettre en place Zabbix, c'est comme installer un **système de télésurveillance intelligent** dans un grand bâtiment. Les agents sont les caméras placées dans chaque pièce (serveurs), le serveur Zabbix est le poste de contrôle qui analyse les images, et le bot Telegram est le talkie-walkie qui prévient instantanément l'agent de sécurité dès qu'une porte est forcée ou qu'une fuite d'eau est détectée.
