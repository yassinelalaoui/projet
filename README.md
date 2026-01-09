Lab SIEM Wazuh : Déploiement et Détection de Menaces sur AWS

Ce projet documente la mise en place d'une solution de supervision de sécurité (SIEM/EDR) basée sur **Wazuh** dans un environnement Cloud **AWS**.

Objectifs du Projet
- Déploiement d'un serveur Wazuh (Manager, Indexer, Dashboard) sur une instance EC2 Ubuntu.
- Sécurisation du réseau via AWS Security Groups (VPC).
- Monitoring d'un client **Windows** et d'un client **Linux**.
- Détection d'attaques et de comportements suspects via **Sysmon**.

Architecture du Lab
- **SIEM :** Wazuh Server (EC2 t3.medium)
- **Agents :** 1x Windows Server/Client (EC2), 1x Ubuntu Client (EC2)
- **Réseau :** VPC dédié (10.0.0.0/16) avec accès restreint par IP.

1. Préparation de l'infrastructure (AWS)
- Déploiement d'un **VPC** (Virtual Private Cloud) avec un sous-réseau public.
- Configuration des **Security Groups** pour autoriser les flux nécessaires :
  - **HTTPS (443)** : Interface Dashboard.
  - **1514 / 1515** : Communication et enregistrement des agents.
  - **SSH (22)** : Administration du serveur.
- Lancement d'une instance **EC2 Ubuntu** pour héberger le serveur Wazuh.

2. Installation du Serveur Wazuh
- Exécution du script d'installation centralisé (Indexer, Server, Dashboard).

3. Déploiement des Agents
- Agent Linux : Installation et liaison au manager via l'adresse IP du serveur.
- Agent Windows : - Installation de l'agent MSI.
- Déploiement de Sysmon pour obtenir une visibilité approfondie sur les processus et les événements système.

4. Tests de Détection et Alerting
J'ai testé la capacité de détection du SIEM avec les scénarios suivants :.
- **Contournement de sécurité :** Modification de l'Execution Policy PowerShell.
- **Persistance :** Simulation de lecture de fichiers sensibles.

Résultats
Les alertes sont centralisées dans le Dashboard Wazuh, permettant une analyse en temps réel des événements de sécurité.
