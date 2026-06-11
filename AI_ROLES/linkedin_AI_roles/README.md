# LinkedIn AI Roles Autopilot

This folder is the LinkedIn-specific source layer for AI-first job discovery and application runs. It does not replace the main autopilot system, duplicate resumes, or create separate application policy. Agents must read the root workflow first, then use this README for LinkedIn filters, Easy Apply behavior, and external ATS handoff.

## Read First

Before using LinkedIn, read these root files:

1. `../../START_HERE_AUTOPILOT.md`
2. `../../APPLICATION_PLAN.md`
3. `../../RECENCY_PREFLIGHT.md`
4. `../../TRACKER_SCHEMA.md`
5. `../../ANSWER_BANK.md`
6. `../../AUTOPILOT_BLOCKER_PLAYBOOK.md`
7. `../../ATS_RETRY_MATRIX.md`

The root rules win on authorization, sponsorship, recency, hard blockers, Gmail proof, account creation, resume use, tracker statuses, and private-data hygiene.

## Folder Contents

This folder contains LinkedIn-specific instructions only. Do not create or use a separate LinkedIn tracker. Record LinkedIn outcomes in the root `JOB_APPLICATION_TRACKER.xlsx`.

Use the canonical resumes directly:

- AI resume PDF: `../Yaswanth_Muppalla_AI_Resume.pdf`
- AI resume DOCX: `../Yaswanth_Muppalla_AI_Resume.docx`
- AI manual-entry fallback: `../Yaswanth_Muppalla_AI_Resume.txt`
- SDE resume PDF: `../../SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.pdf`
- SDE resume DOCX: `../../SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.docx`
- SDE manual-entry fallback: `../../SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.txt`

Do not store resume copies or resume symlinks in this folder. If a resume changes, update the canonical resume once in `AI_ROLES/` or `SDE_ROLES/`; LinkedIn runs should always use those paths.

## LinkedIn Ready Setup

This folder is ready when these are true:

- The only file in this folder is this README.
- LinkedIn-sourced outcomes go into root `JOB_APPLICATION_TRACKER.xlsx`.
- LinkedIn Easy Apply AI outcomes go to the `AI` sheet when submitted/already-applied, or `Blockers` when blocked.
- Resume paths, LinkedIn filters, email routing, and Easy Apply rules live in this README instead of extra workbook setup sheets.
- Agents use LinkedIn Jobs in the `Job Apply - Yaswanth` Chrome profile.
- Agents use `JOB_APPLICATION_TRACKER.xlsx` as durable state and LinkedIn saved jobs only as a temporary queue.
- Agents do not create local resume copies, scratch scripts, screenshots, or backup trackers in this folder.

## Email Routing

Use different emails depending on where the application is submitted:

- LinkedIn account, LinkedIn Jobs, and LinkedIn Easy Apply: `muppallayaswanthsaikumar@gmail.com`
- External company sites and ATS flows reached from LinkedIn `Apply`: `yaswanthmuppalla2025@gmail.com`

If a LinkedIn Easy Apply confirmation or verification is needed, check the LinkedIn email. If the role opens Greenhouse, Ashby, Lever, Workday, company-native, or any other external application flow, use the root application email and the normal root ATS/account workflow.

Credential rule: use the user-provided live credential only inside live official account/login flows when needed. Do not write passwords into this README, the tracker, memory, screenshots, notes, summaries, or result rows.

## Mission

Use LinkedIn to find and submit fresh, fitting AI roles while preserving the existing autopilot standards:

- Apply only to verified 0-15 day roles.
- Prioritize 0-7 day roles first.
- Use 8-15 day roles only for strong AI/backend fit.
- Skip older, unknown-recency, closed, no-sponsorship, citizen-only, clearance-only, U.S.-person-only, poor-fit, duplicate, and suspicious roles.
- Prefer official company or ATS pages for final submission when available.
- Use LinkedIn Easy Apply only when the role passes the same preflight and the correct resume/profile answers can be reviewed before submit.

