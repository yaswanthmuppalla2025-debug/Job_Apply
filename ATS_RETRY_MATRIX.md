# ATS Retry Matrix

Use this when a specific ATS behaves badly. The goal is to recover and submit when truthful, not to mark blockers too early.

## Universal Sequence

1. Verify official open role and sponsorship compatibility.
2. Fill required fields from plan, answer bank, resume, JD, and safe judgment.
3. Run the pre-submit required-widget sweep.
4. Submit once.
5. If no confirmation, read visible validation errors and inspect selected values.
6. Try the ATS-specific recovery below.
7. Try a second distinct recovery path before blocking, such as direct ATS URL, embedded URL, official company route, reload/refill, PDF -> DOCX, text resume fallback, account reset, Gmail code, or Chrome reconnect.
8. For high-fit roles, use a third serious attempt when a safe path remains.
9. Check Gmail before marking failed.
10. Add a real `Blockers` row only after recovery fails, with `Attempt Count`, `Recovery Tried`, and `Next Action` filled.

## Greenhouse

Common issues:

- Email/security code boxes duplicate characters.
- Resume upload looks complete but no file card appears.
- EEO dropdown labels differ by company.
- Invisible reCAPTCHA leaves the form on the same page.

Recovery:

- Use official `job-boards.greenhouse.io` or embedded `job_app` URL when company button fails.
- Confirm resume file card or use manual resume entry.
- Use exact EEO option text; avoid fuzzy dropdown matching.
- For security codes, clear all boxes first, then type one character per box; if duplicate characters appear, press End then Backspace once in each box and verify the joined code.
- If final submit returns to the form, wait briefly, check Gmail, then reload/refill once before blocking.

## Ashby

Common issues:

- Visible radio text looks selected while the underlying input is not checked.
- Submit button below viewport ignores coordinate clicks.
- Possible-spam page appears after a completed form.
- Fields reset after submit.

Recovery:

- Select underlying radio/checkbox inputs and verify checked state.
- Use the real submit button locator so the page scrolls to the control.
- If possible-spam appears after submit, check Gmail before marking blocked.
- If fields reset, refill once, verify hidden selected values, and resubmit only once.
- If Ashby flags possible spam again, mark `Blocked - CAPTCHA`.
- Do not mark a normal Ashby validation/reset issue as blocked until a second path was tried, such as official Ashby URL, cleaned URL, reload/refill, or hidden-value selection.

## Lever

Common issues:

- Location typeahead text is typed but no selected-location value exists.
- hCaptcha or visual challenge appears before or after final submit.
- Submit remains on `/apply` with no visible errors.

Recovery:

- Choose the visible location suggestion and verify selected value.
- Confirm resume upload/manual text and required custom questions.
- If hCaptcha image/visual challenge appears, mark `Blocked - CAPTCHA`.
- If a token exists but no confirmation appears, click submit once more, check Gmail, then block with exact page state.
- If no visual challenge appears, retry through cleaned/direct Lever URL and reselect location/resume/custom fields before blocking.

## Workday

Common issues:

- Account creation/sign-in interrupts application.
- Resume upload or My Experience resets automation.
- Last-4 SSN, DOB, or month/day DOB identity fields appear.
- Source, phone, and review-page hidden widgets stay invalid.
- The tenant returns to profile pages instead of the job form.

Recovery:

- Create/sign in using the job email and the user-provided live credential.
- Use Gmail OTP codes from the newest relevant Workday sender.
- Use `PRIVATE_APPLICATION_FIELDS.md` for official Workday last-4 SSN, DOB, or month/day DOB fields; never record the private values.
- Prefer `Apply Manually` if upload is unstable.
- Complete source fields exactly, including hierarchical source choices when present.
- Verify review page shows phone `+1`, contact method, sponsorship answers, and required profile sections before submit.
- After account creation, navigate back to the exact job application URL, not only the careers home.
- If an account exists but login fails, use password reset through the job Gmail when available, set the same live credential, then return to the exact job URL.
- If Workday drops into candidate home/profile, reopen the exact job URL after login and continue the active application.

Known retry pattern:

- Lowe's Workday `Sr AI Engineer - Physical AI`: retry now that private identity fields are available. Complete last-4 SSN and DOB/month-day fields from `PRIVATE_APPLICATION_FIELDS.md`, then continue sponsorship and review.

## Oracle / Taleo

Common issues:

- Six-code boxes ignore normal fill.
- Question order changes by role.
- Dynamic radio ids break fixed-index selection.

