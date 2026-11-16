# TP : Introduction au Monitoring en DevOps

Ce dépôt contient le compte-rendu et les preuves de réalisation du TP de mise en place d'une solution de monitoring avec **Prometheus**, **Node Exporter** et **Grafana** via **Docker Compose**.

## 🎯 Objectifs
- Comprendre le rôle du monitoring dans la chaîne DevOps.
- Installer un outil open source de supervision.
- Mettre en place un premier tableau de bord avec Prometheus et Grafana.
- Interpréter les indicateurs de performance collectés.

---

## 📂 Architecture du projet
Le laboratoire a été déployé sur une machine virtuelle Ubuntu 22.04 en utilisant Docker Compose.
- **Prometheus** (port 9090) : Collecte et stocke les métriques.
- **Node Exporter** (port 9100) : Expose les métriques système (CPU, RAM, Disque).
- **Grafana** (port 3000) : Interface de visualisation et d'alerting.

---

## 📝 Partie 1 : Réflexion sur le Monitoring en DevOps

**Pourquoi le monitoring est-il essentiel dans une démarche DevOps ?**
Le monitoring est un pilier fondamental du DevOps car il permet de garantir la disponibilité et la fiabilité des applications. Il offre une visibilité en temps réel sur l'état de l'infrastructure et des services, permettant de détecter et de résoudre les incidents de manière proactive (avant que les utilisateurs ne les subissent). De plus, il fournit une boucle de rétroaction (feedback loop) essentielle pour l'amélioration continue, l'optimisation des performances et la prise de décision éclairée concernant l'évolution de l'infrastructure.

---

## 🚀 Partie 0 & 2 : Installation et Lancement

### Prérequis
- Docker Engine et Docker Compose installés.

### Fichier `docker-compose.yml`
```yaml
services:
  prometheus:
    image: prom/prometheus
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
  node_exporter:
    image: prom/node-exporter
    ports:
      - "9100:9100"
  grafana:
    image: grafana/grafana
    ports:
      - "3000:3000"
