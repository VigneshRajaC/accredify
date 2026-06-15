# Accredify — College Inspection Readiness Platform

> **Never panic before an inspection again.**

Accredify is a SaaS product concept and working prototype built for private engineering colleges in Tamil Nadu, India. It replaces the manual, Excel-and-WhatsApp chaos that happens before every NAAC, AICTE, NBA, or Anna University inspection with a single live dashboard — and turns daily academic work into inspection compliance automatically.

---

## Live Demo

**[→ Open the prototype](src/index.html)** *(download and open in any browser — no server needed)*

---

## The Problem

Tamil Nadu has ~2,400 private engineering colleges. Every one of them faces the same pre-inspection panic:

- HODs chase 20+ faculty on WhatsApp for certificates, lesson plans, attendance registers
- Professors are pulled from teaching for 3 weeks to compile Excel sheets and Word reports
- The same faculty data is entered separately for NAAC, AICTE, NBA, and Anna University — each in a different format
- Deficiencies are discovered days before inspection, not months before

In 2025 alone, **141 Tamil Nadu colleges received deficiency notices** from Anna University. 15 had zero student intake as a result.

---

## The Solution

Accredify is **daily academic operations software** — not inspection software. Faculty use it every day to mark attendance, log lesson plan progress, and enter marks. Inspection readiness builds up as a side effect.

When inspection comes, the report is already there. One click.

---

## What's in This Repo

```
accredify/
├── src/
│   └── index.html          # Full working prototype (single-file, no dependencies)
├── docs/
│   ├── product-spec.md     # Full product requirements and feature map
│   ├── market-research.md  # TAM/SAM/SOM, competitor analysis, pricing
│   ├── inspection-bodies.md # Real requirements from NAAC, AICTE, NBA, Anna University
│   └── roadmap.md          # Phase 1 → 3 build plan
├── public/
│   └── screenshots/        # UI screenshots for README
└── README.md
```

---

## Features (Prototype)

### Daily Use (the habit engine)
| Feature | What it does |
|---|---|
| **Mark Attendance** | Faculty mark class-by-class attendance daily. Below-75% students flagged automatically. |
| **Lesson Plan Log** | Unit-by-unit syllabus progress per subject. Behind-schedule courses auto-flagged. |
| **Internal Assessment Marks** | Enter IA1/IA2 marks. CO attainment auto-calculates. Corrective actions logged for NBA. |
| **HOD Feed** | Live activity feed. HOD sees what every faculty did today. One-click "Ping" replaces WhatsApp chasing. |

### Inspection Readiness (the value lock-in)
| Body | Requirements mapped |
|---|---|
| **NAAC** | Binary 2025 framework — all 10 Attributes across Inputs/Processes/Outcomes layers |
| **AICTE** | APH 2024-27 — FSR, cadre ratio, FDP norms, infrastructure, APAAR/ABC compliance |
| **NBA** | SAR 2025 / GAPC v4.0 — 10 criteria, CO attainment loop, continuous improvement |
| **Anna University** | 2026-27 guidelines — geotagged photos, Aadhaar biometric, 10-digit Faculty UID |

### Records & Reports
- Faculty records with qualification, FDP hours, publication tracking
- Syllabus completion tracking with CO-PO mapping
- Student attendance and at-risk flagging
- Lab equipment register
- Document vault
- One-click report generation per inspection body

---

## What Can Be Automated vs. What Can't

### Automated by Accredify
- Tracks every requirement across all 4 bodies — live
- Sends reminders to faculty who are behind (Phase 2)
- Flags cross-body gaps: "This one fix closes 3 inspection body issues"
- Generates reports in the correct format for each body
- Detects ghost/duplicate faculty via Aadhaar match (Phase 2)
- Tracks certificate expiry and inspection deadlines
- CO-PO attainment calculation from entered marks

### Still Needs a Human
- Scanning and uploading physical documents
- Holding IQAC meetings and writing minutes
- CO-PO corrective action judgments (academic call)
- Getting alumni and industry feedback responses
- External Green/Energy Audit (needs ISO-certified agency)
- Faculty biometric and geotagged photos (by design — anti-ghost rule)

---

## Market Opportunity

| | Size |
|---|---|
| Tamil Nadu private engineering colleges | ~2,400 |
| Likely paying segment (top 20%) | ~480 colleges |
| TAM (TN only, ₹25k/yr avg) | ~₹18 Crore/year |
| All-India expansion (40,000+ private colleges) | ~₹300 Crore TAM |

**Pricing model:** ₹15,000–₹30,000/year per college depending on student strength. No per-user fees.

**First mover advantage:** No lightweight, inspection-focused tool exists for smaller TN colleges. Existing solutions (Kalvisalai, Camu, MasterSoft) are either too expensive or too broad.

---

## Build Roadmap

### Phase 1 — MVP (Now)
- [x] All 4 inspection body requirement checklists with live status
- [x] Faculty, syllabus, attendance, infrastructure records
- [x] Department readiness dashboard
- [x] Daily use: attendance, lesson plan log, IA marks, HOD feed
- [x] Basic report generation

### Phase 2 — Full Product (3–4 months)
- [ ] Multi-user logins with role-based access (HOD, faculty, IQAC, admin)
- [ ] Automated email/WhatsApp reminders to faculty
- [ ] Bulk Excel import for migrating existing data
- [ ] Document vault with expiry alerts
- [ ] Mobile-friendly interface (PWA)

### Phase 3 — Intelligence (6–8 months)
- [ ] Auto-generated NAAC SSR / NBA SAR first drafts
- [ ] CO-PO attainment auto-calculation from connected mark systems
- [ ] API integration with Anna University affiliation portal
- [ ] AISHE / NIRF data sync to prevent submission mismatches
- [ ] Multi-college dashboard for management trusts

---

## Tech Stack (Prototype)

The current prototype is intentionally a **single HTML file** — no framework, no build step, no server. This was a deliberate choice to:
- Demo in any browser without setup
- Share with non-technical stakeholders (HODs, principals) as a file
- Validate the concept before committing to a stack

**Planned production stack:**
- Frontend: React + Tailwind CSS
- Backend: Node.js / Express or Supabase (for faster MVP)
- Database: PostgreSQL
- Auth: Supabase Auth or Clerk
- Hosting: Vercel (frontend) + Railway or Supabase (backend)
- File storage: Supabase Storage or AWS S3

---

## Who Built This

Built as a product concept after observing that a private engineering college in Chennai was spending 3+ weeks before every inspection compiling the same data into different formats — by hand, every year.

The inspection requirements (NAAC, AICTE, NBA, Anna University) were sourced directly from official documents:
- NAAC Binary Accreditation Framework (Feb 2025 announcement)
- AICTE Approval Process Handbook 2024-27
- NBA SAR 2025 Format / GAPC v4.0
- Anna University Affiliation Guidelines 2026-27

---

## Running the Prototype

No installation needed.

```bash
# Option 1: Just open the file
open src/index.html

# Option 2: Serve locally (optional)
npx serve src/
# or
python3 -m http.server 8080 --directory src/
```

---

## Contributing / Feedback

This is an early-stage product concept. If you're an HOD, faculty member, or IQAC coordinator at a Tamil Nadu engineering college and want to give feedback or be a pilot user — open an issue or reach out directly.

**Pilot offer:** First 3 colleges get 6 months of free access + full setup support.

---

## License

MIT — free to use, fork, and build on.
