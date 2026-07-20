# Application Plan

## Folder Rules

- `AGENTS.md` is the repository-wide behavior contract for every future agent; read it before the application command center.
- `AI_ROLES/` contains the canonical AI resume only.
- `SDE_ROLES/` contains the canonical SDE resume only.
- `INTERVIEW_PREP/` contains role-specific interview material and is out of scope for application batches.
- `JOB_APPLICATION_TRACKER.xlsx` is the single active tracker workbook with `Summary`, `AI`, `SDE`, and `Blockers` sheets.
- `START_HERE_AUTOPILOT.md` is the first-read command center for every AI/SDE batch.
- `ANSWER_BANK.md` contains reusable short, medium, and long answers for recurring custom application questions.
- `PRIVATE_APPLICATION_FIELDS.md` contains application-only private identity values for official ATS fields; never copy those values into trackers, notes, screenshots, or learning-loop entries.
- `AUTONOMOUS_RUNBOOK.md` contains the compact days/overnight execution loop, Chrome loop, checkpoints, and summary format.
- `AUTOPILOT_BLOCKER_PLAYBOOK.md` is the single blocker and recovery source for ATS validation, upload, account/login, Gmail confirmation, manual/legal blockers, duplicate/cap handling, and morning-review rules.
- `ATS_RETRY_MATRIX.md` contains Greenhouse, Ashby, Lever, Workday, Oracle/Taleo, SmartRecruiters/iCIMS/native, Workable, Indeed, and Phenom/SuccessFactors recovery patterns.
- `RECENCY_PREFLIGHT.md` contains the authoritative recency, fit, source, location, duplicate, and company-spread preflight.
- `TRACKER_SCHEMA.md` is the source of truth for the master workbook columns, status labels, blocker logging, and CAPTCHA parking.
- `LEARNING_LOOP.md` contains short high-value lessons from applications, blockers, platform behavior, and repeat answers.
- Do not keep duplicate resumes in the root folder.
- Do not keep render previews, screenshots, old versions, audit exports, or scratch scripts in this workspace.
- Do not create visible tracker backup files during routine application runs or tracker updates. If a rare structural migration truly needs a safety copy, use a temporary location outside this workspace and clean it up before finishing.
- Do not create routine reports, target queues, cache sheets, CSV files, or JSONL files. Use `JOB_APPLICATION_TRACKER.xlsx` plus `LEARNING_LOOP.md` only.

## Current Resume Use

- AI roles: `AI_ROLES/Yaswanth_Muppalla_AI_Resume.pdf`
- AI editable source: `AI_ROLES/Yaswanth_Muppalla_AI_Resume.docx`
- AI manual-entry fallback: `AI_ROLES/Yaswanth_Muppalla_AI_Resume.txt`
- SDE roles: `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.pdf`
- SDE editable source: `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.docx`
- SDE manual-entry fallback: `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.txt`
- Master tracker: `JOB_APPLICATION_TRACKER.xlsx` using the lean schema in `TRACKER_SCHEMA.md`

## Target AI Roles

- AI Platform Engineer
- LLM Engineer
- Applied AI Engineer
- RAG Engineer
- GenAI Engineer
- AI Backend Engineer
- Software Engineer, AI Products
- Backend Engineer, AI/ML Platform
- LLMOps Engineer

Fit calibration: prioritize backend-to-AI, RAG/LLM, agentic workflow, AI product engineering, MLOps/LLMOps, retrieval platform, evaluation, serving, tooling, and cloud data-pipeline roles. Skip deep ML/research/scientist roles where the core asks are recommender/personalization model strategy, modern deep-learning architecture ownership, distributed training leadership, speech/CV/genomics/domain research, or Staff/Principal-level model science not supported by the resume.

## Target SDE Roles

- Senior Software Engineer
- Backend Engineer
- Software Development Engineer
- Platform Engineer
- Backend Platform Engineer
- Data Platform Engineer
- Cloud Backend Engineer
- Java Backend Engineer
- Python Backend Engineer
- Full-Stack Engineer with strong backend ownership

## Autonomy Mode

Mode: `Aggressive Autopilot`.

