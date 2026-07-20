# Tracker Schema

Use `JOB_APPLICATION_TRACKER.xlsx` as the single source of truth for application tracking.

The workbook has exactly four active sheets:

- `Summary`
- `AI`
- `SDE`
- `Blockers`

The tracker helps Codex move faster, not create new blockers. Keep `AI` and `SDE` lean for readable submission history. Put recovery detail in `Blockers` only when it helps future retries or Yaswanth review.

## Core Principle

- Before any duplicate check or write, run a tracker-integrity gate: verify that `AI`, `SDE`, and `Blockers` have the expected headers, plausible status totals, and no implausible concentration of one canonical `Company` + `Role` + `Application URL` row. If the workbook fails this gate, pause all tracker-based screening and writes; restore a validated snapshot and reconcile only proof-backed later records before resuming.
- Treat historical rows as read-only history when they contain legacy blank `Fit` values, optional metadata gaps, or the retired blocker status `Resolved`. Do not bulk-normalize, delete, or backfill them by inference. New rows and rows edited for another valid reason must follow the current schema; targeted repairs require direct confirmation, portal, official-role, or browser-history evidence.
- New rows go at the top under the header.
- Update the tracker after every submitted, already-applied, or blocked outcome.
- Do not log broad skip-noise in the workbook. Stale, no-sponsorship, closed, low-quality staffing/vendor, poor-fit, and roles outside the allowed recency policy are still skipped, but they are not daily-readable rows unless they become `Already Applied` or a real blocker/manual-review item.
- Before filling and again immediately before final submit, duplicate-check the official job ID when available plus `Company`, `Role`, and `Application URL` across `AI`, `SDE`, and `Blockers`. An exact job ID/canonical URL already `Submitted`/`Already Applied`, or portal-proven prior submission, is a hard duplicate. An exact `Blockers` match routes to that existing row rather than a new attempt; a retry may match its own row. Same-company/title rows with different or unknown IDs require a quick team/location/JD comparison.
- After 3 applications/attempts at one company within 30 days, apply the soft company-spread rule in `RECENCY_PREFLIGHT.md`; this is not a new status or blocker row unless an explicit company cap or user cooldown exists.
- Leave optional metadata blank when it is not derivable quickly. Blank helper fields are not blockers, but `Fit` is not a helper field for new `Submitted` rows.
- Do not create separate report, queue, cache, CSV, or JSONL files for routine runs. `JOB_APPLICATION_TRACKER.xlsx` is the durable state.
- Never store passwords, email codes, full SSN, DOB values, private identity values, passport, bank/payment details, or private email content in tracker cells.

## AI And SDE Sheets

Use `AI` for AI-first roles and LinkedIn-sourced AI roles. Use `SDE` for backend/SDE roles.

Columns:

| Column | Fill Rule |
|---|---|
| Date | Date the outcome was recorded. |
| Company | Company name. |
| Role | Role title. |
| Location | Job location or remote eligibility when visible. |
| Status | `Submitted` or `Already Applied` only. |
| Posted Date | Official posting/repost date when available. |
| Age Days | Days from posted date to check/application date when easy. |
| Recency Proof | Official or reliable dated proof URL. |
| Application URL | Official company/ATS/LinkedIn role URL. Prefer the stable requisition URL over tracking, apply-step, confirmation, or thank-you variants. |
| Source | Discovery or apply source, such as `Greenhouse`, `LinkedIn Easy Apply`, or `LinkedIn -> Workday`. |
| ATS | Greenhouse, Ashby, Lever, Workday, Workable, Oracle/Taleo, LinkedIn Easy Apply, etc. |
| Fit | Required for new `Submitted` rows: `High - JD intent: <backend-to-AI/platform reason>`, `Strong - JD intent: <reason>`, `Strategic Exception: <3-requirement evidence>`, or `High - Exceptional 16-120 day AI match: <reason>`. Keep it short; do not submit blank, low, unknown, keyword-only, or merely adjacent fits. A 16-120 day role cannot use `Strategic Exception`. |
| Sponsorship | `Yes`, `No`, `Unknown`, or `N/A`; use `Yes` only after checking JD/form language. |
| Confirmation Proof | Gmail receipt, success page, application ID, or clear portal proof. |
| Notes | Concise non-private proof or duplicate detail. |

Allowed statuses:

- `Submitted`
- `Already Applied`

Do not use proof-flavored submitted status variants. Keep status simple and put proof in `Confirmation Proof` or `Notes`.

## Blockers Sheet

Use `Blockers` for CAPTCHA, ATS, upload, account/login, anti-spam, manual/legal, missing-info, Chrome/profile, company-level hard blocks, and other real recovery items. Do not use blockers for ordinary email/security-code verification, account creation/reset, upload friction, or reasonable short assessments until the recovery budget is exhausted.

Columns:

| Column | Fill Rule |
|---|---|
| Date | Date the blocker was recorded. |
| Lane | `AI`, `SDE`, or `All` for company-level blocks that apply across lanes. |
| Company | Company name. |
| Role | Role title. |
| Location | Job location or remote eligibility when visible. |
| Status | One of the approved blocker statuses below. |
| Blocker Type | Short exact type, such as `CAPTCHA Parked`, `Upload`, `Account/Login`, `Anti-spam`, `Manual/Legal`, or `Chrome/Profile`. |
| Posted Date | Official posting/repost date when available. |
| Age Days | Days from posted date to check/application date when easy. |
| Application URL | Official company/ATS/LinkedIn application URL. |
| Source | Discovery or apply source. |
| ATS | ATS/platform name when known. |
| Fit | Short fit signal. |
| Attempt Count | Meaningful attempts on the same role. |
| Recovery Tried | Concrete recovery actions tried, not vague text. |
| Next Action | Exact next action if retry or human review is worthwhile. |
| Retry Eligible | `Yes`, `No`, `Expired`, or `Manual Review`. |
| Parked Tab | `Yes` only when a useful CAPTCHA/anti-abuse tab is intentionally open for Yaswanth; otherwise `No` or blank. |
| Learning | `Yes` only for reusable ATS/company learning. |
| Notes | Exact non-private blocker evidence. |

Company-level blocker rows are allowed when a company should be skipped across all roles for a time-bound reason. Example: `Lane = All`, `Company = Capital One`, `Role = All Capital One roles`, `Blocker Type = Company Sponsorship Cooldown`, `Retry Eligible = No`, and `Next Action = Do not apply until 2027-01-07`.

Allowed blocker statuses:

- `Blocked - CAPTCHA`
- `Blocked - ATS`
- `Blocked - Other`

Allowed `Retry Eligible` values:

- `Yes`
- `No`
- `Expired`
- `Manual Review`

## CAPTCHA Parking

Do not bypass CAPTCHA, hCaptcha, visual puzzles, anti-abuse pages, or visual security puzzles. Job-Gmail email/security codes are recoverable ATS verification steps, not CAPTCHA. Reasonable manual assessments are also recoverable when they can be answered truthfully from the resume, answer bank, JD, and careful role-specific judgment.

For a high-fit role that already passed recency, sponsorship, quality, location, and duplicate gates:

- Fill every truthful field possible.
- Stop at the visual CAPTCHA/hCaptcha/reCAPTCHA/anti-abuse challenge.
- Leave the tab open for Yaswanth.
- Add a `Blockers` row:
  - `Status`: `Blocked - CAPTCHA`
  - `Blocker Type`: `CAPTCHA Parked`
  - `Retry Eligible`: `Manual Review`
  - `Parked Tab`: `Yes`
  - `Next Action`: `Yaswanth solve CAPTCHA, then submit/resume from same tab`
  - `Notes`: `Form filled; CAPTCHA parked for human review`
- Continue applying in another tab.

Keep at most 5 parked CAPTCHA tabs open. Each `Parked Tab = Yes` row must match a currently open tab for that exact role. Reconcile these rows with live tabs at run start and end; when the tab no longer exists, set `Parked Tab` to `No` while retaining the blocker row. If 5 are already parked, record the next CAPTCHA as `Blocked - CAPTCHA` with `Parked Tab` blank and move on.

Never park low-quality, stale, no-sponsorship, duplicate, staffing/vendor, or poor-fit roles.

## Minimum Row Standard

For a submitted row, fill at least:

- `Date`
- `Company`
- `Role`
- `Status`
- `Application URL`
- `Confirmation Proof` or concise proof in `Notes`

For an already-applied row, fill at least:

- `Date`
- `Company`
- `Role`
- `Status`
- `Application URL` when available
- `Notes` with duplicate/prior-submission proof

For a blocker row, fill at least:

- `Date`
- `Lane`
- `Company`
- `Role`
- `Status`
- `Blocker Type`
- `Application URL`
- `Retry Eligible`
- `Notes`

For `Blocked - ATS` and non-CAPTCHA `Blocked - Other`, also fill:

- `Attempt Count`
- `Recovery Tried`
- `Next Action`

A non-CAPTCHA technical blocker must show at least 2 serious attempts and 2 distinct recovery paths unless a true hard boundary appeared immediately.

## Recency Gate

Autopilot applies to verified `0-15 day` roles by default. AI roles may use Yaswanth's exceptional live-post exception through `120 days` only when the official page is accepting applications, location and sponsorship are compatible, at least 3 primary JD responsibilities are resume-backed including a core backend-to-AI/API/platform responsibility, and there is no hard must-have mismatch.

- `0-7 days`: highest priority.
- `8-15 days`: apply only for strong resume/JD matches.
- `16-120 days`: AI roles only, strongest-fit live-post exception; record the exceptional evidence in `Fit`.
- `Over 120 days`: skip.
- `Unknown`: skip unless a reliable dated source proves the role is within 15 days and the official application page is open.

If no high/strong matches exist inside the recency gate, scrape deeper through official/company/ATS sources instead of applying stale, medium-adjacent, or weak roles to chase volume.
