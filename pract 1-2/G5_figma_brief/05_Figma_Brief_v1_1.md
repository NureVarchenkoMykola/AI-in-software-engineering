# Student Internship Manager — Figma Design Implementation Brief

**Artifact:** `05_Figma_Brief_v1.1.md`
**Version:** 1.1 — supersedes `05_Figma_Brief_v1.0.md`
**Governing requirement source:** `Student_Internship_Manager_SRS_v1_1_Aligned.docx` (US-01–US-10, **79 AC**, S01–S11, M01–M04). Where this brief and the SRS differ, the SRS wins.
**Other inputs:** `Decision_Log_G2_Approved_v0_1.docx` (D-01–D-12, CH-G2-01–06, as amended in §0 below); `02_Screen_Map_v0.1.docx`; `03_Developer_Verifiable_Screen_Contracts_v0.1.docx`; `04_G4_Critical_Plan_Review_v0.1.docx` (DEF-01–DEF-12); Figma file *Student Internship Manager — MVP Wireframes*.
**Decision status:** D-01–D-12 (except the superseded parts listed in §0), CH-G2-01–06 and D-G5-02/03 are **approved by user**. The five SRS v1.1 business decisions in §0 (**DL-P-01–DL-P-05**) are required by the SRS but their **Decision Log entries are still pending**; this brief treats them as binding only because the SRS requires them. No teacher, client or independent developer sign-off is implied.
**Reference convention:** `AC-…`, `BR-…`, `GR-…` refer to the SRS. `D-…` / `D-G5-…` / `DL-P-…` refer to decisions. `T-…`, `N-…`, `ST-…`, `C-…` are G2/G3 design-plan IDs, not SRS requirements. New navigation or fixtures that have no G2/G3 ID are marked **ID pending**; do not invent IDs for them. `ANNOTATION` is never a product control.

---

## 0. What changed from v1.0

The v1.0 brief was written against SRS v0.2 (US-01–US-09, 30 AC). SRS v1.1 adds US-10 and several behaviours that v1.0 explicitly forbade. The table lists each conflict and how this brief resolves it.

| ID | v1.0 position | SRS v1.1 position | Resolution in v1.1 |
|---|---|---|---|
| **DL-P-01** | S01 is a boundary placeholder; D-09/Q-14: no registration, no login (v1.0 §3, §11) | US-10, AC-10.1–10.5: Login + self-registration of **Student** and **Company Representative** with Email, Password, Role; Moderator accounts are created by a System Administrator, never via public signup | S01 shows Login and Signup forms. S01 is a **product screen**; there is no boundary placeholder left |
| **DL-P-02** | D-07: no notification interface (v1.0 §4, §11) | AC-08.8: bell indicator with unread count in the Student header and an informational banner on S02 when an Application becomes **Accepted** | Bell + banner are drawn. Nothing else (no notification centre, email or push) |
| **DL-P-03** | Q-16: no status-history timeline (v1.0 §11) | AC-06.8, NFR-07: read-only status history on **S11** (status, timestamp, initiator role) | S11 added. History is read-only; no editing |
| **DL-P-04** | Reject is a direct action on S10 | AC-07.13: Reject opens **M04**; optional moderator comment (≤ 500 chars) shown to the Company on S08 beside the Rejected Internship | M04 added; S08 shows the comment |
| **DL-P-05** | D-G5-01: exactly 5 candidate fields; **no** email/phone (v1.0 §4 S09) | AC-08.1: 7 fields incl. **Email and Phone Number** (empty when the student left them empty); **Withdrawn** applications visible read-only; Draft hidden | S09 shows 7 columns and read-only Withdrawn rows. D-G5-01 is amended accordingly |
| Screens | "Exactly S01–S10, M01–M03" | S01–S11, M01–M04 | 15 product frames |
| S02 | Links only | AC-09.9: AI widget with a short prompt field leading to S07 | Required (see §13 — Figma gap) |
| S06 | Resume / Withdraw | adds **Details & History → S11** | Added |
| AC count | 30 | 79 | §12 coverage index |

---

## 1. Purpose and scope

Create **grayscale, low-fidelity, editable Figma wireframes** for **Student Internship Manager**, a web platform for student internship discovery, applications, employer opportunity management, moderation and advisory AI matching. Cover **US-01–US-10 and all 79 AC** with a compact set of canonical screens and selected control/state examples. The deliverable is a visual design artifact, **not a working application, tested system or wired prototype**. [SRS §8.1; KC-01/02]

The three and only three product roles are **Student**, **Company Representative** and **Moderator**. **Company** is a resource owner, not a role. The mentor/supervisor is a contact, not a role. **System Administrator** is a secondary stakeholder with **no product UI** and no screen in this file. Wireframes show static Login/Signup forms and role-specific start screens; they do not implement authentication. [GR-01; AC-10.2; DL-P-01]

---

## 2. Design constraints and deliverable structure