Goal: maximize truthful submissions for high/strong-fit roles that match Yaswanth's AI/SDE profile and are compatible with H-1B transfer. Codex should not pause for ordinary uncertainty, missing wording, optional fields, account creation, Gmail codes, upload friction, or normal ATS issues once a role passes the fit gate. Codex should use the resume, JD, company context, tracker, `ANSWER_BANK.md`, and judgment to keep moving.

Preflight source of truth: use `RECENCY_PREFLIGHT.md` for recency, employer/source quality, location priority, and duplicate checks before filling any form.

Hard-stop-only rule: do not stop the run. Mark a role skipped or blocked, record the exact reason, and continue unless the entire Chrome/profile/workspace is unavailable. Individual roles hard-stop only for:

- Company is Capital One before `2027-01-07`; skip all Capital One AI/SDE/LinkedIn/Workday roles because current Power Day feedback says sponsorship support is unavailable at the eligible hire level until the 6-month reattempt window.
- CAPTCHA, hCaptcha, reCAPTCHA, visual challenge, or anti-abuse page that cannot be completed by AI.
- Role says no visa sponsorship, no immigration support, no H-1B transfer, no current/future sponsorship, citizen/GC-only, U.S.-person-only, clearance-only, or incompatible legal eligibility.
- Role is an obvious low-quality staffing/consulting/vendor/recruiter/aggregator-proxy posting instead of a direct employer application.
- Payment/request-for-money, scam-like behavior, or a form requiring credentials or private facts not provided in `PRIVATE_APPLICATION_FIELDS.md`.
- Required manual assessment, exercise URL, video, portfolio artifact, recruiter contact, reference, or legal attestation that cannot be truthfully completed from the plan/resume.
- Portal remains technically impossible after the recovery ladder in `AUTOPILOT_BLOCKER_PLAYBOOK.md`.

Normal friction is not a stop condition: account creation, job-Gmail email/security-code verification, upload failure with fallback, page reload, direct ATS URL, company page retry, manual resume text entry, unknown optional fields, N/A fields, and closest truthful dropdowns should be handled autonomously.

## Workflow

Use the Codex skill `/Users/yaswanthmuppala/.codex/skills/job-application-autopilot/SKILL.md` for high-volume application batches so Chrome profile selection, tab cleanup, tracker rules, account creation, Gmail codes, and blocker handling are applied consistently. Start with `START_HERE_AUTOPILOT.md`, then use the deeper files only as needed.

Runtime state machine:

1. Run the tracker-integrity gate in `TRACKER_SCHEMA.md`; if it fails, pause submissions and restore/reconcile a validated workbook before using it for duplicate prevention.
2. Discover latest open jobs deeply across official company career pages, ATS boards, and reputable hiring portals.
3. Run `RECENCY_PREFLIGHT.md`, including canonical duplicate and company-spread checks, then verify sponsorship compatibility and fit before opening/filling the application form.
4. Use `TRACKER_SCHEMA.md` for status labels and tracker row rules.
5. Select the role lane: AI resume for AI roles, SDE resume for SDE/backend roles.
6. Fill from `APPLICATION_PLAN.md`, `ANSWER_BANK.md`, the resume, JD, company context, and best truthful judgment.
7. Re-read the newest tracker immediately before final submit, then submit high/strong-fit applications without per-role approval when the job is not submitted/already applied or separately claimed by another agent. A current eligible retry may match its own blocker row.
8. Confirm submission from screen text, application ID, portal state, or Gmail.
9. Update `JOB_APPLICATION_TRACKER.xlsx` immediately after each submitted, already-applied, or blocked outcome.
10. Do not create separate queue/report/cache files; keep durable state in the master workbook.
11. Close/finalize unneeded tabs and continue to the next role.
12. Add only high-value observed lessons to `LEARNING_LOOP.md`.

Recovery state machine:

Use `AUTOPILOT_BLOCKER_PLAYBOOK.md` as the single recovery source, and use `ATS_RETRY_MATRIX.md` only for ATS-specific fixes. Normal friction must be retried through distinct recovery paths before a blocker is recorded. After recovery succeeds or fails, update the tracker using the simplified statuses in `TRACKER_SCHEMA.md` and continue the batch.

