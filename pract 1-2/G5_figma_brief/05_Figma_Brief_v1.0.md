# Student Internship Manager — Figma Design Implementation Brief

**Artifact:** `05_Figma_Brief_v1.0.md`  
**Version:** 1.0 — compiled implementation instructions  
**Decision status:** D-01–D-12, CH-G2-01–06, and D-G5-01–03 **APPROVED BY USER** for this design baseline; no teacher, client, or independent developer sign-off is implied.  
**Authoritative inputs:** `SRS_Student_Internship_Manager_v0_2_G2_Aligned.docx` (§3.2, §5, §6, §8–9); `Decision_Log_G2_Approved_v0_1.docx`; `02_Screen_Map_v0.1.docx`; `03_Developer_Verifiable_Screen_Contracts_v0.1.docx`, subject to the minimal G4 corrections below.  
**Reference convention:** `AC-...` and `BR-...` refer to SRS; `D-...` / `D-G5-...` to user-approved decisions; `T-...`, `N-...`, `ST-...`, and `C-...` are G2/G3 design-plan IDs, not new SRS requirements. `ANNOTATION` is not a product control.

## 1. Purpose and scope

Create **grayscale, low-fidelity, editable Figma wireframes** for **Student Internship Manager**, a responsive web platform for student internship discovery, applications, employer opportunity management, moderation, and advisory AI matching. Cover **US-01–US-09 and all 30 AC** with a compact set of canonical screens and selected control/state examples. The deliverable is a visual design artifact, **not a working application, tested system, or fully wired prototype**. [SRS §8.1; KC-01/02; AC-01.1–09.4]

The three and only three product roles are **Student**, **Company Representative**, and **Moderator**. The **Company** is a resource owner, not a separate user role; the mentor/supervisor is a contact, not an application role. Use preset role contexts for visual demonstration only. [D-01; D-09; SRS §8.2]

## 2. Design constraints and deliverable structure

- **One Figma working page** named `Student Internship Manager — MVP Wireframes`. Use editable **Figma-native text, shapes, instances, frames, and components**, not flattened images. Create **reusable local components** for navigation, input fields, cards, badges, form errors, empty results, disabled actions, and confirmations. Apply **Auto Layout where appropriate**, consistent spacing, readable typography, and simple **grayscale low-fidelity** styling. Use meaningful names such as `S04 / Published Catalogue`, `M01 / Resume Draft`, `ST-08 / Apply Blocked`. [KC-01; NFR-07; G2/G3 inventory]
- Arrange canonical product frames together and compact state examples beside their relevant frame; **do not generate an entire page for every role × status combination**. Label prototype routes with small reviewer notes only; at this stage **do not connect interactive prototype wires**. Put `REF-01` and all other reviewer annotations **outside product frames**. [G2 ST-01–25; REF-01]
- **No page-icon placeholders, decorative squares, row-selection checkboxes, multi-select rows, or bulk-action controls.** UI elements should represent named data or authorized actions only. No invented charts, widgets, tabs, controls, process steps, or extra product screens. [SRS §8.1; G2/G3]
- Respect source language for **literal source copy**: show the exact Ukrainian AI disclaimer and status labels where specified, even though this implementation brief is written in English. Other sample UI wording below describes intent; it must not be treated as separately approved validation copy. [AC-09.3; Q-18 still open]
- **D-G5-02 — approved presentation policy:** **hide controls owned solely by another product role**; **disable a control and show a concise reason** if the current role normally owns that action but its present resource/status/deadline makes it unavailable. Never treat visually hidden/disabled as proof of backend enforcement. [D-G5-02; BR-01/04–07; NFR-04/06]
- For this phase, **only annotate navigation and business-status transitions**. Do **not** request exports from Figma Agent, code, authentication/session management, backend services, persistence, conditional logic, role enforcement in code, live AI generation, or test execution. [D-09; G2/G3 verification boundaries]

## 3. Canonical screens and states — exact IDs

