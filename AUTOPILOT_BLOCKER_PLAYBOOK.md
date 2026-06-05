# Autopilot Blocker Playbook

Use this as the single blocker/recovery playbook for AI, SDE, and LinkedIn application runs.

The goal is Aggressive Autopilot with Hard Stop Only: recover and submit fitting roles whenever the form can be completed truthfully. A blocker is a row outcome after recovery fails, not a reason to stop the batch.

## Core Rules

- Keep applying. One blocked role must not pause the run.
- Recovery first, blocker second.
- Do not mark `Blocked - ATS` or `Blocked - Other` on the first technical failure unless a true hard boundary appears immediately.
- For non-CAPTCHA technical blockers, require at least 2 serious attempts and 2 distinct recovery paths before blocking.
- For high-fit roles, use up to 3 serious attempts when safe recovery paths remain.
- Do not repeat the same failed click, selector, upload, or submit action more than twice. Switch recovery paths.
- Use `ATS_RETRY_MATRIX.md` for ATS-specific fixes before assigning `Blocked - ATS`.
- Use `TRACKER_SCHEMA.md` as the only source of truth for status labels.
- Put proof and exact blocker details in `Confirmation Proof`, `Recovery Tried`, `Next Action`, and `Notes`, not in custom status labels.
- Real blockers must stay in the `Blockers` sheet after recovery fails so Yaswanth can review patterns and improve the system.
- Blank helper fields, optional fields, N/A fields, unfamiliar wording, or unlisted ordinary questions are not blockers when the answer can be derived truthfully from the resume, JD, `ANSWER_BANK.md`, `APPLICATION_PLAN.md`, tracker notes, or common application meaning.

## Hard Stops

Mark the role, record the exact reason, close or finalize the tab, and continue the batch:

- CAPTCHA, hCaptcha, visual puzzle, anti-abuse page, security challenge, or OTP outside job Gmail.
- Explicit no-sponsorship, no H-1B transfer, citizen-only, green-card-only, U.S.-person-only, ITAR-only, government-only, or clearance-required eligibility.
- Payment/request-for-money, suspicious identity harvesting, full SSN, bank/payment info, passport, or unrelated private identity collection.
- Required manual exercise, take-home, video, portfolio artifact, recruiter contact, referral contact, or long external artifact.
- Legal attestation or applicant-authored/no-AI requirement that cannot be completed truthfully by an agent.
- Required material fact not available from the resume, JD, answer bank, plan, private-field file, or safe inference.
- Portal remains technically impossible after the required recovery budget.

Do not bypass CAPTCHA, spam checks, security controls, paywalls, or platform anti-abuse systems.

## Outcome Mapping

| Situation | Correct Outcome |
|---|---|
| Gmail receipt found | `Submitted`; put Gmail proof in `Confirmation Proof` and fill `Gmail Checked At` |
| Success page, application ID, or clear final message shown | `Submitted`; put screen/app ID proof in `Confirmation Proof` |
| Submit likely completed but proof is weak | `Submitted`; record proof gap in `Notes`; check Gmail once |
| CAPTCHA/security challenge blocks form | `Blocked - CAPTCHA`; park high-fit filled forms for Yaswanth when useful |
| ATS submit, validation, or broken portal still fails after recovery | `Blocked - ATS`; fill `Attempt Count`, `Recovery Tried`, `Next Action`, and exact notes |
| Required resume upload cannot be completed after recovery | `Blocked - Other`; record exact upload controls tried |
| Account/login/email-auth wall cannot be completed after recovery | `Blocked - Other` or `Blocked - CAPTCHA`; record exact wall |
| Manual exercise, external artifact, risky legal field, or missing required fact | `Blocked - Other`; record exact requested item |
| No-sponsorship, stale/closed, fit mismatch, duplicate, staffing/vendor, or strategic skip | Skip without broad skip logging |
| Already applied with proof | `Already Applied`; record proof in `AI` or `SDE` |

## Recovery Budget Proof

Before writing `Blocked - ATS` or `Blocked - Other`, the tracker row must prove:

1. The blocker type was identified from visible validation, page state, account state, or browser behavior.
2. At least 2 serious attempts were made, unless a hard boundary appeared immediately.
3. At least 2 distinct recovery paths were tried.
4. Gmail was checked when a submission might already have happened.
5. `Attempt Count`, `Recovery Tried`, `Next Action`, and `Notes` explain the issue without credentials, codes, or private identity values.

