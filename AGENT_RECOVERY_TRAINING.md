# Agent Recovery Training

Use this file when an application hits blocker types 2-7 from the tracker review. CAPTCHA/anti-abuse remains a true hard stop, but the issues below should be handled with structured recovery before any role is abandoned.

Core rule: diagnose the blocker type, run the matching playbook, use `ATS_RETRY_MATRIX.md` for ATS-specific recovery, then record the outcome correctly. `TRACKER_SCHEMA.md` is the source of truth for status labels. Real blockers must be added to the AI/SDE trackers after recovery fails so Yaswanth can review patterns and improve the system. Do not add weak, first-attempt friction as a blocker.

No first-attempt technical blockers: except CAPTCHA/security/legal/manual/hard-eligibility boundaries, `Blocked - ATS` and `Blocked - Other` require at least 2 serious attempts and at least 2 distinct recovery paths. For high-fit roles, use up to 3 serious attempts when safe paths remain.

Keep tracker status simple: use only the approved labels in `TRACKER_SCHEMA.md`. Put proof quality and exact blocker details in `Gmail Checked At`, `Confirmation Proof`, `Recovery Tried`, `Next Retry Path`, and `Notes`.

When a real blocker is added, use tracker recovery fields if they add signal:

- `Attempt Count`: number of serious attempts on this role.
- `Recovery Tried`: exact ladder steps attempted.
- `Next Retry Path`: next concrete action if worth retrying.
- `Learning Candidate`: `Yes` only for reusable ATS/company patterns.

For `Blocked - ATS` and `Blocked - Other`, `Attempt Count`, `Recovery Tried`, and `Next Retry Path` are required fields, not optional helper fields.

## Outcome Mapping

| Situation | Correct Outcome |
|---|---|
| Gmail receipt found | `Submitted`; put Gmail proof in `Confirmation Proof` and fill `Gmail Checked At` |
| Success page or application ID shown, no Gmail yet | `Submitted`; put screen/app ID proof in `Confirmation Proof` |
| Submit appeared to complete, but proof is weak | `Submitted`; record the proof gap in `Notes` |
| CAPTCHA after completed/final form step | `Blocked - CAPTCHA`; record exact challenge type in `Notes` |
| ATS submit, validation, or broken portal issue after recovery | `Blocked - ATS`; record exact failed ladder in `Recovery Tried` and `Notes` |
| Required upload cannot be completed after recovery | `Blocked - Other`; record exact failed controls in `Recovery Tried` and `Notes` |
| Account/login/email-auth wall cannot be completed after recovery | `Blocked - Other`; record exact account wall in `Recovery Tried` and `Notes` |
| Legal/user-authored attestation, manual exercise, or external artifact required | `Blocked - Other`; record exact requested artifact/agreement in `Notes` |
| No-sponsorship, stale/closed, fit mismatch, duplicate without hard already-applied proof, staffing/vendor, or strategic cap | `Skipped`; record the exact skip reason in `Notes` |
| Already applied with proof | Do not duplicate submit; mark `Already Applied` and record proof in `Confirmation Proof` or `Notes` |

## 2. ATS Submit / Validation / No Confirmation

Recognize it:

- Submit button stays disabled.
- Form returns to the same page after submit.
- Validation error remains even though a field looks filled.
- Greenhouse/Ashby/Lever/Workday page reloads without success text.
- Security-code step completes but no confirmation appears.

Recovery:

1. Stop blind clicking. Read visible validation text and inspect required fields.
2. Run the required-widget sweep:
   - Phone country selector is set to United States / `+1`.
   - Location typeahead has a selected option, not only typed text.
   - Resume shows a file card or manual resume text is present.
   - EEO/self-ID dropdowns use exact visible option text.
   - Yes/no radios and custom pills have the active/checked state.
   - Acknowledgement checkboxes and hidden required selectors are complete.
   - Numeric or generated ids are selected safely, such as `[id="430"]`.
3. Click the real submit button or locator after scrolling it into view.
4. If the form loops, reload once and refill from the resume, answer bank, and JD.
5. Try alternate paths: cleaned URL, official company careers page, direct ATS application URL, embedded ATS form.
6. After any possible submit, check Gmail for a confirmation before calling it failed.
7. If no proof remains after at least 2 serious attempts and 2 distinct recovery paths, add a tracker blocker as `Blocked - ATS` with exact field/error details.

Do not:

- Count a role as submitted with no proof.
- Keep retrying the same broken submit action more than twice.
- Add a blocker before the recovery ladder is complete.

## 3. Resume Upload / File Chooser Failure

Recognize it:

- Upload control does not open a file chooser.
- Resume is required but no file card appears.
- The tab becomes unresponsive after upload.
- ATS says resume missing after upload attempt.

Recovery:

1. Try the lane PDF first.
2. If PDF fails or parses poorly, try the lane DOCX.
3. Click the visible upload/attach/import control.
4. Try the accessible file input if one is present.
5. If `Enter manually`, `Apply manually`, or resume text entry exists, paste from the lane `.txt` fallback file and continue.
6. If upload is optional and the form has enough profile/LinkedIn/summary data, submit without upload only when the ATS allows it.
7. If the role is strong, reload once and retry upload before abandoning.
8. If required upload still has no usable file/manual fallback after at least 2 distinct upload/recovery paths, add a tracker blocker as `Blocked - Other` with exact failed controls.

Do not:

- Stop at the first file chooser timeout.
- Treat upload failure as a user-approval issue.
- Leave a half-filled upload tab open after logging the outcome.

## 4. Manual Exercise / External Artifact Required

Recognize it:

- Perplexity-style exercise/thread URL.
- Take-home assignment link.
- Coding assessment, video, portfolio artifact, recruiter contact, or reference contact.
- Required long exercise that cannot be truthfully generated from the resume/JD/defaults.