Create the **10 product/boundary screens** and **3 modal/overlay surfaces** below. The `ST-..` references are example states, not additional screens. IDs are stable; no screen should be split merely because it supports multiple User Stories. [G2 Screen Inventory; G3 Contracts]

| ID | Canonical name / type | Actor and required content | Compact states and source |
|---|---|---|---|
| **S01** | Authentication Boundary / **boundary placeholder** | Reviewer preset links for Student → S02, Company Representative → S08, Moderator → S10; **no credential inputs** | **ST-01**; T-01–03; D-09 |
| **S02** | Student Dashboard / product screen | Student links to Profile, Catalogue, My Applications, AI Recommendations; neutral own-application summary | **ST-02** empty; T-04–07; §9 S02 |
| **S03** | Student Profile / product screen | Own profile fields, Save, required-field errors | **ST-03** valid; **ST-04** invalid; T-08, N-02; AC-01.1–01.3 |
| **S04** | Internship Catalogue / product screen | Published Internship cards; query and four filters; expired card still visible | **ST-05** published/expired; **ST-06** empty; T-09/10; AC-02.1–03.3, D-10 |
| **S05** | Internship Details / product screen | Company-authored terms and guarded Apply | **ST-07** eligible; **ST-08** blocked; T-10/11/38, N-04–06; AC-04.1/04.2 |
| **S06** | My Applications / product screen | Student-owned applications, current status, Resume Draft, eligible Withdraw | **ST-11** seven statuses; T-06/14/17; AC-05.1–06.3 |
| **S07** | AI Recommendations / product screen | Prompt, recommended fields, Published Internship links, indicative score, exact disclaimer, catalogue link | **ST-13** results; **ST-14** failure; T-20–22, N-17/18; AC-09.1–09.4 |
| **S08** | Company Internship Management / product screen | Own opportunities and lifecycle actions Create, Edit, Send for Review, Close, Candidate Pipeline | **ST-15** owned list, **ST-18** corrected Rejected, **ST-19** Closed; T-23–29; AC-07.1–07.3/07.6 |
| **S09** | Company Candidate Pipeline / product screen | Company-owned Submitted+ application rows; **approved candidate-field whitelist**; authorized review actions | **ST-20** screening; **ST-21** invalid/stale state; T-29–34/40; AC-08.1–08.3, **D-G5-01** |
| **S10** | Moderator Internship Review / product screen | Pending Review queue; details of selected Internship, Approve and Reject; no candidate records | **ST-22** queue; **ST-23** outcome; T-35–37; AC-07.4/07.5 |
| **M01** | Application Action / modal | New Draft/Submit and Resume Existing Draft without duplicate | **ST-09** new; **ST-10** resume; T-11–16; AC-05.1–05.3, CH-G2-05 |
| **M02** | Internship Create/Edit / modal | Company-authored Internship fields, Save Draft/changes, Send for Review, Cancel | **ST-16** partial Draft; **ST-17** invalid Send; T-23–27/39; AC-07.1–07.3 |
| **M03** | Withdraw Confirmation / modal | Explicit confirmation for own Submitted/Under Review/Interview Application | **ST-12**; T-17–19; AC-06.2/06.3 |
| **REF-01** | **Reviewer annotation, NOT product screen** | Permission, state-machine, denial, and coverage references outside product frames | **ST-24** roles/ownership; **ST-25** two status machines; BR-03–12 |

`S02–S10` are **product screens**, not authentication placeholders. Only `S01` is a boundary placeholder. This corrects G4 DEF-07 without altering any product requirement. [G2 inventory; D-09]

## 4. Required labels and data

All sample records are **synthetic fixture data**, never real students, employers, contacts, AI results, or implemented logic. Mark them `DEMO DATA` in a reviewer note outside the product frames. Source-defined fields must remain distinguishable from absent values; **never invent missing company-authored internship content**. [BR-13; G3 contract]

### S03 — Student Profile [AC-01.1–01.3; C-S03-01–06]

