# Autopilot Blocker Playbook

This file owns generic recovery and genuine user-only handoffs. ATS-specific mechanics belong in `ATS_RETRY_MATRIX.md`; tracker fields/statuses belong in `TRACKER_SCHEMA.md`.

A blocker is one requisition outcome after bounded recovery—not a stopped batch.

## Bounded Recovery Algorithm

For ordinary technical friction:

1. Read the visible validation, URL, page state, required controls, account state, and upload state. Diagnose before clicking again.
2. Verify committed values: a typed typeahead, visible dropdown label, filename, radio, checkbox, or segmented date may still be uncommitted.
3. Try one direct repair of the current state: required-control sweep, exact option selection, clear/refill, visible upload control, or correct submit locator.
4. Try one genuinely distinct safe path: cleaned/direct ATS URL, official company route, reload/refill, PDF -> DOCX, text/manual resume, account reset, fresh job-Gmail code, or Chrome reconnect.
5. After submit/code attempts, inspect URL, visible success text, portal state, and exact Gmail proof before retrying.
6. Stop ordinary recovery after two distinct paths or about ten minutes, whichever comes first. Use a third attempt only for an unusually strong role with a specific new path or signal.
7. Do not repeat an identical failed action more than twice. Record the blocker or proof-pending state and continue immediately.

Two links that land on the same endpoint with the same failure are one path, not two.

## Normal Work—Not Handoffs

Handle these autonomously when truthful:

- Existing session, normal account creation, sign-in, password reset, and job-Gmail verification code/link.
- Resume PDF/DOCX/text fallback, manual profile entry, parsing correction, and upload verification.
- Phone country, location/source typeahead, dropdown, radio, checkbox, date widget, standard privacy/data/application acknowledgement, and documented EEO selection.
- Required non-material preferences using the answer ladder, optional fields, `N/A`, concise tailored text, and short factual questionnaires.
- One clean reload/refill or official/direct-route retry.

Do not park a tab merely because a widget is awkward or the field is described as applicant information.

## Authentication Ladder

Use only the `Job Apply - Yaswanth` profile and official account flow:

1. Existing authenticated session.
2. Credential securely saved in the dedicated profile.
3. Normal sign-in or account creation with the job email.
4. Password reset or newest relevant code/link through job Gmail.
5. Return to the exact requisition URL and try one clean direct route.

Never expose or persist credentials/codes. If the platform requires an action-time confirmation, request it only when that exact action is ready; do not ask generic permission to continue the ladder.

## Genuine User-Only Boundaries

A user-only handoff exists only for:

- Visible CAPTCHA, hCaptcha, reCAPTCHA, visual puzzle, or anti-abuse challenge.
- Required material/private fact absent from the resume, plan, answer bank, authorized private file, and safe factual inference.
- Explicit applicant-authored/no-AI response.
- Unusual personal legal attestation, signature, or certification requiring Yaswanth's judgment.
- Substantial take-home, coding, video, reference/referral contact, or external artifact that cannot be truthfully completed from existing evidence.
- Suspicious payment, bank, passport, full-SSN, unrelated identity collection, or another unsafe request.

Explicit no-sponsorship/incompatible eligibility, closed roles, duplicates, and poor fits are skips, not handoffs. Never bypass anti-abuse controls or invent the missing fact.

## Outcome Mapping

| Situation | Tracker Outcome |
|---|---|
| Exact success page, application ID, portal state, or requisition-matched Gmail receipt | `Submitted` in the lane sheet with proof. |
| Prior application proven | `Already Applied` in the lane sheet. |
| Submit may have completed but proof is weak | `Blocked - ATS`, `Blocker Type = Proof Pending`; do not resubmit until reconciled. |
| Visual CAPTCHA/anti-abuse challenge | `Blocked - CAPTCHA`; park only when the filled form is useful. |
| ATS validation/submit/code failure after budget | `Blocked - ATS`. |
| Required upload/account/browser failure after budget | `Blocked - Other` unless a more specific current schema mapping applies. |
| Missing material fact, personal attestation, no-AI response, or substantial exercise | `Blocked - Other`, `Retry Eligible = Manual Review`. |
| Closed, duplicate, no-sponsorship, ineligible, outside-filter, staffing/vendor, or poor fit | Skip and continue; record only useful `Already Applied` proof. |

All technical blockers include exact evidence, attempt count, recovery paths, and one concrete next action. Never use vague notes such as `site failed`.

## Park And Continue

Park only when every role gate passed, the form is live and useful, and one genuine user-only boundary remains.

1. Fill and verify every truthful field possible, including the correct visible resume attachment.
2. Preserve the exact deepest stable tab. If a risky alternate route is worth trying, duplicate/open it separately; do not mark the original parked until the genuine handoff is confirmed.
3. Write/update the exact blocker row with the allowed status, precise type, `Retry Eligible = Manual Review`, `Parked Tab = Yes`, and one-step `Next Action`.
4. Continue the batch in another working tab. Never navigate, reload destructively, reuse, or close the parked tab for another role.
5. Before resuming, match the live tab by exact requisition ID or canonical URL. Do not rebuild a usable parked application.
6. After Yaswanth completes the handoff, inspect visible committed controls, verify exact portal/Gmail proof, update the outcome, and set `Parked Tab = No`.

Keep at most five parked handoff tabs. If the cap is reached, record the blocker without parking another tab and continue. Never park closed, stale, outside-filter, no-sponsorship, salary-ineligible, duplicate, staffing/vendor, low-quality, or poor-fit roles.

## Proof Pending Recovery

When submission status is ambiguous:

1. Do not click submit repeatedly.
2. Inspect the URL, success/received text, application ID, candidate portal, and exact Gmail receipt.
3. If proof appears, convert the blocker to the proof-backed lane outcome.
4. If no proof appears, retain `Proof Pending` until one safe reconciliation path is available; never count it toward the target.

## Abandonment Check

Before finalizing a non-user-only blocker, confirm that the blocker was diagnosed, two distinct paths or the time budget were used, proof was checked when submission may have occurred, and tracker evidence is complete. Then select the next role immediately; do not ask whether to continue.