## Target Locations

Run LinkedIn searches against these locations:

- Georgia
- Atlanta, Georgia
- Texas
- Austin, Texas
- Dallas, Texas
- Virginia
- North Carolina
- Tennessee
- Florida
- Remote United States

Avoid roles that are only NYC/NY, Chicago area, Canada-only, foreign-only, clearance-only, contract-only, or not compatible with H-1B transfer.

## Target Role Keywords

Use these keyword families. Rotate them across locations instead of running one giant stale search.

- `AI Engineer`
- `LLM Engineer`
- `RAG Engineer`
- `GenAI Engineer`
- `Generative AI Engineer`
- `Applied AI Engineer`
- `AI Platform Engineer`
- `Backend AI Engineer`
- `Software Engineer AI`
- `ML Platform Engineer`
- `AI Infrastructure Engineer`
- `Agentic AI Engineer`
- `AI Products Engineer`
- `Document AI Engineer`

Use the AI resume by default. Use the SDE resume only when the role is clearly backend/platform-heavy and the SDE resume is the stronger truthful match.

## LinkedIn Filter Recipe

For each search:

1. Open LinkedIn Jobs in the `Job Apply - Yaswanth` Chrome profile.
2. Search one keyword family plus one target location.
3. Set job type to full-time when available.
4. Set workplace to remote, hybrid, or onsite based on the target location. For Remote USA, use remote-only where possible.
5. Set Date posted to `Past week` first.
6. After exhausting strong 0-7 day matches, use `Past month` only to manually verify roles still fall within the 0-15 day gate.
7. Use experience filters for mid-senior/senior/backend/platform roles when useful; do not over-filter if it hides strong matches.
8. Use `Under 10 applicants` as an optional quality slice after the main search, not as a required gate.
9. Use `Easy Apply` as a separate slice. Do not run only Easy Apply searches.
10. Save promising roles only as a temporary queue; the durable state is the tracker.

## Ready LinkedIn Search Filters

Use this filter pack before starting applications. It is intentionally narrow enough to surface current AI/backend-AI roles without turning LinkedIn into a noisy generic job board.

Default LinkedIn URL filters:

- `f_TPR=r604800`: Past week. This is the main operating filter because LinkedIn does not offer an exact `<15 days` option.
- `f_JT=F`: Full-time.
- `sortBy=DD`: Most recent first.
- `f_WT=2`: Remote. Use this only for Remote United States searches.
- Do not set `Easy Apply` for the primary search. Run Easy Apply as a separate pass after official/company apply paths have been checked.
- Do not toggle job alerts while running application filters unless Yaswanth explicitly asks for alert work.

LinkedIn geo IDs for this folder:

- United States: `103644278`
- Georgia: `103950076`
- Atlanta, Georgia: `106224388`
- Texas: `102748797`
- Austin, Texas: `104472865`
- Dallas, Texas: `104194190`
- Virginia: `101630962`
- North Carolina: `103255397`
- Tennessee: `104629187`
- Florida: `101318387`

Primary search queue:

| Priority | Keyword | Location | URL Pattern | Resume |
| --- | --- | --- | --- | --- |
| 1 | `AI Engineer` | Georgia | `https://www.linkedin.com/jobs/search/?keywords=AI%20Engineer&geoId=103950076&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 2 | `AI Engineer` | Texas | `https://www.linkedin.com/jobs/search/?keywords=AI%20Engineer&geoId=102748797&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 3 | `AI Engineer` | Virginia | `https://www.linkedin.com/jobs/search/?keywords=AI%20Engineer&geoId=101630962&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 4 | `AI Engineer` | North Carolina | `https://www.linkedin.com/jobs/search/?keywords=AI%20Engineer&geoId=103255397&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 5 | `AI Engineer` | Tennessee | `https://www.linkedin.com/jobs/search/?keywords=AI%20Engineer&geoId=104629187&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 6 | `AI Engineer` | Florida | `https://www.linkedin.com/jobs/search/?keywords=AI%20Engineer&geoId=101318387&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 7 | `AI Engineer` | Remote United States | `https://www.linkedin.com/jobs/search/?keywords=AI%20Engineer&geoId=103644278&f_WT=2&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 8 | `LLM Engineer` | Remote United States | `https://www.linkedin.com/jobs/search/?keywords=LLM%20Engineer&geoId=103644278&f_WT=2&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 9 | `RAG Engineer` | Remote United States | `https://www.linkedin.com/jobs/search/?keywords=RAG%20Engineer&geoId=103644278&f_WT=2&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 10 | `AI Platform Engineer` | Remote United States | `https://www.linkedin.com/jobs/search/?keywords=AI%20Platform%20Engineer&geoId=103644278&f_WT=2&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |
| 11 | `Backend AI Engineer` | Remote United States | `https://www.linkedin.com/jobs/search/?keywords=Backend%20AI%20Engineer&geoId=103644278&f_WT=2&f_TPR=r604800&f_JT=F&sortBy=DD` | AI or SDE |
| 12 | `Applied AI Engineer` | Remote United States | `https://www.linkedin.com/jobs/search/?keywords=Applied%20AI%20Engineer&geoId=103644278&f_WT=2&f_TPR=r604800&f_JT=F&sortBy=DD` | AI |

Secondary expansion queue:

- Repeat `LLM Engineer`, `RAG Engineer`, `AI Platform Engineer`, `Backend AI Engineer`, and `Software Engineer AI` across Georgia, Texas, and Virginia first.
- Use Atlanta, Austin, Dallas, and city-level filters when the state search is too noisy.
- Use North Carolina, Tennessee, and Florida after the higher-priority Georgia/Texas/Virginia/Remote pass.
- Use `Past month` only as a manual 8-15 day recovery pass. Do not queue roles blindly from `Past month`.
- Add `f_AL=true` only for a separate Easy Apply slice after the main search has been reviewed.

LinkedIn does not provide an exact `<15 days` filter. Treat LinkedIn recency as a clue, then verify:

- `Past 24 hours` and `Past week`: normally eligible for recency preflight.
- `Past month`: inspect the visible LinkedIn age and official posting date. Apply only if evidence shows 0-15 days.
- `2 weeks ago`: acceptable only when the official or visible age still fits the 0-15 day gate.
- `3 weeks ago`, `1 month ago`, unknown age, or no reliable proof: skip as stale and continue.

## Apply Path Decision

LinkedIn shows two main application paths.

### Easy Apply

Use Easy Apply when:

- The role passes AI fit, location, sponsorship, and 0-15 day recency preflight.
- The popup allows all required answers to be completed truthfully from root docs, resume, JD, answer bank, or safe judgment.
- The selected resume is verified as the correct current resume before submit.
- No visual CAPTCHA/hCaptcha/reCAPTCHA/anti-abuse challenge, manual exercise, unusual legal/user-authored attestation, payment, or unsupported private fact appears.

Before clicking final submit:

- Confirm the selected resume filename is current and lane-correct.
- Review all LinkedIn prefilled answers. LinkedIn may reuse saved answers and resumes.
- Correct work authorization: authorized to work = Yes; sponsorship/H-1B transfer = Yes.
- Do not claim citizenship, clearance, green card, no sponsorship need, or unavailable credentials.
- If the form asks for a cover letter or custom answer, tailor from `../../ANSWER_BANK.md`.
- If there is a final review screen, use it. Easy Apply submissions cannot be edited from LinkedIn after submission.

Record proof with the simplified tracker status from `../../TRACKER_SCHEMA.md`:

- Use `Submitted` only when LinkedIn shows success, the LinkedIn Applied tab confirms the application, Gmail/LinkedIn email proof exists, or the external portal shows a clear submitted state or application ID.
- Do not count "submit appeared complete" by itself as proof. If proof is unclear, check the Applied tab and relevant email once before recording the outcome.
- Put screen proof, email proof, application ID, or concise proof notes in `Confirmation Proof` and `Notes`.

