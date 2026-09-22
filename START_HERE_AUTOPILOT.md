# Start Here Autopilot

This is the execution command center for AI, SDE, or combined application batches. Stable boundaries remain in `AGENTS.md`.

## Canonical Launcher

`Use the job-application-autopilot skill and the Job Apply - Yaswanth Chrome profile. Apply the current BATCH FILTERS, then continuously discover, rank, apply, verify, record, recover, and repeat for official High/Strong-fit roles. Begin applying as soon as the first eligible role passes preflight; maintain a rolling pool of roughly 3-5 eligible roles and replenish it continuously. Newly discovered qualifying roles inherit batch authorization. Do not stop on a shortlist, progress update, source change, tracker checkpoint, or individual blocker. Use the correct lane resume, complete ordinary fields with truthful best judgment, recover routine ATS/auth/upload friction, preserve only genuine user-only handoffs, and update JOB_APPLICATION_TRACKER.xlsx immediately after each outcome. End only at a documented full-batch end condition.`

Launcher rules:

- The current `BATCH FILTERS` override same-named defaults in `RECENCY_PREFLIGHT.md`; never copy an old dated snapshot, salary, location, or campaign baseline into a new launch.
- Batch authorization removes workflow and per-role approval gates. Obtain only a platform-required action-time confirmation or a genuine user-only fact at the point it is needed.
- A progress message is non-blocking commentary. Continue in the same run immediately after sending it.

## Batch Setup

1. Parse the active filters and write down only the effective lane, role focus, location, recency, seniority, sources, employer priorities/exclusions, target, and salary rule.
2. Capture the live lane-specific `Submitted` total as this launch's baseline. A new target/filter launch is a new batch unless Yaswanth explicitly says to continue an earlier one.
3. Run the deterministic tracker gate in `TRACKER_SCHEMA.md` once. Re-run it only after a workbook I/O, header, formula, or duplicate-lookup failure.
4. Reconcile any tracker-marked parked tabs quickly. Do not work every old blocker at startup; retry only rows with a currently available distinct next action.
5. If multiple agents are used, assign non-overlapping lane/source slices before discovery. Tag current-run queue items with canonical ID/URL plus owner; one role has one owner until recorded or released.

## Rolling Execution Loop

Repeat continuously:

1. Discover exact official open roles from company pages, ATS boards/APIs, LinkedIn, and reputable sources. Aggregators are discovery leads, not submission proof.
2. Run the single quick gate in `RECENCY_PREFLIGHT.md`. Start applying immediately when the first role passes; do not wait for an arbitrary broad shortlist.
3. Maintain approximately 3-5 eligible roles in the current working pool. Apply in rank order and replenish when fewer than 3 remain.
4. Duplicate-check the official job ID and canonical requisition URL across `AI`, `SDE`, and `Blockers` before filling.
5. Select exactly one lane and upload its canonical resume. AI-system work central -> AI resume; general backend/platform work central and AI peripheral -> SDE resume.
6. Fill from `APPLICATION_PLAN.md`, the relevant `ANSWER_BANK.md` section, the resume, JD, and live form. Use the truthful answer ladder in `AGENTS.md`; a required non-material preference may use a conservative candidate-aligned default.
7. Recover ordinary account, code, upload, parser, widget, and validation friction through `AUTOPILOT_BLOCKER_PLAYBOOK.md`; open the matching `ATS_RETRY_MATRIX.md` section only when useful.
8. Immediately before final submit, re-read the newest tracker and confirm no exact duplicate or concurrent submission appeared.
9. Obtain any platform-required action-time confirmation only when the exact action is ready, then submit without asking for another workflow approval.
10. Verify proof from the success page, application ID, portal state, or exact Gmail receipt. Record the outcome immediately using `TRACKER_SCHEMA.md`.
11. Close/finalize completed or useless tabs, preserve only valid tracker-matched handoffs, and move directly to the next eligible role.

## Fast Pre-Submit Check

Verify only what can change the outcome:

- Exact official requisition is open and still passes active batch filters.
- High/Strong central-responsibility fit, sponsorship/eligibility, salary, and advertised location passed once; re-evaluate only if new page evidence changed them.
- Exact ID/canonical URL is not submitted, already applied, blocked by another active owner, or duplicated across lanes.
- Visible attached filename matches the selected lane; required controls show committed values rather than typed-but-unselected text.
- All answers are truthful; no material candidate/job/proof fact was invented.
- Confirmation proof and tracker destination are ready.

## Recovery And Handoffs

- Use at most two distinct safe recovery paths or about ten minutes on one ordinary form, whichever comes first. A third attempt is reserved for an unusually strong fit with a genuinely new path.
- Do not repeat the same failed click, selector, upload, or code entry more than twice.
- Account creation, saved-credential login, password reset, job-Gmail codes, uploads, manual text entry, short questionnaires, standard notices, documented EEO choices, dropdowns, and typeaheads are recovery work.
- Park only after a narrow user-only boundary defined in `AGENTS.md` remains. Preserve the useful exact tab, write one precise `Next Action`, and continue in another working tab.
- A blocker belongs to that requisition, not to the batch. Record it and continue immediately.

## Browser And State

- Use only the Chrome instance whose profile name is `Job Apply - Yaswanth`.
- Keep at most three working tabs: application, discovery, and Gmail/security code. Up to five extra tabs may exist only as valid tracker-matched parked handoffs.
- A small rolling queue may live in agent context or OS temporary storage during the active run. It is not submission proof and must not contain private data.
- If Chrome is temporarily unavailable, keep discovering official roles and periodically retry the dedicated profile. Never switch to a personal/dev profile.
- If tracker writes are temporarily unsafe, continue discovery but pause final submission until exact duplicate protection and durable recording are restored.

## Full-Batch End Conditions

End only when one of these is true:

- Target proof-confirmed submission count is reached.
- The execution host/turn runtime expires; an arbitrary checkpoint or progress message is not runtime expiry.
- The measurable source-exhaustion rule in `RECENCY_PREFLIGHT.md` is met.
- Tracker-dependent submission cannot be restored safely after focused recovery.
- The required Chrome profile remains unavailable after focused recovery and no useful discovery work remains.

At the end, report current-batch submitted count separately from lifetime totals, plus `Already Applied`, blockers, proof-pending roles, unconfirmed outcomes, and parked handoffs. Never count a prepared form as submitted.
