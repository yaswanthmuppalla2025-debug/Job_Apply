# Tracker Schema

Use this file as the source of truth for both `AI_ROLES/AI_job_tracker.xlsx` and `SDE_ROLES/SDE_job_tracker.xlsx`.

Both trackers must use the same columns, in the same order. `Lane` distinguishes AI from SDE. Existing rows may have blank operational fields; future agents should fill what is derivable without slowing the submission goal.

All active trackers, including the LinkedIn AI sub-tracker, must stay visually consistent: same columns, same simplified status labels, same colors, same filters, and newest rows at the top below the header.

## Core Principle

The tracker helps Codex move faster, not create new blockers.

- Fill fields when the information is visible, derivable from the official page, or learned during the application.
- Leave optional operational fields blank or `Unknown` when they are not derivable quickly.
- Do not stop a valid application just because `Fit Score`, `ATS Type`, `Recovery Tried`, or another helper field is blank.
- For `Blocked - ATS` and `Blocked - Other`, recovery fields are mandatory. A non-CAPTCHA technical blocker must prove at least 2 serious attempts and at least 2 distinct recovery paths unless a hard boundary appeared immediately.
- For high-fit roles, agents should use up to 3 serious attempts when safe paths remain, especially account/login, upload fallback, direct ATS routing, hidden required fields, and Chrome recovery.
- Do not apply when a hard gate fails: posting is older than 15 days, recency cannot be proven within 15 days, role is closed, sponsorship is incompatible, role is already applied, employer/source quality is too low, or a hard security/legal/manual blocker appears.
- Before filling a form, scan the existing `Role` columns in the active trackers. If the same company has the same normalized role title already submitted/attempted, or the same official job id/application URL is already present, record `Already Applied` or `Skipped` and move on. A common role title at a different company is not a duplicate by itself.
- Do not create visible `.backup` tracker files in `AI_ROLES/`, `SDE_ROLES/`, or the workspace root during routine runs. Backup clutter makes future agents and humans read the wrong files.
- Never store passwords, private identity values, email codes, full SSN, passport, bank/payment details, or private email content in tracker cells.
- New rows go at the top of the data area, directly under the header. Do not append new outcomes at the bottom.

## Canonical Columns

| Column | Fill Rule |
|---|---|
| Date Applied | Date the row outcome was recorded. |
| Lane | `AI` or `SDE`. |
| Job ID | Internal queue/job id when available. Optional. |
| Company | Company name. |
| Role | Role title. |
| Location | Job location/remote eligibility when visible. Do not put Yaswanth's current city or form-answer location here unless it is also the job location. Optional if not derivable quickly. |
| Status | Use only the simplified approved statuses below. Put proof and exact reasons in `Confirmation Proof` and `Notes`, not in many status variants. |
| Posted Date | Official posting/repost date when available. |
| Posting Age Days | Days from posted date to check/application date. Optional; fill when easy. |
| Recency Bucket | `0-7 days`, `8-15 days`, `Over 15 days`, or `Unknown`. |
| Recency Proof URL | Official/dated source proving the posting date. |
| Application URL | Official company/ATS application URL. |
| Source | Discovery or ATS source, such as `Greenhouse:reddit`, LinkedIn, Indeed, company site. |
| ATS Type | Greenhouse, Ashby, Lever, Workday, Workable, Oracle/Taleo, Indeed, Phenom, etc. Optional if not obvious. |
| Fit Score | Optional quick score such as `High`, `Medium`, `Low`, or `1-5`. |
| Fit Reason | One concise phrase explaining why the role fits or does not fit. Optional. |
| Sponsorship Checked | `Yes`, `No`, `Unknown`, or `N/A`. Use `Yes` only after checking JD/form language. |
| Open Checked At | Date/time official open status was checked. |
| Attempt Count | Number of meaningful attempts on the same role. Use mainly for blockers/retries. |
| Recovery Tried | Concrete recovery actions tried, not vague text. |
| Next Retry Path | Exact next action if retry is worthwhile and still within the 15-day gate. |
| Retry Eligible | `Yes`, `No`, `Expired`, or `Manual Review`. |
| Learning Candidate | `Yes` only for reusable ATS/company learning. |
| Gmail Checked At | Date/time Gmail was checked for code or confirmation. |
| Confirmation Proof | Gmail receipt, success page, application ID, or portal proof. |
| Notes | Concise old proof/blocker text and details. Do not store private values. |

## Approved Statuses

- `Submitted`
- `Blocked - CAPTCHA`
- `Blocked - ATS`
- `Blocked - Other`
- `Skipped`
- `Already Applied`

Keep the status column simple. Use `Confirmation Proof`, `Gmail Checked At`, and `Notes` to distinguish email proof, screen proof, no confirmation yet, upload failure, account/login wall, manual/legal blocker, no sponsorship, stale role, staffing/vendor skip, or fit mismatch.

## Minimum Row Standard

For a clean submitted row, fill at least:

- `Date Applied`
- `Lane`
- `Company`
- `Role`
- `Status`
- `Application URL`
- `Confirmation Proof` or concise proof in `Notes`

For a skipped stale/no-sponsorship/fit/staffing/vendor/strategic row, fill at least:

- `Date Applied`
- `Lane`
- `Company`
- `Role`
- `Status`
- `Application URL` or discovery URL
- `Notes` with the skip reason

For a skipped duplicate, staffing/vendor/aggregator-proxy, or low-quality strategic row, fill at least:

- `Date Applied`
- `Lane`
- `Company`
- `Role`
- `Status` as `Already Applied` or `Skipped`
- `Application URL` or discovery URL when available
- `Notes` with the short reason, such as `duplicate same company+role`, `staffing/vendor`, or `aggregator proxy; no official company apply`

For a real blocker after recovery fails, fill at least:

- `Date Applied`
- `Lane`
- `Company`
- `Role`
- `Status`
- `Application URL`
- `Attempt Count`, normally `2` or higher for non-CAPTCHA technical blockers
- `Recovery Tried`, with at least 2 distinct paths for non-CAPTCHA technical blockers
- `Next Retry Path`, or a clear reason no truthful AI-safe retry remains
- `Retry Eligible`
- `Notes` with exact blocker evidence

Do not allow vague blocker rows such as `site broken`, `login issue`, `upload failed`, or `validation loop` without the concrete attempt trail. The next agent should know exactly whether to retry account reset, direct ATS URL, manual resume text, Gmail code, hidden-widget sweep, or Chrome reconnect.

## 15-Day Gate

Autopilot applies only to verified `0-15 day` roles.

- `0-7 days`: highest priority.
- `8-15 days`: apply only for strong resume/JD matches.
- `Over 15 days`: skip.
- `Unknown`: skip unless a reliable dated source proves the posting is within 15 days and the official application page is open.

If no close matches exist inside the 15-day gate, report the shortage instead of applying stale roles to chase volume.
