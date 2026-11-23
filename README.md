# Cristian Maldonado Román

**Civil Engineer · AEC Software Engineer · Founder & Lead, Innovation @ IDOM Chile**

Civil engineer (Universidad Diego Portales, Chile) operating as an AEC software engineer. I founded and run IDOM Chile's Innovation function (Apr 2025) as a solo initiative. In 19 months it has shipped 20+ internal tools, with 1,090+ commits across 27 repositories, used by project teams in Santiago and shared with IDOM's international **iHub for BIM & Digital Twins**. Six years of AEC field experience on hospital, residential and education projects from 6,000 m² to 210,000 m² informs what I build and why.

📍 Santiago, Chile · ✉️ maldonado.c24@icloud.com · 🔗 linkedin.com/in/cristian-maldonado

---

## How I work

The function operates like an **internal platform team**: one engineer owns delivery, quality, security and standards for tools that serve several projects and disciplines. I also administer two of IDOM's GitHub Enterprise organizations and maintain the base templates and working rules the other repositories start from.

---

## Stack

**Languages** — C# (.NET 8 + .NET Framework 4.8) · TypeScript · Python 3.12 · SQL · PowerShell  
**AEC / BIM** — Revit API (2023–2026, 4 versions built from one solution) · Navisworks API · AutoCAD COM Automation · Dynamo · IFC2x3/IFC4 export · BIM Execution Plans · multi-discipline coordination · PlanBIM · ISO 19650  
**Web / Backend** — Next.js 15 (App Router) · React 19 · FastAPI · Prisma · SQLAlchemy 2.0 · PostgreSQL / Supabase · PWA (offline-first) · NextAuth v5 + Microsoft Entra ID  
**Desktop** — WPF + MVVM · ClosedXML · iText7 · DocumentFormat.OpenXml · Inno Setup (no-admin installers) · PyInstaller  
**Quality** — xUnit · Vitest · Playwright · GitHub Actions CI/CD · health monitors and tested backups  
**Cloud / DevOps** — Azure (read-only diagnostics, Bicep IaC, Azure MCP) · Vercel · Docker · Coolify  
**AI / LLM** — Gemini 2.5 Flash (batch prompting, few-shot, rate-limit handling) · Azure AI Foundry GPT-4.1 · repository-level agent rules (`AGENTS.md` / `CLAUDE.md`) in 10+ repos

---

## Production Portfolio

The repositories are private (IDOM IP), so each entry says what I built and how much of it is mine. Commit counts come from git history, not from the platform's contributor statistics.

---

### IDOM Tools — Revit Add-in *(flagship, sole developer)*
> **Multi-module Revit ribbon add-in** deployed across IDOM offices. 19 months of continuous development, 202 commits, v2.9.0.

**Stack**: C# · .NET Framework 4.8 · Revit API (2023–2026, 4 build targets) · WPF / Windows Forms · xUnit project on .NET 8 · Supabase  
**Highlights**: modeling, coordination, review, management and export tools. A **multi-format export manager** (PDF/DWG/DWF) with token-based filename resolution. A **BIM QA/QC data extractor** that batch-exports 26 categories of raw model data across a folder of `.rvt` files. Architecture: `Core / Commands / Services / Models / UI`, an `IExportService` strategy interface and a generic `IDataExtractor<T>` used by 25 extractors. **49 xUnit tests** on versioned JSON contracts.

---

### IDOM BIM Orchestrator — Revit ⇄ Navisworks Automation *(sole developer)*
> Built to replace a **closed, vendor-supplied BIM coordination installer** with a tool IDOM controls. v1.3.2, 115 commits.

**Stack**: .NET 8 + .NET Framework 4.8 · Revit API · Navisworks Manage API · WPF · Inno Setup · Windows Task Scheduler API  
**Highlights**: exports configured 3D views to `.nwc`, `.ifc` and `.pdf`, updates Navisworks Clash Detective tests, and runs interactively or unattended. Supports Revit and Navisworks 2023–2026 from one solution. Scheduled tasks run under the user's own account and install **without admin rights**. **37 of 37 real-environment test cases passed**, plus 200 automated tests, as recorded in the repo's test log. The documentation separates "verified" from "compiles but unverified".

---

### Public Procurement Monitor — web platform *(sole developer)*
> **Corporate web platform** that monitors Chile's Mercado Público tenders and filters those relevant to the bidding team. v2.0.2, 115 commits. Rewritten from a WPF desktop app to the cloud.

**Stack**: Next.js 15 · React 19 · TypeScript · Prisma · PostgreSQL (Supabase) · `pg_cron` ingestion · Vitest · Playwright · GitHub Actions → Vercel  
**Highlights**: ingestion every 5 minutes with a persistent queue and retries; shared and personal search profiles; Excel/CSV export. **283 unit + 14 integration + 15 E2E tests** in CI. Health check every 30 minutes that opens and closes an issue automatically, plus a weekly backup workflow with a tested restore. 28 authorized users.

---

### Field Records — offline-first PWA *(sole developer, in development)*
> **Installable PWA for construction-site data capture and supervision**, usable with and without connection. First project: project management of a land-remediation project.

**Stack**: Next.js 15 · TypeScript · service worker · Prisma · PostgreSQL (Supabase) · Vitest with embedded PGlite  
**Highlights**: a record form common to all disciplines and configurable per project; server/client sync; 656 automated tests, CI green; 37 numbered architecture decisions documented. Known limits are stated in the repo: pilot with real data still pending.

