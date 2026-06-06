# Start Here Autopilot

Read this first for any AI or SDE application batch.

## Command Center

1. Use the `Job Apply - Yaswanth` Chrome profile.
2. Run in `Aggressive Autopilot / Hard Stop Only` mode.
3. Enforce the recency gate before filling: prioritize roles posted 0-7 days ago, use 8-15 day roles only for strong resume matches, and use the <=50 day exception only for exceptional AI matches that are officially live, in-bounds, and sponsorship-compatible.
4. Apply strong-fit-first: submit only high/strong AI or SDE/backend matches; treat medium/adjacent roles as skips unless they are a documented strategic exception.
5. Before filling any form, do the simple duplicate check in `JOB_APPLICATION_TRACKER.xlsx`: scan `Company`, `Role`, and `Application URL` across `AI`, `SDE`, and `Blockers`. If the same company has the same normalized role title already submitted/attempted, or the same official URL/job id is already present, skip as duplicate/already applied. A common role title at a different company is only a warning, not a blocker.
6. Location priority: Georgia/Atlanta, Dallas/Austin/Texas, Virginia, Texas, North Carolina, Tennessee, Florida, Remote US, then SF/Bay Area/California only as a last option for unusually strong AI/platform/company fit.
7. Strictly skip no-sponsorship, no-H-1B-transfer, citizen/GC-only, U.S.-person-only, clearance-only, stale, closed, over-50-day, unknown-recency without proof, duplicate, staffing/vendor/aggregator-proxy, and obvious poor-fit roles. Roles older than 15 days still need the exceptional AI-fit live-post exception.
8. Use `RECENCY_PREFLIGHT.md` for fast posting-age checks and `TRACKER_SCHEMA.md` for tracker updates.
9. Use the AI resume for AI roles and the SDE resume for SDE/backend roles. Record outcomes in `JOB_APPLICATION_TRACKER.xlsx`.
10. Fill from `APPLICATION_PLAN.md`, `ANSWER_BANK.md`, the resume, JD, company context, and best truthful judgment.
11. Submit high/strong-fit applications without per-role approval.
12. Recover normal friction before blocking: required-widget sweep, direct ATS URL, embedded form, PDF -> DOCX -> text fallback, account creation, Gmail code, reload/refill, Chrome reconnect.
13. No first-attempt technical blockers: except CAPTCHA/security/legal/manual/hard-eligibility boundaries, a blocked role requires at least 2 serious attempts and at least 2 distinct recovery paths.
14. Account/login walls are recoverable: create account, try existing login, use password reset through the job Gmail when available, retrieve Gmail codes, then return to the exact job URL before blocking.
15. Confirm from screen, application ID, portal state, or Gmail; update `JOB_APPLICATION_TRACKER.xlsx` after every outcome.
16. Put submissions/already-applied rows in `AI` or `SDE`; put CAPTCHA, ATS, upload, account/login, anti-spam, manual/legal, missing-info, and Chrome/profile blockers in `Blockers`.
17. Close/finalize stale tabs and continue to the next role.

## Current Retry Priority

Only retry these if the role still passes the 0-15 day recency gate and `Retry Eligible` is not `Expired`.

1. Any high-fit `Blocked - ATS` or `Blocked - Other` row with blank/`1` attempt count and a live posting inside the 15-day gate. Retry it before chasing weak new roles.
2. Lowe's Workday identity-field blocker using `PRIVATE_APPLICATION_FIELDS.md`.
3. Cargill and JPMorgan account/code flows.
4. Databricks direct Greenhouse/embed retries with country/phone hidden-value sweep.
5. Upload blockers: Accompany Health, Chipply, Harvey AI Platform, Citi, Reddit SDE Ads, Scribd, Vogo. Do not retry staffing/vendor upload rows unless Yaswanth explicitly asks.
6. Greenhouse validation loops: Instacart, Reddit ML, Scale AI.
7. CAPTCHA rows only after Gmail proof check and source-mixing slowdown.
8. Perplexity exercise and legal/user-authored attestation rows only if the real artifact/review exists.

## Pre-Submit Checklist

Before final submit, verify:

