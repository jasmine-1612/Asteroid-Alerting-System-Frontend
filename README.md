# 🛰️ Asteroid Alerting & Notification System
An **event-driven backend system** that monitors Near-Earth Objects (NEOs) using NASA's public API and sends automated email alerts for potentially hazardous asteroids.
The system is designed using **microservices principles**, **Apache Kafka for event streaming**, and **Docker for infrastructure orchestration**, ensuring scalability, decoupling, and ease of local development.

---

## 📌 Project Purpose
This repository contains the **frontend (ORBITAL_UI)** for the Asteroid Alerting & Notification System. It provides a mission-control style dashboard to visualize live telemetry, monitor service health, review notification history, and explore the system's architecture and API — all powered by the backend's Spring Boot, Kafka, and MySQL services.

---

## 🖥️ Pages / Modules
- **`index.html`** — Landing page with mission overview and live telemetry ticker.
- **`dashboard.html`** — Command Center: live alert feed, service health, notification stats.
- **`notification.html`** — Threat Log: full notification history with search, filters, and CSV export.
- **`architecture.html`** — Live system architecture map with real-time service health checks.
- **`documentation.html`** — Interactive API documentation with a runnable `curl` console.

---

## ✨ Features
- 📡 **Real-Time Tracking** — displays continuous ingestion of NASA NEO data with trajectory info.
- ⚡ **Live Service Health** — polls Alerting (`:8080`), Notify (`:8081`), and Kafka (`:8084`) endpoints.
- 🔔 **Live Notification Feed** — streams notification events from the Notify service in near real time.
- 🗂️ **Threat Log / History** — searchable, filterable, paginated table with CSV export.
- 🧭 **Interactive Architecture Diagram** — visualizes the event-driven data flow across services.
- 📖 **Built-in API Docs** — authentication, request/response schemas, and a live API console.
- 🎨 **Mission-control aesthetic** — dark UI built with Tailwind CSS and Material Symbols icons.

---

## 🧱 Tech Stack
- **HTML5 / Vanilla JavaScript**
- **Tailwind CSS** (via CDN)
- **Google Fonts** — Inter, Space Grotesk, JetBrains Mono
- **Material Symbols** icon set
- **Fetch / WebSocket** calls to backend REST + Kafka-backed services

---

## 🔗 Backend Services Consumed
| Service | Port | Purpose |
|---|---|---|
| Alerting Service | `8080` | Triggers NEO scans, evaluates hazard thresholds |
| Notify Service | `8081` | Sends and stores email notifications (MySQL-backed) |
| Kafka | `9092` (broker) / `8084` (UI) | Event streaming between services |
| MySQL | `3307` | Persistence for notification records |

---

## 📂 Project Structure
```
├── index.html            # Landing page
├── dashboard.html        # Command Center / main dashboard
├── notification.html     # Threat Log (notification history)
├── architecture.html     # Live system architecture view
├── documentation.html    # API documentation & test console
```

---

## ⚙️ Setup & Installation
1. **Clone the repository**
   ```bash
   git clone https://github.com/jasmine-1612/Asteroid-Alerting-System-Frontend.git
   cd Asteroid-Alerting-System-Frontend
   ```
2. **Serve the files** (static site, no build step required)
   ```bash
   npx serve .
   ```
3. **Start the backend services** (Alerting, Notify, Kafka, MySQL) so the dashboard, threat log, and architecture pages can display live data.
4. Open `index.html` in your browser, or go directly to `dashboard.html` for the Command Center.

---

## 🔐 API Authentication
All backend API requests require an `X-Orbital-Key` header:
```
X-Orbital-Key: orb_live_7329_alpha_bravo_99
```
Unauthorized requests are logged and terminated with a `401` response.

---

## 📡 Sample API Call
**Trigger Alert Process**
```
POST /api/v1/asteroid-alerting/alert
```
Request:
```json
{
  "start_date": "2024-11-20",
  "end_date": "2024-11-21",
  "distance_threshold_km": 1500000,
  "priority": "CRITICAL"
}
```
Response:
```json
{
  "status": "SUCCESS",
  "events_published": 15,
  "process_id": "uuid-0992-bx-11",
  "timestamp": "2024-11-20T14:42:01Z"
}
```

---

## 📄 License
This project is provided for educational and demonstration purposes.

---

**ORBITAL_UI** — © 2024 Orbital Systems · All Telemetry Active
