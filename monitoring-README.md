


# Monitoring (Netdata / Prometheus /Grafana /

This secction documents my monitoring setup.

## Components
- Netdata (real-time  monitoring)
- Prometheus (metrics collection)
- Grafana (dashboards)


## What I demonstrate 
- Installing monitoring tools
- Tracking CPU, RAM, disk, network
- Montitoring PHP-FPM and postfix
- Creating dashboards

## skills shown 
- Obeservability fundamentals
- Performance troubleshooting
- Service health monitoring

  -------------------------------------------------------------------------------------


**Overview**
This repository documents the installation and configuration of a full monitoring stack consisting of:
 * **Prometheus** - TIme-series metrics
 * database
 * **Node Exprter** - Linux system metrics
 * **Grafana** - Dashboards &
 * visualization
 * **Optional**: WordPress metrics, MySQL metrics, PHP-FPM metrics

This setup provides complete visibility into server performance, WordPress behavior, and system health.

🏗️ ## Architecture

[WordPress / Linux Server]
   ├─ Node Exporter → Prometheus
   ├─ Netdata → Prometheus (optional)
   ├─ MySQL Exporter → Prometheus (optional)
   ├─ PHP-FPM Exporter → Prometheus (optional)
   └─ WordPress Prometheus Plugin → Prometheus (optional)

[Prometheus Server]
   └─ Prometheus → Grafana

[Grafana Server]
   └─ Dashboards + Alerts

[GitHub]
   └─ Stores configs + dashboards

🚀## Install Prometheus 
Prometheus is the core of monitoring stack.
apt update && apt install prometheus 

**Verify Prometheus**
systemctl status prometheus 

🖥️## Install Node Exporter
Noe exporter provides CPU, RAM, disk, network, and system metrics.

**Fixing the "prometheus users exists" issue**
if you previously had a non-system user named prometheus, remove it:
sudo deluser --remove-home prometheus

**Install Node Exporter**
sudo apt install prometheus-node-exporter 

**Verify**
sudo systemctl status prometheus-node-exporter


##Configure Prometheus to screpe Node Exporter

Edit prometheus config:
nano /etc/prometheus/prometheus.yml

**Add**
  - job_name: 'node'
    static_configs:
      - targets: ['<server-ip>:9100']
   
**Reload Prometheus**
sudo systemtl restart prometheus

## Install Grafana

Grafana visualizes metrics

**Install Grafana**

sudo apt install grafana

**Enable and start grafana**
sudo systemctl daemon-reload
sudo systemctl enable grafana-server
sudo systemctl start grafana-server

Grafana runs on: http://server-ip:3000

 **Deault login**
* Username: admin
* Password: admin
  * (You will be asked to set a new password)

## Connect Grafana to Prometheus

inside Grafana:

1. Go to **Configuration --> Data sources**
2. Click **Add data sources**
3. Select **Prometheus**
4. Set URL:
   * htpp://localhost:9090
5. Click **Save & test**

## Installing and configuring prometheus

https://github.com/user-attachments/assets/8dd0e4c6-aca5-416e-8be4-4f404c3e2cda

## Prometheus 

https://github.com/user-attachments/assets/20d66da7-2114-48e1-91d2-349f0113c512

## Node Exporter


https://github.com/user-attachments/assets/a665773b-8455-4721-896b-e9fb8d81a473

## Connecting Node Exporter to Prometheus


https://github.com/user-attachments/assets/1326f442-0395-4e36-bcc8-980ad79e8a3f




<img width="1905" height="899" alt="image" src="https://github.com/user-attachments/assets/3bcb7acf-99a7-472f-ae97-456d0d8acf07" />

<img width="1902" height="859" alt="image" src="https://github.com/user-attachments/assets/9809c6c7-b259-4680-b464-5310506d42ca" />

<img width="1904" height="900" alt="image" src="https://github.com/user-attachments/assets/05d48b26-e18c-4b88-863e-06789bf9479a" />

<img width="1886" height="890" alt="image" src="https://github.com/user-attachments/assets/0df3cc9a-02e6-4b62-b4e0-9b8ec63e880d" />



