macro-risk-engine/
│
├── .github/
│   │
│   └── copilot-instructions.md
│       # คำสั่งหลักสำหรับ GitHub Copilot / AI Agent
│       # บอกให้ AI อ่าน docs/00-skills.md ก่อนเสมอ
│       # กำหนดกฎห้ามเดา Business Logic
│       # กำหนดว่า Business Logic ต้องอ้างอิงจาก docs/business/*
│
├── docs/
│   │
│   ├── 00-skills.md
│   │   # Entry Point ของเอกสารทั้งหมด
│   │   # เป็น Project Constitution / Source of Truth
│   │   # อธิบาย Vision, Mission, Scope, Read Order
│   │   # AI และ Developer ต้องอ่านไฟล์นี้ก่อน
│   │
│   ├── business/
│   │   │
│   │   ├── 01-project-charter.md
│   │   │   # อธิบายเป้าหมายของโปรเจกต์
│   │   │   # Problem Statement
│   │   │   # Business Objective
│   │   │   # Scope / Out of Scope
│   │   │   # Definition of Success
│   │   │
│   │   ├── 02-macro-framework.md
│   │   │   # อธิบายกรอบ Macro Framework
│   │   │   # Layer 0: Central Bank / Money Creation
│   │   │   # Layer A: Cause
│   │   │   # Layer B: Stress
│   │   │   # Layer P: Accelerator
│   │   │   # Layer C: Confirmation
│   │   │   # Layer D: Damage
│   │   │   # Layer E: Deleveraging
│   │   │
│   │   ├── 03-risk-engine.md
│   │   │   # อธิบาย Risk Score Engine
│   │   │   # State Machine
│   │   │   # Risk Score 0-100
│   │   │   # Golden Signal
│   │   │   # Pseudocode
│   │   │
│   │   ├── 04-indicators.md
│   │   │   # Dictionary ของ Indicators ทั้งหมด
│   │   │   # SOFR, DXY, US30Y, Gold, MOVE
│   │   │   # Credit Spread, Treasury Auction
│   │   │   # Bank Reserves, Fiscal Deficit, VIX, TLT
│   │   │
│   │   └── 05-alert-rules.md
│   │       # กฎการแจ้งเตือน
│   │       # Liquidity Stress Alert
│   │       # Debt Stress Alert
│   │       # Golden Signal Alert
│   │       # Acceleration Alert
│   │       # Deleveraging Alert
│   │
│   ├── technical/
│   │   │
│   │   ├── 01-technology-stack.md
│   │   │   # ระบุ Tech Stack ทั้งหมด
│   │   │   # Angular 22
│   │   │   # Node.js 24
│   │   │   # Express
│   │   │   # TypeScript
│   │   │   # PostgreSQL + TimescaleDB
│   │   │   # Prisma, BullMQ, Redis, Docker
│   │   │
│   │   ├── 02-system-architecture.md
│   │   │   # อธิบาย Software Architecture
│   │   │   # Angular Dashboard
│   │   │   # Express API
│   │   │   # Worker
│   │   │   # Risk Engine Package
│   │   │   # Database Package
│   │   │
│   │   ├── 03-api-spec.md
│   │   │   # API Specification
│   │   │   # Endpoint
│   │   │   # Request / Response
│   │   │   # Error Format
│   │   │   # Validation Rule
│   │   │
│   │   ├── 04-database-design.md
│   │   │   # Database Design
│   │   │   # Prisma Schema
│   │   │   # TimescaleDB Hypertable
│   │   │   # Indexes
│   │   │   # Relationships
│   │   │
│   │   ├── 05-coding-standard.md
│   │   │   # Coding Standard
│   │   │   # TypeScript Strict Mode
│   │   │   # Naming Convention
│   │   │   # File Naming
│   │   │   # Error Handling
│   │   │   # Testing Rule
│   │   │
│   │   └── 06-project-rules.md
│   │       # Project Rules
│   │       # Documentation First Development
│   │       # ห้าม Hardcode Threshold
│   │       # ห้าม Business Logic อยู่ใน Controller
│   │       # ห้ามเปลี่ยน Architecture โดยไม่แก้ Docs
│   │
│   ├── ai/
│   │   │
│   │   └── copilot-guide.md
│   │       # คู่มือการใช้ AI / Copilot / Agent
│   │       # Read Order
│   │       # AI Do / Don't
│   │       # Prompt Template
│   │       # วิธีสั่ง Copilot ให้ทำงาน
│   │
│   ├── roadmap/
│   │   │
│   │   └── development-roadmap.md
│   │       # Roadmap การพัฒนา
│   │       # Phase 0: Documentation
│   │       # Phase 1: Project Bootstrap
│   │       # Phase 2: Database
│   │       # Phase 3: Risk Engine
│   │       # Phase 4: API
│   │       # Phase 5: Worker
│   │       # Phase 6: Angular Dashboard
│   │
│   └── adr/
│       │
│       ├── 001-use-angular-22.md
│       │   # เหตุผลที่เลือก Angular 22
│       │
│       ├── 002-use-node-24-express.md
│       │   # เหตุผลที่เลือก Node 24 + Express
│       │
│       ├── 003-use-postgresql-timescaledb.md
│       │   # เหตุผลที่เลือก PostgreSQL + TimescaleDB
│       │
│       ├── 004-use-daily-update.md
│       │   # เหตุผลที่เลือกอัปเดตวันละ 1 ครั้ง
│       │
│       └── 005-use-angular-signals.md
│           # เหตุผลที่เลือก Angular Signals
│
├── apps/
│   │
│   ├── web/
│   │   # Angular 22 Dashboard
│   │   # แสดง Risk Score, Risk State, Alerts, Charts
│   │
│   ├── api/
│   │   # Node.js 24 + Express API
│   │   # ให้บริการ REST API แก่ Frontend
│   │
│   └── worker/
│       # BullMQ Worker
│       # Daily Job สำหรับดึงข้อมูล คำนวณ Risk Score และสร้าง Alert
│
├── packages/
│   │
│   ├── risk-engine/
│   │   # Core Business Logic
│   │   # Risk Score Calculator
│   │   # State Machine
│   │   # Golden Signal Detector
│   │   # Alert Rule Evaluator
│   │
│   ├── database/
│   │   # Prisma Client
│   │   # Database Utilities
│   │   # Repository Helpers
│   │   # TimescaleDB Query Helpers
│   │
│   └── shared/
│       # Shared Types
│       # Shared Enums
│       # Shared Constants
│       # Zod Schemas
│       # DTOs
│
├── config/
│   │
│   ├── thresholds/
│   │   │
│   │   └── default-thresholds.json
│   │       # ค่า Threshold เริ่มต้นของ Indicators
│   │       # ห้าม Hardcode ใน Business Logic
│   │
│   ├── indicators/
│   │   │
│   │   └── indicator-registry.json
│   │       # รายชื่อ Indicators ที่ระบบติดตาม
│   │       # Code, Name, Layer, Source, Frequency
│   │
│   └── risk-score/
│       │
│       └── weights.json
│           # น้ำหนัก Risk Score
│           # เช่น SOFR = 12, US30Y = 12, Gold = 8
│
├── docker/
│   │
│   ├── postgres/
│   │   # Config สำหรับ PostgreSQL + TimescaleDB
│   │
│   ├── redis/
│   │   # Config สำหรับ Redis
│   │
│   └── nginx/
│       # Config สำหรับ Reverse Proxy ในอนาคต
│
├── scripts/
│   │
│   ├── setup.sh
│   │   # Setup project ครั้งแรก
│   │
│   ├── dev.sh
│   │   # Run development environment
│   │
│   └── migrate.sh
│       # Run Prisma migration
│
├── tests/
│   │
│   ├── unit/
│   │   # Unit Test
│   │   # โดยเฉพาะ packages/risk-engine
│   │
│   ├── integration/
│   │   # Integration Test
│   │   # API + Database + Worker
│   │
│   └── fixtures/
│       # Mock Data
│       # Historical Sample Data
│       # Indicator Test Data
│
├── tools/
│   │
│   └── data-importer/
│       # เครื่องมือช่วย Import Historical Data
│       # ใช้ตอน Backtest หรือ Seed Database
│
├── .env.example
│   # ตัวอย่าง Environment Variables
│
├── docker-compose.yml
│   # Local Development Services
│   # PostgreSQL, Redis, API, Worker, Web
│
├── package.json
│   # Root package.json สำหรับ Monorepo
│
├── tsconfig.base.json
│   # Base TypeScript Config ใช้ร่วมกันทั้ง Monorepo
│
└── README.md
    # Overview ของโปรเจกต์


อธิบาย
docs/       = ความรู้และ Source of Truth
apps/       = แอปที่รันจริง
packages/   = โค้ดที่ใช้ร่วมกัน
config/     = ค่า Config และ Threshold
docker/     = Infrastructure
tests/      = ทดสอบระบบ
tools/      = เครื่องมือช่วยพัฒนา