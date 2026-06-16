<div align="center">

# Ricardo Brossard

### AI Integration · Full Stack Developer · Python Backend · Data Engineering

*I build systems that work without supervision — production pipelines, LLM integrations,*  
*and operational tools with real clients and measurable outcomes.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/ricardo-brossard)
[![Email](https://img.shields.io/badge/ricardobingeniero@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:ricardobingeniero@gmail.com)
[![Live Demo](https://img.shields.io/badge/KPI_Dashboard_(live)-000000?style=flat-square&logo=vercel&logoColor=white)](https://excel-to-kpi-dashboard.streamlit.app/)

📍 Argentina · UTC-3 · Available for remote roles worldwide

</div>

---

## What I bring to a team

I design and ship **end-to-end systems** — from database schema to API to production UI — with a strong emphasis on AI integration and workflow automation. My background is in Systems Engineering, and every project I've delivered has had a real client, a real problem, and a real outcome attached to it.

I work well in environments that value **autonomy, technical depth, and delivery over process.** I don't need daily standups to stay aligned, and I don't ship code without tests.

---

## Featured Projects

---

### 🏠 Real Estate CRM — Automated Lead Pipeline · React · Next.js · Python

**Lexinton Propiedades, Palermo, Buenos Aires · 4+ months in active production**  
🔗 [tokkoleads.vercel.app](https://tokkoleads.vercel.app)

A real estate agency was receiving 200+ weekly leads across three portals (ZonaProp, Argenprop, Meta Ads) into a shared Gmail inbox with no system. Agents responded from memory, leads went cold, and management had zero pipeline visibility. Average response time: **54 hours**.

**What I built:**

The ingestion pipeline runs every 20 minutes: Gmail API with OAuth2 → specialized HTML parsers per portal → 4-layer fuzzy Property Matcher (normalizes abbreviations, resolves ambiguous addresses, deduplicates across a 30-minute window) → PostgreSQL with 3-level deduplication. DB Triggers fire automatic alerts for leads untouched for 24+ hours. WhatsApp Cloud API delivers contextual action buttons based on pipeline stage.

The operational frontend runs on Next.js 14 with TanStack Table v8, inline state selectors via React Portal (no disruptive modals), real-time updates via Supabase subscriptions, and a detail drawer with full interaction history and auto-save by debounce. The management dashboard has KPI cards, area chart by portal source (Recharts), agent performance tracking, and role-based access (Admin / Agent) with Row Level Security.

Python work: email parsers, Property Matcher design and validation, re-matching scripts, 40+ pytest test cases against real production data.

> **1,100+ leads captured automatically · 0 duplicates in 4 months · response time 54h → <24h · team eliminated manual inbox review**

![Next.js](https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

---

### 🌐 Real Estate Website — Next.js 14 · Tokko Broker API · ISR · Supabase

**Lexinton Propiedades, Palermo, Buenos Aires · Live in production**  
🔗 [lexinton.com.ar](https://lexinton.com.ar)

The same agency had an outdated WordPress site with no real-time integration to their CRM. Properties were updated manually. Leads generated from the site never reached their system. They depended entirely on ZonaProp and Argenprop for inbound inquiries.

**What I built:**

Full website from scratch. Next.js Route Handlers act as a secure proxy to Tokko Broker (the leading real estate CRM in Argentina) — the API key never reaches the client. ISR with staggered revalidation (300s for properties / 600s for featured & developments) keeps 175+ listings fresh without hammering the API on every visit. Property gallery with lightbox and pinch-to-zoom. Smart neighborhood grouper (Palermo → Soho / Hollywood / Chico / Botánico). Mobile contact modal as bottom-sheet. Framer Motion with dynamic imports to protect TBT. Dual lead system: every form submission goes simultaneously to Tokko via webcontact API and to a proprietary panel in Supabase. 177 property routes pre-generated at build time.

Technical problems solved along the way: Tokko has no public documentation — I mapped the real endpoint structure and required parameters (including `lang=es`) through Python debugging scripts. Property descriptions arrived mixed with a Lexinton footer in the same field — solved with a marker-based cleaning algorithm. Multiple image hostnames from Tokko required dynamic `remotePatterns` configuration in `next.config.mjs`.

> **175+ properties in real time · SEO 100/100 · Accessibility 91/100 · CLS 0 · 177 ISR pre-generated routes · direct lead channel independent of third-party portals**

![Next.js](https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Framer Motion](https://img.shields.io/badge/Framer_Motion-0055FF?style=flat-square&logo=framer&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

---

### 🤖 Real Estate Lead Automation — Make · GPT-4.1 · WhatsApp · Google Apps Script

**Inmobiliaria, Buenos Aires · Active in production**

The commercial team spent 3 hours per day reading incoming messages across multiple channels to identify and classify appraisal opportunities, then following up manually with no traceability or automatic status tracking.

**What I built:**

GPT-4.1 reads each incoming message and classifies commercial intent from natural language ("I want to sell my apartment", "I need my property appraised") returning a structured JSON with category and confidence score. Appraisal leads are automatically routed into a WhatsApp sequence: welcome message + timed follow-ups that stop the moment the client responds. When the agent books a site visit, Google Calendar syncs automatically. A CRM view over Google Sheets tracks full conversation history, status transitions (contacted → qualified → scheduled → completed), phone normalization, and event deduplication. Make handles inbound message routing; Google Apps Script runs all business logic, state management, and integrations.

> **50+ leads/week processed automatically · 3h/day of manual classification → 0h/day · 15 hours/week saved · leads visible to the team in < 15 minutes**

![Make](https://img.shields.io/badge/Make_(Integromat)-6D00CC?style=flat-square&logo=make&logoColor=white)
![Google Apps Script](https://img.shields.io/badge/Apps_Script-4285F4?style=flat-square&logo=google&logoColor=white)
![OpenAI](https://img.shields.io/badge/GPT--4.1-412991?style=flat-square&logo=openai&logoColor=white)
![WhatsApp](https://img.shields.io/badge/WhatsApp_Cloud_API-25D366?style=flat-square&logo=whatsapp&logoColor=white)
![Google Calendar](https://img.shields.io/badge/Google_Calendar_API-4285F4?style=flat-square&logo=googlecalendar&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=flat-square&logo=googlesheets&logoColor=white)

---

### 🚚 Logistics Platform — FastAPI · GPT-4.1 · Google Maps · React

**Distribution company, Mendoza, Argentina**

Hundreds of daily delivery orders were managed through Google Sheets with manual classification. The specific technical challenge: customers entered delivery addresses in free text, and in Mendoza the street nomenclature is inconsistent — unofficial names, changed references, intersections-as-landmarks — which breaks standard geocoders.

**What I built:**

Backend in FastAPI: GPT-4.1 interprets natural language addresses using context engineering with local domain vocabulary and real Mendoza examples. Output includes a normalized address + confidence score; low-confidence cases go to an operator review queue before route generation. Google Maps API with intelligent caching avoids reprocessing known addresses (70%+ API call reduction). Automated order classification engine (own delivery / pickup / carrier) runs on configurable business rules. Real-time observability module logs latency, token usage, and cost per API provider.

Frontend in Next.js/React: operational Kanban board (Ingresado → Listo → Despachado → Pagado), route assignment dashboard, automated daily close. Infrastructure: Docker Compose with 3 containers, PostgreSQL with Alembic migrations.

> **Route calculation 5 min → 15 seconds (20x faster) · Automated geocoding for the vast majority of orders with human review only for genuinely ambiguous cases**

![Python](https://img.shields.io/badge/Python_3.12-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![OpenAI](https://img.shields.io/badge/GPT--4.1-412991?style=flat-square&logo=openai&logoColor=white)
![Google Maps](https://img.shields.io/badge/Google_Maps_API-4285F4?style=flat-square&logo=googlemaps&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

---

### ⚽ Football Stats ETL — Autonomous Data Pipeline · Python · PostgreSQL · Railway

**Professional coach, Primera Autonómica Preferente, Castilla-La-Mancha, Spain**

The regional football federation publishes official match records on a JavaScript-rendered site with no public API. Extracting weekly statistics manually took 3–5 hours per matchweek. The coach needed advanced metrics — individual impact, goal value, substitution patterns, card accumulation — available every Monday without manual intervention.

**What I built:**

Scraper in Selenium with checkpoint/resume via JSON state file and exponential backoff retry. ETL pipeline in Python with strict layer separation: parsers → identity resolvers (players by federation code, coaches by fuzzy matching with abbreviation normalization) → business validators (6 pre-insert validations: scoreline coherence vs. goals, duplicates, referential integrity) → idempotent loaders with ON CONFLICT throughout. A backfill module recalculated 9,226 historical rows from existing data without touching the source.

PostgreSQL data warehouse with 6 schemas (dimensions, facts, analytics, BI, audit, ETL config), star schema, 14 materialized views refreshed with REFRESH CONCURRENTLY, and 59 active DML audit triggers capturing full JSON before/after for every table write. Railway cron runs the full cycle every Monday, autonomously.

> **749 matches · 1,607 goals classified · 968 players tracked · 16,992+ audited changes · 12+ autonomous runs · 0% error rate · ~25 minutes per matchweek (was 3–5 hours)**

![Python](https://img.shields.io/badge/Python_3.12-3776AB?style=flat-square&logo=python&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=flat-square&logo=selenium&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=flat-square&logo=railway&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

---

### 📊 KPI Commercial Dashboard — Open Source · Python · Streamlit

**Public portfolio project**  
🔗 [Live demo](https://excel-to-kpi-dashboard.streamlit.app/) · [Source code](https://github.com/ricardobing/excel-to-kpi-dashboard)

A data pipeline with strict layer separation (ETL / KPI engine / Pareto A-B-C segmentation / automated alert engine). 51 pytest tests validate the complete business logic independently from the UI. 30,000+ records processed in under 3 seconds. Full source code visible on GitHub — this one you can actually read.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat-square&logo=plotly&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

---

## Tech Stack

**AI / LLMs**

![OpenAI](https://img.shields.io/badge/OpenAI_GPT--4.1-412991?style=flat-square&logo=openai&logoColor=white)
![Anthropic Claude](https://img.shields.io/badge/Claude_(Anthropic)-D97757?style=flat-square&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=google&logoColor=white)
![DeepSeek](https://img.shields.io/badge/DeepSeek-536AF5?style=flat-square&logoColor=white)

Context engineering · Prompt engineering · Structured output / function calling · Agentic workflows · AI observability

**Python Backend**

![Python](https://img.shields.io/badge/Python_3.12-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![Alembic](https://img.shields.io/badge/Alembic-6BA539?style=flat-square&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=flat-square&logo=selenium&logoColor=white)

**Frontend**

![Next.js](https://img.shields.io/badge/Next.js_14/16-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript_5-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Zustand](https://img.shields.io/badge/Zustand-443E38?style=flat-square&logoColor=white)
![TanStack](https://img.shields.io/badge/TanStack_Query_/_Table-FF4154?style=flat-square&logo=reactquery&logoColor=white)
![Recharts](https://img.shields.io/badge/Recharts-22B5BF?style=flat-square&logoColor=white)
![Framer Motion](https://img.shields.io/badge/Framer_Motion-0055FF?style=flat-square&logo=framer&logoColor=white)

**Databases**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL_(advanced)-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)

Window functions · CTEs · Materialized views · Triggers · Row Level Security · Star schema · Dimensional modeling

**Automation**

![Make](https://img.shields.io/badge/Make_(Integromat)-6D00CC?style=flat-square&logo=make&logoColor=white)
![Google Apps Script](https://img.shields.io/badge/Google_Apps_Script-4285F4?style=flat-square&logo=google&logoColor=white)
![Supabase Edge Functions](https://img.shields.io/badge/Supabase_Edge_Functions_(Deno)-3FCF8E?style=flat-square&logo=deno&logoColor=white)

Webhooks · DB Triggers · Cron jobs · REST API integrations · Gmail API · WhatsApp Cloud API · Google Maps API · Google Calendar API

**Infrastructure**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=flat-square&logo=railway&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub_/_CI/CD-181717?style=flat-square&logo=github&logoColor=white)

**Testing**

![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

Unit tests · Integration tests · Data quality checks · Business logic validation

---

## How I work

**I think in systems, not features.**  
Before writing a single line I model the data, define the contracts between layers, and map the failure modes. The architecture exists before the first commit.

**I measure what I ship.**  
Every project I've delivered has metrics: leads captured, hours saved, time reduced. I don't consider something done until I can tell the client whether it's working.

**I own the full stack.**  
I take a problem from database schema to API to production UI. No handoffs between layers — one person who understands the whole system.

**I integrate AI where it solves a real problem.**  
Not as a feature, but as a component — with context engineering, structured output validation, fallback logic, and observability. If the LLM fails, the system degrades gracefully instead of silently hallucinating.

**I work async, document as I go, and don't need supervision to stay on track.**  
I've shipped production systems as a solo contributor. I know how to make decisions independently and communicate them clearly in writing.

---

## Education

**B.Eng. in Information Systems Engineering**  
Universidad Tecnológica Nacional (UTN) — Facultad Regional Concepción del Uruguay, Argentina

---

<div align="center">

📍 Argentina · UTC-3 · Open to remote roles worldwide

✉️ [ricardobingeniero@gmail.com](mailto:ricardobingeniero@gmail.com) · [LinkedIn](https://linkedin.com/in/ricardo-brossard)

*If you're building something serious and need someone who ships — let's talk.*

</div>