| Field label | Required? | Absent or invalid presentation |
|---|---|---|
| Full name (ПІБ) | **Yes** | Empty input and per-field error on attempted Save; no save |
| Academic group | **Yes** | Empty input and per-field error on attempted Save; no save |
| Contact email | Not explicitly mandatory | Separate empty field; no invented regex requirement |
| Contact phone | Not explicitly mandatory | Separate empty field; no invented regex requirement |
| Technologies / skills | Not explicitly mandatory | Empty list/input |
| Interests | Not explicitly mandatory | Empty list/input |

Use `Save Profile` and `Back to Dashboard` as in G3. Do not add a password field or editable foreign Student profiles. Exact email/phone pattern validation and unapproved error copy are **not asserted**. [BR-04; Q-18]

### S04/S05 — Internship Catalogue and Details [AC-02.1–04.2; C-S04-01–06; C-S05-01–03]

Each **Published** catalogue card contains **position title, Company, required technology stack, location/format (`Remote` or `Office`), and application deadline**. Search matches **title and description/requirements**, and filters are **Company, technology/stack, Remote/Office format, internship direction**. A zero-match query yields `ST-06` without showing non-Published opportunities. [AC-02.1–03.3; BR-11]

Details contain **full description, duties, requirements, mentor/supervisor contact, location/format, duration and deadline**—all as originally entered by Company. Show the `Apply` control with its eligibility condition and a meaningful blocked reason. An expired Published card remains visible with the source label **«Дедлайн минув»**; `Closed` does not appear in the public catalogue. If a stale Closed detail is illustrated, Apply remains unavailable. The deadline is an **inclusive calendar date in `Europe/Kyiv`**; cut-off is **00:00 the following date** in that zone. [AC-04.1/04.2; BR-11/13; D-08/10; CH-G2-06]

### S06/M01/M03 — Student Applications [AC-05.1–06.3; C-S06-01–03; C-M01-01–05]

Show Internship reference, **own** Application status, and `submitted_at` only when Submitted or later; for Draft it is empty (an explanation such as **«Ще не подано»** can be an annotation rather than a new stored field). `Student ID` and `Internship ID` are assigned by context, not user-entered Application fields. `Application ID` is an identity/reference, not a new required input. [AC-05.1/05.2]

`M01` has **two modes**: `ST-09` **New** (explicit `Save Draft` or `Submit` creates a record) and `ST-10` **Resume** (existing Draft identity is preserved). **Do not map Save Existing Draft to T-12:** T-12 means creation of a **new** Draft. Saving edits to an existing Draft is an **in-place operation with the same ID and unchanged Draft status**, annotated with no invented business-status T-ID. `T-15` handles **the existing Draft → Submitted**. `Cancel` returns to **S05 in new mode** and **S06 in resume mode**, with no creation/change. This is a contract correction, not a newly approved product feature. [CH-G2-05; G4 DEF-01/10; T-12/14/15/16]

My Applications includes statuses `Draft`, `Submitted`, `Under Review`, `Interview`, `Accepted`, `Rejected`, `Withdrawn`. `Resume Draft` opens only own Draft; `Withdraw` opens `M03` only for own `Submitted`, `Under Review`, or `Interview`. Display `Accepted` as status in this view—**no notification interface**. No physical Delete for any Application. [BR-06/08; D-06/07; AC-06.1–06.3]

### S07 — AI Recommendations [AC-09.1–09.4; C-S07-01–07]

Show multiline Student prompt, **recommended professional fields**, **recommended Published internships**, an **indicative match score in `0.00–1.00`** labeled **«Орієнтовна відповідність»**, and a link to full Catalogue. Input derives from the Student's prompt plus **skills and interests**, not contact information. Recommendations are informational and must not hide the full catalogue or cause automatic Apply. [D-12; Q-15; BR-09]

Place this **exact source disclaimer** next to AI results:

> Рекомендації згенеровані штучним інтелектом в ознайомлювальних цілях. AI не приймає рішень щодо відбору

Show a before-request input example, populated result `ST-13`, empty result example and AI-service-failure `ST-14`; Catalogue stays available in the failure example. Any numeric score is **demonstration data, not an AI performance claim**. [AC-09.3; NFR-08]

