# Start Here Autopilot

Read this first for any AI or SDE application batch.

Repository agents must also follow the root `AGENTS.md`; this file owns the active application runtime policy.

Startup reading budget: read this file, `RECENCY_PREFLIGHT.md`, and `TRACKER_SCHEMA.md`. Use `APPLICATION_PLAN.md` and `ANSWER_BANK.md` for answers, and open recovery docs only when friction appears. Search `LEARNING_LOOP.md` by ATS, company, or error text; do not load the full learning archive before applying.

## Canonical Launch Prompt

`Use the Job Apply - Yaswanth Chrome profile and run an Aggressive Autopilot batch for [AI/SDE/both]. Deeply discover and rank official high/strong-fit roles, then submit eligible applications without per-role approval. You may follow official company/ATS links, use the tracker and job Gmail, create/sign in/reset ATS accounts, retrieve job-Gmail verification codes, and recover normal form/upload/browser friction. Prefer stable visible or accessible controls; use iframe, shadow-DOM, or lower-level selectors only when required, and verify every committed value and upload. If one role cannot be completed truthfully after the documented recovery ladder, record its blocker and continue the batch; never halt the full run for a single role.`

Do not add launcher restrictions that forbid official ATS navigation, tracker/Gmail access, account creation, or recovery. Do not require artificial human-like delays, and do not let a single incomplete form halt the batch.

## Batch Identity And Progress

- Before discovery or submission, snapshot the live lane-specific `Submitted` total in the tracker as the baseline for the newly launched batch.
- A user launch with its own filters and target starts a new batch unless the user explicitly says to continue an earlier campaign or target. Do not silently reuse a prior campaign baseline.
- Current-batch submitted count is the current lane-specific `Submitted` total minus that launch baseline. Show that count separately from earlier-campaign and lifetime totals in checkpoints and final reports.
- `Already Applied`, duplicates, blockers, exclusions, and unconfirmed attempts never increase the submitted count. Report those outcome categories separately.
- If a baseline was missed or reused incorrectly, reconstruct it only from proof-backed current-run rows, document the targeted correction in the tracker, and verify the resulting formulas before continuing.

Current tracker-verified snapshot (`2026-08-04`): the AI batch launched `2026-08-03` from a baseline of `1,335` AI submissions and is at `10/100`, with `90` remaining. Refresh this snapshot from the live workbook before new work; it is context, not the counter source.

Current-batch salary interpretation (`2026-08-04` user clarification): an advertised base range qualifies when its upper bound is above `$150,000`; for example, `$120,000-$165,000` passes. A single advertised base amount must be above `$150,000`. Do not infer compensation when the posting provides no advertised base amount or range.

## Command Center