## Quality Targets

- Strong-fit target: prioritize verified high/strong-fit submissions over raw submission count.
- Interview target: optimize the pipeline for at least 10 interview opportunities in the next 30 days.
- Do not spend time on obvious poor fits, no-sponsorship roles, citizen/GC-only roles, expired roles, clearance-only roles, or roles older than 15 days unless they qualify for the strongest-fit AI-only 16-120 day live-post exception in `RECENCY_PREFLIGHT.md`.
- Submission-volume pressure never overrides fit or recency: exhaust strong 0-15 day matches first, then use 16-120 days only for the strongest qualifying AI matches, and summarize the shortage when neither pool has qualified roles.
- Quality targets never override the employer/source gate; skip random staffing, consulting, vendor, recruiter, W2-only, client-confidential, and aggregator-proxy roles even when they are easy submissions.
- For strong-fit roles in target locations, push through normal ATS friction aggressively: direct company page, direct ATS URL, account creation, email verification, manual resume entry, reload/refill, and sensible form retries.
- After 3 applications/attempts at one company within 30 days, use the soft company-spread rule in `RECENCY_PREFLIGHT.md`; rotate employers when there is no positive signal and the next role is not a materially different `High`/exceptional fit. Silence alone is not a hard block.

## Search And Preflight Rules

Use `RECENCY_PREFLIGHT.md` as the single source of truth for freshness, source quality, location priority, and duplicate prevention. Search broadly across company career pages, ATS boards, LinkedIn, Indeed, Wellfound, Y Combinator jobs, Built In, and reputable company-backed hiring sites, but submit through the official company/ATS page whenever available.

If no high/strong resume matches exist inside the preflight gate, scrape deeper across official/company/ATS sources first, then report the shortage instead of applying stale, duplicate, medium-adjacent, low-quality, or off-location roles to chase volume. Mix sources and ATS platforms during long runs to reduce CAPTCHA/possible-spam pressure.

## Dedicated Chrome Profile

Use the verified Chrome profile `Job Apply - Yaswanth` for all logged-in job application work.

Profile lock:

- Chrome profile directory: `Profile 4`
- Application email: `yaswanthmuppalla2025@gmail.com`
- Job-application account credential: user-provided live credential, used only inside live official account flows.
- Private identity fields: use `PRIVATE_APPLICATION_FIELDS.md` only when official ATS forms require last-4 SSN, DOB, or month/day DOB.
- Codex Chrome Extension is installed and enabled in this profile.
- LinkedIn, Indeed, and Gmail were observed under this profile.

Codex selection rule:

- Do not use the default Chrome extension instance blindly. First list available Chrome browser instances and select the extension instance whose metadata has `profileName: Job Apply - Yaswanth`.
- If `Job Apply - Yaswanth` is not available through the Codex Chrome Extension, first reconnect/reopen Chrome and reselect the profile. If it remains unavailable, continue discovery-only review in the browser and note official links in the morning summary instead of switching to a personal/dev profile or creating queue files.
- Do not use personal/dev browsing sessions for applications unless Yaswanth explicitly says to.
- Safe AI command wording from Yaswanth: `Use the Job Apply - Yaswanth Chrome profile and start the AI job batch.`
- Safe SDE command wording from Yaswanth: `Use the Job Apply - Yaswanth Chrome profile and start the SDE job batch.`
- Overnight autopilot command wording from Yaswanth: `Use the Job Apply - Yaswanth Chrome profile and run the overnight autopilot batch for matching roles.`

## Chrome Operating Rules

