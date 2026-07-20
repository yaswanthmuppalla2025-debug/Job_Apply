# Start Here Autopilot

Read this first for any AI or SDE application batch.

Repository agents must also follow the root `AGENTS.md`; this file owns the active application runtime policy.

## Command Center

1. Use the `Job Apply - Yaswanth` Chrome profile.
2. Run in `Aggressive Autopilot / Hard Stop Only` mode.
3. Enforce recency before filling: prioritize 0-7 days, use 8-15 days for strong matches, and use 16-120 days only for the strongest AI matches that satisfy the exceptional-fit evidence in `RECENCY_PREFLIGHT.md` and remain officially live.
4. Apply strong-fit-first: submit only high/strong AI or SDE/backend matches. A medium role can be a documented `Strategic Exception` only inside 0-15 days and only with 3 primary resume-backed JD responsibilities, one core backend-to-AI/API/platform responsibility, and no hard must-have mismatch.
5. Use a lightweight JD-intent check before filling: the role should map to Yaswanth's backend-to-AI plumbing profile, such as APIs/services, RAG/retrieval/context, agents/tooling, data/AI pipelines, eval/serving/observability, cloud/platform integration, or Java/Python backend systems with AI features. Do not make this an essay or slowdown; if credible overlap exists, proceed. Skip roles that are mainly model research, recommender/personalization science, distributed training, CV/speech/domain science, data analysis, or product/program work unless the JD is clearly platform/tooling/serving-heavy.
6. Submission targets are not quotas: if strong matches are scarce, keep searching deeper official/company/ATS sources instead of lowering the fit bar.
7. Before filling, run the tracker-integrity gate in `TRACKER_SCHEMA.md`. Never duplicate-check or write against a workbook with implausible repeated canonical rows, missing expected headers, or inconsistent status totals; restore and reconcile first.
8. Extract the official job ID when visible and duplicate-check it with `Company`, `Role`, and `Application URL` across `AI`, `SDE`, and `Blockers`. Exact ID/canonical URL already submitted/already applied, or portal-proven submission, is a hard duplicate. An exact blocker match must resume/update that row rather than start another attempt. Same-company/title rows with different or unknown IDs require a quick team/location/JD comparison; materially distinct requisitions may proceed. Re-read the newest workbook immediately before final submit so concurrent agents cannot double-submit.
9. Spread applications intelligently: after 3 applications/attempts at one company in 30 days, do one focused Gmail signal check. Without recruiter, assessment, interview, or hiring-team interest, apply there again only for a materially different `High`/exceptional fit; otherwise rotate employers. Silence alone is not a permanent block, but explicit company/ATS caps and user cooldowns are hard boundaries.
10. Location priority: Georgia/Atlanta, Dallas/Austin/Texas, Virginia/DC, North Carolina, Tennessee, Florida, and Remote US only. Do not apply to SF/Bay Area/California/west-only roles unless the specific role is truly Remote US with no west-coast presence requirement.
11. Company-level hard block: do not apply to any Capital One role before `2027-01-07`. Power Day feedback indicated hire-level alignment below the applied level, but Capital One cannot provide sponsorship support at that eligible level right now; skip all Capital One AI/SDE/LinkedIn/Workday roles until the 6-month reattempt window.
12. Strictly skip no-sponsorship, no-H-1B-transfer, citizen/GC-only, U.S.-person-only, clearance-only, stale, closed, over-120-day, unknown-recency without proof, duplicate, staffing/vendor/aggregator-proxy, and obvious poor-fit roles. Roles 16-120 days old still need the exceptional AI-fit live-post rule.
13. Use `RECENCY_PREFLIGHT.md` for preflight and `TRACKER_SCHEMA.md` for tracker updates.
14. Use the AI resume for AI roles and the SDE resume for SDE/backend roles. Record outcomes in `JOB_APPLICATION_TRACKER.xlsx`.
15. Fill from `APPLICATION_PLAN.md`, `ANSWER_BANK.md`, the resume, JD, company context, and best truthful judgment.
16. OmInsights is a personal technical portfolio/learning project only. It is not an active company/product business, employer, consulting business, advisory role, revenue activity, secondary employment, or outside work Yaswanth is committing to continue after joining. For outside-work, secondary-employment, conflict, advisory/founder, business-ownership, or IP questions, follow the OmInsights compliance rule in `APPLICATION_PLAN.md` and `ANSWER_BANK.md`.
17. Submit high/strong-fit applications without per-role approval.
18. Recover normal friction before blocking: required-widget sweep, direct ATS URL, embedded form, PDF -> DOCX -> text fallback, account creation, Gmail code, reasonable assessment/questionnaire completion, reload/refill, Chrome reconnect.
19. No first-attempt technical blockers: except visual CAPTCHA/anti-abuse/legal/private-fact/hard-eligibility boundaries, a blocked role requires at least 2 serious attempts and at least 2 distinct recovery paths.
20. Account/login, email-code, and normal assessment/questionnaire walls are recoverable: create account, try existing login, use password reset through the job Gmail when available, retrieve the newest relevant Gmail code/link, complete truthful short assessment steps, then return to the exact job URL before blocking.
21. Confirm from screen, application ID, portal state, or Gmail; update `JOB_APPLICATION_TRACKER.xlsx` after every outcome.
22. Put submissions/already-applied rows in `AI` or `SDE`; put CAPTCHA, ATS, upload, account/login, anti-spam, manual/legal, missing-info, and Chrome/profile blockers in `Blockers`.
23. Do not create report, queue, cache, CSV, or JSONL artifacts for routine runs; the master workbook is the only durable state.
24. Close/finalize stale tabs and continue to the next role.