- **One Figma working page** named `Student Internship Manager — MVP Wireframes`. Use editable **Figma-native text, shapes, instances, frames and components**; no flattened images. Create **reusable local components** (navigation, input fields, cards, badges, form errors, empty results, disabled actions, confirmations). Apply **Auto Layout where appropriate**, consistent spacing, readable typography and **grayscale low-fidelity** styling. Use meaningful names such as `S04 / Internship Catalogue`, `M01 / Application Action`. Product frames are named `Sxx / …` or `Mxx / …`; the compact state frame beside each is named `Sxx / … reference`.
- Arrange canonical product frames together and put compact state examples **beside** their frame. **Do not generate a page for every role × status combination.** Label navigation with small reviewer notes only; **do not connect interactive prototype wires**. Put `REF-01` and every reviewer annotation **outside product frames**.
- **No decorative icons, page-icon placeholders, decorative squares, row-selection checkboxes, multi-select rows or bulk actions.** The **only permitted icon is the Notification bell** required by AC-08.8. No invented charts, widgets, tabs, controls or process steps.
- **Badges:** the SRS says "coloured badge" (AC-06.1); this file is grayscale, so every status badge is a **gray chip with a text label**. Colour must never carry meaning.
- **Language of copy.** SRS button and message names are partly Ukrainian. Figma uses the English labels listed in §5.1. Only **three literal Ukrainian strings** must appear exactly: the AI disclaimer (AC-09.3), **«Орієнтовна відповідність»** (AC-09.2) and **«Дедлайн минув»** (AC-02.4). Other sample wording describes intent and is not separately approved copy. [Q-18 still open]
- **D-G5-02 — presentation policy:** **hide controls owned solely by another role**; **disable a control and show a concise reason** if the current role normally owns the action but resource, status or deadline makes it unavailable. Hidden or disabled never proves backend enforcement. [GR-03]
- Annotate only navigation and business-status transitions. Do **not** request code, real authentication/session management, backend, persistence, live AI generation or test execution.
- **Layout width:** desktop frames at 1200 px (modals 560–800 px). Responsive breakpoints and WCAG target (Q-21) are open and are **not** asserted by this file. [KC-01]

---

## 3. Canonical screens and states

Create the **11 screens** and **4 modal surfaces** below. `ST-…` are example states, not extra screens. IDs are stable; do not split a screen because it supports several User Stories.

| ID | Canonical Figma name / type | Actor and required content | Compact states and source |
|---|---|---|---|
| **S01** | Login and Signup / product screen | Login (Email, Password, Sign in) and Signup (Email, Password, **Role: Student or Company only**, Sign up); one generic error block. **No Moderator signup.** | **ST-01**; T-01–03; N-01; AC-10.1–10.5; DL-P-01 |
| **S02** | Student Dashboard | Own-application summary; **AI widget with short prompt field and "Request recommendations" action, marked AI**; links to Profile, Catalogue, My Applications; **Accepted banner + bell count** when an Application is Accepted | **ST-02** empty; T-04–07; AC-06.9, AC-08.8, AC-09.9 |
| **S03** | Student Profile | Own profile fields, privacy hint, Save Profile, required-field errors, saved confirmation | **ST-03** valid; **ST-04** invalid; T-08; N-02; AC-01.1–01.6 |
| **S04** | Internship Catalogue | Published cards; query, four filters, **reset**; expired card still visible | **ST-05** published/expired; **ST-06** empty; T-09/10; AC-02.1–03.6 |
| **S05** | Internship Details | Company-authored terms and guarded Apply | **ST-07** eligible; **ST-08** blocked; T-10/11/38; N-04–06; AC-04.1–04.5 |
| **S06** | My Applications | Own applications, status chip, Resume Draft, eligible Withdraw, **Details & History** | **ST-11** seven statuses; T-06/14/17; AC-05.8, AC-06.1–06.7 |
| **S07** | AI Recommendations | Prompt, recommended fields, Published links, indicative score, exact disclaimer, catalogue link | **ST-13** results; **ST-14** failure; T-20–22; N-17/18; AC-09.1–09.10 |
| **S08** | Company Internship Management | Own opportunities, five lifecycle statuses, Create / Edit / Send for Review / Close / Candidate Pipeline; **moderator rejection reason beside Rejected** | **ST-15** list; **ST-18** corrected Rejected; **ST-19** Closed; T-23–29; AC-07.1–07.10, 07.13 |
| **S09** | Company Candidate Pipeline (SRS title: *Company Applications*) | Own-Company application rows; **7 approved columns**; review actions; read-only Withdrawn rows | **ST-20**, **ST-21**; T-29–34/40; AC-08.1–08.7; DL-P-05 |
| **S10** | Moderator Internship Review | Pending Review queue, selected Internship details, Approve and Reject; no candidate data | **ST-22**, **ST-23**; T-35–37; AC-07.4/07.5/07.11/07.12/07.14 |
| **S11** | Application History | Own application summary; read-only chronological **status history** (status, timestamp, initiator role); Back to My Applications; status-appropriate actions | **State reference** beside; AC-06.8, AC-08.8; DL-P-03; **T-ID pending** |
| **M01** | Application Action | New Draft/Submit and Resume Existing Draft | **ST-09** new; **ST-10** resume; T-11–16; AC-05.1–05.8 |
| **M02** | Internship Create/Edit | Company-authored fields, Save Draft/changes, Send for Review, Cancel | **ST-16**, **ST-17**; T-23–27/39; AC-07.1–07.3/07.7/07.8/07.15 |
| **M03** | Withdraw Confirmation | Confirm for own Submitted / Under Review / Interview Application | **ST-12**; T-17–19; AC-06.2/06.3 |
| **M04** | Reject Internship | Internship + company + status; optional comment (≤ 500, with counter); Confirm Reject, Cancel | **State reference** beside; AC-07.13; DL-P-04; **T-ID pending** |
| **REF-01** | Reviewer Reference — **not a product screen** | Role/ownership matrix, both status machines, denial and coverage references, outside product frames | **ST-24**, **ST-25**; BR-03–12 |

