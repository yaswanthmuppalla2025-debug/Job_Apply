# Autonomous Runbook

Use this file for days-long or overnight AI/SDE application runs.

Read `START_HERE_AUTOPILOT.md` first. Use this file for the loop, `ATS_RETRY_MATRIX.md` for ATS-specific recovery, `AGENT_RECOVERY_TRAINING.md` for blocker types 2-7, and `PRIVATE_APPLICATION_FIELDS.md` only for official ATS private identity fields.

Use `RECENCY_PREFLIGHT.md` before filling forms and `TRACKER_SCHEMA.md` when updating either tracker. Use `ROLE_DECISION_CACHE.xlsx` for stale/no-sponsorship/duplicate/staffing/vendor/aggregator-proxy/fit-mismatch discoveries that should not be rediscovered in the next daily run.

## Mission

Maximize truthful, profile-fit submissions. Codex should keep applying, retry normal ATS friction, create accounts, use Gmail codes, and recover from browser issues without asking Yaswanth for per-role approval.

Hard-stop only at the role level. A blocked role is not a stopped run.

Submission push boundary:

- Push hard on recoverable friction: login/account walls, email codes, upload widgets, hidden required fields, ATS validation loops, stale Chrome tabs, and broken apply redirects.
- Do not create a non-CAPTCHA technical blocker on the first failure. `Blocked - ATS` and `Blocked - Other` require at least 2 serious attempts and at least 2 distinct recovery paths unless the page presents a true hard boundary.
- Use up to 3 serious attempts for high-fit roles when the remaining issue is account login, password reset, upload fallback, direct ATS routing, or hidden-widget validation.
- Do not repeat the same failed click/action more than twice. Progress means trying a different recovery path, not hammering the same broken state.
- Still stop at CAPTCHA/visual challenge/security challenge, hard no-sponsorship/legal ineligibility, payment/scam gates, required manual exercises, or private facts not provided in the docs.

## Runtime Loop

For each role:

1. Discover a latest/open role from official company pages, ATS boards, or reputable hiring portals.
2. Verify official open status, posting recency, employer/source quality, location priority, role fit, and sponsorship compatibility before filling. Apply only when the posting is 0-15 days old: prioritize 0-7 days, use 8-15 days for strong matches, and skip >15 days.
3. Run the simple duplicate preflight: scan existing tracker `Role` columns and skip when the same company has the same normalized title already submitted/attempted, or the same official job id/application URL already exists.
4. Choose lane:
   - AI roles: `AI_ROLES/Yaswanth_Muppalla_AI_Resume.pdf`
   - SDE/backend roles: `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.pdf`
5. Fill identity, contact, education, work authorization, sponsorship, location, EEO, and custom fields from `APPLICATION_PLAN.md`, `ANSWER_BANK.md`, resume, JD, and best truthful judgment.
6. Create normal ATS/company accounts when needed using:
   - Email: `yaswanthmuppalla2025@gmail.com`
   - Credential: use the user-provided live credential only inside the live account flow.
7. If an official ATS requires last-4 SSN, DOB, or month/day DOB, fill it from `PRIVATE_APPLICATION_FIELDS.md` and do not record the private values anywhere.
8. When ATS validation, upload, manual exercise, duplicate/cap, legal attestation, identity-field, or account/login blockers appear, follow `AGENT_RECOVERY_TRAINING.md` and `ATS_RETRY_MATRIX.md`.
9. Use Gmail codes when the application sends verification.
10. Submit.
11. Confirm from screen, application ID, portal state, or Gmail receipt.
12. Update tracker immediately with submissions and real blockers after recovery.
13. Cache stale, no-sponsorship, duplicate, staffing/vendor/aggregator-proxy, fit-mismatch, or strategic skip decisions when useful.
14. Close or finalize unneeded tabs.
15. Continue to the next role.

## Preflight Gate

Use `RECENCY_PREFLIGHT.md` as the single source of truth for freshness, employer/source quality, location priority, and duplicate checks. Do not restate or override those rules here.

## Recovery Ladder

Before marking a role blocked, try the relevant ladder.

### Minimum Recovery Budget

Use this budget before `Blocked - ATS` or `Blocked - Other`:

1. First serious attempt: fill carefully, submit, read the exact error, and run the required-widget sweep.
2. Second serious attempt: change the path, such as reload/refill, direct ATS URL, embedded URL, official company careers route, PDF -> DOCX, text resume fallback, account reset, Gmail code, or Chrome reconnect.
3. Third serious attempt for high-fit roles: use a different remaining safe path, especially account/login reset, manual apply, direct job URL return, or browser/profile cleanup.
4. After any possible submit, check Gmail once for proof before calling it failed.
5. If a hard boundary appears at any point, stop that role, record the real blocker, and continue the batch.

Record the attempt count and exact recovery paths in the tracker for every real non-CAPTCHA blocker.

### Browser / Chrome

