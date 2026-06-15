# Accredify — Product Roadmap

## Philosophy

Build the minimum that creates a daily habit first. Inspection readiness is the reason colleges buy. Daily use is the reason they stay.

---

## Phase 1 — MVP (Complete)

**Goal:** Validate that colleges want this. Get 3 pilot colleges using it daily.

### What's built
- [x] All 4 inspection body requirement checklists (NAAC/AICTE/NBA/Anna University)
- [x] Real requirements from official 2024-27 documents — not generic checklists
- [x] Department readiness dashboard with live % per body
- [x] Daily attendance marking (click-to-toggle per student)
- [x] Lesson plan log with unit-by-unit progress tracking
- [x] Internal assessment mark entry with CO attainment auto-calculation
- [x] HOD feed replacing WhatsApp — live activity, ping buttons
- [x] Faculty records with qualification, FDP, publications
- [x] Syllabus tracking with CO-PO mapping status
- [x] Student records with below-75% flagging
- [x] Infrastructure / lab equipment register
- [x] Report generation (formatted per body)
- [x] Document vault

### How it's delivered
Single HTML file — no server, no login, no setup. Opens in any browser. Used for demos, HOD pitches, and pilot onboarding.

### Success criteria
- 3 colleges using it daily for attendance and lesson plan tracking
- HODs report reduced WhatsApp chasing
- At least 1 college uses it to generate a real inspection report

---

## Phase 2 — Full Product (3–4 months)

**Goal:** Make it a real multi-user web application. Get to 20 paying colleges.

### Backend & Auth
- [ ] Supabase project setup (auth + database + storage)
- [ ] Row-level security — each college's data completely isolated
- [ ] Role-based access: Faculty / HOD / IQAC Coordinator / Admin / Principal
- [ ] Invite-based onboarding (HOD invites faculty, IQAC coordinator invites HOD)

### Daily Use Features
- [ ] **Mobile-first attendance** — PWA that works on basic Android phones; offline support with sync
- [ ] **Timetable import** — Upload college timetable CSV; system auto-generates daily class list
- [ ] **WhatsApp integration** — Accredify sends reminders via WhatsApp Business API (not just email)
- [ ] **Bulk Excel import** — Upload existing faculty list, student list, mark sheets; system maps columns
- [ ] **FDP log with ATAL verification** — Link to ATAL Academy certificates by certificate number

### Inspection Features
- [ ] **Auto-reminders engine** — Scheduled job at 8 AM daily: checks pending items, sends reminders
- [ ] **Certificate expiry alerts** — 60-day and 30-day warnings for expiring documents
- [ ] **Aadhaar verification** — Integrate with DigiLocker / UIDAI API for ghost faculty detection
- [ ] **Geotagged photo upload** — Mobile camera capture with GPS metadata requirement

### Data & Reports
- [ ] **Real report templates** — NAAC SSR data export, AICTE compliance report, NBA SAR data pack
- [ ] **Document vault with search** — Full-text search across uploaded PDFs
- [ ] **Audit log** — Every data change logged with who changed it and when

### Infrastructure
- [ ] React + TypeScript frontend
- [ ] Supabase backend (auth, database, storage, realtime)
- [ ] Vercel deployment
- [ ] Basic monitoring (Sentry for errors, Vercel Analytics)

---

## Phase 3 — Intelligence (6–8 months)

**Goal:** Make Accredify irreplaceable. Get to 100 colleges.

### AI-Powered Features
- [ ] **NAAC SSR first draft** — AI generates full SSR narrative from data in Accredify; human edits and approves
- [ ] **NBA SAR pre-fill** — Auto-fills SAR 2025 format from live data; 80% of fields pre-populated
- [ ] **CO corrective action suggestions** — When CO attainment drops below target, AI suggests specific remedial actions based on similar courses
- [ ] **Anomaly detection** — Flags unusual patterns: attendance suddenly dropping in one section, marks spread inconsistent with previous IAs

### Integration
- [ ] **Anna University portal API** — Direct submission of affiliation data from Accredify
- [ ] **AISHE data sync** — Import AISHE data; flag any mismatch with Accredify records before NAAC submission
- [ ] **NIRF sync** — Pull NIRF rankings data; compare against institution's self-assessment
- [ ] **AICTE ERP integration** — Push faculty data directly to AICTE portal
- [ ] **Existing ERP connectors** — Kalvisalai, MasterSoft, Camu — pull attendance and marks data via API to eliminate double entry

### Platform Features
- [ ] **Multi-college trust dashboard** — Management companies running 3–10 colleges see all colleges in one view
- [ ] **Benchmarking** — "Your CO attainment in CS is 62% — average for similar colleges is 71%"
- [ ] **Consultant access** — NAAC/NBA consultants get read-only access to client colleges in Accredify

### Expansion
- [ ] Arts and Science colleges (face NAAC + University inspection; same pain, larger market)
- [ ] Karnataka, Maharashtra, Andhra Pradesh (similar inspection structure)
- [ ] Polytechnics (AICTE-regulated; attendance + marks pain is identical)

---

## Tech Stack (Production)

### Frontend
```
React 18 + TypeScript
Tailwind CSS
React Query (server state)
Zustand (client state)
React Hook Form + Zod (forms + validation)
PWA (Workbox for offline attendance)
```

### Backend
```
Supabase (PostgreSQL + Auth + Realtime + Storage)
Edge Functions for scheduled jobs (reminders, CO calculation)
```

### Infrastructure
```
Vercel (frontend hosting + edge functions)
Supabase cloud (hosted PostgreSQL)
Cloudflare (CDN + DDoS protection)
```

### Integrations (Phase 3)
```
WhatsApp Business API (Twilio or WATI)
DigiLocker API (Aadhaar verification)
AWS S3 or Supabase Storage (document vault)
OpenAI API (SSR/SAR draft generation)
```

---

## Open Questions / Decisions Pending

| Question | Options | Decision by |
|---|---|---|
| Build backend in-house vs. use Supabase | In-house Node/Express vs. Supabase BaaS | Phase 2 kickoff |
| Mobile app vs. PWA | React Native vs. PWA | Pilot feedback — what phones do faculty use? |
| WhatsApp vs. email for reminders | WhatsApp has 98% open rate in TN; email ~20% | Phase 2 — test both |
| Pricing: per-college vs. per-user | Per-user is standard SaaS; per-college is simpler for this market | Pilot feedback |
| AI model for SSR generation | OpenAI GPT-4o vs. Claude vs. fine-tuned local model | Phase 3 |
| Data residency | India-hosted (Supabase has Mumbai region) vs. US | Phase 2 — may matter for some colleges |

---

## Risks and Mitigations

| Risk | Likelihood | Mitigation |
|---|---|---|
| Colleges already have ERP and don't want another tool | High | Position as inspection layer on top of ERP, not replacement. Phase 3 ERP connectors eliminate double entry. |
| Faculty won't adopt daily use | Medium | Make attendance marking faster than paper register. Mobile-first. WhatsApp reminders, not email. |
| NAAC/AICTE changes requirements | Medium | Requirements are stable for 3-year cycles. We monitor official sources. Anna University changes annually — update immediately. |
| College data privacy concerns | Medium | Row-level isolation, no data sharing between colleges, export-everything policy, local backup option. |
| Single-person technical risk | High (early stage) | Prioritize simple stack (Supabase reduces backend work). Document everything. |
| Competing product copies the idea | Low (near-term) | First mover in TN for this specific combination. Relationships and trust with colleges are the moat. |