Also in the file: `Local Components / Wireframe Library` (outside product frames).

---

## 4. Required labels and data

All sample records are **synthetic fixtures**. Mark them `DEMO DATA` in a reviewer note outside product frames. Never invent missing company-authored content. [BR-13]

### 4.1 S01 — Login and Signup [AC-10.1–10.5]

| Block | Content |
|---|---|
| Login | Email, Password, **Sign in** |
| Signup | Email, Password, **Role** with exactly two choices — **Student**, **Company**; **Sign up** |
| Error | One **generic** error block for invalid credentials or invalid registration; it must not reveal which field is wrong (AC-10.4) |
| Reference states | invalid credentials; **email already exists** (signup); session ended; N-01 *Protected content unavailable* for a wrong role |
| Post-login intent (annotation) | Student → S02, Company Representative → S08, Moderator → S10 (T-01/02/03) |

Do **not** add Moderator or Administrator choices, SSO, password reset or a company-selection field (the SRS does not define one; see §13 OQ-01).

### 4.2 S02 — Student Dashboard [AC-06.9, AC-08.8, AC-09.9]

Student name and group; **My application summary** (Internship, Company, Application reference, current status) with link to My Applications; cards for Profile and Catalogue; **AI widget** with a short prompt field, an action to request recommendations and an AI mark; when an Application is Accepted, a **banner** with the Internship name and a **View Application History** action to S11 plus the bell count in the header. No banner and no count when there is nothing unread. The notification never changes a status. ST-02 shows the empty state (no applications).

### 4.3 S03 — Student Profile [AC-01.1–01.6]

| Field label | Required? | Absent or invalid presentation |
|---|---|---|
| Full name (ПІБ) | **Yes** | Empty input and per-field error on attempted Save; no save |
| Academic group | **Yes** | Same |
| Contact email | No | Separate empty field; basic format check only if filled |
| Contact phone | No | Separate empty field; no invented pattern |
| Technologies / skills | No | Empty list/input |
| Interests | No | Empty list/input |

Show a **privacy hint**: email and phone are visible only to the Company Representative of the company to which the student applied (AC-01.4). Show a **saved confirmation** after a successful Save (AC-01.6). Buttons: `Save Profile`, `Back to Dashboard`. Do not add a password field or other students' profiles.

### 4.4 S04 / S05 — Catalogue and Details [AC-02.1–04.5]

Each **Published** card: position title, Company, technology stack, location/format (`Remote` or `Office`), application deadline, `View Details`. Search matches title, description and requirements; filters are **Company, Technology/stack, Format (Remote/Office), Internship direction**; all combine with AND; a **reset** action clears query and filters (AC-03.6). Zero matches → ST-06 (query and filters stay available). No published internships at all → empty state with explanation (AC-02.7). Missing card data stays empty (AC-02.5). An expired Published card stays visible with **«Дедлайн минув»**; **Closed** never appears in the catalogue. For Company and Moderator the catalogue is **view mode**: search, filters and Apply are hidden (AC-02.6, D-G5-03).

S05 shows: title, status, company, full description, duties, requirements, direction, stack, format, duration, places, mentor/supervisor contact, deadline, `Apply`, `Back to Catalogue`. Apply is enabled only if Published, before deadline, with no active (Draft, Submitted, Under Review, Interview) and no Accepted application. Blocked reasons (AC-04.3): **deadline passed**; **active application exists** (continue the Draft in My Applications); **already accepted**; **internship closed**. A stale Closed detail keeps Apply unavailable (AC-04.4). Company and Moderator do not see Apply (AC-04.5). Deadline is an **inclusive calendar date in `Europe/Kyiv`**; cut-off is 00:00 the following date (GR-02).

### 4.5 S06 / S11 / M01 / M03 — Student Applications [AC-05.1–06.9]

S06 row: Internship, Company, Application reference, `submitted_at` (empty for Draft; «Ще не подано» is an annotation only), status chip, and actions: `Resume Draft` (Draft only), `Withdraw` (Submitted / Under Review / Interview only), `Details & History` (every status → S11). For Accepted, Rejected and Withdrawn, Withdraw is disabled with *terminal status* explanation; for Draft it is unavailable with *Resume Draft instead*. Seven statuses: `Draft`, `Submitted`, `Under Review`, `Interview`, `Accepted`, `Rejected`, `Withdrawn`. No physical Delete. Empty state when the student has no applications.

