<div align="center">

![Header](https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,100:00f2ff&height=120&section=header&text=&fontSize=0)

</div>

# ð Ãtude et Mise en Åuvre d'Outils de Monitoring RÃ©seau

<div align="center">

![Zabbix](https://img.shields.io/badge/Zabbix-CC0000?style=for-the-badge&logo=zabbix&logoColor=white) ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white) ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white) ![SNMP](https://img.shields.io/badge/SNMP-Network_Monitoring-00b4d8?style=for-the-badge) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

![ESMT](https://img.shields.io/badge/ESMT_Dakar-Licence_ASR-purple?style=flat-square) ![Type](https://img.shields.io/badge/Type-Monitoring_&_Supervision-green?style=flat-square) ![Status](https://img.shields.io/badge/Status-Terminé-success?style=flat-square)

</div>

> **Projet TutorÃ©** : Analyse comparative et dÃ©ploiement d'une solution de supervision proactive.

---

## ð¯ 1. Introduction et Contexte
Dans une infrastructure moderne, la supervision rÃ©seau est un pilier fondamental pour garantir la **stabilitÃ©**, la **performance** et la **sÃ©curitÃ©** des systÃ¨mes. Ce projet s'inscrit dans le cadre de la formation en **Administration et SÃ©curitÃ© des RÃ©seaux (ASR)** et rÃ©pond Ã  la problÃ©matique du choix et de la configuration d'outils adaptÃ©s pour une surveillance proactive.

### Objectifs principaux :
*   Comparer les solutions de monitoring (Open Source vs Commerciales).
*   DÃ©ployer une solution capable de surveiller la disponibilitÃ© et d'anticiper les pannes.
*   Mettre en place des alertes en temps rÃ©el et des tableaux de bord dynamiques.

---

## âï¸ 2. Ãtude Comparative des Solutions
Sept outils majeurs ont Ã©tÃ© rigoureusement Ã©valuÃ©s selon des critÃ¨res techniques, ergonomiques et Ã©conomiques.

| CritÃ¨res | **Zabbix** | **Nagios** | **Centreon** | **PRTG (Free)** |
| :--- | :--- | :--- | :--- | :--- |
| **Interface** | Moderne, intuitive | Basique, vieillissante | Intuitive (franÃ§ais) | TrÃ¨s conviviale |
| **Apprentissage** | Moyenne | ÃlevÃ©e (config manuelle) | Faible Ã  moyenne | Faible (trÃ¨s rapide) |
| **FonctionnalitÃ©s** | TrÃ¨s riches, tout-en-un | Essentielles via plugins | Riches (dÃ©pendant Nagios) | Riches (limitÃ© 100 capteurs) |
| **Performance** | Excellente, scalable | Robuste | Bonne | Bonne (petits rÃ©seaux) |
| **CoÃ»t** | **Gratuit, Open Source** | Gratuit | Gratuit (Ã©dition de base) | Version complÃ¨te payante |

> **ð Choix retenu : Zabbix.** Il se dÃ©marque par son interface moderne, sa scalabilitÃ© (architecture distribuÃ©e) et sa communautÃ© trÃ¨s active.

---

## âï¸ 3. Zoom sur la Solution : Zabbix
Zabbix est une plateforme centralisÃ©e permettant de surveiller en temps rÃ©el la disponibilitÃ© et l'intÃ©gritÃ© des Ã©quipements.

### Architecture Technique :
*   **Zabbix Server** : Le cÅur du systÃ¨me qui traite les donnÃ©es et gÃ¨re les alertes.
*   **Zabbix Agent** : InstallÃ© sur les hÃ´tes pour collecter les indicateurs locaux (CPU, RAM, Disque).
*   **Zabbix Proxy** : Pour la supervision dÃ©centralisÃ©e sur des sites distants.
*   **Base de DonnÃ©es** : Stockage des configurations et de l'historique (PostgreSQL utilisÃ© ici).

**Ports essentiels :** TCP 10050 (Agent) et TCP 10051 (Serveur/Proxy).

---

## ð ï¸ 4. Mise en Åuvre et Environnement de Test
Le dÃ©ploiement a Ã©tÃ© rÃ©alisÃ© dans un environnement virtualisÃ© sous **VMware Workstation**.

### Topologie du Laboratoire :
*   **Serveur Zabbix** : Ubuntu 22.04 (IP: 192.168.81.132).
*   **Client Ubuntu Server** : Supervision du service Apache et SSH.
*   **Client Kali Linux** : Machine cliente supervisÃ©e.
*   **Client Windows 10** : Supervision du service Spooler.

---

## ð 5. ScÃ©narios de Test et Alerting (Telegram)
Pour assurer une rÃ©activitÃ© maximale, nous avons intÃ©grÃ© un **bot Telegram** pour la rÃ©ception des alertes.

### Simulations rÃ©alisÃ©es :
1.  **IndisponibilitÃ© de Service** : L'arrÃªt d'Apache sur Ubuntu dÃ©clenche immÃ©diatement un trigger et une notification Telegram.
2.  **Saturation d'Espace Disque** : CrÃ©ation d'un fichier de 15 Go pour simuler un dÃ©passement du seuil critique (80%).
3.  **Panne Windows** : DÃ©tection de l'arrÃªt du service "Spooler" sur la VM Windows 10.

---

## ð 6. Visualisation (Dashboards)
Le tableau de bord mis en place offre une vue synthÃ©tique incluant :
*   **Current problems** : Suivi des alertes actives par sÃ©vÃ©ritÃ©.
*   **Map** : ReprÃ©sentation visuelle de la topologie rÃ©seau en direct.
*   **CPU Usage** : Graphique d'Ã©volution temporelle comparatif.
*   **Host Availability** : Ãtat global (Disponible / Indisponible).

---

## ð Conclusion
Ce projet dÃ©montre que Zabbix est une solution de rÃ©fÃ©rence capable de fournir une supervision complÃ¨te et proactive. L'implÃ©mentation a prouvÃ© l'efficacitÃ© de l'outil pour collecter des donnÃ©es, analyser les performances et gÃ©nÃ©rer des alertes en temps rÃ©el, garantissant ainsi une haute disponibilitÃ© des infrastructures.

---
### ð Documents du Projet
*   [ð Rapport Complet (PDF)](docs/Projet_TutorÃ©_Groupe11FINAL.pdf)
  
---
**Analogie finale :**
Mettre en place Zabbix, c'est comme installer un **systÃ¨me de tÃ©lÃ©surveillance intelligent** dans un grand bÃ¢timent. Les agents sont les camÃ©ras placÃ©es dans chaque piÃ¨ce (serveurs), le serveur Zabbix est le poste de contrÃ´le qui analyse les images, et le bot Telegram est le talkie-walkie qui prÃ©vient instantanÃ©ment l'agent de sÃ©curitÃ© dÃ¨s qu'une porte est forcÃ©e ou qu'une fuite d'eau est dÃ©tectÃ©e.


---

<div align="center">

### 🔗 Liens

[![Portfolio](https://img.shields.io/badge/Portfolio-00f2ff?style=for-the-badge&logo=firefox&logoColor=black)](https://kim-san04.github.io) [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/hakim-sawadogo) [![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Kim-San04)

**Cheick Abdel Hadime Hakim SAWADOGO**
*Mastère Cybersécurité, Réseaux & Cloud — Efrei Bordeaux*
📧 cheick.sawadogo@efrei.net

![Footer](https://capsule-render.vercel.app/api?type=waving&color=0:00f2ff,100:0d1117&height=80&section=footer)

</div>
