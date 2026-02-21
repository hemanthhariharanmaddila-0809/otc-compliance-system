# otc-compliance-system
A production-ready RegTech (Regulatory Technology) application that automates RBI's 2027 UTI (Unique Transaction Identifier) compliance mandate for OTC derivative trades. The system implements a complete trade negotiation workflow with cryptographic audit trails and real-time regulatory reporting.
🏗️ System Architecture
text
┌─────────────────────┐     ┌─────────────────────┐
│    User 1 Portal    │     │    User 2 Portal    │
│   (FastAPI :8001)   │     │   (FastAPI :8002)   │
└─────────┬───────────┘     └─────────┬───────────┘
          │                            │
          │    Initiate/Accept Trades  │
          ▼                            ▼
┌─────────────────────────────────────────────┐
│         RBI Central Server (Flask :5000)     │
│  • UTI Generation (Waterfall Logic)          │
│  • Trade Processing & Validation             │
│  • Real-time Dashboard & Analytics           │
└─────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────────┐
│            Shared Data Volume                │
│  • LEI Database (10,000+ records)           │
│  • Trades Database (SQLite)                  │
│  • Pending Trade Requests                    │
└─────────────────────────────────────────────┘
✨ Key Features
🔐 LEI-Based Authentication
Secure login using 20-character Legal Entity Identifiers

Real-time validation against GLEIF-compliant database

10,000+ synthetic LEI records with 80% ISSUED status

🤝 Peer-to-Peer Trade Negotiation
Initiate Trade: Create pending trade requests with full details

Accept/Reject: Counterparty review with one-click decisions

Real-time Notifications: Live updates on trade status changes

Status Tracking: Pending → Accepted → Rejected → Confirmed

🏛️ RBI 2027 Waterfall UTI Generation
Implements complete regulatory hierarchy:

Level 1: CCP-cleared trades → CCIL generates UTI

Level 2: ETP-executed trades → Platform generates UTI

Level 3: Cross-border trades → Clearing Member generates UTI

Level 4: Creator role → Bank generates 52-char UTI

Level 5: Receiver role → Counterparty provides UTI

📊 Comprehensive Dashboards
User Portals: Beautiful purple-gradient UIs with:

Trade initiation forms

Incoming/Outgoing request management

Confirmed trades history

Quick-action presets

Real-time clock and statistics

RBI Central Dashboard:

Live trade monitoring

UTI generator distribution charts

Complete transaction ledger

5-second auto-refresh

🔒 Security Features
HTTP-only session cookies

In-memory session management

CORS protection

Input validation with Pydantic

SQL injection prevention

🛠️ Technology Stack
Component	Technology	Purpose
Backend	FastAPI + Flask	High-performance async APIs
Frontend	Jinja2 + Vanilla JS	Dynamic server-rendered UIs
Database	SQLite	Lightweight, portable storage
Container	Docker + Compose	Easy deployment & scaling
Validation	Pydantic	Type-safe data validation
HTTP Client	HTTPX	Async API communications
Templating	Jinja2	Reusable HTML components
📦 Project Structure
text
rbi-uti-compliance-system/
├── docker-compose.yml           # Multi-container orchestration
├── shared-data/                  # Shared volume
│   ├── lei_database.db           # LEI records (10k+)
│   └── load_lei_data.py           # LEI generator script
├── rbi-server/                    # RBI Central Server (Flask)
│   ├── app.py                      # Main application
│   ├── database.py                  # DB operations
│   ├── utils.py                      # UTI generation logic
│   └── templates/
│       └── rbi_dashboard.html        # Monitoring dashboard
├── user1/                           # User 1 Portal (FastAPI)
│   ├── main.py                       # FastAPI application
│   ├── config.py                      # Configuration
│   ├── database.py                     # LEI validation
│   ├── models.py                        # Pydantic models
│   └── templates/
│       ├── login.html                    # Authentication
│       └── dashboard.html                 # Trading interface
└── user2/                           # User 2 Portal (FastAPI)
    └── (same structure as user1)



    Acknowledgments
Reserve Bank of India (RBI) guidelines

Global Legal Entity Identifier Foundation (GLEIF)

FastAPI and Flask communities

Docker team