S11: own application summary and a **read-only** table *Status · Timestamp (Europe/Kyiv) · Initiator role* in chronological order, where initiator is **Student** or **Company Representative**. Actions follow status: `Resume Draft` only for Draft, `Withdraw` only for the three allowed statuses; `Back to My Applications` → S06.

M01 has **two modes**: `ST-09` **New** (Save Draft creates Draft, Submit creates Submitted; opening or cancelling creates nothing) and `ST-10` **Resume** (existing Draft identity preserved). **Save Existing Draft is not T-12**: it updates the same record with the same ID and Draft status; no status T-ID. `T-15` is the existing Draft → Submitted. `Cancel` → S05 in new mode, S06 in resume mode (T-16, origin-qualified). After a successful save or submit the student lands on S06 (AC-05.8). Student ID and Internship ID come from context; Application reference is identity, not input. [DEF-01/DEF-10]

### 4.6 S07 — AI Recommendations [AC-09.1–09.10]

Multiline prompt; line stating what is used (*prompt, technologies/skills and interests; contact information is not used*); `Request Recommendations`; **Recommended professional fields**; **Recommended Published internships** (stack, format, deadline, **«Орієнтовна відповідність»** with a value in `0.00–1.00`, `View Internship`); `Full Catalogue`. Place this **exact disclaimer** next to AI results:

> Рекомендації згенеровані штучним інтелектом в ознайомлювальних цілях. AI не приймає рішень щодо відбору

Show four states: before request, results (ST-13), empty («No recommendations available» intent) and AI-service failure (ST-14, catalogue stays reachable, applications unchanged). The score is demonstration data, not an AI performance claim. Student only; hidden for the other roles (AC-09.10).

### 4.7 S08 / M02 / M04 — Company Internship management [AC-07.1–07.10, 07.13, 07.15]

S08 lists **own Company's** Internships with title, status and deadline; sample rows for all five statuses (Draft, Pending Review, Published, Rejected, Closed). Actions `Create Internship`, `Edit`, `Send for Review`, `Close Internship`, `Candidate Pipeline`; unavailable actions are disabled with a reason. A **Rejected** row shows the **moderator rejection reason** when one was given. Empty state with `Create Internship`.

M02 fields: **Title, Direction, Technology stack, Description/duties, Requirements, Places, Location/format (Remote or Office), Duration, Mentor contact, Deadline**. **Company ID is read-only**, taken from context. Save Draft may leave fields empty. `Send for Review` needs every field, `Places` a **positive integer**, a valid deadline; a Rejected Internship needs **saved corrections** before re-send. Edit is allowed only for own Draft or Rejected. `Cancel` saves nothing and returns to S08.

M04: title *Reject Internship?*, Internship name and Company, status Pending Review, short explanation, **optional comment up to 500 characters** with a character counter, `Confirm Reject`, `Cancel`. Confirm → S10 with the record in Rejected and out of the queue; Cancel → S10 unchanged.

### 4.8 S09 — Company Candidate Pipeline [AC-08.1–08.7; DL-P-05]

For Applications to Internships of the authenticated Company show **exactly these columns**: **Name, Application reference, Status, Skills, Interests, Email, Phone**. Email and Phone appear only if the student filled them; otherwise the cell stays empty and nothing is invented. **Withdrawn** rows are visible **read-only** with no actions. Private Student Drafts and other Companies' applications are never shown. Actions `Start Review`, `Invite Interview`, `Accept`, `Reject`, each only in its allowed state; stale or forbidden actions show an *action unavailable* reason and an unchanged status. Closed internships do not stop permitted processing of submitted applications (AC-08.5). Empty state when there are no Submitted-or-later applications. `Back to Internship Management` → S08.

### 4.9 S10 — Moderator Internship Review [AC-07.4/07.5/07.11/07.12/07.14]

Only **Pending Review** records and the selected Company's submitted details (Company, Direction, Stack, Description/duties, Requirements, Places, Location/format, Duration, Mentor contact, Deadline). Actions `Approve` (→ Published) and `Reject` (→ M04 → Rejected). No *Approved* status, no candidate table, profile or application control. Empty queue state; stale item → actions unavailable, record unchanged.

---

## 5. Controls and permission rules

| Operation / resource | Student | Company Representative | Moderator |
|---|---|---|---|
| Sign in / sign out | Yes | Yes | Yes |
| Self-register | Yes | Yes | **No** (account created by System Administrator) |
| View Published Catalogue | Yes | Yes (view mode) | Yes (view mode) |
| Edit Student Profile | Own only | No | No |
| View Application | Own only, incl. history | Own Company's Submitted+ and Withdrawn (read-only); limited fields | No |
| New Draft / Submit / Resume / Withdraw | Own, only when eligible | No | No |
| Create / Edit Internship | No | Own Company; edit Draft/Rejected only | No |
| Send for Review / Close Internship | No | Own valid Draft or corrected Rejected / own Published | No |
| Screen candidate Application | No | Own Company's eligible Applications only | No |
| Approve / Reject publication | No | No | Pending Review only |
| Request AI Recommendations | Yes | No | No |

