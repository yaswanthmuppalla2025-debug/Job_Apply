# Autonomous Runbook

Use this compact loop for long AI/SDE application runs after `START_HERE_AUTOPILOT.md`. Do not duplicate policy here.

Owners:

- Role filters: `RECENCY_PREFLIGHT.md`
- Tracker, duplicate identity, proof, and statuses: `TRACKER_SCHEMA.md`
- Candidate facts and prose: `APPLICATION_PLAN.md` and `ANSWER_BANK.md`
- Generic recovery/handoffs: `AUTOPILOT_BLOCKER_PLAYBOOK.md`
- ATS mechanics: matching section of `ATS_RETRY_MATRIX.md`

## Rolling Loop

1. Validate effective batch filters, live baseline, tracker gate, Chrome profile, and assigned source slice.
2. Discover until the first exact official role passes preflight; begin applying immediately.
3. Maintain roughly 3-5 eligible roles. Apply in rank order while replenishing below three; never wait for a large shortlist.
4. Run fit/filter review once, duplicate-check, choose one lane resume, fill truthfully, and recover within the shared budget.
5. Re-read exact duplicate state immediately before submit, obtain only any required action-time confirmation, submit, verify proof, and record the outcome.
6. Finalize the tab and select the next role. A blocker, checkpoint, progress message, or empty source never pauses the loop.

Fresh eligible roles normally outrank old blockers. Retry a blocker only when it remains open/eligible and `Next Action` names a distinct path currently available. Do not work every parked/manual row at startup.

## Working State

- Use only `Job Apply - Yaswanth`.
- Keep at most three working tabs: application, discovery, and Gmail/security code. Additional tabs are allowed only for valid tracker-matched parked handoffs, up to five.
- A small rolling queue may live in agent context or OS temporary storage without private data. Delete temporary state at run end.
- After each tracker-worthy outcome, write it immediately. Do not log routine skip noise.
- Every 10-20 attempts, close stale/completed tabs, confirm the Chrome profile, verify tracker writes, and continue immediately.
- If Chrome fails, reduce tab pressure, reconnect the dedicated profile, reopen the exact official URL, and continue discovery while recovery is underway.
- If tracker writes fail, continue discovery but pause final submission until duplicate lookup and durable outcome writing are safe.

## Non-Blocking Checkpoints

A checkpoint is maintenance, not a review request. Verify tracker state, proof/blocker evidence, parked-tab matching, tab hygiene, and the next selected role; then continue.

Add to `LEARNING_LOOP.md` only when a genuinely new observed pattern produced a reusable successful action. Search it by ATS/company/error; never read or rewrite it end to end during a run.

## Finish

Stop only for a full-batch end condition in `START_HERE_AUTOPILOT.md`. Report:

- Current-batch proof-confirmed submissions versus target.
- `Already Applied` outcomes.
- Technical, CAPTCHA, and manual-review blockers.
- Proof-pending/unconfirmed outcomes.
- Parked tabs and their exact one-step handoffs.
- Recruiter or Gmail items requiring attention.

Do not report routine skip totals unless they were maintained reliably in current runtime state.
