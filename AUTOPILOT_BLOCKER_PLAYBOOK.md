# Autopilot Blocker Playbook

Use this during AI and SDE job-application runs when a form, portal, custom field, upload widget, account flow, Chrome session, or spam check blocks progress.

Primary rule:

- Keep applying. Do not stop the whole run for one blocked role.
- Recovery first, blocker second. Try the relevant recovery ladder before marking a role blocked.
- No first-attempt technical blockers. Except CAPTCHA/security/legal/manual/hard-eligibility boundaries, `Blocked - ATS` and `Blocked - Other` require at least 2 serious attempts and at least 2 distinct recovery paths.
- For high-fit roles, spend up to 3 serious attempts when the remaining issue is account/login, upload fallback, direct ATS routing, hidden required fields, or Chrome recovery.
- Do not retry the same failed click/action more than twice; switch paths instead.
- For blocker types 2-7, use `AGENT_RECOVERY_TRAINING.md` before assigning a final tracker status.
- For ATS-specific failures, use `ATS_RETRY_MATRIX.md` before assigning `Blocked - ATS`.
- Real blockers must stay in the AI/SDE trackers after recovery fails. Keep the status simple and put the exact failed recovery path in `notes`.
- For `Blocked - ATS` and `Blocked - Other`, `Attempt Count`, `Recovery Tried`, and `Next Retry Path` are required. `Learning Candidate` is required when the blocker reveals reusable ATS/company behavior.
- Both trackers use the canonical schema in `TRACKER_SCHEMA.md`. Fill what is derivable quickly, but do not create new blockers from blank helper fields.
- If a job application sends an email security code to the job Gmail, retrieve it from `yaswanthmuppalla2025@gmail.com` using the Gmail connector or the `Job Apply - Yaswanth` Chrome profile and continue the form.
- If normal ATS account creation is required, create the account with the job email and user-provided live credential, then continue the form.
- If an official ATS requires last-4 SSN, DOB, or month/day DOB, use `PRIVATE_APPLICATION_FIELDS.md` and never record the private values.
- If CAPTCHA, external exercise, security prompt, or manual confirmation blocks the form, log the issue in tracker notes, mark the role clearly, and keep moving to the next role.
- If the blocker cannot be completed truthfully or safely by Codex, mark the role with a clear blocker status and continue to the next role.
- Do not treat ordinary N/A, optional fields, alternate wording, or fields not explicitly listed in `APPLICATION_PLAN.md` as blockers when they can be answered truthfully from the resume, JD, company context, tracker notes, or common application meaning.
- Do not bypass CAPTCHA, spam checks, access controls, security controls, paywalls, or platform anti-abuse systems.
- Do not invent credentials, certifications, clearance, work authorization, citizenship, employment facts, salary history, references, or legal attestations.

## Status Source

Use `TRACKER_SCHEMA.md` as the single source of truth for status labels. Do not create new statuses in this playbook. Keep proof, skip reasons, and blocker details in `Confirmation Proof`, `Recovery Tried`, `Next Retry Path`, and `Notes`.

## Preflight Before Filling

Before spending time on a form:

1. Run `RECENCY_PREFLIGHT.md`; it owns freshness, quality, location, and duplicate gates.
2. Check the JD and form for sponsorship language.
3. Strictly skip if the employer says no sponsorship, no immigration support, no H-1B transfer, or no current/future sponsorship.
4. Strictly skip if citizenship, green card, U.S.-person status, or clearance is mandatory.
5. Use the correct resume lane: AI resume for AI roles, SDE resume for SDE/backend roles.

## Recovery Rules

Use these ladders before assigning a final blocker status. For every recovery attempt, keep the role state in the tracker rather than relying on browser tabs.

### Blocked Row Proof Requirement

Do not write `Blocked - ATS` or `Blocked - Other` unless the tracker row can prove:

1. The first failure was diagnosed from visible validation, page state, or browser behavior.
2. At least 2 serious attempts were made, unless a hard boundary appeared immediately.
3. At least 2 distinct recovery paths were tried, such as reload/refill, direct ATS URL, embedded ATS URL, official company route, PDF -> DOCX, text resume fallback, account reset, Gmail code, or Chrome reconnect.
4. Gmail was checked when submission might already have happened.
5. `Attempt Count`, `Recovery Tried`, `Next Retry Path`, and `Notes` explain what happened without credentials, codes, or private identity values.