Never add another role. Never infer the right to modify an Application from the ability to view a Published Internship. Navigation: **Student** — Dashboard, Profile, Catalogue, My Applications, AI Recommendations, Notifications (bell), Logout. **Company Representative** — Internship Management, Catalogue, Logout. **Moderator** — Internship Review, Catalogue, Logout (AC-10.5, D-G5-03).

### 5.1 Label mapping (SRS wording → Figma label)

| SRS | Figma | SRS | Figma |
|---|---|---|---|
| Подати заявку | Apply | Зберегти чернетку | Save Draft |
| Зберегти наявну чернетку | Save Existing Draft | Подати | Submit |
| Мої заявки | My Applications | Продовжити чернетку | Resume Draft |
| Відкликати заявку | Withdraw | Підтвердити (M03) | Confirm Withdraw |
| Скасувати | Cancel | Передати на модерацію | Send for Review |
| Редагувати | Edit | Закрити | Close Internship |
| Applications (S08 дія) | Candidate Pipeline | Створити | Create Internship |
| Переглянути деталі | View Details | Деталі та історія | Details & History |
| Назад до каталогу | Back to Catalogue | Назад до Dashboard | Back to Dashboard |
| Confirm Reject | Confirm Reject | Отримати рекомендації | Request Recommendations |

---

## 6. Allowed business-status transitions — complete reference

Business-status changes are distinct from navigation. **Only** the following are allowed; saving without a status change is not a transition.

### Application — seven statuses, nine allowed transitions [BR-02/06; SRS §8.3]

| From → To | Actor | Route / condition |
|---|---|---|
| Draft → Submitted | Student | Same own Draft ID, Published, before deadline; T-15 |
| Submitted → Withdrawn | Student | Own; confirm in M03; T-17/18 |
| Under Review → Withdrawn | Student | Own; confirm in M03; T-17/18 |
| Interview → Withdrawn | Student | Own; confirm in M03; T-17/18 |
| Submitted → Under Review | Company Representative | Own Company; T-30 |
| Under Review → Interview | Company Representative | Own Company; T-31 |
| Under Review → Rejected | Company Representative | Own Company; T-32 |
| Interview → Accepted | Company Representative | Own Company; T-33 |
| Interview → Rejected | Company Representative | Own Company; T-34 |

`Accepted`, `Rejected`, `Withdrawn` are terminal for their existing Application. A **new** Application after Withdrawn or Rejected is allowed only if the Internship is Published, before deadline, with no active application; after **Accepted** it is prohibited. Draft, Submitted, Under Review and Interview count as active. [BR-03; D-05]

### Internship — five statuses, five allowed transitions [SRS §8.4]

| From → To | Actor | Route / condition |
|---|---|---|
| Draft → Pending Review | Company Representative | Own, all fields valid; T-27 |
| Rejected → Pending Review | Company Representative | Own, corrections saved; T-25/26/27 |
| Pending Review → Published | Moderator | `Approve`; T-36 |
| Pending Review → Rejected | Moderator | `Reject` via M04; T-37 |
| Published → Closed | Company Representative | Own; `Close Internship`; T-28 |

`Closed` is terminal; it blocks new Applications and Submit of a saved Draft, while existing Submitted+ Applications continue their permitted processing (D-11, AC-07.9).

---

## 7. "Important" predicate — not applicable

Student Internship Manager has no `Issue`, `Priority`, `Assignee`, `Team Lead`, `Resolved` or `Important Issues`. The Mini Issue Tracker predicate and its four-by-four matrices must **not** appear in product frames or reviewer matrices. `REF-01 / ST-24–25` shows the **three** product roles and the full **seven-/five-status** matrices from §5–6.

---

## 8. Required empty, validation, denial and error examples

Render as compact labelled fixtures beside the relevant frame, not as extra screens. Messages are descriptive unless exact copy is quoted in §4. A denial illustration never proves server-side authorization or atomicity.

| Ref | Surface and fixture | Expected visible result |
|---|---|---|
| N-01 | Protected area, wrong role | No protected content or action; no T-ID |
| N-02 | S03, missing name or group | Field-specific errors; no Save outcome; ST-04 |
| N-03 | S04, zero matches | Empty result; query/filters stay; ST-06 |
| N-04 | S05, expired Published | «Дедлайн минув»; Apply disabled with reason; ST-08 |
| N-05 | S05, active Draft or Accepted | Apply disabled; Draft resumes via S06; Accepted blocks permanently |
| N-06 | S05, stale Closed detail | Apply disabled; Closed absent from catalogue |
| N-07 | M01, duplicate/stale | Reason distinguishes active duplicate from Accepted; no second ID |
| N-08 | S06, Draft or terminal | Withdraw unavailable; never Delete |
| N-09 | M01 resume after deadline/Closed | Same identity; Submit unavailable |
| N-10 | M02, incomplete Send / invalid Places | Field errors; status unchanged; ST-17 |
| N-11 | S08, edit Pending Review/Published/Closed | Edit disabled; resource unchanged |
| N-12 | S08, Rejected unchanged | Resend disabled until corrections saved |
| N-13 | S09, forbidden/stale transition | *Action unavailable*; same status; no T-ID; ST-21 |
| N-14 | S09, foreign Company or private Draft | Candidate data absent; denial note |
| N-15 | S10, no longer Pending Review | Approve/Reject unavailable; record unchanged |
| N-16 | S10, candidate action sought | No candidate/profile/status controls |
| N-17 | S07, AI unavailable | Error; catalogue still reachable; ST-14 |
| N-18 | S07, AI results | Read-only advice; no automatic Apply or status change |
| *ID pending* | S01, signup with existing email | Generic registration error; no account created |
| *ID pending* | S01, session ended | Prompt to sign in again; no protected content |
| *ID pending* | S02, Accepted update | Bell count and banner; status unchanged by the notification |
| *ID pending* | M04, comment at 500 characters | Counter at limit; longer input not accepted |
| *ID pending* | S09, Withdrawn row | Visible read-only; no actions |