- Prefer one reusable application tab for live submissions. Navigate that tab from role to role instead of opening a new tab per application.
- Keep at most 3 working tabs: one active application tab, one discovery/source tab, and one Gmail/security-code tab. Up to 5 additional tabs may remain open only as tracked CAPTCHA handoffs, for an absolute maximum of 8 tabs.
- After each submitted, blocked, skipped, or hard-stop result, record the outcome, update the tracker, then close or finalize unneeded tabs immediately.
- For days-long and overnight runs, checkpoint after every role: tracker updated, proof noted, tabs cleaned, next role selected.
- Every 10-20 application attempts, do a Chrome hygiene cycle: close stale tabs, keep only the active application/discovery/Gmail tabs, confirm `Job Apply - Yaswanth` is still the selected profile, and continue from the tracker.
- Before ending any Chrome-backed turn, call Chrome tab finalization and omit/close research, duplicate, confirmation, expired, and completed application tabs unless the user needs a live handoff page.
- If the Chrome bridge slows or times out, first reduce tab pressure: close completed/research tabs through the browser UI if possible, then reconnect to `Job Apply - Yaswanth`.
- If Chrome automation becomes stuck, close/finalize tabs when possible, reopen or reconnect to the `Job Apply - Yaswanth` Chrome profile, reload the current official ATS/company page, and resume from the tracker row rather than abandoning the batch.
- If a tab or form is stale after reconnect, reopen the official posting/application URL from the tracker and restart that role with attempt count incremented.
- Reuse direct ATS URLs and the same active tab for retries. Do not leave old failed form tabs open after logging the result.
- At run start and end, reconcile open CAPTCHA handoff tabs with `Blockers`: every `Parked Tab = Yes` row must have a live exact-role tab; set it to `No` if the tab no longer exists while retaining the blocker row.

## Tracker Recovery Fields

`JOB_APPLICATION_TRACKER.xlsx` is the only active tracker. Use `AI` and `SDE` for lean `Submitted` and `Already Applied` rows. Use `Blockers` for CAPTCHA, ATS, upload, account/login, anti-spam, manual/legal, missing-info, Chrome/profile, and other real recovery rows.

- Use `Attempt Count`, `Recovery Tried`, `Next Action`, and `Learning` for real blockers or meaningful retries.
- Do not overfill the lean AI/SDE submission sheets.
- `Recovery Tried` should name concrete actions, not vague text. Example: `required-widget sweep; direct Greenhouse embed; Gmail code; reload/refill`.
- `Next Action` should be actionable. Example: `Retry Workday after account login; use Apply Manually`.
- Mark `Learning` only for rows that reveal reusable ATS/company behavior worth adding to `LEARNING_LOOP.md`.
- Do not log broad skip-noise. Stale, no-sponsorship, closed, over-15-day roles outside the strong AI live-post exception, low-quality staffing/vendor, and poor-fit roles are still skipped, but only `Already Applied` and real blockers are tracked.

## Learning Cadence

- Every 2-3 hours of applying, or every 50 submitted applications, add 5-6 high-value sentences to `LEARNING_LOOP.md` only if the run produced reusable observations.
- Write learnings as observed pattern -> recovery/action. Example: `Greenhouse code boxes duplicated characters; clear boxes, type one character per box, then verify the joined code before submit.`
- Prioritize ATS-specific behavior, company-specific field mappings, upload/account/code recovery, Gmail confirmation proof, CAPTCHA/source-mixing lessons, and tracker classification improvements.
- Do not add generic status updates, motivation, credentials, passwords, one-off frustration, or policy restatements already covered by the plan/runbook/playbook.

## Application-Time Decisions

