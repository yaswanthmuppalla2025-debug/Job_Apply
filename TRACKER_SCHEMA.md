# Tracker Schema

`JOB_APPLICATION_TRACKER.xlsx` is the durable source of application outcomes. It has exactly four active sheets: `Summary`, `AI`, `SDE`, and `Blockers`.

## Deterministic Integrity Gate

Run this once at batch start and again only after a workbook read/write, header, formula, or duplicate-lookup failure:

1. The workbook opens and the four required sheets are readable.
2. `AI`, `SDE`, and `Blockers` contain the required identity, status, URL, and proof/recovery headers listed below.
3. Exact official job ID and canonical-URL lookup works across all three outcome sheets.
4. A new row can be written using the existing table/format without overwriting headers, formulas, or historical rows.
5. Required Summary counters contain no formula errors. Optional metadata blanks and legacy blank `Fit` values do not fail the gate.

If the gate fails, do not overwrite, bulk-normalize, or invent a restored snapshot. Continue discovery in agent context or OS temporary storage, repair only the affected structure from direct evidence, and pause final submission until duplicate lookup plus safe durable writing are restored. Re-run the gate, then continue the batch without asking for workflow approval.

Historical rows are read-only unless direct portal, confirmation, official-role, or browser evidence supports a targeted repair.

## Exact Duplicate Identity

- Before filling and immediately before final submit, compare official job ID plus canonical requisition URL across `AI`, `SDE`, and `Blockers`.
- Remove tracking parameters and terminal apply/confirmation/thanks variants only when they still identify the same requisition. A generic careers, candidate-home, or confirmation URL is not a job ID.
- Exact ID/canonical URL already `Submitted` or `Already Applied`, or portal-proven prior submission, is a hard duplicate.
- An exact `Blockers` match belongs to that existing attempt; update it when retry-eligible rather than opening a second application.
- Same company/title with different or unknown IDs gets one quick team/location/JD comparison. Materially distinct requisitions may proceed.
- Concurrent agents use non-overlapping source/lane slices. Re-read the newest tracker before final submit; if another owner recorded the exact role, skip that requisition and continue the batch.

## AI And SDE Outcome Sheets

Use `AI` for AI-lane outcomes and `SDE` for SDE-lane outcomes. Allowed statuses are only `Submitted` and `Already Applied`.

Required columns:

| Column | Rule |
|---|---|
| Date | Outcome date. |
| Company | Direct employer name. |
| Role | Exact role title. |
| Location | Advertised role location/remote eligibility. |
| Status | `Submitted` or `Already Applied`. |
| Application URL | Canonical official company/ATS requisition URL. |
| Fit | New submissions: `High - <central JD responsibility + evidence>` or `Strong - <central JD responsibility + evidence>`. |
| Confirmation Proof | Success page, application ID, exact portal state, or requisition-matched Gmail receipt. |
| Notes | Concise non-private proof or duplicate detail when useful. |

Optional existing metadata—`Posted Date`, `Age Days`, `Recency Proof`, `Source`, `ATS`, and `Sponsorship`—may remain blank when not quickly available and not required by the active gate.

Do not call a role `Submitted` without proof. Do not create proof-flavored status variants.

## Blockers Sheet

Use `Blockers` only for real unresolved outcomes after bounded recovery or a genuine immediate hard boundary. Do not create blockers for ordinary account creation, job-Gmail codes, upload/widget friction, or short questionnaires before the recovery budget is used.

Required columns:

| Column | Rule |
|---|---|
| Date | Outcome date. |
| Lane | `AI`, `SDE`, or `All` for a company-wide hard block. |
| Company | Employer name. |
| Role | Exact role title. |
| Status | `Blocked - CAPTCHA`, `Blocked - ATS`, or `Blocked - Other`. |
| Blocker Type | Exact type: `CAPTCHA Parked`, `Proof Pending`, `Upload`, `Account/Login`, `Validation`, `Manual/Legal`, `Missing Material Fact`, `Chrome/Profile`, etc. |
| Application URL | Canonical official requisition URL. |
| Retry Eligible | `Yes`, `No`, `Expired`, or `Manual Review`. |
| Parked Tab | `Yes` only when a useful exact-role handoff tab is currently live; otherwise `No` or blank. |
| Notes | Exact non-private evidence. |

For recoverable technical blockers also fill `Attempt Count`, `Recovery Tried`, and `Next Action`. Existing optional columns such as location, source, ATS, fit, posted date, age, and learning may be used when helpful.

### Proof Pending

When submit may have completed but confirmation is weak:

- Do not write `Submitted` or resubmit immediately.
- Write/update `Blockers` as `Blocked - ATS`, `Blocker Type = Proof Pending`, `Retry Eligible = Yes`, with the exact ID/URL and the next portal/Gmail reconciliation action.
- Reconcile the exact portal and Gmail once. Convert to `Submitted` only when proof appears; otherwise retain a truthful blocker or retry through one clearly safe path.

This is the durable representation for an unconfirmed attempt and prevents accidental duplicate submission.

### Parked Tab Field

Parking procedure belongs to `AUTOPILOT_BLOCKER_PLAYBOOK.md`. The tracker rule is simple: every `Parked Tab = Yes` row must match one live exact-role tab by requisition ID or canonical URL. Set it to `No` when the tab is gone or resolved; retain the historical blocker evidence.

## Minimum Outcome Rows

- Submitted: date, company, role, status, canonical URL, fit, and confirmation proof.
- Already applied: date, company, role, status, canonical URL when available, and proof note.
- Blocker: date, lane, company, role, status, blocker type, canonical URL, retry eligibility, and evidence; add recovery fields for technical blockers.

Write the next safe row using the workbook's existing table pattern. Do not force a top-row insertion when it risks formulas or formatting. Update immediately after every submitted, already-applied, blocker, or proof-pending outcome.

Do not log routine stale, closed, outside-filter, no-sponsorship, duplicate-without-useful-proof, staffing/vendor, or fit-mismatch skip noise.

## Batch Counter

- Capture live lane-specific `Submitted` totals before each new launch. A new target/filter launch is a new baseline unless the user explicitly continues a prior campaign.
- Current-batch submitted = current lane `Submitted` total minus that launch baseline.
- `Already Applied`, blockers, proof-pending, exclusions, and unconfirmed attempts do not reduce the remaining target.
- Summary formulas, not Markdown snapshots, own totals. Report current-batch, earlier-campaign, and lifetime counts separately.

## Privacy And Repository State

Never store passwords, codes, full SSN, DOB, passport, bank/payment information, private identity values, or private email content in the workbook. A small current-run queue may exist only in agent context or OS temporary storage without private data. Do not create routine repository queue, report, audit, cache, backup, CSV, JSON, or JSONL artifacts.