Also show empty states: **S02/S06 no own applications**, **S04 no published internships**, **S08 no own Internship**, **S09 no candidate applications**, **S10 no Pending Review items**, **S07 no recommendations**. An absent optional field stays empty.

For `AC-05.3`/`05.4` show **four distinct examples** with different application references: (1) an active application blocks another; (2) Accepted blocks another permanently; (3) Withdrawn allows a *new* Application if Published and before deadline; (4) Rejected allows a *new* Application under the same conditions.

---

## 9. Navigation intent — annotations only

Annotate **outside** product frames. Keep the original T-ID where one exists; do not invent T-IDs.

| Flow | Route | Gate / consequence |
|---|---|---|
| Role entry | S01 → S02 / S08 / S10 (`T-01/02/03`) | Role decided after sign-in or sign-up |
| Student browse | S02 → S04 (`T-05`) → S05 (`T-10`) | Published only; expired browseable |
| Profile | S02 → S03 (`T-04`); Save `T-08` | Required errors N-02 |
| Search | S04 → S04 filtered (`T-09`) | Zero matches N-03 |
| New application | S05 → M01 new (`T-11`) → S06 Draft (`T-12`) or Submitted (`T-13`) | Nothing created on open/Cancel |
| Resume Draft | S06 → M01 resume (`T-14`) → S06 Submitted (`T-15`) | Same ID; Save Existing Draft is not T-12 |
| Cancel M01 | new → S05; resume → S06 (`T-16`) | No change |
| Withdraw | S06 → M03 (`T-17`) → S06 Withdrawn (`T-18`) or Cancel (`T-19`) | Three statuses only |
| AI | S02 → S07 (`T-07`); result (`T-20`); S05 (`T-21`); manual Apply (`T-11`); S04 (`T-22`) | No automatic Apply |
| Company opportunity | S08 → M02 (`T-23/25`); Save (`T-24/26`); Send (`T-27`); Close (`T-28`) | Corrected Rejected before resend |
| Company candidates | S08 → S09 (`T-29`); transitions `T-30–34`; back `T-40` | Ownership + 7 columns |
| Moderation | S10 queue → detail (`T-35`); Approve (`T-36`); Reject (`T-37`) | Pending Review only |
| Back to catalogue | S05 → S04 (`T-38`) | No new screen |
| Other-role catalogue | S08 / S10 → existing S04 | D-G5-03; no new T-ID |
| **S11 history** | S06 *Details & History* → S11 → S06; S02 Accepted banner → S11 | **ID pending** |
| **M04 reject** | S10 Reject → M04 → S10 (Confirm Reject or Cancel) | **ID pending**; replaces direct T-37 click-through |
| **Sign-in routing** | S01 → role start screen (see Role entry) | Covered by T-01/02/03 |
| **Logout** | any protected screen → S01 | **ID pending** |

Do **not** add `Return to AI` (D-G3-03 unapproved). Omit unapproved optional S03/S06 cross-navigation unless an approved ID covers it.

---

## 10. Synthetic sample data — visual fixtures only

| Fixture | Example data | Demonstrates |
|---|---|---|
| Student profile | `Olena Kovalenko`; `SE-23-4`; skills `C#, SQL`; interest `Backend development`; email/phone empty | S03 required vs optional |
| Company / internship | `Northstar Labs` / `Backend Internship`; stack `C#, SQL`; `Remote`; direction `Backend`; places `2`; duration `8 weeks`; mentor `Demo Mentor` | S04/S05/M02 |
| Published, in deadline | `Backend Internship`, deadline `2026-12-15` | Eligible Apply (ST-07) |
| Published, expired | `QA Internship`, deadline `2026-10-20` | «Дедлайн минув», disabled Apply |
| Closed | `Data Internship`, `Closed` | S08 list, S05 stale detail |
| Drafts / applications | `APP-DEMO-01` Draft; `APP-DEMO-02` Submitted; `APP-STATE-UNDER-REVIEW`, `APP-STATE-INTERVIEW`, `APP-STATE-ACCEPTED`, `APP-STATE-REJECTED`, `APP-STATE-WITHDRAWN` | Seven statuses (independent snapshots) |
| Screening | `Olena Kovalenko`, `APP-DEMO-02`, `Submitted`, `C#, SQL`, `Backend development`; plus `APP-WITHDRAWN-01` Withdrawn | S09 seven columns, Withdrawn read-only |
| History | `Submitted` · `2026-11-07 10:00 Europe/Kyiv` · `Student` | S11 |
| Notification | Accepted `APP-STATE-ACCEPTED`, bell count `1` | S02 banner |
| AI | prompt `I know C# and SQL and want backend work`; score `0.78` | S07 |
| Moderation | `Pending Review` opportunity; comment `Clarify the internship duties and requirements.` (47/500) | S10, M04, S08 |
| Signup | `student@university.edu`, `newuser@university.edu`, masked passwords | S01 |