Examples of distinct recovery paths: reload/refill, cleaned URL, direct ATS URL, embedded ATS URL, official company route, required-widget sweep, PDF -> DOCX upload, `.txt` resume fallback, account creation, password reset through Gmail, fresh email code, Chrome reconnect, or restarting from the exact job URL.

## CAPTCHA Parking

Do not bypass CAPTCHA, hCaptcha, visual puzzles, anti-abuse pages, spam checks, or security challenges.

For high-fit roles that passed the 0-15 day recency gate, sponsorship check, quality gate, location priority, and duplicate check:

1. Fill every truthful field possible.
2. Stop at the CAPTCHA/security challenge.
3. Leave the tab open for Yaswanth.
4. Record a `Blockers` row:
   - `Status`: `Blocked - CAPTCHA`
   - `Blocker Type`: `CAPTCHA Parked`
   - `Retry Eligible`: `Manual Review`
   - `Parked Tab`: `Yes`
   - `Next Action`: `Yaswanth solve CAPTCHA, then submit/resume from same tab`
   - `Notes`: `Form filled; CAPTCHA parked for human review`
5. Continue applying in another tab.

Keep at most 5 parked CAPTCHA tabs open. If 5 are already parked, record the CAPTCHA without parking another tab and continue. Never park stale, no-sponsorship, duplicate, low-quality staffing/vendor, or poor-fit roles.

## Blocker Type Recovery

### ATS Submit / Validation / No Confirmation

Recognize:

- Submit button stays disabled.
- Form returns to the same page after submit.
- Validation remains even though the field looks filled.
- Greenhouse, Ashby, Lever, Workday, or another ATS reloads without success text.
- Security-code step completes but no confirmation appears.

Recovery:

1. Stop blind clicking and read the visible validation text.
2. Run a required-widget sweep: phone country `United States/+1`, committed location typeahead, resume file card or manual text, EEO dropdowns, yes/no radios, custom pills, acknowledgements, hidden required selectors, and selected values that actually stuck.
3. Click the real submit button after scrolling it into view.
4. Reload once and refill from resume, answer bank, and JD if the form loops.
5. Try alternate route: cleaned URL, official company careers page, direct ATS application URL, or embedded ATS form.
6. Check Gmail if a submit may have completed.
7. If still no proof after the recovery budget, use `Blocked - ATS`.

### Resume Upload / File Chooser Failure

Recovery:

1. Upload the lane PDF first.
2. If PDF fails or parses poorly, try DOCX.
3. Use the visible upload/attach/import control.
4. Try the accessible file input when available.
5. If `Enter manually`, `Apply manually`, or resume text entry exists, paste the matching lane `.txt` resume and continue.
6. If upload is optional and the form has enough profile, LinkedIn, summary, and manual data, submit without upload only when the ATS allows it.
7. Try the official company/ATS route instead of an aggregator or broken embed.
8. If required upload still cannot work after recovery, use `Blocked - Other`.

### Account / Login / Email-Auth Wall

Use this ordered protocol:

1. Use only the `Job Apply - Yaswanth` Chrome profile.
2. If a logged-in session exists, continue the form.
3. If normal account creation is required, create the account with the job email and user-provided live credential.
4. If the site says an account exists, try normal sign-in once with the job email and live credential.
5. If sign-in fails and password reset is available through job Gmail, reset with the same live credential.
6. Retrieve only the newest relevant Gmail code or link for the active application.
7. After account creation, sign-in, or reset, return to the exact official job application URL, not just the careers homepage.
8. If the portal requires profile setup before the job form, complete only required profile sections from resume/defaults and return to the job.
9. If CAPTCHA, security prompt, OTP outside Gmail, inaccessible reset, or another non-AI challenge blocks the account, use `Blocked - CAPTCHA` or `Blocked - Other`.

Never store passwords, codes, or private email content in trackers, docs, screenshots, result JSON, or learning notes.

### Email Security Code

- Search `yaswanthmuppalla2025@gmail.com` only for the active company, ATS, or domain.
- Use the code only for the active job flow.
- If the code expires, request one fresh code when supported.
- If the code is missing or still fails after one fresh-code attempt, use `Blocked - ATS` and record the email-code issue.

### Manual Exercise / External Artifact

- If optional, leave blank or use `N/A` only when accepted.
- If required, do not invent exercise URLs, assessment results, portfolio artifacts, recruiter contacts, references, publications, or manual confirmations.
- If the built-in assessment can be completed after submission, submit only if the current form does not require it first.
- Otherwise use `Blocked - Other` with the exact requested artifact.

### Legal / User-Authored Attestation Risk