---

### Internal R&D Portal *(sole developer)*
> **Tool-catalogue and request-management portal** that replaced an email-driven flow with a tracked, role-based workflow. v1.0.0, 111 commits.

**Stack**: Next.js 15 · TypeScript · Prisma + PostgreSQL/Supabase · NextAuth v5 + Microsoft Entra ID · Vitest · Vercel  
**Highlights**: corporate SSO restricted to the company tenant; 2FA with session revocation, CSP/HSTS and rate limiting; PostgreSQL full-text search (`tsvector` + GIN); a `test:critical` suite for auth, permissions and rate limiting.

---

### Decision Engine for infrastructure alternatives *(sole developer)*
> **Web tool to compare infrastructure alternatives** with data that shows its source and confidence level: prioritize, size, and estimate cost and transaction scheme.

**Stack**: Next.js 15 · React 19 · TypeScript · Vitest (187 unit tests) + Playwright · Vercel · GitHub Actions  
**Highlights**: versioned JSON datasets; first horizon delivered in 10 days for an internal presentation.

---

### Office Booking App *(sole developer)*
> **Booking web app** for office parking and corporate vehicles. v1.7.0, 213 unit tests. Became the **reference architecture** that I reused for the Procurement Monitor and the Field Records PWA.

**Highlights**: double booking prevented by a **PostgreSQL constraint, verified with 8 simultaneous requests**; weekly and monthly calendar; admin panel with audit trail.

---

### BIM Document Generator *(co-developer · Spain–Chile collaboration, iHub BIM & Digital Twins)*
> **AI-assisted BIM Execution Plan (BEP) generator** with project management, document storage and embedded AI assistants. Co-developed with an IDOM Spain colleague (I authored 49 of 99 commits).

**My scope**: backend, BEP form resources, and the 2026 delivery of the editor and dashboard, multi-document generation, project/draft persistence, upload and extraction, the AI chat assistant and the template system.  
**Stack**: Python 3.12 · FastAPI · SQLAlchemy 2.0 · Lit 3 + Vite · PostgreSQL/Supabase · Azure AI Foundry (GPT-4.1) · Docker

---

### DWG Manager — Export Layouts *(sole developer, v4.4.0)*
> **WPF tool for the Structures team**: manages AutoCAD `.dwg` files and exports layouts to individual DWGs via AutoCAD COM Automation.

**Stack**: .NET 8 · WPF + MVVM · AutoCAD COM · P/Invoke · Supabase telemetry  
**Highlights**: bulk layout export with a **P/Invoke dialog dismisser** for unattended runs; an **"AutoFix" flow** that repairs dimension-layer artifacts specific to Revit-to-DWG exports. Migrated from a legacy Python implementation.

---

### ExcelCompleteAI *(sole developer, v2.1.0)*
> **WPF app** that fills incomplete Excel review files using Gemini 2.5 Flash, built for AEC engineers answering repetitive review observations.

**Highlights**: **2-pass pipeline** (local keyword index first, AI only for unknowns); **batch prompting** (5× fewer API calls); **neighbor-context few-shot**; exponential backoff that tells rate limits from exhausted quota.

---

### Cloud and standards work
- **Azure administration** — read-only diagnostic of a corporate Azure subscription with an executive report of prioritized findings, Bicep IaC (validated locally, not deployed), naming/tag/region guardrails and an Azure MCP configuration.
- **Organization templates** — base repositories and technical standards for two IDOM units: project template, technology matrix, contribution rules, issue/PR templates and AI-agent working rules.
- **Reporting pipeline for the BIM QA/QC Validator** — I contributed 38 of 175 commits to this team project: the scheduled email KPI report (GitHub Actions), secrets handling and deployment. The validation engine is mainly a colleague's work.

### Smaller tools
Word Document Manager (WPF + OpenXml, [public mirror](https://github.com/CristianMaldonado24/IDO_GEN_WordManager)) · Document Management Suite (5 Python tools consolidated into one WPF app) · Excel/Power BI prep tool · Man-hours consolidation (migrated from VBA, source kept for traceability) · Navisworks add-in · installer generator for no-admin deployment · Site-activity analytics for a remediation project · DWG bulk text editor.

---

## AEC Background

- Hospital-sector BIM projects for Chile's public health network (IDOM, 2022–present) — structural + MEP modeling and Dynamo automation tooling
- +210,000 m² hospital project (René Lagos Engineers, 2020–2022) — structural modeling and rebar detailing at Design and Detail Design stages
- +70,000 m² mixed-use project (Freelance) — BIM coordination and full MEP modeling across 11 disciplines
- Education (+30,000 m²) and police facilities (+6,000 m²) (Freelance) — structural BIM

---

## Education & Certifications

- **Civil Engineering** — Universidad Diego Portales (2014–2019)
- **Parametric Design with Visual Programming in BIM** — Diploma, Zigurat Global Institute of Technology (Barcelona), 2021
- **Leading Digital Transformation** — MIT Professional Education (40 hrs), via Becas Santander, 2020
- **Dynamo and Revit API with C#** — BMLearning specialization
- **Introduction to BIM Methodology** — PlanBIM (score 90/100), 2020
- **WallStreet English** — Level 16, B2/C1 CEFR (in active progression)

---

*All production repos are private (IDOM IP). Available to discuss architecture, design decisions and outcomes directly.*