- Salary fields: decide at application time from the posted range, role seniority, location, and market context.
- Location fields: decide at application time using the preferred and excluded locations below.
- Role-specific long answers: draft directly from the JD, company context, and resume.
- Recency/open-status behavior: apply only after confirming the role is open, within the verified 0-15 day gate by default or within the strongest-fit AI-only 16-120 day live-post exception, and reachable through an official company/ATS application page when available. Skip anything older than 120 days.
- Duplicate behavior: use the official job ID and canonical role URL when available, check all three tracker sheets before filling, and re-read the newest workbook immediately before final submit. Concurrent agents must work non-overlapping lane/source slices; stop when the job is submitted/already applied or separately claimed, but allow an eligible retry to match its own blocker row.
- Submit behavior: when Yaswanth starts an autopilot batch, that command is explicit approval to submit matching applications without per-application review.
- Account creation behavior: during an approved autopilot run, create normal ATS/job-board/company-career accounts when required using the job email and user-provided live credential. Do not pause for ordinary account creation.
- Credential hygiene: the live credential is allowed for job-application account creation in this workspace. Do not write it into trackers, learning-loop notes, screenshots, summaries, scratch outputs, or browser-visible notes. Use it only to complete account/login flows.
- Private identity hygiene: values in `PRIVATE_APPLICATION_FIELDS.md` are allowed only for official ATS identity fields. Do not write those values into trackers, learning-loop notes, screenshots, summaries, scratch outputs, or browser-visible notes.
- Do not ask Yaswanth for approval during an approved autopilot run. Decide ordinary fields from `APPLICATION_PLAN.md`, `ANSWER_BANK.md`, the JD, posted salary range, location, and available form options.
- Judgment fallback: if a normal application field is not explicitly listed here, use best truthful judgment from the resume, JD, company context, tracker notes, and common application meaning. Do not turn ordinary missing wording, optional fields, or N/A-style fields into blockers.
- N/A behavior: if a field is optional, irrelevant, or not applicable, use `N/A`, `Not applicable`, the closest truthful dropdown option, or leave it blank when the form allows blank values.
- Closest-option behavior: if a form option does not exactly match the default answer, choose the closest truthful option and continue.
- Blocker behavior: use `AUTOPILOT_BLOCKER_PLAYBOOK.md`; recover aggressively when safe, mark the role clearly only after recovery attempts, and continue the run instead of stopping.
- No first-attempt technical blockers: except visual CAPTCHA/anti-abuse/legal/manual/hard-eligibility boundaries, do not mark `Blocked - ATS` or `Blocked - Other` until at least 2 serious attempts and 2 distinct recovery paths have been tried. For high-fit roles, use up to 3 serious attempts when safe paths remain.
- Blocked-row proof behavior: every `Blocked - ATS` and non-CAPTCHA `Blocked - Other` row must fill `Attempt Count`, `Recovery Tried`, `Next Action`, and exact non-private blocker notes in `Blockers`.
- Hard blockers: mark and move on only for visual CAPTCHA/anti-abuse challenge, duplicate/already-applied state, payment/request-for-money, missing required information that cannot be truthfully derived from the resume/JD/defaults/private-field file, no-sponsorship/ineligible role, or a form that remains technically impossible after the recovery ladder. Use the simplified tracker statuses in `TRACKER_SCHEMA.md`.
- Account creation is not a hard blocker when the form accepts normal email/password signup and the application email is usable.
- Account/login recovery behavior: create the normal ATS/company account, try existing login once if the account exists, use password reset through the job Gmail when available, retrieve Gmail codes/links, complete required profile sections, and return to the exact job application URL before blocking.
- Last-4 SSN, DOB, and month/day DOB are not blockers when requested by a normal official ATS form; use `PRIVATE_APPLICATION_FIELDS.md`.
- Do not bypass CAPTCHA, anti-abuse pages, visual security puzzles, or legal eligibility requirements. Treat those as hard blockers or manual review.
- CAPTCHA parking behavior: for high-fit roles that pass all gates, fill every truthful field possible, leave the CAPTCHA/anti-abuse tab open for Yaswanth, record `Blocked - CAPTCHA` with `Blocker Type = CAPTCHA Parked`, `Retry Eligible = Manual Review`, `Parked Tab = Yes`, and continue in another tab. Keep at most 5 parked CAPTCHA tabs and never park stale/no-sponsorship/low-quality roles.
- Capital One company cooldown: before `2027-01-07`, skip every Capital One role immediately and do not retry older Capital One Workday lessons. The current reason is company-level sponsorship support unavailable at the eligible hire level after Power Day, not resume fit.
- Sponsorship hard skip: strictly skip any role whose JD or application says the employer does not sponsor visas, does not provide immigration support, cannot sponsor or transfer H-1B, does not sponsor now or in the future, requires no current/future sponsorship, or otherwise rejects visa-related work authorization support.
- Compliance hard skip: strictly skip any role that clearly requires U.S. citizenship, permanent residency/green card, U.S.-person status, export-control eligibility that H-1B does not satisfy, active security clearance, or government/clearance eligibility not compatible with H-1B transfer.
- If sponsorship is not mentioned or is ambiguous, apply and answer sponsorship questions truthfully from the defaults below.
- Gmail confirmation behavior: after submissions, monitor Gmail for company/ATS confirmation emails. Keep tracker status as `Submitted` and record proof quality in `Confirmation Proof` and `Notes` only.

