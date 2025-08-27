# 🍓 Raspberry Pi-Based SOC Lab  
**Threat Detection • Log Aggregation • Real-Time Monitoring**

> Built, tested, and documented by **Lamar Scott** – August 2025  
> scottlamar05@gmail.com

---

## 📑 Table of Contents
1. [Executive Summary](#executive-summary)  
2. [Architecture Diagram](#architecture-diagram)  
3. [Tools & Tech Stack](#tools--tech-stack)  
4. [Step-by-Step Deployment](#step-by-step-deployment)  
5. [Troubleshooting Highlights](#troubleshooting-highlights)  
6. [Exploit Simulation (SQLi)](#exploit-simulation-sqli)  
7. [Results & Key Metrics](#results--key-metrics)  
8. [Lessons Learned & Next Steps](#lessons-learned--next-steps)

---

## Executive Summary
Deployed a **fully-functional Security Operations Center** on a Raspberry Pi 5 using Docker Compose.  
• Processed **97,000+ packets** with **zero drops**  
• Generated **6,000+ Suricata alerts** and live-streamed them into **Grafana** dashboards  
• Simulated real attacks with **DVWA SQL injection** to validate end-to-end detection

Skill areas: containerization, IDS/IPS tuning, log pipeline design, dashboarding, and incident analysis.

---

## Architecture Diagram
![SOC Architecture](media/architecture.png)

Traffic ➜ **Suricata / Zeek / ntopng** ➜ **Promtail** ➜ **Loki + EveBox** ➜ **Grafana**  
All services orchestrated with **docker-compose**; key ports: Grafana 3002, ntopng 3001, Loki 3100, DVWA 8080.

---

## Tools & Tech Stack
| Layer | Tool | Version | Purpose |
|-------|------|---------|---------|
| Detection | **Suricata** | 7.0.11 | Packet inspection & alerts |
|   | **Zeek** | 7.1.1 | Protocol & log analytics |
| Visibility | **ntopng** | 6.5 | Flow monitoring |
| Logs | **Promtail** | 2.9.8 | Log scraping |
|   | **Loki** | 2.9.8 | Central log store |
| Dashboards | **Grafana** | 12.2.0 | Visualization |
| Attack Sim | **DVWA** | latest | Vulnerable web app |
| Orchestration | **Docker/Compose** | 24.x | Container management |

_All images run on **arm64** for Pi 5._

---

## Step-by-Step Deployment
