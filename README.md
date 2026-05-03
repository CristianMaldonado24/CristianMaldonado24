# Cristian Maldonado Román

**Civil Engineer · AEC Software Engineer · Innovation Lead**

Civil engineer (Universidad Diego Portales, Chile) operating as an AEC software engineer. As **Innovation Lead at IDOM Chile**, I founded and run a solo innovation function (Apr 2025) that ships production tooling used across the office and IDOM's international **iHub for BIM & Digital Twins**. Six years of AEC field experience on hospital, residential and education projects from 6,000 m² to 210,000 m² informs what I build and why.

📍 Santiago, Chile · ✉️ cristian.maldonado@idom.com · 🔗 [linkedin.com/in/cristian-maldonado](https://linkedin.com/in/cristian-maldonado) · 🐙 [github.com/CristianMaldonado24](https://github.com/CristianMaldonado24)

---

## Stack

**Languages** — TypeScript · Python 3.12 · C# (.NET 8 + .NET Framework 4.8) · SQL  
**Web / Backend** — Next.js 15 (App Router, server actions) · FastAPI · SQLAlchemy 2.0 · Prisma · PostgreSQL  
**Auth / Infra** — NextAuth v5 + Microsoft Entra ID · Docker (multi-stage) · Coolify · Azure VM (Ubuntu 24.04) · Supabase · GitHub Actions  
**Desktop** — WPF + MVVM · ClosedXML · iText7 · DocumentFormat.OpenXml · PyInstaller · Inno Setup  
**APIs** — LinkedIn API (OAuth 2.0) · Microsoft Teams Webhooks · Mercado Público REST · Pillow  
**AEC / BIM** — Revit API (C#, 2023–2025) · Dynamo · Navisworks · multi-discipline coordination · PlanBIM  
**AI / LLM** — Google Gemini 2.5 Flash (batch prompting, neighbor-context few-shot, rate-limit handling) · Azure AI Foundry GPT-4.1

---

## Production Portfolio

All tools below are in active use inside IDOM. Repos are private (IDOM IP), but the work is real.

---

### Internal R&D Portal
> **Corporate tool-catalogue and request management portal** — replaces an email-driven flow with a tracked, role-based web workflow.

**Stack**: Next.js 15 · TypeScript · Prisma 7 + PostgreSQL/Supabase · NextAuth v5 + Microsoft Entra ID · Tailwind · Docker · Coolify on Azure VM  
**Highlights**: Microsoft corporate auth with RBAC and DEV-bypass; PostgreSQL full-text search (`tsvector` + GIN index) over the tool catalogue; 6-state request workflow with email + Microsoft Teams webhook notifications; CSV export with UTF-8 BOM; strict TypeScript, server-first React (server actions + Zod validation, `"use client"` only where necessary).

---

### BIM Document Generator *(Spain–Chile collaboration, iHub BIM & Digital Twins)*
> **AI-powered BIM Execution Plan (BEP) generator** with project management, document storage, and two embedded AI assistants: one for document generation and one for project-context-grounded chat. Backend lead on a cross-office collaboration between IDOM Spain and IDOM Chile.

**Stack**: Python 3.12 · FastAPI · SQLAlchemy 2.0 · Lit 3 Web Components + Vite + Tailwind · PostgreSQL/Supabase · Azure AI Foundry (GPT-4.1) · Docker · Coolify on Azure VM  
**Highlights**: AI chat assistant with 10-turn history and dynamic system prompt built from live project state; document upload (PDF/DOCX/XLSX/PPTX, 20 MB limit, UUID-prefixed storage); template system with shared draft/template schema; anonymization script for 60+ real BIM resource documents for safe QA; 6 delivery levels from initial UI to full AI integration.

---

### IDOM Tools — Revit Add-in *(iHub BIM challenge, sole developer)*
> **Multi-module Revit ribbon add-in** deployed across IDOM offices and teams. Sole developer for an iHub BIM & Digital Twins challenge; currently live for a 5-6 person team with architecture designed to scale to the full office, additional technical areas and geographic locations.

**Stack**: C# 7.3 · .NET Framework 4.8 · Revit API (2023–2025) · WPF + Windows Forms  
**Highlights**: 7 ribbon panels — modeling (section generation, parameter concatenation), coordination (scope box alignment), review (zero-volume element scanner with TXT report), management (auto-sync with daily timer), and a **ProSheets-equivalent multi-format export manager** (PDF/DWG/DWF/DWFx) with token-based filename resolution (`{Sheet Number}`, `{Project Number}`, `{Date}`, …). Architecture: `Core / Commands / Services / Models / UI / Resources`; `IExportService` strategy interface for extensibility.

---

### ExcelCompleteAI
> **WPF desktop app** that fills incomplete Excel files using Google Gemini 2.5 Flash — built for AEC engineers responding to repetitive client review observations.

**Stack**: .NET 8 · WPF + MVVM · ClosedXML · Google Gemini 2.5 Flash API · self-contained single-file exe (~164 MB)  
**Highlights** (prompt-engineering, not just "I called the API"):
- **2-pass pipeline** — in-memory keyword index (Spanish stopword tokenizer) resolves previously-seen rows without API calls; only unknowns hit the model.
- **Batch prompting** — groups N rows per call (default 5) → **5× fewer API calls** vs. row-by-row.
- **Neighbor-context few-shot** — uses ±N already-resolved adjacent rows as dynamic few-shot examples.
- **Production-grade rate limiting** — respects Gemini free tier (5 RPM / 20 RPD), exponential backoff (8 s → 16 s → 32 s, 4 retries), distinguishes `429 rate-limit` from quota-exhausted with user-facing diagnostics.
- Configurable engineering discipline (ARQ / EST / MEP / PRE / COO) adapts the system prompt.

---

### Public Procurement Monitor
> **Automated tendering monitor** over Chile's Mercado Público REST API — surfaces civil-engineering tenders relevant to the firm.

**Stack**: Dual implementation with identical UX — Python 3 + tkinter + pandas + PyInstaller (~62 MB) · .NET 8 + WPF + ClosedXML + Inno Setup (~66 MB). Supabase telemetry.  
**Highlights**: 11 tender-type filters + exclusion-keyword list with Unicode normalization (case + accent insensitive); persistable user filter profiles (save/rename/duplicate/delete); multi-sheet Excel export (main / enriched-by-amount / type-reference); modeless progress window with cancel and real-time stats. The dual-language implementation is intentional evidence of polyglot proficiency.

---

### Document Management Suite
> **Unified WPF suite** consolidating 5 previous standalone Python tools into a single .NET 8 executable — File Explorer, Folder Comparator, Excel Comparator, Document Report and PDF Cleaner.

**Stack**: .NET 8 · WPF · ClosedXML · iText7 · Supabase telemetry · self-contained single-file exe  
**Highlights**: module sidebar with per-module `UserControl` and shared IDOM theming (`IdomColors.xaml` + `IdomStyles.xaml`); Excel Comparator handles 2–5 files and up to 10 column pairs with color-coded output; PDF Cleaner offers 6 independent strip options (annotations, form fields, links, bookmarks, metadata, layer flatten); anonymous telemetry to Supabase (timestamp, module, op, user, host, OS) with **local fallback log** if connectivity fails — non-blocking.

---

### IDO_GEN Word Manager *(public — [github.com/CristianMaldonado24/IDO_GEN_WordManager](https://github.com/CristianMaldonado24/IDO_GEN_WordManager))*
> **WPF desktop tool** for managing Word document structures — loads `.docx` files, visualizes heading hierarchies, marks sections for hiding or deletion, and exports filtered documents with Excel-based batch filtering support.

**Stack**: C# · .NET 8 · WPF + MVVM · DocumentFormat.OpenXml · self-contained single-file exe (~160 MB)  
**Highlights**: hierarchical heading view (H1–H6) with level, numbering and visual indentation; multi-selection with Ctrl+Click / Shift+Click for batch operations; granular hide (yellow) / delete (red) marking per section or subtree; collapsible tree navigation; **Excel-batch filtering** — load `.xlsx` to apply hide/delete across hundreds of headings in one pass; vanish-text reveal (removes hidden formatting from Word documents); smart `.docx` export excluding marked sections.

---

### LinkedIn Auto-Publisher *(personal · public)*
> **Automated LinkedIn post scheduler** — reads a `schedule.json` content calendar, generates branded 1080×1080 px images programmatically and publishes posts via the LinkedIn API on a daily cron.

**Stack**: Python 3 · Pillow · LinkedIn API (OAuth 2.0) · GitHub Actions · python-dotenv  
**Highlights**: two image generators (profile card + certificate/milestone style) using Pillow with Poppins/Segoe UI fonts; OAuth 2.0 flow with automatic browser-launch + callback capture + token persistence; GitHub Actions cron at 9 AM Santiago daily; manual `workflow_dispatch` with optional `--date` and `--force` flags; `schedule.json` auto-updated after each publish to prevent duplicate posts.

---

### Man-Hours Consolidation Tool
> **WPF desktop app** migrated from an Excel VBA macro — consolidates man-hours by person and project across multiple Excel source files used in workforce planning.

**Stack**: .NET 8 · WPF + MVVM · ClosedXML · self-contained single-file exe  
**Highlights**: async consolidation with cancellable progress bar; real-time search by person or group; dual-sheet styled Excel export with area grouping, banded rows and visual highlighting of values exceeding threshold; linked-file list persisted to `linked_files.json` across sessions.

---

## AEC Background

- Hospital-sector BIM projects for Chilean public health network (IDOM, 2022–present) — structural + MEP modeling and Dynamo automation tooling
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

---

*All production repos are private (IDOM IP). Available to discuss architecture, design decisions and outcomes directly.*
