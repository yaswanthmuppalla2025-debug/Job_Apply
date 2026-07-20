# Job Application Agent Contract

This repository is an execution workspace for finding and truthfully applying to high-fit AI, backend-to-AI, and backend systems roles for Yaswanth Muppalla. Optimize for verified fit and confirmed submissions, not raw form volume.

## Start Here

1. Read `START_HERE_AUTOPILOT.md` for the active command center.
2. Read `RECENCY_PREFLIGHT.md` before discovery or form filling.
3. Read `TRACKER_SCHEMA.md` before duplicate checks or workbook writes.
4. Use `APPLICATION_PLAN.md` and `ANSWER_BANK.md` for candidate and form answers.
5. Open `AUTOPILOT_BLOCKER_PLAYBOOK.md`, `ATS_RETRY_MATRIX.md`, or `AUTONOMOUS_RUNBOOK.md` only when that depth is needed.

Application batches ignore `INTERVIEW_PREP/`; that directory is for interview-specific work only.

## Truth Order

When facts conflict, prefer the newest direct evidence in this order:

1. The live official company or ATS role/form page.
2. A visible confirmation page, application ID, portal state, or matching Gmail receipt.
3. The current `JOB_APPLICATION_TRACKER.xlsx` workbook.
4. The current command-center Markdown files.
5. Browser history, search results, or older notes as supporting evidence only.

Do not call an application submitted without confirmation evidence. Do not invent a job ID, posting date, sponsorship policy, candidate fact, answer, workflow state, or proof.

## Role Gate

- AI lane: AI platform, applied AI, LLM/RAG, agent/tooling, evaluation, serving, observability, data/AI pipelines, and backend-to-AI product roles.
- SDE lane: backend, platform, distributed systems, Java/Python services, cloud, data platform, and backend-heavy full-stack roles.
- Apply only when the role passes the current recency, employer-quality, geography, sponsorship, company-spread, and fit rules in `RECENCY_PREFLIGHT.md`.
- Skip deep model-research/scientist roles, weak keyword matches, staffing/vendor proxies, and incompatible eligibility requirements.
- Do not apply to Capital One before `2027-01-07`.

## Execution Behavior

- Once Yaswanth starts an autopilot batch, submit eligible high/strong-fit roles without per-role approval.
- Respect a user instruction to stop before submit literally. Fill the form and stop at the final submit control.
- Reuse the `Job Apply - Yaswanth` Chrome profile and keep the tab set lean.
- Use official ATS/company pages for submission even when discovery starts elsewhere.
- Recover ordinary account, upload, verification-code, widget, and validation friction before recording a blocker.
- Never bypass CAPTCHA or guess legal/private facts. Use the blocker workflow and continue to another role.
- Use the correct lane resume and the `.txt` fallback only when upload/parsing is unreliable.

## Tracker Contract

- `JOB_APPLICATION_TRACKER.xlsx` is the only durable application state.
- Run the tracker-integrity gate before screening or writing.
- Duplicate-check all lanes before filling and re-read the newest workbook immediately before final submit.
- Use official job ID plus canonical requisition URL; same company/title can be a distinct role when the requisition, team, location, or JD is materially different.
- Concurrent agents must use non-overlapping lane/source slices. A role already submitted, already applied, or actively owned by another agent is off limits; an eligible retry updates its existing blocker row.
- Update the workbook immediately after every submitted, already-applied, or blocked outcome.
- Historical rows with legacy blanks or statuses are read-only unless direct evidence supports a targeted repair. Never bulk-infer missing Fit, dates, proof, or status.

## Repository Hygiene

- Do not create routine queue, report, audit, cache, JSON, JSONL, CSV, screenshot, preview, backup, or helper-script artifacts in the repository.
- Use an OS temporary directory for transient work and remove or quarantine it before finishing.
- Keep only canonical resumes in `AI_ROLES/` and `SDE_ROLES/`.
- Never write passwords, verification codes, private identity values, private email contents, or form-only data into the tracker, docs, logs, screenshots, or summaries.
- `PRIVATE_APPLICATION_FIELDS.md` is local and form-only. Do not quote or expose its values.

## Finish Standard

Before ending a batch, confirm proof-backed outcomes are written, workbook formulas and headers are intact, blockers match any parked tabs, temporary artifacts are outside the repo, and browser tabs are finalized. Report submitted, already-applied, blocked, and unconfirmed outcomes separately.
