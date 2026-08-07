# ATS Retry Matrix

Use this when a specific ATS behaves badly. The goal is to recover and submit when truthful, not to mark blockers too early.

## Universal Sequence

1. Verify official open role and sponsorship compatibility.
2. Fill required fields from plan, answer bank, resume, JD, and safe judgment.
3. Run the pre-submit required-widget sweep.
4. Submit once.
5. After any submit, email-code, or security-code attempt, inspect the current URL, title, visible body text, portal state, and Gmail proof before retrying the same widget. Confirmation/thanks/received proof wins over stale validation text.
6. If no confirmation, read visible validation errors and inspect selected values.
7. Try the ATS-specific recovery below.
8. Try a second distinct recovery path before blocking, such as direct ATS URL, embedded URL, official company route, reload/refill, PDF -> DOCX, text resume fallback, or Chrome reconnect. For login walls, complete the full session/saved-credential -> sign-in/signup -> job-Gmail reset/code -> exact-job return -> clean-route ladder in `AUTOPILOT_BLOCKER_PLAYBOOK.md`.
9. For high-fit roles, use a third serious attempt when a safe path remains.
10. Check Gmail before marking failed.
11. Add a real `Blockers` row only after recovery fails, with `Attempt Count`, `Recovery Tried`, and `Next Action` filled.

## Greenhouse

Common issues:

- Email/security code boxes duplicate characters.
- Generic submit or processing error may actually be waiting for an email-code verification step.
- Resume upload looks complete but no file card appears.
- EEO dropdown labels differ by company.
- Invisible reCAPTCHA leaves the form on the same page.

Recovery:

- Use official `job-boards.greenhouse.io` or embedded `job_app` URL when company button fails.
- Confirm resume file card or use manual resume entry.
- Use exact EEO option text; avoid fuzzy dropdown matching.
- After any submit or security-code attempt, first inspect the current URL, page title, and visible body text. If Greenhouse is on `/confirmation` and shows `Thank you for applying` or `Your application has been received`, stop retrying the code widget and record the role as screen-confirmed submitted.
- For Greenhouse security codes, treat the Gmail-delivered code as recoverable ATS verification, not CAPTCHA. Retrieve the newest relevant code from job Gmail, clear all boxes, type one character per box, and if duplicate characters appear, press End then Backspace once in each box before verifying the joined code.
- If the segmented code widget becomes polluted with doubled text, stale tail text, or disabled-submit state after two cleanup paths, reload/refill the same official role once instead of continuing to mutate the corrupted widget. Re-check for `/confirmation` before redoing the code step.
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

- Create/sign in using the job email and the credential securely saved in the dedicated profile or supplied at runtime.
- Use Gmail OTP codes from the newest relevant Workday sender.
- Use `PRIVATE_APPLICATION_FIELDS.md` for official Workday last-4 SSN, DOB, or month/day DOB fields; never record the private values.
- Prefer `Apply Manually` if upload is unstable.
- Complete source fields exactly, including hierarchical source choices when present.
- Verify review page shows phone `+1`, contact method, sponsorship answers, and required profile sections before submit.
- After account creation, navigate back to the exact job application URL, not only the careers home.
- If an account exists but login fails, use password reset through the job Gmail when available, set the secure runtime credential, then return to the exact job URL.
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

- Create a normal account using the job email and the credential securely saved in the dedicated profile or supplied at runtime.
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
- Create/sign in using the job email and secure saved/runtime credential, then return to the exact role URL.
- If the page remains technically impossible after one clean reload/refill, mark `Blocked - ATS`.

## Source Mixing To Reduce CAPTCHA

- Avoid long consecutive runs on the same ATS or company.
- Mix Ashby, Greenhouse, Lever, Workday, SmartRecruiters, native portals, LinkedIn-discovered official links, and Indeed-discovered official links.
- Keep one active apply tab and low tab count.
- Prefer official company/ATS URLs over aggregator iframes.
- Slow down after repeated possible-spam or hCaptcha events and move to a different ATS/company cluster.

## Dynamic Retry Ranking

Read the current `Blockers` sheet instead of maintaining company names here. A row is retryable only when the exact job is not already submitted, the official posting remains open and recency-eligible under `RECENCY_PREFLIGHT.md`, fit is still high/strong, `Retry Eligible = Yes` (or `Manual Review` after the required human action is known complete), fewer than 3 serious attempts have been exhausted, and a distinct recovery path remains.

1. Prioritize recoverable job-Gmail code, account, upload, required-widget, and validation rows for high-fit roles.
2. Then retry other `Blocked - ATS` or `Blocked - Other` rows whose `Recovery Tried` and `Next Action` identify a new ATS-specific path from this matrix.
3. Skip rows marked `No`, `Expired`, closed, stale, already submitted, explicit company cooldown, or exhausted without a new safe path.
4. Do not spend agent retries on unresolved visual CAPTCHA/anti-abuse rows. Keep useful forms parked for Yaswanth, then retry only after the challenge is known resolved or a clean official route avoids it.
5. Re-run duplicate, company-spread, recency, fit, sponsorship, and location preflight immediately before retry submission.