### S08/M02 — Company Internship management [AC-07.1–07.6; C-S08-01–06; C-M02-01–14]

Company's Internship list shows **own Company title, status and deadline**, including sample rows for all five Internship statuses. `M02` fields are **Title, Direction, Technology stack, Description/duties, Requirements, Places, Location/Remote-or-Office format, Duration, Mentor contact, Deadline**. **Company ID comes from the authenticated Company context and is read-only**, never input by the user. Save Draft may keep incomplete fields. `Send for Review` requires all listed fields, with `Places` a **positive integer**; a rejected Internship must have **saved edits** before re-send. Editing is restricted to own `Draft` or `Rejected`; `Pending Review`, `Published` and `Closed` are not editable in MVP. [BR-05/10/12/13; D-03; CH-G2-03]

### S09 — Company Candidate Pipeline [AC-08.1–08.3; C-S09-01–07; **D-G5-01**]

For Applications to Internships belonging to the authenticated Company, display exactly this **approved candidate whitelist**: **candidate full name, Application reference, current Application status, Student technologies/skills, Student interests**. Do **not** display candidate email, phone, unrelated profile data, foreign-Company applications, or private Student `Draft` applications. Empty optional skills/interests stay empty rather than being fabricated. [CH-G2-01; D-G5-01; BR-05; NFR-06]

The allowed Company actions are `Start Review`, `Invite Interview`, `Reject` (from Under Review), `Accept`, and `Reject` (from Interview) **only in their specified state**. Represent denied/stale actions with a concise reason and unchanged status. [BR-06/07; AC-08.2/08.3]

### S10 — Moderator Internship Review [AC-07.4/07.5; C-S10-01–04]

Display only **Pending Review** Internship records and the selected Company's submitted Internship details; two actions are **`Approve`** (result `Published`) and **`Reject`** (result `Rejected`). There is **no `Approved` status**, candidate table, candidate profile, or Application status control. [BR-10; D-02; NFR-06]

## 5. Controls and permission rules

Use only the named G3 C-ID controls above. Apply the role ownership and invalid-state presentation policy **once**, using the matrix below. The `Catalogue` is viewable by all preset authenticated roles; Student-only search/application workflows remain Student-scoped. **D-G5-03** approves navigation to existing `S04` from the Company and Moderator workspaces: include a simple `Catalogue` navigation entry within their existing navigation, **not a new catalogue screen**. Such added entry references are **D-G5-03 annotations, not fabricated T-01–40 IDs**. [D-G5-02/03; §8.2; BR-01/04/05/09]

| Operation/resource | Student | Company Representative | Moderator |
|---|---|---|---|
| View Published Catalogue | Yes | Yes | Yes |
| Edit Student Profile | Own profile only | No | No |
| View Application | Own only | Submitted+ on own Company's Internship only, limited fields | No |
| New Draft / Submit / Resume / Withdraw | Own, only when eligible | No | No |
| Create/Edit Internship | No | Own Company, edit Draft/Rejected only | No |
| Send for Review / Close Internship | No | Own valid Draft or corrected Rejected / own Published respectively | No |
| Screen candidate Application | No | Own Company's eligible Applications only | No |
| Approve/Reject publication | No | No | Pending Review only |
| Request AI Recommendations | Yes | No | No |

Never add an extra product role (e.g., Administrator, Supervisor, Coordinator), and never infer right to modify an Application from the ability to view a Published Internship. [D-01; BR-01–10]

## 6. Allowed business-status transitions — complete reference

These are **business-status changes**, distinct from screen navigation. **Only** the following are allowed; all other status changes have **no navigation/business transition**, and unsuccessful fixtures show unchanged records. Editing/saving a record without changing its status is **not** another status transition. [BR-06/07/10; D-04]

### Application — seven statuses, nine allowed transitions [BR-02/06; SRS §8.3]