- Role is official, open, verified 0-15 days old by default or <=50 days old under the exceptional AI-fit live-post exception, fit-aligned, and sponsorship-compatible.
- Fit is `High`/`Strong` for the selected lane. `Medium` is allowed only as `Strategic Exception` when the role has target geography/company quality and at least 2-3 resume-backed core requirements.
- Posting date is verified from an official company/ATS source or reliable dated search result before spending time on the form: 0-7 days preferred, 8-15 days strong fit only, 16-50 days only for exceptional AI matches with official live proof, >50 days skipped.
- Employer is a direct product/platform/enterprise employer or a clearly high-quality direct company role; skip obvious staffing, consulting, vendor, recruiter, W2-only, client-confidential, or aggregator-proxy postings.
- Location matches the priority order: Georgia/Atlanta, Dallas/Austin/Texas, Virginia, Texas, North Carolina, Tennessee, Florida, Remote US, then SF/Bay Area/California only for elite fit.
- `JOB_APPLICATION_TRACKER.xlsx` has been scanned for a simple duplicate check before filling.
- Correct lane resume is uploaded, parsed, or pasted through the lane `.txt` fallback.
- Official ATS identity fields such as last-4 SSN, DOB, or month/day DOB are filled from `PRIVATE_APPLICATION_FIELDS.md` when required.
- Phone includes United States / `+1` when a country selector exists.
- Location typeahead has an actual selected option.
- Work authorization is truthful: authorized Yes, sponsorship/H-1B transfer Yes.
- Required EEO/self-ID fields use exact visible option text.
- Required radios, checkboxes, custom pills, acknowledgements, and hidden selectors are active.
- Any required custom answer is tailored from `ANSWER_BANK.md`, resume, JD, and company context.
- Submit button is the real locator/control, not only a coordinate click.

## Two-Hour Learning Checkpoint

Every 2-3 hours of applying, or every 50 submitted applications, add 5-6 high-value sentences to `LEARNING_LOOP.md` only if the run produced new reusable observations.

Good learning:

- Specific ATS behavior plus the successful recovery.
- Company-specific field mapping that prevented validation errors.
- Upload, account, code, or confirmation pattern that recurs.
- CAPTCHA/anti-abuse pattern that changes source-mixing strategy.
- Tracker classification lesson that avoids false submitted or false blocked rows.

Bad learning:

- Generic narration.
- Motivation or status updates.
- One-off frustration.
- Credentials, passwords, codes, or private email content.
- Policies already written in `APPLICATION_PLAN.md`, `AUTONOMOUS_RUNBOOK.md`, or `AUTOPILOT_BLOCKER_PLAYBOOK.md`.

Private-field rule: never copy values from `PRIVATE_APPLICATION_FIELDS.md` into trackers, blocker reasons, learning-loop entries, screenshots, or result JSON.

## Tracker Rules

`JOB_APPLICATION_TRACKER.xlsx` is the only active tracker. Use the lean `AI` and `SDE` sheets for `Submitted` and `Already Applied` rows. Use `Blockers` for CAPTCHA, ATS, upload, account/login, anti-spam, manual/legal, missing-info, Chrome/profile, and other real recovery items.

Use these fields only when they add signal:

- `Attempt Count`: increment for retries on the same role.
- `Recovery Tried`: concise list such as `reload/refill; direct Greenhouse; Gmail code; text resume`.
- `Next Action`: the next concrete action if the role is worth retrying.
- `Learning`: `Yes` only when the row reveals a reusable ATS/company pattern for `LEARNING_LOOP.md`.

For `Blocked - ATS` and non-CAPTCHA `Blocked - Other`, these fields are not optional. A non-CAPTCHA technical blocker must show the serious attempts, distinct recovery paths, and the next action or a clear reason no truthful AI-safe retry remains.

Do not log broad skip-noise. Stale, no-sponsorship, duplicate, staffing/vendor/aggregator-proxy, outside-location, or fit-mismatch roles are skipped and the run continues; only record `Already Applied` when duplicate proof is useful.

## CAPTCHA Parking

For high-fit roles that already pass freshness, sponsorship, quality, location, and duplicate gates, CAPTCHA should not discard the opportunity. Fill every truthful field possible, leave the CAPTCHA/security tab open for Yaswanth, record the row in `Blockers` as `Blocked - CAPTCHA` with `Blocker Type = CAPTCHA Parked`, `Retry Eligible = Manual Review`, `Parked Tab = Yes`, and continue applying in another tab.

Keep at most 5 parked CAPTCHA tabs open. Never park low-quality, stale, no-sponsorship, duplicate, staffing/vendor, or poor-fit roles.