1. Use the `Job Apply - Yaswanth` Chrome profile.
2. Run in `Aggressive Autopilot / Hard Stop Only` mode.
3. Enforce recency before filling: prioritize 0-7 days, use 8-15 days for strong matches, use 16-90 days for live strong-fit SDE/backend roles, and use 16-120 days for the strongest AI matches that satisfy the lane-specific evidence in `RECENCY_PREFLIGHT.md` and remain officially live.
4. Apply strong-fit-first: submit only `High` or `Strong` AI and SDE/backend matches. `Medium`, adjacent, keyword-only, and strategic-exception roles are skips even when the submission target is behind.
5. Use a lightweight JD-intent check before filling: the role should map to Yaswanth's backend-to-AI plumbing profile, such as APIs/services, RAG/retrieval/context, agents/tooling, data/AI pipelines, eval/serving/observability, cloud/platform integration, or Java/Python backend systems with AI features. Do not make this an essay or slowdown; if credible overlap exists, proceed. Skip roles that are mainly model research, recommender/personalization science, distributed training, CV/speech/domain science, data analysis, or product/program work unless the JD is clearly platform/tooling/serving-heavy.
6. Submission targets are not quotas: if strong matches are scarce, keep searching deeper official/company/ATS sources instead of lowering the fit bar. Deep discovery may take longer than form filling; inspect a broad pool, rank the strongest roles, and apply in that order. Once the official JD, advertised location, and central-responsibility fit pass, do not repeat a subjective hiring-manager review unless new evidence appears.
7. Before filling, run the tracker-integrity gate in `TRACKER_SCHEMA.md`. Never duplicate-check or write against a workbook with implausible repeated canonical rows, missing expected headers, or inconsistent status totals; restore and reconcile first.
8. Extract the official job ID when visible and duplicate-check it with `Company`, `Role`, and `Application URL` across `AI`, `SDE`, and `Blockers`. Exact ID/canonical URL already submitted/already applied, or portal-proven submission, is a hard duplicate. An exact blocker match must resume/update that row rather than start another attempt. Same-company/title rows with different or unknown IDs require a quick team/location/JD comparison; materially distinct requisitions may proceed. Re-read the newest workbook immediately before final submit so concurrent agents cannot double-submit.
9. Spread applications intelligently: prefer fresh qualified companies. After 3 applications/attempts at one company in 30 days, do one focused Gmail signal check. Without recruiter, assessment, interview, or hiring-team interest, treat that company as saturated for the batch and rotate employers. Apply there again only for a materially different `High`/exceptional fit that beats the available fresh-company alternatives. After 5+ recent submissions with no positive signal, skip by default unless Yaswanth explicitly requested that employer or the role is a rare exact-fit target. Silence alone is not a permanent block, but it should strongly lower priority; explicit company/ATS caps and user cooldowns are hard boundaries.
10. Current batch location priority and exclusions come only from `RECENCY_PREFLIGHT.md`. Check the role's actual advertised location once and use that result throughout the application; applicant location, employer headquarters, and relocation willingness never relabel the job. For the active AI batch, a requisition whose official location type is `Hybrid` or `On-site` outside Atlanta, Dallas, Austin, or North Carolina is ineligible even when description prose says remote candidates may be considered or reviewed case by case. Nationwide remote qualifies only when the official requisition advertises the role itself as Remote US.
11. Company-level hard blocks: do not apply to any Capital One role before `2027-01-07`. Power Day feedback indicated hire-level alignment below the applied level, but Capital One cannot provide sponsorship support at that eligible level right now; skip all Capital One AI/SDE/LinkedIn/Workday roles until the 6-month reattempt window. Also skip Cargill roles during current autopilot batches unless Yaswanth explicitly reopens the employer; prior Cargill attempts/signals indicate they will not sponsor H-1B transfer.
12. Strictly skip no-sponsorship, no-H-1B-transfer, citizen/GC-only, U.S.-person-only, clearance-only, stale, closed, unknown-recency without proof, duplicate, staffing/vendor/aggregator-proxy, and obvious poor-fit roles. SDE/backend roles older than 90 days and AI roles older than 120 days are stale; older-window roles still need the lane-specific strong/exceptional live-post rule.
13. Use `RECENCY_PREFLIGHT.md` for preflight and `TRACKER_SCHEMA.md` for tracker updates.
14. Use the AI resume for AI roles and the SDE resume for SDE/backend roles. Record outcomes in `JOB_APPLICATION_TRACKER.xlsx`.
15. Fill from `APPLICATION_PLAN.md`, `ANSWER_BANK.md`, the resume, JD, company context, and best truthful judgment. For an unfamiliar field, use this order: documented answer -> factual resume/JD/company inference -> closest truthful option -> blank or `N/A` when allowed. Never make up a material candidate, legal, eligibility, compensation, or private fact.
16. OmInsights is a personal technical portfolio/learning project only. It is not an active company/product business, employer, consulting business, advisory role, revenue activity, secondary employment, or outside work Yaswanth is committing to continue after joining. For outside-work, secondary-employment, conflict, advisory/founder, business-ownership, or IP questions, follow the OmInsights compliance rule in `APPLICATION_PLAN.md` and `ANSWER_BANK.md`.
17. Submit high/strong-fit applications without per-role approval.
18. Recover normal friction before blocking: required-widget sweep, direct ATS URL, embedded form, PDF -> DOCX -> text fallback, account creation, Gmail code, reasonable assessment/questionnaire completion, reload/refill, Chrome reconnect.
19. No first-attempt technical blockers: except visual CAPTCHA/anti-abuse/legal/private-fact/hard-eligibility boundaries, a blocked role requires at least 2 serious attempts and at least 2 distinct recovery paths.
20. Account/login, email-code, and normal assessment/questionnaire walls are recoverable: use the existing session or securely saved browser credential, create an account when needed, try sign-in, use password reset through the job Gmail, retrieve only the newest relevant code/link, return to the exact job URL, and try one clean direct-route reload before blocking. Never ask for approval during this ladder, and never expose credentials or codes in durable artifacts.
21. For email/security-code gates, use confirmation-first navigation: after every submit or code attempt, inspect the current URL, title, visible success text, portal state, and Gmail before touching the code widget again. If a confirmation/thanks page, application ID, received message, or matching Gmail proof exists, record `Submitted` immediately; do not keep retrying stale validation text or segmented boxes.
22. If a segmented code widget becomes corrupted after two distinct cleanup paths, reload/refill the same official role once or request one fresh code when supported. Do not loop on the same broken code boxes; recover cleanly, block with evidence if still impossible, and continue the batch.
23. Confirm from screen, application ID, portal state, or Gmail; update `JOB_APPLICATION_TRACKER.xlsx` after every outcome.
24. Put submissions/already-applied rows in `AI` or `SDE`; put CAPTCHA, ATS, upload, account/login, anti-spam, manual/legal, missing-info, and Chrome/profile blockers in `Blockers`.
25. Do not create report, queue, cache, CSV, or JSONL artifacts for routine runs; the master workbook is the only durable state.
26. Close/finalize stale tabs and continue to the next role.