### Chrome / Browser Recovery

1. Reuse one active application tab where possible.
2. Close stale completed/research/duplicate/expired tabs after logging outcomes.
3. Keep no more than 3-5 live tabs: active application, discovery/source, Gmail/security-code, and at most one temporary verification tab.
4. If Chrome control slows or times out, reduce tab pressure first.
5. Reconnect to the `Job Apply - Yaswanth` extension instance by profile metadata.
6. If a tab is stale or form state is lost, reopen the official application URL from the tracker and restart that role with attempt count incremented.
7. If Chrome itself must be restarted, preserve tracker state first, close/reopen the `Job Apply - Yaswanth` profile, reconnect, and resume from the next actionable row.

### Judgment Fallback For Unlisted Fields

Use judgment and keep moving when a field is ordinary but not explicitly listed in the plan.

Allowed fallback behavior:

1. Use the resume and JD to answer ordinary experience, skills, project, location, role-interest, and availability questions.
2. Use `ANSWER_BANK.md` for long-answer fields, then tailor to the JD.
3. Use `N/A` or `Not applicable` for fields that are irrelevant or do not apply.
4. Use the closest truthful dropdown option when the exact default is not available.
5. Leave optional irrelevant fields blank when the form allows it.
6. Use conservative resume-based values for years of experience; do not inflate beyond the resume.

Do not block unless the answer would require guessing or inventing a material fact, legal status, credential, clearance, certification, salary history, reference, or employer-confidential detail.

### CAPTCHA Or Spam Check

- Do not bypass.
- Do not retry aggressively.
- Record in tracker notes that the role needs manual CAPTCHA/spam-check clearance.
- Mark `Blocked - CAPTCHA` and continue to the next role.
- If there are many CAPTCHA blocks, slow the run down, use fewer tabs, and prefer direct official company/ATS links.

### Email Security Code

- Search `yaswanthmuppalla2025@gmail.com` for the newest code from the company, ATS, or domain shown on the application page.
- Use the code only for the active job application flow that requested it.
- Do not read unrelated mailbox content beyond what is needed to identify the relevant code.
- If the code expires, request one fresh code when the form supports it.
- If the code is missing or the page still fails after entry and one fresh-code attempt, mark `Blocked - ATS`, explain the email-code issue in `notes`, and continue.

### External Exercise Or Manual Confirmation

- Do not invent exercise URLs, assessment results, portfolio artifacts, recruiter contacts, or manual confirmation details.
- Log the company, role, and exact requested manual step in the tracker and morning summary.
- Mark `Blocked - Other`, explain the manual step in `notes`, and continue the batch.

### Broken ATS Flow

Try:

1. Reload once.
2. Remove tracking parameters from the URL.
3. Open the official company careers page and navigate to the role again.
4. Try the direct ATS application link if available.
5. Try an embedded ATS URL if the company button is broken.
6. Run a required-widget sweep: select phone country `+1` before the local number, typeahead-selected location, resume file card/manual text, EEO dropdowns, yes/no radios, acknowledgements, hidden required selectors; verify the selected value actually stuck, especially the committed `+1` chip/value. If the phone widget commits another country code, reopen it and correct to United States / `+1` before calling the ATS broken.
7. Preserve entered data only if the page is stable.

If still broken after the minimum recovery budget, mark `Blocked - ATS` and continue.

### Resume Upload Failure

Try:

1. Upload the PDF first.
2. If PDF fails or parsing looks poor, try the DOCX.
3. Use the visible upload button.
4. Use the underlying file input if it is accessible.
5. Reload the application page once and retry.
6. If `Enter manually`, `Apply manually`, or resume text entry is available, paste the matching lane `.txt` resume fallback and continue.
7. Try the official company/ATS link instead of an aggregator or embedded form.

If file chooser/upload still fails after the minimum recovery budget, mark `Blocked - Other`, explain the upload failure and exact controls tried in `notes`, and continue.

### Login Or Account Wall

Use this as an ordered protocol, not a suggestion:

1. Use only the `Job Apply - Yaswanth` Chrome profile.
2. If the logged-in session is available, continue the form.
3. If normal account creation is required, create the account with the job email and user-provided live credential.
4. If the site says an account exists, try normal sign-in once with the job email and live credential.
5. If sign-in fails and password reset is available through the job Gmail, request reset and set the same live credential.
6. If the account sends an email verification code or link, retrieve the newest relevant Gmail message and continue.
7. After account creation, sign-in, or reset, return to the exact official job application URL from the tracker, not only the careers homepage.
8. If the portal requires profile setup before the job form, complete only required profile sections from the resume/defaults and return to the job.
9. If the account wall requires CAPTCHA, a security prompt, OTP outside the job Gmail, a password reset that cannot be completed, or another non-AI challenge after the protocol above, mark `Blocked - CAPTCHA` or `Blocked - Other`, explain the issue in `notes`, and continue.
10. Do not switch to personal/dev profiles. If `Job Apply - Yaswanth` remains unavailable after reconnect/reopen, continue discovery-only queue building with official apply links and note the profile issue in the morning summary.

### Risky Custom Fields

Answer without asking if the answer can be truthfully derived from:

- `APPLICATION_PLAN.md`
- `ANSWER_BANK.md`
- AI or SDE resume
- Job description
- Company context
- Existing tracker notes

Skip the role when a required field reveals a true eligibility or fit mismatch. Use `Blocked - ATS` only if the required field cannot be truthfully derived from the resume, JD, defaults, answer bank, or common application meaning, and would require guessing or inventing:

- A certification, license, clearance, degree, or credential not listed.
- Citizenship, green card, U.S.-person, or no-sponsorship status.
- People-management claims not supported by the resume.
- Legal attestations that are not covered by the plan.
- Exact private salary history or employer-confidential facts not provided.
- References or contact names not provided.

### Private Identity Fields

- Standard official ATS fields for last-4 SSN, DOB, and month/day DOB are not blockers now that `PRIVATE_APPLICATION_FIELDS.md` is available.
- Use private identity values only inside the official ATS/company form.
- Never write private identity values into tracker notes, learning-loop entries, screenshots, result JSON, or morning summaries.
- If the site asks for full SSN, passport number, bank/payment information, or suspicious identity collection beyond normal ATS verification, mark the role `Blocked - ATS` or security blocker and continue.

### Duplicate Or Already Applied

- Before filling a form, scan the AI, SDE, and active sub-tracker `Role` columns for the normalized role title.
- If the same company has the same normalized role title, skip before filling.
- If the same official application URL or job id already exists, skip before filling.
- If only the role title matches but the company is different, do not skip automatically; common titles are not duplicates by themselves.
- If the ATS says already applied, mark `Already Applied`.
- Search Gmail for company/application confirmation if useful.
- Do not attempt duplicate submissions.

## Gmail Confirmation Watch

After each submitted application, keep an eye on Gmail for proof that the submission actually happened.

Use the connected Gmail tool when available. If not available, use the `Job Apply - Yaswanth` Chrome profile and Gmail search.

Suggested Gmail searches:

- `newer_than:2d ("thank you for applying" OR "application received" OR "we received your application" OR "your application has been received")`
- `newer_than:2d ("application" "received" "Yaswanth")`
- `newer_than:2d from:(greenhouse.io OR lever.co OR ashbyhq.com OR workday.com OR smartrecruiters.com)`
- `newer_than:7d ("thank you for your interest" OR "we have received your application" OR "your application to")`

Confirmation handling:

- If Gmail confirmation is found, keep tracker status as `Submitted` and put the Gmail proof in `Confirmation Proof`.
- If only the ATS screen confirms submission, keep tracker status as `Submitted` and put the screen proof in `Confirmation Proof`.
- If submission likely completed but no proof is visible, keep tracker status as `Submitted` and record the uncertainty in `Notes`.
- If rejection or recruiter follow-up appears, update the tracker immediately.
- Do not send email replies, delete emails, archive emails, or change Gmail labels unless Yaswanth explicitly asks.

## Morning Review

At the end of an overnight run, summarize:

- Submitted count.
- Email-confirmed count.
- Screen-confirmed count.
- Unconfirmed submissions.
- Skipped no-sponsorship/ineligible roles.
- CAPTCHA and ATS blockers, with exact details kept in tracker notes.
- Best roles still worth manual retry.
- Gmail replies or recruiter messages that need attention.