Recovery:

- Clear code boxes with Backspace/Delete and type the full newest code into the first box if auto-advance works.
- Map yes/no fields by nearby question text and `aria-pressed`, not by index.
- Find radios by visible label or stable values rather than dynamic ids.
- If code expires, request one fresh code and use only the newest email.

## SmartRecruiters / iCIMS / Company Native

Common issues:

- Account wall, login loop, or profile import step.
- Required source/referral fields.
- Disabled submit until every accordion section is reviewed.

Recovery:

- Create normal account using job email and the user-provided live credential.
- Use Gmail verification and return to the same job URL.
- Fill source/referral as `LinkedIn`, `Company careers page`, or `Not referred` when truthful.
- Open every required accordion/profile section and verify completion state.
- If optional resume parsing is poor, manually correct only required fields and continue.
- If login/account loops, use the account protocol from `AUTOPILOT_BLOCKER_PLAYBOOK.md` before blocking.

## Workable

Common issues:

- Resume upload times out.
- Sponsorship wording is inverted, such as `without requiring sponsorship`.
- Optional upload can be bypassed with enough profile data.

Recovery:

- Try PDF then DOCX.
- If upload is optional, submit with full profile/summary/LinkedIn/cover letter when allowed.
- For inverted sponsorship questions, inspect exact radio value; do not fuzzy-match `NO` from question text.
- If required upload has no file/manual fallback, mark `Blocked - Other` with controls tried in `Recovery Tried` and `Notes`.

## Indeed / Aggregator Forms

Common issues:

- Final review submit disabled by expired reCAPTCHA.
- Employer word-check questions block final submit.
- Aggregator flow hides the official ATS link.

Recovery:

- Prefer official company/ATS link when available.
- If using Indeed, complete final review and qualification questions exactly.
- Leave optional job-alert/calls/text boxes unchecked unless required.
- If reCAPTCHA expires or visual challenge appears, mark `Blocked - CAPTCHA`.

## Phenom / SuccessFactors

Common issues:

- Dropdowns show a value while a stale required error remains.
- Final submit temporarily disables before navigating.
- Account creation or sign-in interrupts application.

Recovery:

- Toggle stale dropdowns to another option, then back to the intended option, blur, and continue.
- Wait 10-15 seconds after final submit if the URL is changing or button is disabled.
- Create/sign in using job email and the user-provided live credential and return to the exact role URL.
- If the page remains technically impossible after one clean reload/refill, mark `Blocked - ATS`.

## Source Mixing To Reduce CAPTCHA

- Avoid long consecutive runs on the same ATS or company.
- Mix Ashby, Greenhouse, Lever, Workday, SmartRecruiters, native portals, LinkedIn-discovered official links, and Indeed-discovered official links.
- Keep one active apply tab and low tab count.
- Prefer official company/ATS URLs over aggregator iframes.
- Slow down after repeated possible-spam or hCaptcha events and move to a different ATS/company cluster.

## Current High-Value Retry Queue

Use this as priority guidance when reprocessing current blockers.

Retry only if the role still passes the 0-15 day recency gate in `RECENCY_PREFLIGHT.md` and `Retry Eligible` is not `Expired` in the tracker.

1. Any high-fit `Blocked - ATS` or `Blocked - Other` row with blank/`1` attempt count and a live posting inside the 15-day gate: retry before chasing weak new roles.
2. Lowe's Workday identity-field blocker: retry first using `PRIVATE_APPLICATION_FIELDS.md`.
3. Cargill and JPMorgan account/code flows: retry with job email and the user-provided live credential, Gmail OTP, exact job URL return.
4. Databricks Greenhouse roles: retry direct Greenhouse/embed URL, reselect country/phone hidden values, request/use fresh code, check Gmail.
5. Accompany Health, Chipply, Harvey AI Platform, Citi, Reddit SDE Ads, Scribd, United Hire Staffing, and Vogo upload blockers: retry with file access, PDF -> DOCX -> `.txt` fallback when available.
6. Instacart, Reddit ML, and Scale AI validation loops: required-widget sweep, reload/refill once, direct ATS path, Gmail proof check.
7. CAPTCHA/anti-abuse rows: check Gmail first; if no proof, mark/keep `Blocked - CAPTCHA`, slow down, and switch ATS/company clusters.
8. Perplexity exercise and legal/user-authored attestation rows: keep hard-stopped unless the real artifact or user-authored/legal review exists.
