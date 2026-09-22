# ATS Retry Matrix

Open only the section matching the current platform after using the generic algorithm in `AUTOPILOT_BLOCKER_PLAYBOOK.md`. This file contains reusable ATS mechanics—not batch policy, candidate legal answers, hard-coded company retries, or reporting rules.

For every ATS, verify the official requisition is still open, inspect committed values rather than typed text, check proof before resubmitting, and stay within the shared recovery budget.

## Greenhouse

Common failures: segmented email-code boxes duplicate characters; upload lacks a file card; EEO labels differ; submit returns to the form; invisible reCAPTCHA/anti-abuse appears.

- Prefer the official `job-boards.greenhouse.io` or company-embedded application URL.
- Confirm the resume attachment card, not merely the filename field.
- Select exact EEO option text and verify the underlying control.
- After submit/code entry, inspect URL and body first. `/confirmation`, `Thank you for applying`, or `application received` is proof even if stale code text remains.
- Use only the newest job-Gmail code. Clear every segment, enter one character per box, and verify the joined value.
- If the code widget remains corrupted after two cleanup methods, reload/refill the exact role once rather than mutating the same boxes repeatedly.
- A visible CAPTCHA/anti-abuse challenge is a user-only boundary.

## Ashby

Common failures: radio text looks selected while the input is unchecked; coordinate clicks miss submit; form resets; possible-spam page appears.

- Select the underlying radio/checkbox and verify checked state.
- Use the real visible/accessibility submit control so the page scrolls to it.
- If fields reset, refill once and verify hidden selected values before one safe resubmit.
- On possible-spam, check URL, page text, portal state, and Gmail. If the anti-abuse state persists, use the CAPTCHA outcome.

## Lever

Common failures: location is typed but not selected; submit remains on `/apply`; hCaptcha appears.

- Choose the visible location suggestion and verify a committed location token/value.
- Confirm resume attachment/manual text and required custom questions.
- If no challenge appears and proof is absent, retry once through the cleaned/direct Lever URL and reselect required controls.
- A visible hCaptcha or visual challenge is a user-only boundary.

## Workday

Common failures: account flow interrupts the role; candidate home replaces the application; upload/parser resets profile; source/phone/date/review widgets look filled but remain invalid.

- Complete the authentication ladder, then return to the exact requisition URL—not the careers home.
- Prefer `Apply Manually` when resume parsing is unstable; use the visible upload control and verify the attachment.
- Complete hierarchical source controls exactly. For LinkedIn discovery, choose the visible social-media hierarchy offered by that tenant and verify the selected pill; typed search text is not committed.
- Verify phone includes `United States (+1)`, location/source tokens are selected, segmented dates render fully, and Review shows every required answer.
- Resume parsing may create a false current `Founder` role from OmInsights; delete it and keep OmInsights only as a portfolio project/website.
- Use `Bachelor of Technology`; when unavailable, `Bachelor of Engineering` is the closest truthful degree. Leave an undocumented field of study blank/`No Response`.
- External-applicant `Employee ID (if applicable)` stays blank. Clear parser-filled text, blur/save, and verify Review shows `No Response`.
- Use `PRIVATE_APPLICATION_FIELDS.md` for exact private/identity/legal selections without copying values elsewhere. Documented applicant facts may be entered autonomously; do not wait for Yaswanth merely because Workday calls them applicant information.

## Oracle / Taleo

Common failures: verification boxes ignore normal fill; question order and radio IDs change.

- Clear boxes and type the newest full code into the first box when auto-advance supports it.
- Request at most one fresh code after expiry and use only the newest email.
- Map yes/no controls by nearby question text, visible label, role, and `aria-pressed`; never rely on fixed index or dynamic ID.

## SmartRecruiters / iCIMS / Company-Native

Common failures: account loop; required source/referral; disabled submit until profile sections are reviewed.

- Complete the shared authentication ladder and return to the same role URL.
- Use the truthful source—`LinkedIn`, `Company careers page`, or `Not referred`; never invent a referral.
- Open every required accordion/profile section and verify its completed state.
- Correct required parser fields manually instead of polishing optional profile fields.

## Workable

Common failures: upload timeout; inverted sponsorship wording; optional upload blocks progress.

- Try PDF, then DOCX. If upload is optional, use complete profile/manual information instead.
- For wording such as `authorized without requiring sponsorship`, inspect the exact question and radio value; do not fuzzy-match `Yes`/`No` from keywords.
- If required upload has no visible/manual fallback after the shared budget, record exact controls tried.

## Indeed And Aggregator Forms

Common failures: expired reCAPTCHA; qualification word check; official ATS route hidden.

- Prefer the official company/ATS route whenever available.
- Complete qualification/review questions exactly and leave optional marketing alerts/calls/text unchecked unless the profile default says otherwise.
- An expired or visible reCAPTCHA/visual challenge is a user-only boundary.

## Phenom / SuccessFactors

Common failures: stale required error after selection; controlled registration text does not commit; account flow interrupts; attachment remains `Uploading...`.

- Toggle a stale dropdown to another option and back, blur, then verify the intended committed value.
- Enter controlled username/password fields sequentially when bulk fill displays but does not commit text.
- Complete authentication and return to the exact requisition.
- If upload remains `Uploading...`, reload the exact application once and verify the matching attachment card before refilling.
- After submit, inspect active processing/navigation and confirmation proof before clicking again.

## Google Careers

Common failure: uploading another lane resume with profile auto-fill enabled overwrites accurate saved employment, education, or location.

- When the saved applicant profile is accurate, disable `Fill out your application with your resume information` before uploading the selected lane resume.
- If parsing already overwrote the profile, exit without saving the bad changes, restore the accurate profile, upload with auto-fill disabled, and verify the visible filename plus affected sections.

## LinkedIn Easy Apply

Common failures: hidden required steps, stale saved answers, upload mismatch, or final anti-abuse challenge.

- Verify the exact requisition and company before using Easy Apply; prefer the official employer route when available.
- Re-read saved sponsorship, location, phone, and resume answers; old LinkedIn defaults do not override current batch facts.
- Verify the attached filename and every review-page required control.
- A visible anti-abuse/CAPTCHA challenge follows the user-only handoff rule.

## Rotation After Anti-Abuse

After repeated possible-spam or visual-challenge events, immediately rotate to another ATS/company/source cluster. Do not insert artificial human-like delays, evade anti-abuse systems, or let one platform halt discovery and applications elsewhere.
