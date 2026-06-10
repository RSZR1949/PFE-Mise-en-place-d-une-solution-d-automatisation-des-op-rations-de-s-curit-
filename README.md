# Mise en place d’une solution d’automatisation des opérations de sécurité

## Présentation

Ce projet de fin d'études a pour objectif la conception et l'implémentation d'une architecture SOC (Security Operations Center) automatisée basée sur des technologies Open Source.

La solution permet de :

- Centraliser les journaux de sécurité (logs)
- Détecter les activités malveillantes en temps réel
- Automatiser les actions de réponse aux incidents
- Enrichir les alertes grâce à la Threat Intelligence
- Assister les analystes SOC à l'aide d'un modèle d'intelligence artificielle (LLM)
- Centraliser la gestion des incidents

---

## Objectifs

- Réduire le temps de détection (MTTD)
- Réduire le temps de réponse (MTTR)
- Automatiser les tâches répétitives des analystes SOC
- Améliorer la qualité des investigations
- Fournir une plateforme de gestion des incidents centralisée

---

## Architecture globale

L'architecture repose sur plusieurs composants interconnectés :

### Collecte et détection

- Wazuh SIEM/XDR
- Wazuh Agents
- Sysmon
- Suricata IDS/IPS

### Orchestration et automatisation

- n8n (SOAR)
- Webhooks
- API REST

### Threat Intelligence

- VirusTotal

### Gestion des incidents

- DFIR-IRIS

### Communication

- Discord Notifications

### Intelligence Artificielle

- LLM intégré dans les workflows n8n pour :
  - analyser les alertes
  - générer des résumés d'incidents
  - proposer des recommandations

---

## Stack technologique

| Fonction | Solution |
|-----------|-----------|
| SIEM/XDR | Wazuh |
| IDS/IPS | Suricata |
| SOAR | n8n |
| Incident Response | DFIR-IRIS |
| Threat Intelligence | VirusTotal |
| Firewall | pfSense |
| Endpoint Monitoring | Sysmon |
| Virtualisation | VMware / VirtualBox |
| Notification | Discord |
| Intelligence Artificielle | LLM |

---


## Environnement technique déployé

L'infrastructure du laboratoire a été construite à l'aide de machines virtuelles et de conteneurs Docker afin de reproduire un environnement SOC réaliste tout en garantissant l'isolation des différents composants.

| Composant | Type | Rôle |
|------------|--------|--------|
| Wazuh | Machine Virtuelle | SIEM / XDR pour la collecte, la corrélation et l'analyse des événements de sécurité |
| Suricata | Docker sur VM Linux | IDS/IPS pour la surveillance et l'analyse du trafic réseau |
| n8n (SOAR) | Docker sur VM Linux | Orchestration et automatisation des workflows de sécurité |
| DFIR-IRIS | Docker sur VM Linux | Gestion des incidents et centralisation des investigations |
| VirusTotal | API Cloud | Enrichissement des indicateurs de compromission (IoC) |
| pfSense | Machine Virtuelle | Pare-feu et contrôle du trafic réseau |
| Sysmon | Agent Windows | Surveillance avancée des événements système et des processus |
| Discord | API Cloud | Notification en temps réel des incidents et alertes SOC |
| LLM (IA) | API Cloud | Analyse des alertes, génération de résumés et assistance à la prise de décision |

### Infrastructure

- Plusieurs machines virtuelles Linux hébergent les services Docker.
- Un poste Windows est utilisé comme Endpoint supervisé.
- pfSense assure le filtrage et la segmentation réseau.
- Les composants communiquent via API REST, Webhooks et flux JSON.
- L'ensemble de l'environnement a été conçu pour simuler un SOC automatisé capable de détecter, analyser et répondre aux incidents de sécurité en temps réel.




## Workflow SOAR

1. Détection d'une activité suspecte par Wazuh ou Suricata.
2. Envoi automatique d'une alerte vers n8n via Webhook.
3. Analyse et extraction des IoCs.
4. Enrichissement via VirusTotal.
5. Analyse complémentaire par LLM.
6. Création automatique d'un incident dans DFIR-IRIS.
7. Notification en temps réel sur Discord.
8. Exécution d'actions de réponse automatisées (blocage IP, etc.).

---

## Cas d’usage implémentés

### Brute Force Detection

- Détection des tentatives répétées d'authentification.
- Identification de l'adresse IP source.
- Blocage automatique via pare-feu.
- Notification des analystes.

### Détection d'activité malveillante Endpoint

- Surveillance Sysmon.
- Analyse des processus suspects.
- Vérification des hash via VirusTotal.
- Création automatique d'un dossier d'investigation.

### Gestion automatisée des incidents

- Création d'un Case DFIR-IRIS.
- Ajout automatique des IoCs.
- Génération d'une chronologie d'événements.

---

## Environnement de laboratoire

### Machines utilisées

| Machine | Rôle |
|----------|--------|
| Wazuh Server | SIEM/XDR |
| pfSense | Firewall |
| Suricata | IDS/IPS |
| DFIR-IRIS | Gestion des incidents |
| n8n | Automatisation SOAR |
| Windows Endpoint | Poste utilisateur |
| Linux Endpoint | Serveur Linux |

---

## Résultats obtenus

- Réduction significative du temps de traitement des alertes.
- Automatisation du cycle de réponse aux incidents.
- Centralisation des investigations.
- Amélioration de la visibilité sur les événements de sécurité.
- Validation de plusieurs scénarios d'attaque dans un environnement contrôlé.
  
---

## Auteurs

### Zakaria Rehhaby
### Abdelilah Arrassa

---

## Licence

Projet académique réalisé dans le cadre du Projet de Fin d'Études (PFE).
