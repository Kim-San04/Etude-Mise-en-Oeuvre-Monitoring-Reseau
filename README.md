<div align="center">

![Header](https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,100:00f2ff&height=120&section=header&text=&fontSize=0)

</div>

# 📊 Monitoring Réseau — Étude & Déploiement Zabbix

<div align="center">

![Zabbix](https://img.shields.io/badge/Zabbix-CC0000?style=for-the-badge&logo=zabbix&logoColor=white) ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white) ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white) ![SNMP](https://img.shields.io/badge/SNMP-Network_Monitoring-00b4d8?style=for-the-badge) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

![ESMT](https://img.shields.io/badge/ESMT_Dakar-Licence_ASR-purple?style=flat-square) ![Type](https://img.shields.io/badge/Type-Monitoring_%26_Supervision-green?style=flat-square) ![Status](https://img.shields.io/badge/Status-Terminé-success?style=flat-square)

</div>

---

## 🎯 Introduction

Projet tutoré : analyse comparative des solutions de supervision réseau open-source, déploiement de la solution retenue (Zabbix) et mise en place d'un système d'alerting automatisé.

---

## ⚖️ Étude Comparative

| Solution | Type | Points forts | Points faibles |
| :--- | :--- | :--- | :--- |
| **Zabbix** | Agent/Agentless | Très complet, SNMP natif | Interface datée |
| **Nagios** | Agent | Écosystème mature | Configuration complexe |
| **Prometheus** | Pull-based | Idéal cloud/containers | Pas d'agents réseau natifs |
| **PRTG** | Propriétaire | Très ergonomique | Coût élevé |

**Choix retenu : Zabbix** — meilleur rapport fonctionnalités/complexité pour un réseau hybride.

---

## ⚙️ Architecture Zabbix

```
[Équipements réseau]  ──SNMP──►  [Zabbix Server]  ──►  [Base de données MySQL]
[VMs Linux/Windows]  ──Agent──►  [Zabbix Server]  ──►  [Frontend Web]
                                                    ──►  [Alerting Telegram/Email]
```

**Composants déployés :**
- **Zabbix Server** sur Ubuntu 22.04
- **Agents Zabbix** sur les hôtes supervisés
- **MySQL** pour le stockage des métriques
- **Nginx** + PHP pour le frontend
- **Grafana** pour les dashboards avancés (via datasource Zabbix)

---

## 🛠️ Mise en Œuvre

**Métriques supervisées :**
- Disponibilité des hôtes (ping / ICMP)
- Utilisation CPU, RAM, disque
- Trafic réseau (octets/s, paquets/s)
- Services critiques (HTTP, SSH, DNS)
- Température matérielle via SNMP

**Configuration SNMP :**
```bash
# Installation de l'agent SNMP sur les hôtes
apt install snmp snmpd
# Configuration de la communauté
echo "rocommunity public 192.168.1.0/24" >> /etc/snmp/snmpd.conf
```

---

## 🚀 Alerting — Notifications Telegram

Intégration d'un bot Telegram pour les alertes critiques en temps réel :

| Sévérité | Délai d'alerte | Canal |
| :--- | :--- | :--- |
| **Disaster** | Immédiat | Telegram + Email |
| **High** | 2 min | Telegram |
| **Average** | 5 min | Email |
| **Warning** | 15 min | Dashboard uniquement |

---

## 📈 Résultats

- **14 hôtes** supervisés dans l'environnement de test
- **47 triggers** configurés (alertes conditions)
- Temps de détection d'une panne : **< 30 secondes**
- Dashboard Grafana avec métriques temps réel

---

<div align="center">

[![Portfolio](https://img.shields.io/badge/Portfolio-00f2ff?style=for-the-badge&logo=firefox&logoColor=black)](https://kim-san04.github.io) [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/hakim-sawadogo) [![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Kim-San04)

![Footer](https://capsule-render.vercel.app/api?type=waving&color=0:00f2ff,100:0d1117&height=80&section=footer)

</div>
