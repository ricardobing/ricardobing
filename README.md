<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/header-dark.svg">
  <img src="assets/header-light.svg" alt="Ricardo Brossard — AI Engineer · Full Stack Developer. I build AI products that run in production: LLMs handle language and judgment; deterministic code handles the numbers." width="100%">
</picture>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-ricardo--brossard-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/ricardo-brossard)
[![Email](https://img.shields.io/badge/Email-ricardobingeniero%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:ricardobingeniero@gmail.com)
![Location](https://img.shields.io/badge/Argentina_·_UTC--3-remote-2dd4bf?style=flat-square)

</div>

I design and build complete systems, from the database schema to the production UI, for businesses that run on WhatsApp, spreadsheets and manual work. I usually work as the only engineer, directly with the owner, and answer for the result end to end. AI is a component I engineer carefully: the model reads, talks and judges, while prices, state and money go through code that can be tested.

## Featured work

<table>
  <tr>
    <td width="50%">
      <a href="#lexinton-crm"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/card-crm-dark.svg"><img src="assets/card-crm-light.svg" alt="Lexinton CRM — live, client since May 2026. 3,500+ inquiries with no manual entry, 98% auto-linked to their property, 10 users." width="100%"></picture></a>
    </td>
    <td width="50%">
      <a href="#zizu"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/card-zizu-dark.svg"><img src="assets/card-zizu-light.svg" alt="Zizu — live, zizu.com.ar. Multi-merchant delivery with 4 real-time roles, 209 tests in CI, 118 migrations." width="100%"></picture></a>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <a href="#tomanota"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/card-tomanota-dark.svg"><img src="assets/card-tomanota-light.svg" alt="TomaNota — own product, live at tomanota.lat. AI WhatsApp assistant with 8 tools, 900+ tests, 1,203 simulated conversations." width="100%"></picture></a>
    </td>
    <td width="50%">
      <a href="#tasador-rag"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/card-tasador-dark.svg"><img src="assets/card-tasador-light.svg" alt="Tasador RAG — public code, verified with real data. 11-node LangGraph agent, retriever chosen over 113 queries, 547 tests." width="100%"></picture></a>
    </td>
  </tr>
</table>

---

<a id="lexinton-crm"></a>
## Lexinton CRM · every inquiry in one panel

**Real estate agency in Buenos Aires · Live since May 2026 · 10 users** · [panel.lexinton.com.ar](https://panel.lexinton.com.ar)

<img src="assets/crm-hero.webp" alt="Lexinton CRM: owner dashboard and the WhatsApp inbox inside the panel (demo data)" width="100%">

Buyer and tenant inquiries arrived every day through listing portals, Facebook ads and the website, and ended up in a shared inbox. Each one depended on someone copying it into a spreadsheet by hand. Now every inquiry lands in a single panel with no manual entry: already linked to the property it asks about, assigned to the right agent, and followed up from there, including on the agency's WhatsApp.

- **6 intake channels, zero manual entry.** The inbox is read every 15 minutes. Each inquiry is matched to its portal, repeat contacts are detected (also when the same lead arrives from the portal and again through Tokko), and the lead is linked to its property by listing code or, failing that, by address.
- **Tokko Broker integration.** Read-only mirror of the agency's listings, prices, developments and agents. The same inventory feeds the agency's website, which I also built: [lexinton.com.ar](https://lexinton.com.ar), with 177 pre-generated pages and a 100/100 SEO score.
- **WhatsApp on Meta's official Cloud API.** Every conversation sticks to the client's record. Signed webhooks, sends queued in PostgreSQL, 24-hour window handled with 9 approved templates.
- **Automations that know when to stop.** 7 follow-up flows, configurable from the panel, that cancel themselves the moment the client replies.
- **Google Calendar per agent** for visits, and a dashboard where the owner sees the business in numbers for the first time.

> **3,500+ inquiries · 98% of last month's portal leads linked to their property automatically · 207 valuations · 186 visits · 6,805 audited status changes · 100 unit + 33 E2E tests**

`Next.js 14` `TypeScript` `Supabase (PostgreSQL · RLS · Realtime · Edge Functions)` `Tokko Broker API` `WhatsApp Cloud API` `Gmail API` `Google Calendar API` `Vitest` `Playwright` `Vercel`

<sub>Screenshots use demo data.</sub>

---

<a id="zizu"></a>
## Zizu · multi-merchant delivery with online payments

**Client in Argentina · Live in production** · [zizu.com.ar](https://zizu.com.ar)

<img src="assets/zizu-hero.webp" alt="Zizu: customer catalog, and the same order updating live on the store's screen and the customer's timeline" width="100%">

In small cities, shops take orders by phone and WhatsApp, with no platform to coordinate customer, shop and courier. Zizu is that platform: the customer orders, the shop prepares, the courier delivers and the admin oversees, each on their own screen, all watching the same order update live. I built it solo, from scratch, in 4 milestones that were delivered, audited and billed.

- **Money that can't be corrupted.** Mercado Pago end to end: checkout, chargebacks, refunds and commissions, plus cash. Every payment is confirmed server to server through a signed, idempotent webhook. The payment ledger is append-only, protected by triggers, and can't be edited even with direct database access.
- **Rules live in the database, not the UI.** Row Level Security on all 30 tables and order state transitions enforced server-side, so each role can only make its own moves.
- **Atomic order assignment.** If two couriers tap "Take" at the same time, exactly one wins. This is verified by a real concurrency test.
- **Real time and installable.** Supabase Realtime across the four areas, an installable PWA, and code-splitting by role.

> **152 E2E + 57 unit tests on every change, against a production-identical environment · 118 versioned migrations · 4 milestones delivered and billed**

`React 18` `Vite` `TypeScript` `Supabase (PostgreSQL · RLS · Realtime · Edge Functions · pg_cron)` `Mercado Pago` `TanStack Query` `Zustand` `Playwright` `GitHub Actions` `Vercel`

---

<a id="tomanota"></a>
## TomaNota · an AI assistant that takes orders on WhatsApp

**Own product · Live** · [tomanota.lat](https://tomanota.lat) · [Try the demo, no sign-up](https://app.tomanota.lat/probar)

<img src="assets/tomanota-hero.webp" alt="TomaNota: product website and a full WhatsApp order confirmed on the phone" width="100%">

The neighborhood pizzeria takes orders on WhatsApp while the owner works the counter. At peak hours messages go unanswered and orders get jotted on paper, with mistakes. TomaNota answers that WhatsApp: it chats with the customer like a person would, builds the order with the menu's real prices, confirms it and drops it on a board for the shop to prepare. Orders from WhatsApp, the online QR menu and the counter all land on the same board.

- **The model can't get the money wrong.** It works through 8 tools with closed parameters: it emits product ids and quantities, and the server computes every price and total. No order exists until the customer taps *Confirm*. Anything that isn't on the menu doesn't get promised.
- **Deterministic guards before the model.** Messages are processed in order per chat, duplicates are discarded in Redis and in the database, the bot goes silent when the owner writes, and bot-to-bot loops are cut off. A rules engine takes over if the model fails.
- **Built for real stores.** Sizes, extras with min and max, nicknames ("muza"), half-and-half with its own price, and sale by weight. Delivery zones are inferred from the address: 17 of 17 real addresses resolved without asking.
- **Multi-tenant from the first table.** Row Level Security on 46 of 46 tables. A new store is configuration, not code.

<img src="assets/tomanota-panel.webp" alt="TomaNota store panel: delivery zones, product editor with sizes and extras, and the online menu on a phone" width="100%">

> **900+ automated tests (847 unit + 88 against real Postgres) · 13 full conversations stored as specification · test bench with 1,203 simulated conversations against the real model**

`Node.js 22` `TypeScript` `Fastify` `Vercel AI SDK · OpenAI-compatible API` `tool calling` `Supabase (PostgreSQL · RLS · Realtime)` `Redis` `WhatsApp Cloud API` `React 18` `Vite` `Docker` `Vitest`

---

<a id="tasador-rag"></a>
## Tasador RAG · property valuations where the model never sets the price

**Real estate agency in Buenos Aires · Full application verified end to end with real market data** · [Source code](https://github.com/ricardobing/tasador-rag)

To price a listing, an agent compares it by hand against similar listings: 30 to 60 minutes per valuation, with no written reasoning. Tasador produces the report in about a minute, with the comparable listings that justify the price. AI finds and reads the listings and decides which ones are comparable. **The price comes from an explicit formula, never from the model**, and every fact the AI extracts carries a quote that is checked against the original text, without AI.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/rag-eval-dark.svg">
  <img src="assets/rag-eval-light.svg" alt="Retriever comparison, nDCG@25 over 113 queries: SQL + recency 0.747, dense truncated 0.805, dense sentence chunks 0.760, lexical 0.821 (switched on), hybrid RRF 0.781, hybrid + reranker 0.790." width="100%">
</picture>

- **A full RAG stack, measured before choosing.** Chunking, local embeddings in pgvector, Spanish full-text search, Reciprocal Rank Fusion and a cross-encoder reranker. They were compared over 113 queries with a paired bootstrap, against acceptance criteria written *before* measuring. Lexical search, the simplest option, won and is the one switched on. Dense retrieval and the reranker are built, measured and switched off.
- **An 11-node LangGraph agent** with a Postgres checkpoint: if the process dies at step 6, it resumes at step 6.
- **A two-phase critic.** A deterministic pass traces every number in the generated text back to the data, and one untraceable number rejects the draft. An adversarial model pass follows. Audited with injected fake prices: 50.5% got through at first, and 4.3% after three measured fixes.
- **It knows when to say "I don't know".** With fewer than 5 valid comparables, it returns `INSUFFICIENT_DATA`. A second RAG ("Ask the report") answers with verified citations, or refuses in milliseconds when there's no evidence.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/tasador-architecture-dark.png">
  <img src="assets/tasador-architecture-light.png" alt="Tasador architecture: Next.js web, FastAPI API, Redis queue, LangGraph worker, PostgreSQL with pgvector, LiteLLM gateway and local models" width="100%">
</picture>

> **492 backend tests + 55 Playwright E2E tests against the real stack, in CI · 9-service Docker Compose · 2 to 5 US cents per report, cost traced per node**

`Python 3.12` `FastAPI` `LangGraph` `PostgreSQL 16 + pgvector` `Redis` `fastembed` `LiteLLM` `Next.js 15 (React 19, TypeScript)` `Docker Compose` `GitHub Actions` `pytest` `Playwright`

---

## More public work

| Project | What it shows |
| --- | --- |
| [**CORIS · Claude tool use agent**](https://github.com/ricardobing/CORIS-claude-tool-use) | Agent built on Anthropic's tool use: agent loop, schemas, parallel tools, prompt-injection defenses, retries with feedback, deterministic fallback, and cost, token and latency metrics |
| [**Doctor de Planillas**](https://github.com/ricardobing/excel-doctor) | Diagnoses and cleans messy Excel files: ~20 detectors, a 0-100 health score, and every fix logged |

## Stack

<p>
  <img src="https://skillicons.dev/icons?i=py,fastapi,ts,nodejs,react,nextjs,vite,tailwind&theme=dark" alt="Python, FastAPI, TypeScript, Node.js, React, Next.js, Vite, Tailwind">
  <br>
  <img src="https://skillicons.dev/icons?i=postgres,supabase,redis,docker,githubactions,vercel&theme=dark" alt="PostgreSQL, Supabase, Redis, Docker, GitHub Actions, Vercel">
</p>

**AI:** LangGraph · Vercel AI SDK · Anthropic Claude · OpenAI-compatible APIs · tool calling · RAG (pgvector, full-text, RRF, reranking) · retrieval evaluation (nDCG, MRR, bpref) · eval benches against the real model

**Integrations:** WhatsApp Cloud API · Mercado Pago · Tokko Broker · Gmail API · Google Calendar API · signed, idempotent webhooks · Make

**Quality:** Playwright E2E · Vitest · pytest · CI on every push · RLS and concurrency tests · environments identical to production

## How I work

- **I own the problem, not a ticket.** I take it from the first conversation with the owner to the schema, the API, the UI, the deploy and the support after launch.
- **I build with AI agents, and I test like it.** I design the architecture and direct AI coding agents (Claude Code) to build it. Quality comes from automated tests and CI on every push, not from ceremony.
- **The model never touches the money.** LLMs handle language and judgment. Prices, totals, state transitions and confirmations go through deterministic code that tests can pin down.
- **I measure before I decide.** Retrievers, prompts and critics get compared with a metric written down beforehand, and I switch on what wins, even when it's the least impressive option.

<div align="center">

**Systems Engineering, Universidad Tecnológica Nacional (UTN)** · English: professional written communication (docs, email, Slack, PRs)

[LinkedIn](https://linkedin.com/in/ricardo-brossard) · [ricardobingeniero@gmail.com](mailto:ricardobingeniero@gmail.com)

</div>