Recovery:

1. Check whether the field is optional. If optional, leave blank or use `N/A` only when accepted by the form.
2. If required, do not invent an artifact or contact.
3. If the company provides a built-in assessment that can be completed later after submission, submit only if the current application form does not require completion first.
4. Add a tracker blocker as `Blocked - Other` with `manual exercise/artifact required`, including the exact requested artifact.

Do not:

- Fabricate exercise URLs, assessment results, references, recruiter contacts, publications, portfolio links, or legal attestations.
- Mark manual-exercise roles as generic site errors. The blocker reason must name the missing artifact.

## 5. Strategic Cap / Duplicate

Recognize it:

- ATS says already applied.
- Gmail already has an application receipt.
- Same company/role/title appears from an earlier successful row.
- Employer has an application cap, such as a maximum applications per time window.

Recovery:

1. Search the current tracker and Gmail before duplicate submitting.
2. If already applied, do not submit again.
3. If there is an application cap, choose the highest-fit roles first and skip lower-fit roles.
4. Record duplicates/cap decisions as `Already Applied`, `Skipped`, or a concise tracker note.

Do not:

- Waste an application cap slot on a weak or specialist mismatch role.
- Mark strategic skips as `Blocked`.

## 6. Legal / User-Authored Attestation Risk

Recognize it:

- Form says answers must be only the applicant's own words.
- Form says AI-generated content or plagiarism disqualifies the application.
- Arbitration, legal agreement, non-compete, reference authorization, or unusual certification is required.
- A field asks for legal status, citizenship, clearance, salary history, or confidential employer facts not already documented.

Recovery:

1. Standard privacy notices, EEO acknowledgements, and application processing consent may be accepted when they are ordinary required ATS terms.
2. User-authored/no-AI attestations are hard stops for generated long answers. Do not submit generated prose under that attestation.
3. Legal agreements beyond ordinary ATS processing, such as arbitration or unusual binding terms, become `Blocked - Other` with `legal/user-authored attestation` in the reason.
4. If a required legal/private fact is not in the plan, resume, answer bank, JD, or safe defaults, do not invent it.

Do not:

- Click through unusual legal agreements just to increase submissions.
- Claim citizenship, clearance, green card, or no-sponsorship status.
- Submit AI-written answers when the form explicitly forbids AI/generated content.

## 7. Account / Login / Email-Auth Wall

Recognize it:

- Workday, SuccessFactors, Oracle, iCIMS, or company portal asks for account creation.
- Existing account login appears.
- Email code is required before the form continues.
- Privacy modal or terms checkbox blocks the next step.

Recovery:

1. Use only the `Job Apply - Yaswanth` Chrome profile.
2. Create normal job/ATS/company accounts when required:
   - Email: `yaswanthmuppalla2025@gmail.com`
   - Credential: use the user-provided live credential only inside the live account flow
3. If the site says an account exists, try the user-provided live credential once.
4. If login fails and password reset is available through the job Gmail, reset using the same user-provided live credential unless CAPTCHA/security challenge appears.
5. Retrieve email codes from Gmail and enter the newest relevant code only.
6. If the portal requires profile setup before the job form, complete only required profile sections from the resume/defaults.
7. After account creation, sign-in, or reset, return to the exact same job application URL, not only the careers homepage.
8. Retry the job form after login with `Apply Manually` or direct job URL when available.
9. If CAPTCHA, OTP outside Gmail, inaccessible password reset, or security prompt blocks the account after the account protocol, add a tracker blocker as `Blocked - CAPTCHA` or `Blocked - Other` with `account/security wall`.

Do not:

- Switch to personal/dev Chrome profiles.
- Treat normal account creation as a blocker.
- Read unrelated Gmail content beyond the code/confirmation needed for the active application.

## 8. Private Identity Fields

Recognize it:

- Workday or another official ATS asks for last-4 SSN.
- Workday or another official ATS asks for date of birth, month/day birth date, or DOB.
- The field appears inside an official company/ATS application, not an unrelated payment or identity-harvesting flow.

Recovery:

1. Confirm the page is an official company or known ATS domain for the active role.
2. Use `PRIVATE_APPLICATION_FIELDS.md` for last-4 SSN, DOB, and month/day DOB fields.
3. Continue the application flow after identity fields are accepted.
4. In tracker notes, write only generic wording such as `required identity fields completed from private application defaults`.
5. If the form asks for full SSN, passport, bank details, payment, or suspicious identity information, do not complete it; mark `Blocked - ATS` for official ATS failure or `Blocked - Other` for suspicious/security collection and continue.

Do not:

- Copy private identity values into tracker rows, notes, learning-loop entries, screenshots, result JSON, or morning summaries.
- Treat standard official ATS last-4 SSN/DOB fields as blockers now that values are available.
- Use private identity values on non-official, suspicious, payment, or recruiter-message forms.

## Agent Self-Check Before Abandoning A Role

Before a non-CAPTCHA role is abandoned, the agent must be able to say:

1. I identified the blocker type.
2. I ran the matching recovery ladder.
3. I made at least 2 serious attempts and tried at least 2 distinct recovery paths, unless a true hard boundary appeared.
4. I checked Gmail when submission might have happened.
5. I did not invent legal/private facts.
6. If official ATS identity fields were required, I used `PRIVATE_APPLICATION_FIELDS.md` and did not record the values.
7. I filled `Attempt Count`, `Recovery Tried`, `Next Retry Path`, and `Notes` for every `Blocked - ATS` or `Blocked - Other` row.
8. I added a real blocker to the tracker only after recovery failed.
9. I preserved the exact retry reason in the tracker note and morning summary.