## Application Answer Sheet

Codex follows this rule: use the defaults below. If a field depends on the job, decide at application time from the JD, posted salary, location, and available form options. Do not stop for ordinary application questions; fill them end to end using the best truthful answer available. During an approved autopilot run, submit matching applications without asking Yaswanth for per-application approval.

### Identity And Contact

| Question | Default Answer                                           |
|---|----------------------------------------------------------|
| Legal name | Yaswanth Muppalla |
| Preferred/resume name | Yaswanth Muppalla                                         |
| Email | yaswanthmuppalla2025@gmail.com                           |
| Phone | +1 845-663-4330                                          |
| Current city/state | Atlanta, GA                                              |
| Full address | 741 Morosgo Dr, Atlanta, Georgia, 30324                  |
| LinkedIn | https://www.linkedin.com/in/yaswanth-muppalla-7a676814a/ |
| GitHub | https://github.com/ominsights                            |
| Portfolio / personal website | https://ominsights.in/                                                  |

### Work Authorization And Sponsorship

| Question | Default Answer      |
|---|---------------------|
| Are you legally authorized to work in the United States? | Yes                 |
| Will you now or in the future require visa sponsorship? | Yes                 |
| Do you require H-1B transfer, new H-1B, OPT, CPT, STEM OPT, TN, O-1, or other visa support? | H-1B transfer       |
| Can you provide proof of identity and employment authorization after hire? | Yes                 |
| Are you at least 18 years old? | Yes                 |
| Are you subject to export-control restrictions for this role? | No                  |
| Is this role restricted to U.S. persons / citizens / permanent residents? | No; H-1B transfer does not satisfy citizen/GC-only restrictions. Strictly skip if this is mandatory. |
| Does the employer say it does not sponsor visas or immigration support? | Strictly skip; do not apply. |
| Does the employer say it cannot sponsor or transfer H-1B? | Strictly skip; do not apply. |

### Location, Remote Work, Travel

| Question | Default Answer                                                     |
|---|--------------------------------------------------------------------|
| Preferred work location | Georgia/Atlanta; Dallas/Austin/Texas; Virginia/DC; North Carolina; Tennessee; Florida; Remote US only |
| Open to remote roles? | Yes                                                                |
| Open to hybrid roles? | Yes                                                                |
| Open to onsite roles? | Yes                                                                |
| Open to relocate? | Yes, including for hybrid roles in the location being applied to when the role is otherwise a strong fit. |
| Locations you will not consider | Chicago area; New York City/NY; roles close to Chicago             |
| Willing to travel for work? | Yes                                                                |
| Time zone preference | Any                                                                |

Location search priority for agents:

1. Georgia / Atlanta
2. Dallas / Austin / Texas
3. Virginia / DC
4. North Carolina
5. Tennessee
6. Florida
7. Remote US

### Availability And Compensation

| Question | Default Answer                  |
|---|---------------------------------|
| Earliest start date | ASAP, subject to reasonable notice if currently employed |
| Notice period | 2 weeks after offer acceptance unless Yaswanth says otherwise |
| Desired base salary | Decide at application time from posted range, role seniority, location, and market context. |
| Desired total compensation | Decide at application time from posted range, role seniority, location, and market context. |
| Minimum acceptable compensation | Decide at application time; do not choose a low value just to submit. |
| Contract hourly rate, if asked | Not applicable by default because contract roles are not preferred; if unavoidable, decide from role/location market context. |
| Open to contract roles? | NO                              |
| Open to contract-to-hire roles? | NO                              |

### Resume And Role Selection