### Apply / External ATS

Use the external apply route when LinkedIn sends the agent to a company site or ATS. After opening the external page:

1. Verify official company/ATS domain.
2. Verify open status and posting date from official page, ATS data, or reliable dated source.
3. Continue under the normal autopilot flow and `../../ATS_RETRY_MATRIX.md`.
4. Use direct ATS URLs over broken LinkedIn redirect pages when available.
5. Record `Source` as `LinkedIn -> <ATS/company>`.
6. Record `ATS` as Greenhouse, Ashby, Lever, Workday, Workable, SmartRecruiters, iCIMS, Oracle/Taleo, Phenom, LinkedIn Easy Apply, or company-native.

If the external site is stale, closed, no-sponsorship, or not official, do not force it. Skip and continue without creating skip-noise.

## Sponsorship And Eligibility Gate

Hard skip if the LinkedIn job detail, company page, or ATS form says:

- no visa sponsorship
- no immigration support
- cannot sponsor or transfer H-1B
- no current or future sponsorship
- authorized for any employer without sponsorship
- U.S. citizen only
- green card/permanent resident only
- U.S. person only
- active clearance required
- ITAR/export-control eligibility that H-1B cannot satisfy

If sponsorship is not mentioned, continue and answer sponsorship questions truthfully.

## Tracking Rules

Use root `JOB_APPLICATION_TRACKER.xlsx` for LinkedIn-sourced work. It follows the lean workbook schema in `../../TRACKER_SCHEMA.md`.

For submitted or already-applied rows, use the exact `AI` / `SDE` sheet columns from `../../TRACKER_SCHEMA.md`:

- `Date`
- `Company`
- `Role`
- `Location`
- `Status`
- `Posted Date`
- `Age Days`
- `Recency Proof`
- `Application URL`
- `Source`
- `ATS`
- `Fit`
- `Sponsorship`
- `Confirmation Proof` or concise proof in `Notes`

Useful LinkedIn values:

- Sheet choice: use `AI` by default; use `SDE` only for backend-heavy roles where the SDE resume is the stronger truthful match.
- `Source`: `LinkedIn`, `LinkedIn Easy Apply`, or `LinkedIn -> <ATS/company>`.
- `ATS`: `LinkedIn Easy Apply` for direct LinkedIn applications; otherwise the external ATS/company platform.
- `Recency Proof`: LinkedIn job URL or official posting URL proving recency.
- `Fit`: `High`, `Strong`, or `Strategic Exception: <why>` only; do not submit blank, low, unknown, or merely adjacent fits.
- `Sponsorship`: `Yes`, `No`, `Unknown`, or `N/A`; use `Yes` only after checking JD/form language.
- Blocked LinkedIn outcomes go to `Blockers`, where `Retry Eligible` is `Yes`, `No`, `Expired`, or `Manual Review`.

Leave optional fields blank or `Unknown` when not derivable quickly. Blank helper fields are not blockers.

Do not log broad LinkedIn skip-noise. Stale, no-sponsorship, duplicate, fit-mismatch, staffing/vendor, aggregator-proxy, and strategic LinkedIn discoveries are skipped unless they are useful `Already Applied` proof or a real blocker/manual-review item.

## LinkedIn Queue Discipline

LinkedIn saved jobs are a temporary queue, not the system of record.

- Save only roles that pass a quick title/location/recency/fit scan.
- Do not let saved jobs pile up as hidden state.
- After each role, update `JOB_APPLICATION_TRACKER.xlsx`, then unsave/archive/close the completed tab when practical.
- Keep one LinkedIn search tab, one active apply tab, and one Gmail/security-code tab if needed.
- Every 10-20 attempts, close stale tabs and rotate search keywords or location.

