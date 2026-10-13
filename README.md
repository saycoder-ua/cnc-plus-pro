<div align="center">

# ⚙️ CNC Plus Pro

### Smart Manufacturing Platform for CNC Workshops & Production Facilities

Production-grade PWA platform for CNC machine monitoring, OEE analytics, workforce management, AI-powered drawing recognition, G-code development, and digital shop-floor operations.

<p align="center">
  <img src="docs/screenshots.png
</p>

<br>

![React](https://img.shields.io/badge/React-19-61DAeact&logoColor=white
![TypeScript](https://img.shields.io/badge/TypeScript-5=typescript&logoColor=white
![Node.js](https://img.shields.io/badge/Node.js-18+-339933?logo=node.js&hite
![Firebase](https://img.shields.io/badge/Firebase8?logo=firebase&logoColor=black
![PWA](https://img.shields.io/badge/PWA5A0FC8
![AI](https://img.shields.io/badge/AI-Gemini%20%7C%20Claude%20OpenAI-success
![License](httpslds.io/badge/License-Private-red

---

### 🏭 Monitor • Analyze • Automate • Optimize

Built for CNC operators, setup technicians, production managers, manufacturing engineers, and machine shops.

</div>

---

# 📑 Table of Contents

- [-overview
- #-key-features
- [-screenshots
- [Technologyy-stack
- [-ai-agents
- [Architecture](#-architecture#-quick-start
- [Environment Configuration](#-environment #-firebase-integration
- [API Referencee
- #-security
- #-roadmap
- [License](#---

# 🚀 Overview

CNC Plus Pro is a modern digital manufacturing platform that combines:

- CNC machine monitoring
- OEE and KPI analytics
- Workforce management
- Shift scheduling
- Tool management
- AI-powered engineering assistance
- Drawing recognition
- G-code generation
- Digital production journals
- Cloud synchronization

The system operates as a Progressive Web Application (PWA), allowing deployment on:

- Industrial touch panels
- Shop-floor terminals
- Desktop workstations
- Tablets
- Smartphones

---

# ✨ Key Features

## 🖥 CNC Machine Monitoring

- Real-time machine status
- Production timers
- Downtime tracking
- Machine utilization metrics
- OEE calculations
- Shift-based performance monitoring

## 📊 Manufacturing Analytics

- Overall Equipment Effectiveness (OEE)
- KPI dashboards
- Shift comparison reports
- Productivity statistics
- Downtime analysis

## 📅 Shift & Workforce Management

- Shift scheduling
- Attendance tracking
- Working hours calculation
- Salary calculation
- Piecework production accounting

## 🔧 Tool Management

- Tool inventory
- Tool wear tracking
- Coolant monitoring
- Maintenance planning
- Purchasing records

## 📐 Drawing Management

- Engineering drawing storage
- PDF support
- Image support
- AI-assisted dimension extraction
- Technical requirement recognition

## 💻 G-Code Studio

- Advanced editor
- Syntax highlighting
- Toolpath visualization
- G-code simulation
- AI-assisted programming

## 📝 Production Journals

- Downtime logs
- Defect tracking
- Shift handovers
- Digital signatures
- Operator notes

---

# 📸 Screenshots

## CNC Monitoring Dashboard

Real-time machine tracking and production overview.

docs/screenshots/dashboard.png

---

## Analytics & OEE

Manufacturing performance reports and KPI analysis.

docs/screenshots/analytics.png

---

## Shift Management

Scheduling, attendance tracking, and workforce planning.

docs/screenshots/shifts.png

---

## G-Code Studio

Editor, simulator, and AI-assisted code generation.

docs/screenshots/gcode-studio.png

---

## AI Drawing Recognition

Automated extraction of dimensions and manufacturing information.

docs/screenshots/drawing-ai.png

---

## AI Agents

Production-focused intelligent assistants.

docs/screenshots/ai-agents.png

---

# 🛠 Technology Stack

## Frontend

| Technology | Purpose |
|------------|----------|
| React 19 | UI Framework |
| TypeScript 5.8 | Strong Typing |
| Tailwind CSS 4 | Styling |
| Vite 6 | Development & Build |
| Recharts | Analytics |
| jsPDF | PDF Export |
| JSZip | Archive Generation |

---

## Backend

| Technology | Purpose |
|------------|----------|
| Node.js | Runtime |
| Express | API Layer |
| TypeScript | Server Logic |
| LRU Cache | Performance Optimization |

---

## Cloud Services

| Service | Purpose |
|----------|---------|
| Firebase Auth | Authentication |
| Firestore | Synchronization |
| Google Drive | Backup |
| Cloudflare R2 | Storage |
| Cloudflare D1 | Database |

---

# 🤖 AI Agents

CNC Plus Pro includes a configurable AI Agent Platform.

## Available Agents

### CNC Programmer Agent

Capabilities:

- Generate CNC programs
- Optimize toolpaths
- Validate machining strategies
- Improve cycle times

---

### Manufacturing Engineer Agent

Capabilities:

- Process planning
- Fixture recommendations
- Tool selection assistance
- Technology calculations

---

### Drawing Recognition Agent

Capabilities:

- Interpret technical drawings
- Extract dimensions
- Detect tolerances
- Prepare manufacturing summaries

---

### Shop-Floor Assistant

Capabilities:

- Operator support
- Shift documentation
- Troubleshooting guidance
- Production reporting

---

### Multi-Provider AI Support

Supported providers:

- Google Gemini
- Gemini Vision
- Anthropic Claude
- OpenAI

---

# 🏗 Architecture

```text
┌─────────────────────────────────────┐
│            React PWA UI             │
└────────────────┬────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│          App Context Layer          │
└────────────────┬────────────────────┘
                 │
 ┌───────────────┼─────────────────┐
 ▼               ▼                 ▼

IndexedDB    Firebase        AI Services
Local DB     Firestore       Gemini/Claude/OpenAI

 ▼               ▼                 ▼

Storage      Authentication   Drawing Analysis
Caching      User Roles       G-Code Generation
Offline      Sync Engine      AI Agents
```

---

# 🧩 Modules

## Production Modules

| Module | Description |
|----------|------------|
| machines | CNC Monitoring |
| tools | Tool Management |
| drawings | Engineering Drawings |
| files | Production Files |
| gcode | G-Code Studio |
| calendar | Shift Calendar |
| defects | Defect Management |
| stats | Analytics |
| log | Production Journals |
| customTemplate | Custom Extensions |

---

## Settings Modules

| Module | Purpose |
|----------|----------|
| settings_telegram | Notifications |
| settings_integrations | Integrations |
| settings_notifications | Alerts |
| settings_salary | Payroll |
| settings_shifts | Shift Management |
| settings_appearance | UI |
| settings_ai_agents | AI Configuration |
| settings_backup | Backups |
| settings_gdrive | Google Drive |
| settings_cloudflare | Cloudflare |

---

# ⚡ Quick Start

## Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/cnc-plus-pro.git
cd cnc-plus-pro
```

## Install

```bash
install.bat
```

Or manually:

```bash
npm install
copy .env.example .env
```

---

## Configure

```env
GEMINI_API_KEY=YOUR_API_KEY
```

---

## Run

```bash
start-dev.bat
```

Application:

```text
http://localhost:3000
```

---

# 🔑 Environment Configuration

```env
# AI PROVIDERS

GEMINI_API_KEY=
CLAUDE_API_KEY=
OPENAI_API_KEY=

# APPLICATION

PORT=3000
APP_URL=http://localhost:3000

# FIREBASE

FIREBASE_API_KEY=
FIREBASE_AUTH_DOMAIN=
FIREBASE_PROJECT_ID=
FIREBASE_STORAGE_BUCKET=
FIREBASE_APP_ID=
```

---

# 📜 Scripts

```bash
npm run dev
```

Development mode.

```bash
npm run build
```

Production build.

```bash
npm run start
```

Run production server.

```bash
npm run lint
```

TypeScript validation.

```bash
npm run clean
```

Clean build artifacts.

---

# 🔥 Firebase Integration

Supported:

- Firebase Authentication
- Firestore Synchronization
- Multi-user Collaboration
- Real-time Updates

The application remains fully functional offline using IndexedDB.

---

# 🌐 API Reference

## Core

| Method | Endpoint |
|----------|----------|
| GET | /api/health |
| GET | /api/check-model |
| GET | /api/available-models |

---

## AI Services

| Method | Endpoint |
|----------|----------|
| POST | /api/chat |
| POST | /api/agent-task |
| POST | /api/generate-gcode |
| POST | /api/recognize-drawing |

---

## Cache

| Method | Endpoint |
|----------|----------|
| GET | /api/cache/stats |
| POST | /api/cache/clear |

---

# 🔒 Security

- Firebase Authentication
- Role-based access control
- Firestore Security Rules
- Offline-first architecture
- Secure AI API proxy
- HTTPS deployment support

---

# 👥 User Roles

| Role | Permissions |
|--------|-------------|
| admin | Full system access |
| operator | Production operations |
| viewer | Read-only |

---

# 📈 Roadmap

## Completed

- ✅ CNC Monitoring
- ✅ OEE Analytics
- ✅ Shift Management
- ✅ Tool Management
- ✅ Firebase Sync
- ✅ AI Drawing Recognition
- ✅ G-Code Studio

## Planned

- ⏳ Fanuc FOCAS Integration
- ⏳ MTConnect Support
- ⏳ OPC UA Connector
- ⏳ Siemens SINUMERIK Integration
- ⏳ MES Integration
- ⏳ ERP Integration
- ⏳ Android App
- ⏳ iOS App

---

# 📝 License

Private License.

All Rights Reserved.

Unauthorized reproduction, distribution, or modification is prohibited.

---

<div align="center">

# ⚙️ CNC Plus Pro

### Digital Manufacturing Ecosystem for CNC Production

**Built for modern machine shops and manufacturing facilities.**

⭐ Star this repository if you find it useful.

</div>