1. Reuse the active application tab when possible.
2. Close completed, stale, duplicate, expired, and research tabs after logging outcomes.
3. Keep only:
   - one active application tab
   - one discovery/source tab
   - one Gmail/security-code tab
   - one temporary verification tab if needed
4. If Chrome slows or the bridge times out, close stale tabs and reconnect to `Job Apply - Yaswanth`.
5. If the browser is stuck, finalize tabs when possible, reconnect or reopen the `Job Apply - Yaswanth` profile, and resume from the tracker.
6. If the current form state is lost, reopen the official application URL from the tracker and restart that role with attempt count incremented.

### ATS / Form

1. Required-widget sweep: phone country code, selected location typeahead, resume file card/manual text, EEO dropdowns, yes/no radios, checkboxes, acknowledgements, hidden required selectors.
2. Click the real submit button/locator, not only a coordinate.
3. If validation loops, reload once and refill from tracker/resume/defaults.
4. Try cleaned URL without tracking parameters.
5. Try direct ATS URL, official company careers page, or embedded ATS form.
6. If still impossible, mark `Blocked - ATS` with exact details in notes and continue.

### Resume Upload

1. Upload PDF.
2. If PDF fails or parses badly, upload DOCX.
3. Use visible upload/attach control.
4. Use accessible file input when available.
5. If upload fails and manual resume entry exists, paste from the relevant lane `.txt` resume fallback and continue.
6. Reload once and retry if the role is strong.
7. If upload is required and no upload/manual fallback works, mark `Blocked - Other` and continue.

### Account Creation / Login

1. Create normal ATS/company/job-board accounts when required; do not treat the account prompt itself as a blocker.
2. Use `yaswanthmuppalla2025@gmail.com`.
3. Use the user-provided live credential only inside the live account flow.
4. Do not store the password in trackers, screenshots, result notes, or learning-loop entries.
5. If the site says an account exists, try normal sign-in once with the same job email and live credential.
6. If sign-in fails and password reset is available through the job Gmail, request reset, retrieve the newest relevant email/code/link, set the same live credential, and continue.
7. If email verification is sent, use Gmail to retrieve the newest relevant code.
8. After account creation, sign-in, or reset, return to the exact official job application URL from the tracker, not only the careers homepage.
9. If the portal drops into profile setup, complete only required profile sections, then return to the active job and submit.
10. If CAPTCHA, security prompt, OTP outside Gmail, inaccessible password reset, or another non-AI challenge blocks the account after this protocol, mark `Blocked - CAPTCHA` or `Blocked - Other` as appropriate and continue.

### Gmail Codes And Confirmation

1. Keep one Gmail/security-code tab when browser-based Gmail is needed.
2. Use Gmail connector when available and pointing to the job mailbox.
3. Search only for the relevant company/ATS code or confirmation.
4. Enter the newest relevant code.
5. If the code expires, request a new code once when the form supports it.
6. After submission, search for confirmation and update tracker:
   - `Submitted`

## Hard Stop Only

Mark and move on. Do not stop the batch. Use `TRACKER_SCHEMA.md` as the single source of truth for status labels, and put exact proof/blocker detail in `Confirmation Proof`, `Recovery Tried`, `Next Retry Path`, and `Notes`.

## Checkpoints

After every role:

- Tracker row has current status.
- Notes include the exact proof, skip reason, or blocker detail. Real blockers stay in the tracker after recovery fails so they can improve future runs.
- `Attempt Count`, `Recovery Tried`, and `Next Retry Path` are filled for every `Blocked - ATS` or `Blocked - Other` row. `Learning Candidate` is updated when a real blocker or meaningful retry creates reusable signal.
- Optional helper fields may remain blank when not derivable quickly. Do not let metadata cleanup disturb the submission goal.
- Gmail confirmation is checked when practical.
- Unneeded tabs are closed.

Every 10-20 attempts:

- Reconfirm `Job Apply - Yaswanth` Chrome profile.
- Clean tab count.
- Save/export tracker state.
- Continue from the next queued/latest role that passes the 0-15 day recency gate.
- If no close matches remain inside 0-15 days, summarize the shortage for Yaswanth instead of applying to stale roles.

Every 2-3 hours, or every 50 submitted applications:

- Add 5-6 high-value sentences to `LEARNING_LOOP.md` only if there are new reusable observations.
- Focus on ATS-specific patterns, field mappings, upload/account/code recovery, Gmail confirmation behavior, source-mixing/CAPTCHA patterns, and tracker classification lessons.
- Do not add generic run narration, credentials, passwords, private identity values, one-off frustration, or copied policy.

## Morning Summary

Report:

- Submitted total.
- Email-confirmed total.
- Screen-confirmed total.
- Unconfirmed total.
- Skipped no-sponsorship/ineligible/closed total.
- Blocked CAPTCHA/ATS/upload/account/manual-legal total.
- Top manual retries worth Yaswanth attention.
- Gmail replies or recruiter messages needing action.
