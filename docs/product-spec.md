# Accredify — Product Specification

## Problem Statement

Private engineering colleges in Tamil Nadu run their inspection compliance entirely on paper, Excel sheets, and WhatsApp group chats. Before every NAAC, AICTE, NBA, or Anna University inspection, the HOD spends 3–4 weeks:

1. Sending messages to 20+ faculty members requesting certificates, lesson plans, FDP proofs
2. Compiling the same data into 4 different formats for 4 different inspection bodies
3. Discovering gaps (missing certificates, incomplete registers) days before inspection
4. Diverting professors from teaching to do administrative paperwork

The result: stressed faculty, compromised teaching quality, and colleges showing up under-prepared despite having the underlying data somewhere in scattered Excel files.

---

## Core Insight

**The daily problem is not inspection readiness — it is teaching load and admin burden.**

Faculty already do the work that generates inspection records every day: they mark attendance, update lesson plans, enter marks. The problem is that this work happens in disconnected systems (paper registers, Excel, WhatsApp) that cannot be compiled into inspection formats automatically.

Accredify makes the daily academic workflow the inspection compliance workflow. Faculty use it every day for normal work. Inspection readiness accumulates as a side effect.

---

## User Personas

### Primary: Faculty Member
- Marks attendance for 4–6 classes per day
- Updates syllabus progress weekly
- Enters IA marks after each assessment
- Uploads certificates, FDP proofs, publications periodically
- Pain: being chased by HOD for documents, especially before inspections

### Primary: Head of Department (HOD)
- Monitors department performance across all subjects
- Approves faculty records and submissions
- Responsible for department readiness before inspections
- Pain: manually collecting data from 15–25 faculty; no visibility into who is behind

### Secondary: IQAC Coordinator
- Manages NAAC and NBA documentation
- Compiles AQARs, SSRs, SARs
- Coordinates with all departments
- Pain: chasing departments for data in 4 different formats

### Secondary: Principal / Admin
- Needs college-wide overview
- Signs off on inspection submissions
- Pain: no single view of where the college stands across all 4 bodies

---

## Feature Map

### Module 1: Daily Attendance
**User:** Faculty
**Frequency:** Every class, every day
**Core flow:**
1. Faculty opens Accredify → sees today's class schedule
2. Clicks into a class → sees student list as clickable dots
3. Marks present/absent per student (tap/click)
4. Saves — percentage auto-calculates
5. System flags students below 75% threshold

**Inspection linkage:**
- Anna University: attendance registers auto-populated
- NAAC A5: Teaching-Learning process evidence
- AICTE: attendance norm compliance tracked automatically

**HOD view:**
- Real-time department attendance dashboard
- Alerts when any class has abnormally low attendance
- Weekly summary without asking anyone

---

### Module 2: Lesson Plan & Syllabus Tracking
**User:** Faculty (updates), HOD (monitors)
**Frequency:** Weekly faculty update, daily HOD check
**Core flow:**
1. Semester start: HOD uploads syllabus / unit plan for each subject
2. Faculty marks unit completion weekly (Unit 1 done, Unit 2 in progress, etc.)
3. System compares against expected pace (Week 11 = should be at Unit 4)
4. Behind-schedule subjects flagged to HOD feed automatically

**Inspection linkage:**
- Anna University: lesson plan records auto-generated
- NBA C2: teaching-learning process evidence
- NAAC A5: blended/experiential learning documentation

---

### Module 3: Internal Assessment Marks
**User:** Faculty (enters), HOD (monitors)
**Frequency:** After each IA (typically 2x per semester)
**Core flow:**
1. Faculty opens subject → enters marks per student
2. System shows previous IA for comparison (trend: improved/dropped)
3. Students below pass mark flagged
4. Submit triggers CO attainment calculation automatically

**CO Attainment sub-feature:**
- System maps marks to Course Outcomes based on predefined CO-question mapping
- Calculates direct attainment % per CO
- Flags COs below 60% threshold
- Prompts faculty to log corrective action (required for NBA C3)
- Corrective action stored and linked to NBA Continuous Improvement tracker

**Inspection linkage:**
- Anna University: IA mark sheets auto-populated
- NBA C3: CO attainment calculation (the most painful NBA requirement)
- NBA C7: corrective action documentation (continuous improvement loop)
- NAAC A5: outcome-based assessment evidence

---

### Module 4: HOD Feed
**User:** HOD
**Frequency:** Daily check (replaces WhatsApp monitoring)
**Core flow:**
1. HOD opens feed → sees real-time activity from all faculty
2. Each action logged: attendance marked, syllabus updated, document uploaded
3. Overdue items flagged with days-late count
4. "Ping" button sends in-app + WhatsApp/email reminder to specific faculty
5. "Ping All" sends to everyone with pending items in one click