| Question | Default Answer |
|---|---|
| AI role resume | AI_ROLES/Yaswanth_Muppalla_AI_Resume.pdf |
| AI role DOCX resume | AI_ROLES/Yaswanth_Muppalla_AI_Resume.docx |
| SDE role resume | SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.pdf |
| SDE role DOCX resume | SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.docx |
| Use PDF or DOCX? | Use PDF by default; use DOCX if portal parsing looks poor or asks for Word. |

### Education

| Question | Default Answer |
|---|---|
| Highest degree | Master of Science, Computer Science |
| Graduate school | State University of New York, New Paltz |
| Graduate completion | May 2020 |
| Graduate GPA | 3.6/4.0 |
| Bachelor degree | Bachelor of Technology |
| Bachelor school | JNTUK |
| Bachelor completion | 2018 |
| Bachelor CGPA | 8.5/10 |

### Experience And Skills Defaults

| Question | Default Answer                                    |
|---|---------------------------------------------------|
| Current target title for AI roles | AI Platform Engineer / LLM Engineer / RAG Engineer |
| Current target title for SDE roles | Senior Software Engineer / Backend Engineer       |
| Years of professional software experience | 6+ based on visible resume timeline; use 7+ only if Yaswanth confirms earlier qualifying experience |
| Years of Python experience | 4+                                                |
| Years of Java/Spring experience | 3+                                                |
| Years of AWS experience | 5+                                                |
| Years of AI/LLM/RAG experience | 2+ based on OmInsights Jan 2024 - Present; use more only if Yaswanth confirms earlier AI work |
| Years of Angular/TypeScript experience | 1+                                                |
| Years of data engineering experience | 5+                                                |
| Management experience | Technical/project leadership; do not claim people management unless Yaswanth confirms |
| Open-source contribution answer | GitHub/portfolio project: OmInsights; if a numeric field is required, answer based on visible GitHub/project evidence at application time. |

### Common Short Answers

| Question | Default Answer                                                                         |
|---|----------------------------------------------------------------------------------------|
| Why are you interested in this role? | Draft based on JD and resume; no approval needed.    |
| Why this company? | Draft based on JD and company research; no approval needed. |
| Tell us about a project you are proud of. | Use OmInsights summary, then tailor to role.                                           |
| Describe AI/LLM experience. | Use OmInsights RAG, Context Engine, MCP, document intelligence, source-backed answers. |
| Describe backend/cloud experience. | Use AMEX/Skechers metrics, AWS, Python APIs, Java/Spring, Flink/Airflow.               |
| Cover letter required? | Create a concise tailored cover letter if required.                                    |

For custom text boxes, first use `ANSWER_BANK.md` for the right short, medium, or long base answer, then tailor to the JD and company.

### OmInsights Compliance Rule

OmInsights is a personal technical portfolio/learning project. It is not an active company/product business, active employer, client-serving product, consulting business, advisory role, revenue activity, secondary employment, or outside work Yaswanth is committing to continue after joining an employer.

Agents may use OmInsights as technical evidence for AI/backend/platform experience. Agents must not describe it as an ongoing business or outside employment.

For compliance-style fields, answer from this rule:

| Question Pattern | Default Answer |
|---|---|
| Will you continue OmInsights after joining? | No. Do not say Yaswanth will continue OmInsights as outside work. |
| Outside business activity / secondary employment / paid or unpaid work for another entity? | No, because OmInsights is only a personal learning/portfolio technical project. |
| Advisory/founder role / board role / business ownership? | No, unless the form separately allows a portfolio-project explanation; do not represent OmInsights as an active company role. |
| IP assignment / outside invention / pre-existing project disclosure? | If explanation is allowed: pre-existing personal technical portfolio project for learning and skill demonstration; no customers, users, revenue, or employer confidential information. |

Manual review is only needed when the form forces a legal certification that cannot be answered truthfully using the above facts.

### Voluntary EEO / Demographic Self-Identification

These are usually voluntary or compliance-related. Use the explicit defaults below during autopilot; do not infer beyond these defaults.