Use compact chips or `REF-01` rows for the terminal and Internship statuses, not separate pages. Fixtures are **not executed tests**.

---

## 11. Exclusions — prohibited features

**Do not include:** the Mini Issue Tracker model; any fourth product role; an Administrator UI; **public Moderator signup**; SSO, password reset or email verification (not in the SRS); CV upload/parsing; PDF referrals; document generation; chat/video; ERP, dean's-office or HR integrations; analytics or reporting; native mobile apps; autonomous AI selection or Apply; a **notification centre, email or push alerts** (only the bell and the Accepted banner are allowed); any status history other than the read-only S11 table; physical Application Delete; bulk or row-selection functions; additional business statuses; any invented persistence, authentication, backend or security implementation.

HTTPS, server authorization, atomic changes, backup/restore, audit-trail storage, performance and real AI availability remain **implementation-level** obligations; they are not product screens and are **not** verified by these wireframes. [NFR-01–08]

---

## 12. Acceptance checklist and coverage index

Planned inspection checklist, **not test evidence**. Every result is `NOT RUN` until a reviewer checks the artifact.

| Check | Expected inspection evidence | Source |
|---|---|---|
| `F-01` | Single page; native editable layers; named frames/components; Auto Layout; grayscale low-fi; one icon only (bell) | §2 |
| `F-02` | Exact `S01–S11`, `M01–M04`; `REF-01` outside product frames; `ST-01–25` as compact references | §3 |
| `F-03` | S01 Login and Signup, role choice Student/Company only, generic error, existing-email and session-ended states | AC-10.1–10.5 |
| `F-04` | S03 required errors, optional contacts, privacy hint, saved confirmation | AC-01.1–01.6 |
| `F-05` | S04 complete cards, search, four filters, reset, zero-match, no-published and expired examples; view mode for other roles | AC-02.1–03.6 |
| `F-06` | S05 and three distinct Apply blocks (+ already-accepted wording) | AC-04.1–04.5 |
| `F-07` | M01 new vs resume, same ID, no duplicate, no Submit after deadline/Closed, four reapply examples | AC-05.1–05.8 |
| `F-08` | S06 seven statuses, eligible Withdraw, terminal explanations, Details & History | AC-06.1–06.7 |
| `F-09` | S11 read-only history with initiator role; S02 summary, bell and Accepted banner | AC-06.8/06.9, AC-08.8 |
| `F-10` | M02 full field list, Company ID read-only, partial Draft, invalid Send, corrected Rejected resend | AC-07.1–07.3/07.7/07.8 |
| `F-11` | S10 queue → Approve/Reject; M04 comment ≤ 500; S08 shows comment; no Approved status | AC-07.4/07.5/07.11–07.14 |
| `F-12` | S09 seven columns, Withdrawn read-only, Draft hidden, five transitions | AC-08.1–08.7 |
| `F-13` | S07 prompt, links, indicative score, exact disclaimer, four states, S02 widget | AC-09.1–09.10 |
| `F-14` | Hidden vs disabled policy applied; moderator has no application controls | D-G5-02; BR-06 |
| `F-15` | Catalogue reachable from Company and Moderator navigation without new screens | D-G5-03 |
| `F-16` | `REF-01` shows three roles, 7/5 status sets, allowed arrows only, denial examples | §8.2–8.4 |
| `F-17` | All 79 AC traceable through frames and annotations; no prohibited functions | §12 index |
| `F-18` | No claim of server RBAC, real authentication, AI inference, persistence, test PASS or teacher approval | NFR-01–08 |

### AC-to-frame coverage index (79 criteria; planned only)

