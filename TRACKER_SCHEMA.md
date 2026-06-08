# Tracker Schema

Use `JOB_APPLICATION_TRACKER.xlsx` as the single source of truth for application tracking.

The workbook has exactly four active sheets:

- `Summary`
- `AI`
- `SDE`
- `Blockers`

The tracker helps Codex move faster, not create new blockers. Keep `AI` and `SDE` lean for readable submission history. Put recovery detail in `Blockers` only when it helps future retries or Yaswanth review.

## Core Principle

- New rows go at the top under the header.
- Update the tracker after every submitted, already-applied, or blocked outcome.
- Do not log broad skip-noise in the workbook. Stale, no-sponsorship, closed, low-quality staffing/vendor, poor-fit, and over-15-day roles are still skipped, but they are not daily-readable rows unless they become `Already Applied` or a real blocker/manual-review item.
- Before filling a form, duplicate-check the `Company`, `Role`, and `Application URL` columns across `AI`, `SDE`, and `Blockers`.
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
| Application URL | Official company/ATS/LinkedIn application URL. |
| Source | Discovery or apply source, such as `Greenhouse`, `LinkedIn Easy Apply`, or `LinkedIn -> Workday`. |
| ATS | Greenhouse, Ashby, Lever, Workday, Workable, Oracle/Taleo, LinkedIn Easy Apply, etc. |
| Fit | Required for new `Submitted` rows: `High`, `Strong`, or `Strategic Exception: <why>`. Do not submit blank, low, unknown, or merely adjacent fits. |
| Sponsorship | `Yes`, `No`, `Unknown`, or `N/A`; use `Yes` only after checking JD/form language. |
| Confirmation Proof | Gmail receipt, success page, application ID, or clear portal proof. |
| Notes | Concise non-private proof or duplicate detail. |

Allowed statuses:

- `Submitted`
- `Already Applied`

Do not use proof-flavored submitted status variants. Keep status simple and put proof in `Confirmation Proof` or `Notes`.

## Blockers Sheet

Use `Blockers` for CAPTCHA, ATS, upload, account/login, anti-spam, manual/legal, missing-info, Chrome/profile, and other real recovery items.

Columns:

| Column | Fill Rule |
|---|---|
| Date | Date the blocker was recorded. |
| Lane | `AI` or `SDE`. |
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
| Parked Tab | `Yes` only when a useful CAPTCHA/anti-abuse tab is intentionally left open for Yaswanth. |
| Learning | `Yes` only for reusable ATS/company learning. |
| Notes | Exact non-private blocker evidence. |

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

Do not bypass CAPTCHA, hCaptcha, visual puzzles, anti-abuse pages, or visual security puzzles. Job-Gmail email/security codes are recoverable ATS verification steps, not CAPTCHA.

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

Keep at most 5 parked CAPTCHA tabs open. If 5 are already parked, record the next CAPTCHA as `Blocked - CAPTCHA` with `Parked Tab` blank and move on.

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

Autopilot applies to verified `0-15 day` roles by default. AI roles may use Yaswanth's exceptional live-post exception up to `50 days` only when the role is an excellent/strong match, official page is still accepting applications, location is in-bounds, and sponsorship answers are compatible.

- `0-7 days`: highest priority.
- `8-15 days`: apply only for strong resume/JD matches.
- `16-50 days`: AI roles only, exceptional strong-fit live-post exception.
- `Over 50 days`: skip.
- `Unknown`: skip unless a reliable dated source proves the role is within 15 days and the official application page is open.

If no high/strong matches exist inside the recency gate, scrape deeper through official/company/ATS sources instead of applying stale, medium-adjacent, or weak roles to chase volume.
