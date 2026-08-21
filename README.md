# Cristian Maldonado Román

**Civil Engineer · AEC Software Engineer · Founder & Lead, Innovation @ IDOM Chile**

Civil engineer (Universidad Diego Portales, Chile) operating as an AEC software engineer. I founded and run IDOM Chile's Innovation function (Apr 2025) as a solo initiative — 16 months and 13 production tools later, it ships tooling used across the office and IDOM's international **iHub for BIM & Digital Twins**. Six years of AEC field experience on hospital, residential and education projects from 6,000 m² to 210,000 m² informs what I build and why.

📍 Santiago, Chile · ✉️ maldonado.c24@icloud.com · 🔗 linkedin.com/in/cristian-maldonado

---

## Stack

**Languages** — TypeScript · Python 3.12 · C# (.NET 8 + .NET Framework 4.8) · SQL  
**Web / Backend** — Next.js 15 (App Router, server actions) · FastAPI · SQLAlchemy 2.0 · Prisma · PostgreSQL  
**Auth / Infra** — NextAuth v5 + Microsoft Entra ID · Docker (multi-stage) · Coolify · Azure VM (Ubuntu 24.04) · Supabase · GitHub Actions  
**Desktop** — WPF + MVVM · ClosedXML · iText7 · DocumentFormat.OpenXml · AutoCAD COM Automation · PyInstaller · Inno Setup  
**AEC / BIM** — Revit API (C#, 2023–2026, 4 versions built simultaneously) · AutoCAD COM Automation · Dynamo · Navisworks Clash Detective automation · IFC2x3/IFC4 export · multi-discipline coordination · PlanBIM · ISO 19650  
**AI / LLM** — Google Gemini 2.5 Flash (batch prompting, neighbor-context few-shot, rate-limit handling) · Azure AI Foundry GPT-4.1

---

## Production Portfolio

13 tools in active use inside IDOM. Repos are private (IDOM IP), but the work is real.

---

### Internal R&D Portal
> **Corporate tool-catalogue and request management portal** — replaces an email-driven flow with a tracked, role-based web workflow.

**Stack**: Next.js 15 · TypeScript · Prisma 7 + PostgreSQL/Supabase · NextAuth v5 + Microsoft Entra ID · Tailwind · Docker · Coolify on Azure VM  
**Highlights**: Microsoft corporate auth with RBAC and DEV-bypass; PostgreSQL full-text search (`tsvector` + GIN index) over the tool catalogue; 6-state request workflow with email + Microsoft Teams webhook notifications; CSV export with UTF-8 BOM; strict TypeScript, server-first React (server actions + Zod validation, `"use client"` only where necessary).

---

### BIM Document Generator *(Spain–Chile collaboration, iHub BIM & Digital Twins)*
> **AI-powered BIM Execution Plan (BEP) generator** with project management, document storage, and two embedded AI assistants. Backend lead on a cross-office collaboration between IDOM Spain and IDOM Chile.

**Stack**: Python 3.12 · FastAPI · SQLAlchemy 2.0 · Lit 3 Web Components + Vite + Tailwind · PostgreSQL/Supabase · Azure AI Foundry (GPT-4.1) · Docker · Coolify on Azure VM  
**Highlights**: AI chat assistant with 10-turn history and dynamic system prompt built from live project state; document upload (PDF/DOCX/XLSX/PPTX, 20 MB limit, UUID-prefixed storage); template system with shared draft/template schema; anonymization script for 60+ real BIM resource documents for safe QA.

---

### IDOM Tools — Revit Add-in *(flagship, sole developer)*
> **Multi-module Revit ribbon add-in** deployed across IDOM offices. The longest-running tool in the portfolio: 16 months of continuous development, 154 commits, v2.3.1.

**Stack**: C# 7.3 · .NET Framework 4.8 · Revit API (2023–2026, 4 versions built from one solution) · WPF + Windows Forms · xUnit test project on .NET 8  
**Highlights**: 7 ribbon panels — modeling, coordination, review, management and a **ProSheets-equivalent multi-format export manager** (PDF/DWG/DWF/DWFx) with token-based filename resolution. A **BIM QA/QC validator** batch-exports 26 categories of raw model data (levels, worksets, materials, warnings, shared parameters) across a folder of `.rvt` files for automated quality analysis, plus zero-volume element checks across 20 configurable categories. **13/13 unit tests passing** on versioned JSON contracts. Architecture: `Core / Commands / Services / Models / UI / Resources`; `IExportService` strategy interface; generic `IDataExtractor<T>` interface used by 25 BIM-data extractors.

---

### Revit ⇄ Navisworks Automation
> Built after **Autodesk's own BIM coordination installer broke** and stopped working reliably. Automates Revit-to-`.nwc` export, updates Navisworks Clash Detective tests, and runs without admin rights — unlike the tool it replaces.

**Stack**: C# · .NET 8 + .NET Framework 4.8 · Revit API (`Nice3point.Revit.Api.*`, no local Revit install needed to build) · Navisworks Manage API · Windows Task Scheduler API  
**Highlights**: supports 4 Revit versions and 4 Navisworks Manage versions from one solution; scheduled task runs under the user's own account instead of the `System` account the original tool required; native IFC2x3/IFC4 exporter, adding scope beyond the original vendor tool; **41 automated tests**, dependency-free (no Revit/Navisworks/network required to run); documentation explicitly separates "verified" from "compiles but unverified" functionality rather than overselling MVP status.

---

### ExcelCompleteAI
> **WPF desktop app** that fills incomplete Excel files using Google Gemini 2.5 Flash — built for AEC engineers responding to repetitive client review observations.

**Stack**: .NET 8 · WPF + MVVM · ClosedXML · Google Gemini 2.5 Flash API · self-contained single-file exe (~164 MB)  
**Highlights** (prompt-engineering, not just "I called the API"):
- **2-pass pipeline** — in-memory keyword index resolves previously-seen rows without API calls; only unknowns hit the model.
- **Batch prompting** — groups N rows per call → **5× fewer API calls** vs. row-by-row.
- **Neighbor-context few-shot** — uses ±N adjacent already-resolved rows as dynamic examples.
- **Production-grade rate limiting** — exponential backoff, distinguishes `429 rate-limit` from quota-exhausted with user-facing diagnostics.

---

### Word Document Manager
> **WPF desktop tool** for structured management of Word documents — used by IDOM project directors to strip confidential or irrelevant sections before sharing BIM Execution Plans and technical reports.

**Stack**: C# · .NET 8 · WPF + MVVM · DocumentFormat.OpenXml · self-contained single-file exe (~160 MB)  
**Highlights**: hierarchical heading visualization (H1–H6) with collapsible tree; multi-selection (Ctrl+Click, Shift+Click) with bulk Hide/Delete actions; **Excel-driven batch filtering** — load a `.xlsx`, pick the column, choose mode and action, apply across all matched headings in one click; hierarchical renumbering; vanish-text reveal; exports filtered `.docx`. Shared with and in active use by IDOM project directors.

---

### Public Procurement Monitor
> **Automated tendering monitor** over Chile's Mercado Público REST API — surfaces civil-engineering tenders relevant to the firm.

**Stack**: Dual implementation — Python 3 + tkinter + pandas + PyInstaller (~62 MB) · .NET 8 + WPF + ClosedXML + Inno Setup (~66 MB). Supabase telemetry.  
**Highlights**: 11 tender-type filters + exclusion-keyword list with Unicode normalization; persistable user filter profiles; multi-sheet Excel export; modeless progress window with cancel and real-time stats. Dual-language implementation is intentional evidence of polyglot proficiency.

---

### Document Management Suite
> **Unified WPF suite** consolidating 5 previous standalone Python tools — File Explorer, Folder Comparator, Excel Comparator, Document Report and PDF Cleaner.

**Stack**: .NET 8 · WPF · ClosedXML · iText7 · Supabase telemetry · self-contained single-file exe  
**Highlights**: module sidebar with shared IDOM theming; Excel Comparator handles 2–5 files with color-coded output; PDF Cleaner offers 6 independent strip options; anonymous telemetry to Supabase with **local fallback log** if connectivity fails — non-blocking.

---

### Man-Hours Consolidation Tool
> **WPF desktop app** migrated from an Excel VBA macro — consolidates man-hours by person and project across multiple Excel source files used in workforce planning.

**Stack**: .NET 8 · WPF + MVVM · ClosedXML · self-contained single-file exe  
**Highlights**: async consolidation with cancellable progress bar; real-time search by person or group; dual-sheet styled Excel export with area grouping and visual threshold highlighting; linked-file list persisted to `linked_files.json` across sessions.

---

### DWG Manager — Export Layouts *(v4.1.2, production)*
> **WPF desktop tool** for IDOM's Structures team: manages AutoCAD `.dwg` files and exports layouts to individual DWGs via AutoCAD COM Automation.

**Stack**: C# · .NET 8 · WPF + MVVM · AutoCAD COM Automation · Supabase REST · P/Invoke · self-contained single-file exe  
**Highlights**: bulk layout export via AutoCAD COM (specific layout by name or all with `*`); **P/Invoke dialog dismisser** — auto-closes AutoCAD pop-ups during unattended batch runs (`EnumWindows`); an **"AutoFix" flow that repairs dimension-layer artifacts specific to Revit-to-DWG exports** (backs up dimension text, runs `EXPLODE`, restores text) — direct Revit↔AutoCAD interoperability work, not a generic CAD script. Supabase telemetry logging. Migrated from a legacy Python implementation.

---

### DWG Editor — Bulk Text Editor *(in development, v0.2)*
> **Python desktop tool** for mass text operations across multiple DWG files via AutoCAD COM Automation. Planned integration with DWG Manager into a unified DWG management suite.

**Stack**: Python 3 · tkinter · pywin32 · AutoCAD COM Automation  
**Highlights**: bulk **verify** (title block text vs. filename), **replace** (revision numbers, fields) and **delete** text at configurable XY coordinates — up to 10 coordinate pairs per run; `.bak` cleanup; progress bar with real-time stats and detailed per-file operation reports.

---

### BIM QA/QC Validator *(in active development — migration lead, cybersecurity & GitHub admin)*
> **Full-stack migration** of a Streamlit BIM audit platform to a decoupled modern architecture. YAML-driven rules engine validates BIM nomenclature (families, types, views, systems, coordinates, levels) from Revit plugin exports.

**Stack**: Python · FastAPI · SQLAlchemy · React 19 · TypeScript · TailwindCSS · Vite · PostgreSQL/Supabase · Docker · GitHub Actions · Vercel  
**Highlights**: FastAPI backend wrapping existing ETL core; React 19 + TypeScript frontend with 6 pages, dark mode, persistent sidebar filters and mock auth (→ Azure AD/Entra ID); CI/CD via GitHub Actions + Vercel monorepo deploy; DB migration CSV → PostgreSQL/Supabase in progress.  
**Role scope**: migration lead; cybersecurity posture (secrets management, access control, dependency scanning); GitHub org admin (team permissions, CI/CD workflow permissions, protected branches).

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
- **WallStreet English** — Level 16, B2/C1 CEFR (in active progression)

---

*All production repos are private (IDOM IP). Available to discuss architecture, design decisions and outcomes directly.*