| AC | Figma evidence | AC | Figma evidence |
|---|---|---|---|
| 01.1 | S03 fields | 01.2 | S03 ST-04 / N-02 |
| 01.3 | S03 / REF-01 | 01.4 | S03 optional fields + privacy hint |
| 01.5 | S03 / REF-01 ST-24 | 01.6 | S03 saved confirmation, Back to Dashboard |
| 02.1 | S04 ST-05 | 02.2 | S04 published card |
| 02.3 | S04 ST-05 / REF-01 | 02.4 | S04 expired card |
| 02.5 | S04 absent-data card | 02.6 | S04 D-G5-03 note / REF-01 |
| 02.7 | S04 no-published state | 03.1 | S04 search |
| 03.2 | S04 filters | 03.3 | S04 ST-06 / N-03 |
| 03.4 | S04 four filters | 03.5 | S04 expired kept in results |
| 03.6 | S04 reset | 04.1 | S05 |
| 04.2 | S05 ST-07 | 04.3 | S05 ST-08 / N-04–06 |
| 04.4 | S05 N-06 | 04.5 | S05 T-38; role note |
| 05.1 | M01 ST-09 | 05.2 | M01 identity notes |
| 05.3 | M01 / S05 N-05, N-07 | 05.4 | M01 reapply examples (3)–(4) |
| 05.5 | M01 ST-10 | 05.6 | M01 N-09 |
| 05.7 | M01 T-16 | 05.8 | M01 → S06 |
| 06.1 | S06 ST-11 | 06.2 | S06 / N-08 |
| 06.3 | M03 | 06.4 | S06 terminal notes |
| 06.5 | S06 Draft note | 06.6 | S06 empty state |
| 06.7 | S06 / REF-01 | 06.8 | S11 |
| 06.9 | S02 summary | 07.1 | M02 |
| 07.2 | S08 / M02 N-11 | 07.3 | M02 ST-17 / T-27 |
| 07.4 | S10 T-36 | 07.5 | S10 → M04 / T-37 |
| 07.6 | S08 ST-19 / T-28 | 07.7 | M02 ST-17 / N-10 |
| 07.8 | S08 N-12 | 07.9 | S08 ST-19 |
| 07.10 | S08 ST-15 | 07.11 | S10 ST-22 |
| 07.12 | S10 N-15 | 07.13 | M04; S08 Rejected row |
| 07.14 | S10 / N-16 | 07.15 | M02 Cancel |
| 08.1 | S09 ST-20 | 08.2 | S09 T-30–34 |
| 08.3 | S09 N-13 / ST-21 | 08.4 | S09 N-14 |
| 08.5 | S09 navigation note | 08.6 | S09 empty state |
| 08.7 | S08 → S09 T-29 / T-40 | 08.8 | S02 bell + banner; S11 |
| 09.1 | S07 prompt | 09.2 | S07 fields, links, score |
| 09.3 | S07 disclaimer | 09.4 | S07 → S05 → M01; N-18 |
| 09.5 | S07 data note | 09.6 | S07 ST-14 / N-17 |
| 09.7 | S07 empty state | 09.8 | S07 AI mark |
| 09.9 | S07 → S05; **S02 AI widget** | 09.10 | S07 / REF-01 ST-24 |
| 10.1 | S01 Login and Signup | 10.2 | S01 note (no Moderator signup, no admin UI) |
| 10.3 | S01 post-login intent T-01–03 | 10.4 | S01 error; N-01 |
| 10.5 | Role navigation + Logout in headers | | |

Classification: **79/79 planned, 0 verified.**

---

## 13. Known gaps and open items

**Known Figma gaps** at the time of this brief (text-level review of the current file; each must be closed or consciously waived before G6):

| # | Where | Gap | Source |
|---|---|---|---|
| G-1 | S02 | AI card is a link with no prompt field and no AI mark | AC-09.9 |
| G-2 | S01 reference | No *email already exists* or *session ended* state | S01 states, AC-10.4 |
| G-3 | S03 | No privacy hint about email/phone; no saved confirmation | AC-01.4, AC-01.6 |
| G-4 | S04 | No reset action; no *no published internships* state | AC-03.6, AC-02.7 |
| G-5 | M01 / S05 | Reapply examples (3) Withdrawn and (4) Rejected not found | AC-05.4; DEF-03 |
| G-6 | REF-01 | States that full 79-AC definitions were not available; replace with the §12 index | F-17 |

**Open items that the SRS does not resolve (do not decide in Figma):**

- **OQ-01 — Company binding at signup.** AC-10.1 collects only Email, Password and Role, yet AC-07.1 requires a Company ID "from the company context" and §2.2 says no company administration exists in the MVP. The SRS must define how a self-registered Company Representative obtains a Company. Until then Figma shows no company field.
- **OQ-02 — Frame name.** Figma and this brief use *Company Candidate Pipeline* for S09; SRS §9 uses *Company Applications*. Align one of them.
- **OQ-03 — Decision Log.** DL-P-01–DL-P-05 need Decision Log entries (they supersede parts of D-07, D-09, Q-14, Q-16 and D-G5-01).
- **OQ-04 — Screen Map and Contracts.** `02_Screen_Map` and `03_Screen_Contracts` still describe the v0.2 baseline (no S11, M04, signup, S02 widget, bell). They need new T-/C-/N-IDs before the G4 coverage review can be repeated.
- **OQ-05 — Still open from the Decision Log:** Q-18 (validation and error copy), Q-20 (performance workload), Q-21 (WCAG level, breakpoints).

**Acceptance status at authoring:** `NOT RUN` for every check. This brief is **ready to use as Figma instructions**; the generated frames still require **G4/G6 human review**, and no verification or external approval is claimed.