## Anti-Abuse And Limits

LinkedIn has Easy Apply speed/daily limits and anti-abuse controls. Respect them.

- Do not brute-force Easy Apply.
- Mix Easy Apply with external ATS/company applications.
- Slow down after repeated challenge, spam, or suspicious activity signals.
- Do not bypass CAPTCHA, visual challenges, access controls, or anti-abuse checks.
- If LinkedIn shows a limit, suspicious activity prompt, visual CAPTCHA/hCaptcha/reCAPTCHA, or anti-abuse challenge, mark the active role `Blocked - CAPTCHA` for true CAPTCHA or `Blocked - Other` for limits/access walls, then pivot to external official roles or another source.

## Scam And Suspicious Job Handling

Skip or report when a LinkedIn job asks for:

- payment, equipment purchase, fees, or training costs
- bank details, full SSN, passport, or unrelated private identity data
- account passwords
- pressure to move off-platform immediately
- unclear employer identity or wrong company page
- application through a non-official suspicious domain

Skip suspicious or low-quality roles without a tracker row unless there is useful `Already Applied` proof or a real blocker/manual-review item. If the form already reached a suspicious private-data, payment, CAPTCHA, access-limit, or anti-abuse wall worth reviewing, record the exact non-private blocker in `Blockers`, then continue.

## Job Alerts

LinkedIn supports job alerts, but the account limit is finite. Use alerts only for high-value searches.

Recommended alert set if creating alerts:

- `AI Engineer` in Remote United States
- `LLM Engineer` in Remote United States
- `RAG Engineer` in Remote United States
- `AI Platform Engineer` in Georgia
- `AI Platform Engineer` in Texas
- `Applied AI Engineer` in Virginia
- `Backend AI Engineer` in North Carolina
- `GenAI Engineer` in Tennessee
- `AI Engineer` in Florida

Do not spend an application run managing alerts unless it helps near-term fresh discovery.

## End Of Run Summary

Summarize LinkedIn runs with:

- submitted total
- Easy Apply submitted count
- external ATS submitted count
- proof-backed submitted count
- email-confirmed count
- screen-confirmed count
- rough skipped no-sponsorship/ineligible/stale count, if useful, without adding skip-noise tracker rows
- CAPTCHA/account/ATS/manual blockers
- best manual retries
- Gmail confirmations or recruiter replies needing attention

## Source Notes

LinkedIn behavior was checked against LinkedIn Help in June 2026:

- LinkedIn job filters include location, date posted, Easy Apply, company, experience, employment type, under-10-applicants, and other filters.
- Date posted filters are `past 24 hours`, `past week`, and `past month`, not exact 15-day filtering.
- `Easy Apply` submits inside LinkedIn; `Apply` routes to the company website or job board.
- LinkedIn can save resumes and screening answers for reuse, so agents must review prefilled data before final submit.
- LinkedIn has Easy Apply limits intended to reduce automated/high-speed submissions.
- LinkedIn saved jobs and job alerts are useful queue tools, but this folder's tracker remains the durable state.

Useful LinkedIn Help references:

- Filter and sort job search results: `https://www.linkedin.com/help/linkedin/answer/a507441/filter-and-sort-job-search-results`
- Apply for jobs on LinkedIn: `https://www.linkedin.com/help/linkedin/answer/a512388/apply-for-jobs-on-linkedin`
- Apply directly on LinkedIn / Easy Apply: `https://www.linkedin.com/help/linkedin/answer/a512353`
- Saved application information: `https://www.linkedin.com/help/linkedin/answer/a507694/save-your-job-application-information`
- Job alerts: `https://www.linkedin.com/help/linkedin/answer/a511279/job-alerts-on-linkedin`
- Saved jobs: `https://www.linkedin.com/help/linkedin/answer/a513247`
- Report broken, incorrect, scam, or spam jobs: `https://www.linkedin.com/help/linkedin/answer/a513290/reporting-jobs-on-linkedin`