| From → To | Authorized actor | G2 route / condition |
|---|---|---|
| Draft → Submitted | Student | Same own Draft ID, Published and before deadline; T-15 |
| Submitted → Withdrawn | Student | Own record, confirm in M03; T-17/18 |
| Under Review → Withdrawn | Student | Own record, confirm in M03; T-17/18 |
| Interview → Withdrawn | Student | Own record, confirm in M03; T-17/18 |
| Submitted → Under Review | Company Representative | Own Company; T-30 |
| Under Review → Interview | Company Representative | Own Company; T-31 |
| Under Review → Rejected | Company Representative | Own Company; T-32 |
| Interview → Accepted | Company Representative | Own Company; T-33 |
| Interview → Rejected | Company Representative | Own Company; T-34 |

`Accepted`, `Rejected`, `Withdrawn` are terminal for their existing Application. Reapplication after `Withdrawn` or `Rejected` creates a **new** Application only if the Internship remains Published, the deadline has not passed, and no active application exists; reapplication after `Accepted` is prohibited. `Draft`, `Submitted`, `Under Review`, `Interview` count as active for the same Student–Internship pair. [BR-03; D-05]

### Internship — five statuses, five allowed transitions [BR-10/12; SRS §8.4]

| From → To | Authorized actor | G2 route / condition |
|---|---|---|
| Draft → Pending Review | Company Representative | Own, complete valid fields; T-27 |
| Rejected → Pending Review | Company Representative | Own, corrections already edited and saved; T-25/26/27 |
| Pending Review → Published | Moderator | `Approve` action; T-36 |
| Pending Review → Rejected | Moderator | `Reject` action; T-37 |
| Published → Closed | Company Representative | Own, `Close Internship`; T-28 |

`Closed` is terminal and prevents new Applications and Submit of a previously saved Draft. **Existing Submitted+ Applications preserve their statuses and can continue through their otherwise permitted processing and Withdraw transitions.** [D-11; AC-07.6]

## 7. “Important” predicate — applicability clarification

**NOT APPLICABLE TO THIS PROJECT.** Student Internship Manager has no `Issue`, `Priority`, `Assignee`, `Team Member`, `Team Lead`, `Resolved`, `Not Set` priority, or `Important Issues` feature. The Mini Issue Tracker predicate `priority IN {High, Critical} AND status != Closed` and its four Issue statuses/four role–assignee contexts **must not appear in product frames or reviewer state matrices**. They are **not** Student Internship Manager source requirements. [SRS §8.1–8.5; D-01; G4 source review]

Instead, `REF-01 / ST-24–25` must show the **three** approved product roles and both complete **seven-/five-status** matrices from §5–6 of this brief. This is the only valid state-reference replacement for the unrelated four-by-four Issue Tracker request. [D-01/02/04; G2 REF-01]

## 8. Required empty, validation, denial and error examples

Render these as **compact labeled fixtures/components**, not full duplicate screens. Messages can be **descriptive reviewer annotations** unless exact source copy is quoted above; do not treat illustrative copy as a new accepted product text requirement. **Do not claim the depicted denial demonstrates server-side authorization or atomicity.** [G2 N-01–18; BR-07; NFR-04/05]

| Reference | Surface and fixture | Expected visible result |
|---|---|---|
| N-01 | Protected area / wrong preset context | No protected product content or action for wrong role; no T-ID |
| N-02 | S03, missing name or academic group | Field-specific error, no Save outcome; ST-04 |
| N-03 | S04, zero matches | Empty results message, query/filters remain available; ST-06 |
| N-04 | S05, expired Published | Expired label and disabled Apply with reason; ST-08 |
| N-05 | S05, existing active Draft or Accepted | New Apply disabled; own Draft resumes via S06; Accepted prevents new Apply |
| N-06 | S05, stale Closed detail | Apply disabled; Closed absent from catalogue |
| N-07 | M01, duplicate/stale Application | Reason distinguishes active duplicate from Accepted; no second ID/status change |
| N-08 | S06, Draft or terminal Application | Withdraw unavailable; never Delete |
| N-09 | M01 resume Draft after deadline/Closed | Save identity preserved; Submit unavailable; no Draft→Submitted |
| N-10 | M02, incomplete Send / Places invalid | Field-specific errors; Internship remains Draft/Rejected; ST-17 |
| N-11 | S08, edit Pending Review/Published/Closed | Edit disabled for Company actor; resource unchanged |
| N-12 | S08, Rejected unchanged | Resend disabled until corrected edits saved; Rejected unchanged |
| N-13 | S09, forbidden or stale status transition | Error annotation; same status, **no permitted T-ID**; ST-21 |
| N-14 | S09, foreign Company / private Student Draft | Candidate data absent; access denial annotation |
| N-15 | S10, no longer Pending Review | Approve/Reject unavailable; record not mutated |
| N-16 | S10, candidate/Application action sought | No candidate/profile/status product controls |
| N-17 | S07, AI unavailable | Error example; normal Catalogue route still available; ST-14 |
| N-18 | S07, AI results | Read-only advice; no automatic Application or status change |

