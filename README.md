# Cristian Maldonado Román

**Civil Engineer · AEC Software Engineer · Innovation Lead**

Civil engineer (Universidad Diego Portales, Chile) operating as an AEC software engineer. As **Innovation Lead at IDOM Chile**, I founded and run a solo innovation function (Apr 2025) that ships production tooling used across the office and IDOM's international **iHub for BIM & Digital Twins**. Six years of AEC field experience on hospital, residential and education projects from 6,000 m² to 210,000 m² informs what I build and why.

📍 Santiago, Chile · ✉️ cristian.maldonado@idom.com · 🔗 linkedin.com/in/cristian-maldonado

---

## Stack

**Languages** — TypeScript · Python 3.12 · C# (.NET 8 + .NET Framework 4.8) · SQL  
**Web / Backend** — Next.js 15 (App Router, server actions) · FastAPI · SQLAlchemy 2.0 · Prisma · PostgreSQL  
**Auth / Infra** — NextAuth v5 + Microsoft Entra ID · Docker (multi-stage) · Coolify · Azure VM (Ubuntu 24.04) · Supabase · GitHub Actions  
**Desktop** — WPF + MVVM · ClosedXML · iText7 · DocumentFormat.OpenXml · AutoCAD COM Automation · PyInstaller · Inno Setup  
**AEC / BIM** — Revit API (C#, 2023–2025) · AutoCAD COM · Dynamo · Navisworks · multi-discipline coordination · PlanBIM · ISO 19650  
**AI / LLM** — Google Gemini 2.5 Flash (batch prompting, neighbor-context few-shot, rate-limit handling) · Azure AI Foundry GPT-4.1

---

## Production Portfolio

8 tools in active use inside IDOM + 2 in development. Repos are private (IDOM IP), but the work is real.

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

### IDOM Tools — Revit Add-in *(iHub BIM challenge, sole developer)*
> **Multi-module Revit ribbon add-in** deployed across IDOM offices. Sole developer; live for a 5-6 person team with architecture designed to scale to the full office and additional geographic locations.

**Stack**: C# 7.3 · .NET Framework 4.8 · Revit API (2023–2025) · WPF + Windows Forms  
**Highlights**: 7 ribbon panels — modeling, coordination, review, management and a **ProSheets-equivalent multi-format export manager** (PDF/DWG/DWF/DWFx) with token-based filename resolution (`{Sheet Number}`, `{Project Number}`, `{Date}`, …). Architecture: `Core / Commands / Services / Models / UI / Resources`; `IExportService` strategy interface for extensibility.

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

### DWG Manager — Export Layouts *(in active development)*
> **WPF desktop tool** for managing AutoCAD `.dwg` files and exporting layouts to individual DWGs via AutoCAD COM Automation. Migrated from a Python legacy script at v4.0.

**Stack**: C# · .NET 8 · WPF + MVVM · AutoCAD COM Automation · Supabase REST · P/Invoke · self-contained single-file exe  
**Highlights**: bulk layout export via AutoCAD COM (specific layout by name or all with `*`); **P/Invoke dialog dismisser** — auto-closes AutoCAD pop-ups during unattended batch runs (`EnumWindows`); Supabase telemetry logging (user, hostname, domain, timestamp, layouts exported). Dual implementation history: Python 3 legacy → C# .NET 8 WPF.

---

### BIM QA/QC Validator *(in development — architecture & governance role)*
> **Platform for BIM quality assurance and quality control**. My role: cybersecurity lead, repo architect, and GitHub organization administrator.

**Role scope**: define repo structure, branching strategy and contribution guidelines; own the cybersecurity posture (secrets management, access control, dependency scanning); GitHub org admin (team permissions, CI/CD workflow permissions, protected branches).

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
- **WallStreet English** — Level 17 (in active progression)

---

*All production repos are private (IDOM IP). Available to discuss architecture, design decisions and outcomes directly.*