## Dynamic Blocker Retry Priority

Read the live `Blockers` sheet at run start and checkpoints; do not use a hard-coded company queue. A row is retryable only when the exact job is not already submitted, the official posting is still open and recency-eligible, fit remains high/strong, `Retry Eligible = Yes` (or `Manual Review` after the human action is known complete), fewer than 3 serious attempts have been exhausted, and a distinct safe recovery path remains.

1. Retry AI-resolvable email-code, account, upload, required-widget, or validation blockers first when they are high fit.
2. Retry other `Blocked - ATS` or `Blocked - Other` rows only when `Recovery Tried` and `Next Action` identify a new path.
3. Do not retry `No`, `Expired`, explicit company cooldown, already-submitted, stale, or closed rows.
4. Do not let CAPTCHA rows consume agent retries. Keep them parked for Yaswanth when useful, and retry only after the challenge is known resolved or a clean official non-CAPTCHA route exists.
5. Short truthful assessments/questionnaires remain recoverable; long take-homes, coding/video exercises, legal attestations, and missing applicant-only facts remain hard stops.

## Pre-Submit Checklist

Before final submit, verify:

- Role is official, open, verified 0-15 days old by default or 16-120 days old under the strongest-fit AI-only live-post exception, fit-aligned, and sponsorship-compatible.
- Fit is `High`/`Strong` for the selected lane and backed by a short JD-intent reason. A 0-15 day `Strategic Exception` or 16-120 day exceptional AI match needs 3 primary resume-backed JD responsibilities, one core backend-to-AI/API/platform responsibility, and no hard must-have mismatch.
- Posting date is verified from an official company/ATS source or reliable dated result: 0-7 days preferred, 8-15 days strong fit, 16-120 days strongest AI fits only with official live proof, and >120 days skipped.
- Employer is a direct product/platform/enterprise employer or a clearly high-quality direct company role; skip obvious staffing, consulting, vendor, recruiter, W2-only, client-confidential, or aggregator-proxy postings.
- Location matches the priority order: Georgia/Atlanta, Dallas/Austin/Texas, Virginia/DC, North Carolina, Tennessee, Florida, or Remote US only.
- `JOB_APPLICATION_TRACKER.xlsx` has been re-read immediately before submit; the job is not submitted/already applied or separately claimed by another agent. A current eligible retry may match its own blocker row.
- Company concentration has passed the soft 3-in-30-day signal check or this is a materially different `High`/exceptional role.
- Correct lane resume is uploaded, parsed, or pasted through the lane `.txt` fallback.
- Official ATS identity fields such as last-4 SSN, DOB, or month/day DOB are filled from `PRIVATE_APPLICATION_FIELDS.md` when required.
- Phone includes United States / `+1` when a country selector exists.
- Location typeahead has an actual selected option.
- Work authorization is truthful: authorized Yes, sponsorship/H-1B transfer Yes.
- OmInsights compliance answers are truthful: personal technical portfolio/learning project only; not active company/product business, not secondary employment, not advisory work, not outside work to continue after joining.
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

Private-field rule: never copy values from `PRIVATE_APPLICATION_FIELDS.md` into trackers, blocker reasons, learning-loop entries, screenshots, scratch files, or summaries.

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

For high-fit roles that already pass freshness, sponsorship, quality, location, and duplicate gates, CAPTCHA should not discard the opportunity. Fill every truthful field possible, leave the CAPTCHA/anti-abuse tab open for Yaswanth, record the row in `Blockers` as `Blocked - CAPTCHA` with `Blocker Type = CAPTCHA Parked`, `Retry Eligible = Manual Review`, `Parked Tab = Yes`, and continue applying in another tab.

Keep 3 working tabs at most (application, discovery, Gmail/security code) plus up to 5 parked CAPTCHA handoff tabs, for an absolute maximum of 8. Every `Parked Tab = Yes` row must match a live exact-role tab; reconcile the tracker with open tabs at run start and end. Never park low-quality, stale, no-sponsorship, duplicate, staffing/vendor, or poor-fit roles.
