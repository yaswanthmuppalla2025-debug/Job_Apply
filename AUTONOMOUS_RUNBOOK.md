# Autonomous Runbook

Use this for days-long or overnight AI/SDE application runs after reading `START_HERE_AUTOPILOT.md`.

This file owns the execution loop only. Do not duplicate policy here:

- Freshness, quality, location, and duplicate gates: `RECENCY_PREFLIGHT.md`
- Tracker columns and statuses: `TRACKER_SCHEMA.md`
- Blocker recovery and hard stops: `AUTOPILOT_BLOCKER_PLAYBOOK.md`
- ATS-specific fixes: `ATS_RETRY_MATRIX.md`
- Reusable answers: `ANSWER_BANK.md`
- Observed lessons: `LEARNING_LOOP.md`

## Mission

Maximize truthful, profile-fit submissions without per-role approval. Push through normal ATS friction, account creation, Gmail codes, upload fallbacks, form validation, and Chrome recovery. A hard-stopped role is one row outcome, not a stopped batch.

## Runtime Loop

For each role:

1. Discover latest open roles from official company pages, ATS boards, LinkedIn, and reputable hiring portals.
2. Run `RECENCY_PREFLIGHT.md` before filling anything.
3. Skip early when the role is stale, closed, duplicate, low-quality, no-sponsorship, legally ineligible, outside priority location, or poor fit.
4. Choose the lane:
   - AI roles: `AI_ROLES/Yaswanth_Muppalla_AI_Resume.pdf`
   - SDE/backend roles: `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.pdf`
5. Fill identity, contact, education, work authorization, sponsorship, location, EEO, and custom fields from `APPLICATION_PLAN.md`, `ANSWER_BANK.md`, the resume, JD, company context, and best truthful judgment.
6. Use normal account creation, Gmail codes, and official ATS private identity fields when required.
7. Submit when all required fields are truthfully complete.
8. Capture proof from confirmation page, application ID, portal state, or Gmail receipt.
9. Update the active tracker immediately using `TRACKER_SCHEMA.md`.
10. Cache stale, no-sponsorship, duplicate, staffing/vendor, aggregator-proxy, fit-mismatch, or strategic skip decisions in `ROLE_DECISION_CACHE.xlsx` when it prevents rediscovery.
11. Close or finalize stale/completed tabs and continue to the next role.

## Recovery Loop

When normal friction appears, do not give up:

1. Diagnose the exact blocker from visible validation, page state, account state, upload state, or browser behavior.
2. Use `AUTOPILOT_BLOCKER_PLAYBOOK.md` for blocker-type recovery.
3. Use `ATS_RETRY_MATRIX.md` for ATS-specific behavior.
4. Try a distinct recovery path instead of repeating the same failed action: reload/refill, direct ATS URL, embedded form, official company page, PDF -> DOCX, `.txt` resume fallback, account creation/reset, Gmail code, or Chrome reconnect.
5. For high-fit roles, use up to 3 serious attempts when safe paths remain.
6. Check Gmail once when a submit might already have completed.
7. If recovery fails, record the real blocker with `Attempt Count`, `Recovery Tried`, `Next Retry Path`, and exact non-private notes.
8. Continue the batch.

## Chrome Loop

- Use only the `Job Apply - Yaswanth` Chrome profile.
- Prefer one reusable application tab.
- Keep at most 3-5 live tabs: active application, discovery/source, Gmail/security-code, and one temporary verification tab.
- After every submitted, skipped, blocked, or already-applied outcome, update tracker first, then close/finalize unneeded tabs.
- Every 10-20 attempts, run a hygiene cycle: close stale tabs, confirm the profile, save tracker state, and continue from the next eligible role.
- If Chrome gets stuck, reduce tab pressure, reconnect/reopen `Job Apply - Yaswanth`, reopen the exact official job URL from the tracker, increment attempt count, and keep going.
- Do not switch to personal/dev Chrome profiles unless Yaswanth explicitly says to.

## Checkpoints

After every role:

- Tracker row has current status.
- Proof, skip reason, or blocker detail is recorded.
- `Blocked - ATS` and `Blocked - Other` rows have recovery fields filled.
- Gmail confirmation was checked when practical.
- Tabs are clean enough for the next role.

Every 2-3 hours, or every 50 submitted applications:

- Add 5-6 high-value sentences to `LEARNING_LOOP.md` only if new reusable observations exist.
- Focus on ATS-specific patterns, field mappings, upload/account/code recovery, Gmail confirmation behavior, source-mixing/CAPTCHA lessons, and tracker classification.
- Do not add generic narration, motivation, copied policy, credentials, passwords, codes, private identity values, or private email content.

## Morning Summary

Report:

- Submitted total.
- Email-confirmed total.
- Screen-confirmed total.
- Unconfirmed total.
- Skipped no-sponsorship/ineligible/closed/stale total.
- Blocked CAPTCHA/ATS/upload/account/manual-legal total.
- Best manual retries worth Yaswanth attention.
- Gmail replies or recruiter messages needing action.