## Dynamic Blocker Retry Priority

Read the live `Blockers` sheet at run start and checkpoints; do not use a hard-coded company queue. A row is retryable only when the exact job is not already submitted, the official posting is still open and recency-eligible, fit remains high/strong, `Retry Eligible = Yes` (or `Manual Review` after the human action is known complete), fewer than 3 serious attempts have been exhausted, and a distinct safe recovery path remains.

1. Retry AI-resolvable email-code, account, upload, required-widget, or validation blockers first when they are high fit.
2. Retry other `Blocked - ATS` or `Blocked - Other` rows only when `Recovery Tried` and `Next Action` identify a new path.
3. Do not retry `No`, `Expired`, explicit company cooldown, already-submitted, stale, or closed rows.
4. Do not let CAPTCHA rows consume agent retries. Keep them parked for Yaswanth when useful, and retry only after the challenge is known resolved or a clean official non-CAPTCHA route exists.
5. Short truthful assessments/questionnaires remain recoverable; long take-homes, coding/video exercises, legal attestations, and missing applicant-only facts remain hard stops.

## Pre-Submit Checklist

Before final submit, verify:

- Role is official, open, verified 0-15 days old by default, 16-90 days old under the live strong-fit SDE/backend exception, or 16-120 days old under the strongest-fit AI exception; it is fit-aligned and sponsorship-compatible.
- Fit is `High`/`Strong` for the selected lane and backed by a short JD-intent reason. Every older-window match needs 3 primary resume-backed JD responsibilities, one core backend-to-AI/API/platform/distributed-systems/backend-service responsibility, a credible experience band, and no hard must-have mismatch.
- Posting date is verified from an official company/ATS source or reliable dated result: 0-7 days preferred, 8-15 days strong fit, 16-90 days strong SDE/backend or exceptional AI fit with official live proof, 91-120 days exceptional AI fit only, and older roles skipped.
- Employer is a direct product/platform/enterprise employer or a clearly high-quality direct company role; skip obvious staffing, consulting, vendor, recruiter, W2-only, client-confidential, or aggregator-proxy postings.
- Advertised job location passes the current allowed-location rule in `RECENCY_PREFLIGHT.md`; do not substitute applicant location, company headquarters, or relocation wording.
- `JOB_APPLICATION_TRACKER.xlsx` has been re-read immediately before submit; the job is not submitted/already applied or separately claimed by another agent. A current eligible retry may match its own blocker row.
- Company concentration has passed the saturated-company gate: if the employer has 3+ recent attempts and no positive signal, a same-company role proceeds only when it is materially different, `High`/exceptional, and better than current fresh-company alternatives; 5+ silent submissions is skip-by-default.
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

## Learning Checkpoint

At a long-run checkpoint, add one concise observed-pattern -> successful-action lesson only when it is genuinely new and reusable. Do not add required sentence counts, policy restatements, run narration, credentials, codes, private values, or private email content. `LEARNING_LOOP.md` is a searchable archive, not startup reading.

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