- Standard ATS privacy notices, EEO acknowledgements, and application-processing consent may be accepted when ordinary.
- Do not submit generated prose under an explicit applicant-authored/no-AI attestation.
- Do not click through unusual legal agreements solely to increase submissions.
- Do not claim citizenship, clearance, green card, no-sponsorship status, certifications, licenses, references, or salary history not documented.
- Use `Blocked - Other` when a required legal/private fact cannot be completed truthfully.

### Private Identity Fields

- Standard official ATS fields for last-4 SSN, DOB, and month/day DOB are not blockers when the page is an official company/ATS application.
- Use `PRIVATE_APPLICATION_FIELDS.md` only inside the live official form.
- In tracker notes, write only generic wording such as `required identity fields completed from private application defaults`.
- Never write private identity values into tracker rows, notes, learning entries, screenshots, result JSON, morning summaries, or GitHub.
- If the site asks for full SSN, passport, bank/payment data, payment, or suspicious identity collection, do not complete it.

### Duplicate / Already Applied / Strategic Cap

- Before filling, scan `Company`, `Role`, and `Application URL` across the `AI`, `SDE`, and `Blockers` sheets in `JOB_APPLICATION_TRACKER.xlsx`, plus official job IDs when visible.
- Same company + same normalized role title or same official job ID/application URL means skip or `Already Applied`.
- Common role title at a different company is not a duplicate.
- If the ATS says already applied, mark `Already Applied`.
- If a company has an application cap, submit the strongest-fit roles first and skip lower-fit roles.
- Do not attempt duplicate submissions.

## Chrome Recovery

- Reuse one active application tab when possible.
- Keep at most 3-5 live tabs: active application, discovery/source, Gmail/security code, and one temporary verification tab.
- Close completed, stale, duplicate, expired, and research tabs after logging outcomes.
- If Chrome control slows or times out, reduce tab pressure first.
- If a tab is stale or form state is lost, reopen the official application URL from the tracker and increment attempt count.
- If Chrome must restart, preserve tracker state first, close/reopen the `Job Apply - Yaswanth` profile, reconnect, and resume from the next actionable row.
- Do not switch to personal/dev profiles.

## Gmail Confirmation Watch

After each submitted application, check Gmail for proof when possible.

Suggested searches:

- `newer_than:2d ("thank you for applying" OR "application received" OR "we received your application" OR "your application has been received")`
- `newer_than:2d ("application" "received" "Yaswanth")`
- `newer_than:2d from:(greenhouse.io OR lever.co OR ashbyhq.com OR workday.com OR smartrecruiters.com)`
- `newer_than:7d ("thank you for your interest" OR "we have received your application" OR "your application to")`

Handling:

- Gmail confirmation found: keep `Submitted`, put Gmail proof in `Confirmation Proof`, and fill `Gmail Checked At`.
- Screen confirmation only: keep `Submitted`, put screen proof in `Confirmation Proof`.
- Weak proof but likely submitted: keep `Submitted`, record the uncertainty in `Notes`.
- Rejection or recruiter follow-up appears: update tracker immediately.
- Do not send replies, delete emails, archive emails, or change labels unless Yaswanth explicitly asks.

## Agent Self-Check Before Abandoning A Role

Before abandoning a non-CAPTCHA role, confirm:

1. I identified the blocker type.
2. I used this playbook and `ATS_RETRY_MATRIX.md` when ATS-specific.
3. I made at least 2 serious attempts and tried at least 2 distinct recovery paths unless a true hard boundary appeared.
4. I checked Gmail when submission might have happened.
5. I did not invent legal, credential, private, salary, reference, or employer-confidential facts.
6. If official ATS identity fields were required, I used `PRIVATE_APPLICATION_FIELDS.md` and did not record the values.
7. I filled `Attempt Count`, `Recovery Tried`, `Next Action`, and `Notes` for every `Blocked - ATS` or non-CAPTCHA `Blocked - Other`.
8. I added a real blocker only after recovery failed.
9. I closed or finalized the tab and continued the batch.

## Morning Review

At the end of an overnight run, summarize:

- Submitted count.
- Email-confirmed count.
- Screen-confirmed count.
- Unconfirmed submissions.
- Skipped no-sponsorship/ineligible/stale/duplicate/low-quality roles.
- CAPTCHA and ATS blockers, with exact details kept in `Blockers`.
- Parked CAPTCHA tabs waiting for Yaswanth.
- Best roles worth manual retry.
- Gmail replies or recruiter messages that need attention.