**Design principle:** HOD should never need to ask "did you submit X?" — the answer is visible in the feed before they ask.

---

### Module 5: Faculty Records
**User:** Faculty (self-updates), HOD (approves), Admin (manages)
**Frequency:** When records change (certificate upload, FDP completion, publication)
**Fields tracked:**
- Qualification (UG, PG, PhD) with certificate upload
- Designation and department
- Experience (total, at current institution)
- FDP hours logged (with proof upload, linked to ATAL Academy)
- Publications (Scopus/SCI link, year, journal)
- Bank account details (Anna University 2026-27 requirement)
- Aadhaar UID (for ghost faculty detection)
- Geotagged on-campus photo (Anna University 2026-27 requirement)

**Inspection linkage:**
- All 4 bodies: faculty register auto-generated per body's format
- AICTE: FDP hours, qualification norms, cadre ratio auto-checked
- Anna University: ghost faculty verification via Aadhaar match
- NBA C5: 3-year faculty history (CAY/CAYm1/CAYm2) auto-compiled

---

### Module 6: Inspection Readiness Dashboard
**User:** HOD, IQAC Coordinator, Principal
**Frequency:** Weekly check, daily in inspection month
**Features:**
- Select inspection body (NAAC / AICTE / NBA / Anna University)
- See all requirements for that body with Green / Amber / Red status
- Each requirement links to the underlying record
- Cross-body gap detection: "Fixing this one item improves NAAC A2, AICTE F, and Anna University F simultaneously"
- Overall readiness % per body per department

---

### Module 7: Report Generation
**User:** IQAC Coordinator, HOD
**Frequency:** Pre-inspection (1–4x per year)
**Output:**
- NAAC SSR data export (all 10 Attributes, formatted)
- AICTE annual compliance report (faculty list, FSR, FDP, infrastructure)
- NBA SAR 2025 data pack (10 criteria, CO attainment, 3-year history)
- Anna University affiliation inspection report
- Full cross-body readiness report (for Principal / Management)

---

### Module 8: Document Vault
**User:** All roles
**Frequency:** When uploading or finding documents
**Features:**
- Upload any document (PDF, image)
- Tag to a faculty member, department, or inspection requirement
- Expiry date tracking (certificates that need renewal)
- Search across all documents
- Bulk download per inspection body

---

## Data Model (High Level)

```
College
  └── Departments[]
        └── Faculty[]
              └── Qualifications[]
              └── FDPRecords[]
              └── Publications[]
        └── Subjects[]
              └── LessonPlanUnits[]
              └── AttendanceRecords[]
                    └── StudentAttendance[]
              └── IAMarks[]
                    └── StudentMarks[]
              └── COAttainment[]
        └── LabEquipment[]
  └── InspectionBodyRequirements[]
        └── RequirementStatus[]
  └── Documents[]
  └── AuditLog[]
```

---

## Automation vs. Manual Boundary

### Automated
| What | How |
|---|---|
| Readiness % calculation | Triggered on every record update |
| Cross-body gap flagging | Rule engine on shared data fields |
| Faculty reminders | Scheduled job: checks pending items daily at 8 AM |
| CO attainment calculation | Triggered on IA mark submission |
| Below-75% attendance alerts | Triggered on attendance save |
| Report generation | Template engine pulls from live data |
| Ghost faculty detection | Aadhaar dedup check on faculty upload |
| Certificate expiry alerts | Scheduled job: 60-day and 30-day warnings |

### Always Manual
| What | Why |
|---|---|
| Physical document upload | Physical scan required |
| IQAC meeting minutes | Meeting must actually happen |
| CO corrective action content | Academic judgment |
| Alumni/industry feedback | Human relationship required |
| External audit (Green/Energy) | ISO-certified agency required by NAAC |
| Faculty geotagged photos | Designed to require physical presence |

---

## Non-Functional Requirements

- **Performance:** Dashboard loads in <2s with 1,000 faculty records
- **Mobile:** Faculty attendance marking must work on a basic Android phone
- **Offline:** Attendance marking should work offline and sync when connected (PWA)
- **Data privacy:** Each college's data is fully isolated (row-level security)
- **Export:** All data exportable to Excel/PDF — no vendor lock-in
- **Uptime:** 99.5% minimum during inspection season (Nov–Feb, Jun–Jul)

---

## Success Metrics

| Metric | Target (Year 1) |
|---|---|
| Pilot colleges | 3 |
| Paying colleges (end of Year 1) | 25 |
| Daily active users per college | ≥60% of faculty |
| HOD WhatsApp messages before inspection | Reduced by 80% (self-reported) |
| Time to generate inspection report | <5 minutes (vs. 3 weeks manual) |
| NPS | ≥40 |