Also show: **S02 no own applications**, **S06 no own applications**, **S08 no own Internship**, **S09 no eligible candidate Applications**, **S10 no Pending Review items**, **S07 no recommendations**. An absent optional field stays empty; a missing required Company-authored Published detail is a **data problem**, not permission to invent a value. [AC-03.3; US-06–09; BR-13]

For `AC-05.3` show **four distinct data examples** in annotations: (1) active application blocks another; (2) Accepted blocks another permanently for the same Internship; (3) Withdrawn allows a *new* Application if Published and before deadline; (4) Rejected allows a *new* Application under the same conditions. Existing terminal records remain. Use different application references to make the distinction visible; no numeric IDs are prescribed by source. [BR-03; D-05; G4 DEF-03]

## 9. Navigation intent — annotations only

Annotate the routes below **outside** product frames. The route list describes *intent*; it is **not a request to build prototype wiring, conditional logic, or database behavior**. Keep the original G2 T-ID where available; do not invent T-ID for additional navigation. [G2 T-01–40; D-G5-03]

| Flow | Annotated route | Key gate / visible consequence |
|---|---|---|
| Role entry | S01 → S02 / S08 / S10 (`T-01/02/03`) | Preset role, no true login |
| Student browse | S02 → S04 (`T-05`) → S05 (`T-10`) | Published cards only; expired still browseable |
| Student profile | S02 → S03 (`T-04`), Save `T-08` | Required field errors `N-02` |
| Student search | S04 → S04 filtered (`T-09`) | No matches `N-03` |
| New application | S05 → M01 new (`T-11`) → S06 Draft (`T-12`) **or** Submitted (`T-13`) | No application on opening modal or Cancel |
| Resume Draft | S06 → M01 resume (`T-14`) → S06 Submitted (`T-15`) | Same Application ID; `Save existing Draft` is **not T-12** |
| Cancel M01 | M01 new → S05; M01 resume → S06 (`T-16` origin-qualified) | No create/submit/status transition |
| Withdraw | S06 → M03 (`T-17`) → S06 Withdrawn (`T-18`), or Cancel (`T-19`) | Only permitted three statuses |
| AI advisory | S02 → S07 (`T-07`), results (`T-20`), S05 (`T-21`), then manual Apply (`T-11`) | No AI automatic Apply; full S04 via `T-22` |
| Company opportunity | S08 → M02 (`T-23/25`), Save (`T-24/26`), Send (`T-27`), Close (`T-28`) | Corrected Rejected required before resend |
| Company candidates | S08 → S09 (`T-29`), transitions `T-30–34`, back `T-40` | Company ownership and approved field whitelist |
| Moderator publication | S10 queue → detail (`T-35`), Approve (`T-36`) or Reject (`T-37`) | Only Pending Review |
| Return to Catalogue | S05 → S04 (`T-38`) | No additional product screen |
| Other-role Catalogue | S08 or S10 navigation → **existing S04** | **Approved D-G5-03**; annotation has **no new G2 T-ID** |