| Question | Default Answer                                                        |
|---|-----------------------------------------------------------------------|
| Gender | Male, unless Yaswanth changes the default; use `I do not wish to answer` if that option is preferred later. |
| Race | Asian, unless Yaswanth changes the default; use `I do not wish to answer` if that option is preferred later. |
| Hispanic or Latino ethnicity | No / Not Hispanic or Latino, unless Yaswanth changes the default. |
| Disability status / Form CC-305 | No, I do not have a disability and have not had one in the past, unless Yaswanth changes the default. |
| Protected veteran status | I am not a protected veteran, unless Yaswanth changes the default. |
| LGBTQ+ identity, where asked | Prefer not to answer unless Yaswanth provides a specific default. |
| Pronouns | he/him, unless Yaswanth changes the default. |
| Need accommodation for application/interview? | No |

### Legal, Background, And Compliance Questions

| Question | Default Answer              |
|---|-----------------------------|
| Have you worked at this company before? | NO                          |
| Are you related to anyone at this company? | NO                          |
| Do you have a non-compete or conflict restriction? | NO                          |
| Outside employment / secondary employment / outside business activity? | NO, based on OmInsights being only a personal technical portfolio/learning project. |
| Will you continue OmInsights after joining? | NO, do not represent OmInsights as ongoing outside work. |
| Business ownership, advisory role, or board role? | NO, unless Yaswanth explicitly provides a company-specific different answer. |
| Pre-existing personal project / outside invention disclosure | Disclose OmInsights only as a pre-existing personal technical portfolio project when the form specifically asks for projects or IP. |
| Are you willing to complete a background check? | YES                         |
| Are you willing to complete a drug screen, if required? | YES                         |
| Do you hold required licenses/certifications? | No, unless the required certification is explicitly listed in the resume or profile. |
| Security clearance | NO                          |
| Government/public-sector eligibility questions | Answer truthfully based on H-1B transfer status; strictly skip roles requiring citizenship/clearance if not eligible. |
| Criminal history question | NO criminal history         |

### Reusable Legal And Private-Fact Defaults

Use these defaults for recurring official application questions. Do not convert them into blockers unless the question asks for a different specific fact, a company-specific exception is known, or the form requires private details not documented here or in `PRIVATE_APPLICATION_FIELDS.md`.

| Question | Default Answer |
|---|---|
| Country of citizenship / nationality | India |
| Any other citizenships? | No |
| Relatives employed at this company? | No |
| Is current/former employer a client of this company? | No |
| Regulatory, licensing, investigation, or settlement history? | No |
| Professional license investigated, revoked, suspended, cancelled, or disciplined? | No |
| Surrendered a professional license? | No |
| Board member, trustee, trust protector, executor, or personal representative? | No |
| Discharged, separated by mutual agreement, or resigned after being given the option? | No |
| Required coworker/recruiter/referral/reference contact | Manual unless Yaswanth provides the specific reusable contact and permission to use it. |
| Explicit employer instruction not to use AI assistance for written answers | Manual applicant-authored response; fill objective fields only. |

### Data, AI, And Privacy Consent

| Question | Default Answer |
|---|----------------|
| Consent to process application data | YES            |
| Consent to SMS/text recruiting messages | Yes if job-related; No if it is clearly marketing-heavy or unrelated. |
| Consent to AI-assisted application review | YES            |
| Opt out of automated processing, if offered | No, unless Yaswanth explicitly wants to opt out; keep consistent with AI-review consent |
| Talent community consent | YES            |

### Platform Rules

| Platform/Form | What Codex Should Expect |
|---|---|
| Ashby | Custom forms can ask resume, location, education, URLs, files, yes/no, multiple choice, long answers, and private questions; verify role is open before submitting. |
| Lever | Custom questions may be required and some answers can be marked secret/sensitive; verify role is open before submitting. |
| Greenhouse | Usually resume plus employer-specific custom questions; upload PDF or DOCX as requested; verify role is open before submitting. |
| Workday | Often asks structured profile fields, experience, education, work authorization, demographic info, and company-specific questions; verify role is open before submitting. |
| LinkedIn / Indeed | Use mainly for discovery; prefer official company/ATS pages for overnight autopilot submissions. |

For CAPTCHA, upload failure, ATS breakage, login wall, risky custom field, duplicate submission, or Gmail confirmation handling, follow `AUTOPILOT_BLOCKER_PLAYBOOK.md`.
