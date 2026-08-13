<div align="center">

# Ricardo Brossard

### AI Engineer · Full Stack Developer

**Python · FastAPI · LLMs · OpenAI | React · Next.js · TypeScript · Node.js · PostgreSQL**

*I build full-stack systems with AI and automation that ship to production*
*and get used every day — real clients, real problems, measurable outcomes.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/ricardo-brossard)
[![Email](https://img.shields.io/badge/ricardobingeniero@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:ricardobingeniero@gmail.com)
[![Zizu Demo](https://img.shields.io/badge/Zizu_Delivery_(live_demo)-000000?style=flat-square&logo=vercel&logoColor=white)](https://delivery-ten-mu.vercel.app)
[![KPI Dashboard](https://img.shields.io/badge/KPI_Dashboard_(live)-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://excel-to-kpi-dashboard.streamlit.app/)

📍 Argentina · UTC-3 · Available for remote roles worldwide

</div>

---

## What I bring to a team

I design and ship **end-to-end systems** — from database schema to API to production UI, across **TypeScript and Python backends** — with a strong emphasis on AI integration and workflow automation. My background is in Systems Engineering, and every project I've delivered has had a real client, a real problem, and a real outcome attached to it.

I work well in environments that value **autonomy, technical depth, and delivery over process.** I don't need daily standups to stay aligned, and I don't ship code without tests.

---

## Featured Projects

---

### 🛵 Zizu — Multi-Store Delivery Platform · React · TypeScript · Supabase · Mercado Pago

**Real client, billed by milestones · Live on Vercel**
🔗 [delivery-ten-mu.vercel.app](https://delivery-ten-mu.vercel.app)

A delivery platform for small cities, built solo from zero to production. One SPA, four role areas — customer, store, courier, admin — coordinated in real time over a single Postgres database. The hard part was never the UI: it was making payments, accounting and courier assignment impossible to corrupt.

**What I built:**

- **Multi-tenant isolation via Row Level Security** on every table — each store and courier sees exactly their own data; the same pattern as a multi-tenant SaaS.
- **Order state machine enforced in the database** (`security definer` functions): each role can only execute its own transitions. The UI disables buttons, but the rule holds even against direct API calls.
- **Real-time everything** (Supabase Realtime): new orders ring on the store's screen, the customer's timeline updates live, out-of-stock items vanish from open menus.
- **Atomic courier assignment** — two couriers tapping "Take" simultaneously get exactly one winner, verified with a real concurrency test (two competing sessions).
- **Mercado Pago end-to-end**: server-to-server payment confirmation, signed (HMAC) idempotent webhook, chargebacks and refunds covered by tests, and an **append-only accounting ledger** protected by triggers — changing today's commission can never rewrite yesterday's books.
- **Installable PWA** with custom install UX for Android and iOS.

<img src="assets/zizu-realtime.png" alt="Zizu — store screen receiving an order while the customer timeline updates live" width="100%">

<table>
  <tr>
    <td width="50%"><img src="assets/zizu-catalog.png" alt="Zizu — customer catalog" width="100%"></td>
    <td width="50%"><img src="assets/zizu-courier.png" alt="Zizu — courier view with an order ready for pickup" width="100%"></td>
  </tr>
</table>

> **138 E2E tests (Playwright, real browsers) on every push in GitHub Actions · 101 versioned SQL migrations — the whole system reproduces from the repo · 4 milestones delivered and billed · test environment identical to production, self-restoring after every CI run**

![React](https://img.shields.io/badge/React_18-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Mercado Pago](https://img.shields.io/badge/Mercado_Pago-00B1EA?style=flat-square&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

---

### 🏠 Real Estate CRM with WhatsApp built in — Next.js 14 · Supabase · WhatsApp Cloud API

**Lexinton Propiedades, Buenos Aires · In production since April 2026 · 8 daily active users**
🔗 [panel.lexinton.com.ar](https://panel.lexinton.com.ar)

The agency ran on spreadsheets — one per property. Leads were logged by hand (or not at all), follow-up depended on each agent's memory, and the owner had zero visibility. Today the entire agency operates on one system, and the business's WhatsApp lives inside it.

**What I built:**

- **Automatic lead ingestion from 5 sources** (ZonaProp, Argenprop, Tokko, Meta Ads, web chat) via Gmail API: one parser per portal, deduplication in a 30-minute window, and **4-layer fuzzy matching** against the property inventory — leads land in the panel with the right property already linked.
- **Sales and appraisal pipelines as state machines** with a full audit trail: who changed what, and when — always.
- **WhatsApp Cloud API integrated directly — no BSP, no monthly license**: a multi-agent inbox inside the panel (per-context tabs, live unread counters, role-based permissions), HMAC-SHA256 signed webhook, and 24-hour-window handling with Meta-approved templates read live from the API.
- **An automation engine backed by a Postgres queue**: messages scheduled by business events (new appraisal, status change, upcoming visit), with configurable offsets, business-hours windows — and **automatic cancellation of the whole chain the moment the client replies**. 7 flows, all configurable from the panel without touching code.
- Google Calendar integration (per-user OAuth) and a results dashboard the owner opens every morning.

It replaced a stack of Google Sheets + Apps Script + Make + OpenAI (with monthly costs) with a one-time-payment system.

<img src="assets/crm-whatsapp-inbox.png" alt="Multi-agent WhatsApp inbox inside the CRM (demo data)" width="100%">

<table>
  <tr>
    <td width="50%"><img src="assets/crm-dashboard.png" alt="Owner dashboard — KPIs and weekly evolution (aggregated metrics only)" width="100%"></td>
    <td width="50%"><img src="assets/crm-ingestion-architecture.png" alt="Ingestion architecture — 5 sources, zero manual entry" width="100%"></td>
  </tr>
</table>

<sub>*Screenshots use synthetic/demo data — no real client information.*</sub>

> **2,631 leads · 383 appraisals · 3,695 audited status changes · 8 daily users · 9 Meta-approved WhatsApp templates · 7 automation flows · response time cut from 54h to under 24h**

![Next.js](https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![WhatsApp](https://img.shields.io/badge/WhatsApp_Cloud_API-25D366?style=flat-square&logo=whatsapp&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

---

### 🌐 Real Estate Website — Next.js 14 · Tokko Broker API · ISR · Supabase

**Lexinton Propiedades, Buenos Aires · Live in production**
🔗 [lexinton.com.ar](https://lexinton.com.ar)

Full website from scratch, replacing an outdated WordPress with no CRM integration. Next.js Route Handlers act as a secure proxy to Tokko Broker — the API key never reaches the client. ISR with staggered revalidation keeps 175+ listings fresh without hammering the API. Dual lead system: every form submission goes simultaneously to Tokko and to the CRM above. Tokko has no public documentation — I mapped the real endpoint structure through Python debugging scripts.

> **175+ properties in real time · SEO 100/100 · CLS 0 · 177 ISR pre-generated routes · direct lead channel independent of third-party portals**

![Next.js](https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

---

### 📊 KPI Commercial Dashboard — Open Source · Python · Streamlit

**Public portfolio project**
🔗 [Live demo](https://excel-to-kpi-dashboard.streamlit.app/) · [Source code](https://github.com/ricardobing/excel-to-kpi-dashboard)

A data pipeline with strict layer separation (ETL / KPI engine / Pareto A-B-C segmentation / automated alert engine). 51 pytest tests validate the complete business logic independently from the UI. 30,000+ records processed in under 3 seconds. Full source code visible on GitHub — this one you can actually read.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

---

## Tech Stack

**AI / LLMs**

![OpenAI](https://img.shields.io/badge/OpenAI_GPT--4.1-412991?style=flat-square&logo=openai&logoColor=white)
![Anthropic Claude](https://img.shields.io/badge/Claude_(Anthropic)-D97757?style=flat-square&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=google&logoColor=white)

Context engineering · Prompt engineering · Structured output / function calling · Deterministic fallback + human escalation · Agentic workflows · AI observability

**Backend**

![Python](https://img.shields.io/badge/Python_3.12-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase Edge Functions](https://img.shields.io/badge/Edge_Functions_(Deno)-3FCF8E?style=flat-square&logo=deno&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=flat-square&logo=selenium&logoColor=white)

**Frontend**

![Next.js](https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React_18/19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Zustand](https://img.shields.io/badge/Zustand-443E38?style=flat-square&logoColor=white)
![TanStack](https://img.shields.io/badge/TanStack_Query_/_Table-FF4154?style=flat-square&logo=reactquery&logoColor=white)
![PWA](https://img.shields.io/badge/PWA-5A0FC8?style=flat-square&logo=pwa&logoColor=white)

**Databases**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL_(advanced)-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)

Row Level Security · Triggers · Append-only ledgers · Window functions · CTEs · Materialized views · State machines in the database · Realtime

**Integrations & Automation**

![Mercado Pago](https://img.shields.io/badge/Mercado_Pago-00B1EA?style=flat-square&logoColor=white)
![WhatsApp](https://img.shields.io/badge/WhatsApp_Cloud_API-25D366?style=flat-square&logo=whatsapp&logoColor=white)
![Make](https://img.shields.io/badge/Make_(Integromat)-6D00CC?style=flat-square&logo=make&logoColor=white)
![Google Apps Script](https://img.shields.io/badge/Google_Apps_Script-4285F4?style=flat-square&logo=google&logoColor=white)

Signed webhooks (HMAC) · Idempotent payment processing · Gmail API · Google Calendar API · Google Maps API · Cron jobs · DB triggers

**Testing & Infrastructure**

![Playwright](https://img.shields.io/badge/Playwright_E2E-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions_CI/CD-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=flat-square&logo=railway&logoColor=white)

E2E tests in real browsers · Concurrency tests · RLS security tests · Test environments identical to production · Feature flags

---

## How I work

**I think in systems, not features.**
Before writing a single line I model the data, define the contracts between layers, and map the failure modes. The architecture exists before the first commit.

**I measure what I ship.**
Every project I've delivered has metrics: leads captured, hours saved, time reduced. I don't consider something done until I can tell the client whether it's working.

**I own the full stack.**
I take a problem from database schema to API to production UI. No handoffs between layers — one person who understands the whole system.

**I integrate AI where it solves a real problem.**
Not as a feature, but as a component — with context engineering, structured output validation, fallback logic, and observability. If the LLM fails, the system degrades gracefully instead of silently hallucinating. And I know when *not* to use it: I once replaced a monthly OpenAI classification bill with deterministic rules that did the same job for free.

**I work async, document as I go, and don't need supervision to stay on track.**
I've shipped production systems as a solo contributor. English: professional written communication — docs, email, Slack, PRs.

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