Do **not** introduce the previously proposed `Return to AI` control (`D-G3-03` remains unapproved); existing AI-to-details and full-catalogue routes suffice. Likewise omit unapproved optional S03/S06 cross-navigation unless an existing approved T-ID covers it; simply label such references as reviewer-only if needed. This removes G4 DEF-04 without silently approving new UX controls. [G3 C-S05-04; G4 DEF-04; D-G5-03]

## 10. Synthetic sample data — visual fixtures only

Use the following **illustrative values** solely to make the approved fields and guards visible. These values do not define product content, AI effectiveness, data storage, matching logic, or validated test outcomes.

| Fixture | Example data | Intended demonstration |
|---|---|---|
| Student profile | `Olena Kovalenko`; `SE-23-4`; skills `C#, SQL`; interest `Backend development`; email/phone empty | S03 required versus optional fields |
| Company and internship | `Northstar Labs` / `Backend Internship`; stack `C#, SQL`; `Remote`; direction `Backend`; places `2`; duration `8 weeks`; mentor `Demo Mentor` | S04/S05/M02 Company-authored fields |
| Published, within deadline | `Backend Internship`, `Published`, deadline `2026-12-15` | Eligible S05 Apply, ST-07 |
| Published, expired | `QA Internship`, `Published`, deadline `2026-10-20` | Still S04-visible; expired label, disabled Apply |
| Closed | `Data Internship`, `Closed` | S08 list and S05 stale-detail denial; absent from S04 |
| New and existing Draft | `APP-DEMO-01` Draft vs `APP-DEMO-02` Submitted, separate application references | M01 New/Resume and submitted_at treatment |
| Screening | `Olena Kovalenko`, `APP-DEMO-02`, `Submitted`, `C#, SQL`, `Backend development` | S09 only the D-G5-01 whitelist |
| AI | Student prompt `I know C# and SQL and want backend work`; indicative score `0.78` | Read-only score and exact source disclaimer |
| Moderation | `Pending Review` sample Company-authored opportunity | S10 Approve / Reject outcomes |

When showing the three terminal Application states and all Internship statuses, use compact **state chips or `REF-01` rows**, not separate product pages. The fixtures are **not test data that have been executed**. [ST-11, ST-15, ST-24/25]

## 11. Exclusions — prohibited features, once

**Do not include:** Mini Issue Tracker's Issue/Important/Priority/Assignee/Team Lead/Team Member models; other product roles; CV file upload/parsing, PDF referrals/orders, document generation, chat/video, university ERP/dean's-office/HR integrations, advanced analytics or reporting, native mobile applications, autonomous AI candidate selection or Apply, registration, a real login/password/SSO screen, notification center/email/push alerts, fabricated status-history event timeline, physical Application Delete, bulk/row-selection functions, unrelated product controls, additional business statuses, or any invented persistence, authentication, backend, security or workflow implementation. [SRS §2.3; KC-04/06/07; D-01/07/09; BR-08/09; G4]

Technical NFRs such as **HTTPS, server authorization, atomic state changes, backup/restore, performance and real AI availability** remain implementation-level obligations but **must not become product screens** or be claimed verified through these wireframes. [NFR-01–06/08]

## 12. Acceptance checklist for the delivered Figma design

Use this as a **planned inspection checklist**, not test evidence. Mark all results `NOT RUN` until a reviewer actually checks the generated artifact. [G3 test design; G4]

| Check | Expected inspection evidence | Source |
|---|---|---|
| `F-01` | Single working page; editable native layers; named frames/components; usable Auto Layout; grayscale low-fi | §2 constraints |
| `F-02` | Exact `S01–S10`, `M01–M03`; `REF-01` outside product frames; `ST-01–25` via compact references | G2 inventory |
| `F-03` | Student profile fields and missing required-field example; only own edits | AC-01.1–01.3 |
| `F-04` | Published-only Catalogue with complete card data, search, four filters, no-results and expired examples | AC-02.1–03.3; D-10 |
| `F-05` | Internship Details and three distinct Apply blocks: expired, active/Accepted, Closed | AC-04.1/04.2; BR-03/11 |
| `F-06` | M01 new vs resume; existing Draft keeps same reference, no duplicate; explicit Draft vs Submit; no Submit after deadline/Closed | AC-05.1–05.3; CH-G2-05; G4 DEF-01 |
| `F-07` | Own My Applications showing all seven statuses, eligible Withdraw and terminal states; no Delete | AC-06.1–06.3 |
| `F-08` | M02 full field list; Company ID auto; partial Draft; invalid Send; corrected Rejected resend | AC-07.1–07.3/07.5; D-03 |
| `F-09` | S10 Pending Review → Published/Rejected, S08 Published → Closed; no Approved status | AC-07.4–07.6; BR-10 |
| `F-10` | S09 Submitted+ own-company candidates with only approved field whitelist and five permitted screening transitions | AC-08.1–08.3; D-G5-01 |
| `F-11` | AI prompt, Published links, indicative `0.00–1.00` score, exact disclaimer, error and manual Apply route | AC-09.1–09.4; D-12 |
| `F-12` | Role-based hidden controls; same-role invalid-state controls disabled with explanation; moderator has no Application controls | D-G5-02; BR-06 |
| `F-13` | Existing S04 reachable from Company and Moderator contexts by annotation, without new screens/T-IDs | D-G5-03 |
| `F-14` | `REF-01` shows three product roles, full 7/5 business-state sets, allowed arrows only, terminal states and denial examples | §8.2–8.4; D-01/02/04 |
| `F-15` | All 30 AC are traceable through these frames and annotations; no prohibited functions or invented UX decisions | US-01–09; §11 |
| `F-16` | No claim of server RBAC, actual AI inference, backend persistence, test PASS, or teacher approval | NFR-01–08; G4 |


### AC-to-frame coverage index (30 source criteria; planned only)

| Source AC | Figma evidence | Source AC | Figma evidence |
|---|---|---|---|
| AC-01.1 | S03 / C-S03-01–05 | AC-01.2 | S03 / ST-04 / N-02 |
| AC-01.3 | S03 / REF-01 | AC-02.1 | S04 / ST-05 |
| AC-02.2 | S04 / published card | AC-02.3 | S04 / REF-01 |
| AC-03.1 | S04 / C-S04-01 | AC-03.2 | S04 / C-S04-02–05 |
| AC-03.3 | S04 / ST-06 | AC-04.1 | S05 / C-S05-01 |
| AC-04.2 | S05 / ST-07–08 / N-04–06 | AC-05.1 | M01 / ST-09–10 |
| AC-05.2 | M01 / S06 / identity annotations | AC-05.3 | S05 / M01 / N-05/07 |
| AC-06.1 | S06 / ST-11 | AC-06.2 | S06 / M03 / N-08 |
| AC-06.3 | M03 / T-18/19 / S06 | AC-07.1 | M02 / C-M02-01–11 |
| AC-07.2 | S08 / M02 / N-11 | AC-07.3 | M02 / ST-17 / T-27 |
| AC-07.4 | S10 / T-36 | AC-07.5 | S10 / T-37; S08 / ST-18 |
| AC-07.6 | S08 / ST-19 / T-28 | AC-08.1 | S09 / D-G5-01 / N-14 |
| AC-08.2 | S09 / T-30–34 | AC-08.3 | S09 / ST-21 / N-13 |
| AC-09.1 | S07 / C-S07-01/02 | AC-09.2 | S07 / C-S07-03–05 |
| AC-09.3 | S07 / C-S07-06 | AC-09.4 | S07 → S05 → M01; N-18 |

Coverage classification: **30/30 planned**, **0 actually verified**. This is an index of visual evidence and annotations, not a claim that an absent implementation has passed acceptance tests. [SRS §5; G2 coverage; G3 Traceability]

**Acceptance status at authoring:** `NOT RUN` for every check. The brief is **READY TO USE AS FIGMA GENERATION INSTRUCTIONS** under the explicitly approved D-G5-01–03 baseline; generated screens still require **G4/G6 human review**, and no verification or external approval is claimed.
