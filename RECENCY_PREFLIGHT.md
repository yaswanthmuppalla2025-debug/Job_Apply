# Recency Preflight

Use this before spending time on a form. The goal is to save tokens and apply only to fresh, strong-fit, quality, non-duplicate roles.

## Rule

Autopilot applies to roles verified as posted or genuinely reposted within the last 15 days by default. For the strongest AI matches only, Yaswanth allows a live-post exception through 120 days when the official employer/ATS page is still accepting applications, the location is in-bounds, sponsorship answers can be truthful, and the JD evidence meets the exceptional-fit rule below.

- `0-7 days`: apply first.
- `8-15 days`: apply only when the resume/JD match is strong.
- `16-120 days`: AI roles only. Apply only when the match is exceptional, the official posting is live, and at least 3 primary JD responsibilities are resume-backed, including a core backend-to-AI, API, or platform responsibility. There must be no hard must-have mismatch.
- `>120 days`: skip even when the page is still live.
- Unknown date: skip unless reliable dated evidence proves the role is within 15 days.

Do not stop the run because a date is unavailable. Skip the role as unknown/stale and continue to fresher roles.

## Fit, Quality, Location, And Duplicate Gate

Before filling a form, run these quick checks after the recency check:

0. Company hard block: skip every Capital One role before `2027-01-07`, across AI, SDE, LinkedIn, Workday, and any recruiter/ATS source. Recent Power Day feedback showed hire-level alignment below the applied level, but Capital One cannot provide sponsorship support at that eligible level right now; do not spend tokens on Capital One until the 6-month reattempt window.
1. Fit: submit only `High`/`Strong` lane matches. `Medium` is a skip unless it is a `Strategic Exception` inside the normal 0-15 day window with target geography/company quality, at least 3 primary JD responsibilities backed by the resume, at least one core backend-to-AI/API/platform responsibility, and no hard must-have mismatch. `Strategic Exception` cannot justify a 16-120 day role.
   - For AI roles, Yaswanth's strongest center of gravity is backend-to-AI/platform work: LLM/RAG systems, agentic workflows, AI product/backend engineering, LLMOps/MLOps infrastructure, retrieval platforms, evaluation/serving/tooling, and cloud data pipelines.
   - Do not treat `embeddings`, `retrieval`, `ML systems`, or `AI platform` keywords as sufficient. Read the real JD responsibilities and candidate profile. If the hiring manager primarily needs a deep ML model owner, recommender/personalization strategist, research scientist, distributed-training lead, or domain-modeling specialist, skip unless the role is clearly platform/tooling/serving-heavy.
   - Before submitting a mixed AI role, ask: would the hiring manager see Yaswanth as a backend-to-AI platform builder for this role, or expect a deep ML model/research owner? If the second is true, skip or mark it as a low-confidence stretch; do not submit it just for volume. If credible backend/API/platform/RAG/agent plumbing overlap exists, keep moving rather than over-filtering.
2. Quality: prefer direct employer roles at product, AI, SaaS, platform, cloud, fintech, enterprise, healthcare-tech, infrastructure, major-retail, transportation, or similar durable companies. Skip random staffing, consulting, vendor, recruiter, W2-only, client-confidential, and aggregator-proxy postings.
3. Location: apply only to Remote US, Georgia/Atlanta, Dallas/Austin/Texas, Virginia/DC, North Carolina, Tennessee, or Florida. Skip SF/Bay Area/California/west-only roles even when the company is attractive; keep California-based companies only when the specific role is truly Remote US and does not require west-coast presence.
4. Duplicate: extract the official ATS/requisition/job ID when visible and scan it with `Company`, `Role`, and `Application URL` across `AI`, `SDE`, and `Blockers` before filling. Treat tracking parameters and terminal `/apply`, `/confirmation`, or `/thanks` variants as the same URL when they identify the same requisition; a generic portal or confirmation URL is not a job ID. An exact ID/canonical URL already `Submitted`/`Already Applied`, or a portal-proven prior submission, is a hard duplicate. An exact match in `Blockers` means do not start a second application; resume and update that existing row only when it is dynamically retry-eligible. Same company plus the same normalized title with a different or unknown ID requires a quick team/location/JD comparison: submit when materially distinct, otherwise skip or record `Already Applied` when proof is clear. A common title at another company is not a duplicate. Re-read the newest workbook immediately before final submit; stop if another agent submitted or separately claimed the job, but allow the current eligible blocker retry to match its own row.
5. Company spread: after 3 applications or attempts at the same normalized company within 30 days, run one focused job-Gmail search for that company. Recruiter contact, an assessment, an interview, or hiring-team follow-up is a positive signal; a generic receipt, rejection, or silence is not. Without a positive signal, submit another role there only when it is a materially different requisition/team and still `High` or exceptional fit; otherwise rotate to another qualified employer. Silence alone never creates a permanent company hard block. Obey any explicit employer/ATS application cap or user-directed cooldown.

## Fast Source Order

Prefer these sources, in order:

1. Official company careers page or ATS job page.
2. Public ATS data embedded in the official page.
3. Public ATS API when available.
4. Reliable dated search result only as a quick fallback.

Use aggregators for discovery, but submit through the official company or ATS application URL whenever possible.

## ATS Date Signals

| ATS | Preferred Date Signal |
|---|---|
| Greenhouse | `first_published` from the public Job Board API. Treat it as stricter than `updated_at`. |
| Ashby | JobPosting JSON-LD `datePosted` on the Ashby role page. |
| Lever | Public posting `createdAt` from Lever posting data when available. |
| Workday | JobPosting JSON-LD `datePosted` on the Workday role page when exposed. |
| Workable | JobPosting JSON-LD `datePosted`. |
| Eightfold / Phenom | JobPosting JSON-LD `datePosted` when exposed. |
| Indeed / LinkedIn / Aggregators | Use only as discovery or fallback proof; prefer official source before applying. |

## Reposted Or Refreshed Roles

Use a refreshed/updated date only when the official page clearly indicates the role was recently reposted, refreshed, or reopened.

Do not let a newer `updated_at` hide an old first-published date on evergreen roles unless there is clear repost/reopen evidence.

## What To Record

When applying, fill what is available in `JOB_APPLICATION_TRACKER.xlsx`:

- `Posted Date`
- `Age Days`
- `Recency Proof`
- `Application URL`
- `Fit`

If any of these are not derivable quickly, leave them blank or `Unknown` unless they are needed for the hard gate. The goal is to keep moving, not to turn every metadata field into a blocker.

## Skip Cases

Skip and move on when:

- Company is Capital One and today's date is before `2027-01-07`.
- Posted date is 16-120 days and the role is not an exceptional AI-role match under the live-post rule.
- Posted date is older than 120 days.
- Official page is closed, expired, or no longer accepting applications.
- Recency is unknown and no reliable proof shows the role is within 15 days.
- Location is SF/Bay Area/California/west-only, or any place outside the current allowed geography, unless the role itself is explicitly Remote US.
- Aggregator result does not resolve to an official open application page.
- Fit is low, unknown, merely adjacent, or medium without a strategic-exception reason.
- The posting is a low-quality staffing/consulting/vendor/recruiter/aggregator-proxy role.
- The same official job ID/canonical role URL is already submitted/already applied, another active blocker owns the attempt, portal proof shows a prior submission, or the same-company/title comparison shows it is not a materially distinct requisition.

Status mapping:

- Stale, closed, expired, no-sponsorship, fit-mismatch, staffing, consulting, vendor, recruiter, client-confidential, aggregator-proxy, or low-value location/source choices: skip without logging broad skip-noise.
- Exact/non-distinct job already submitted/already applied, or portal-proven prior submission: record `Already Applied` in the appropriate `AI` or `SDE` sheet when proof is clear; otherwise skip. An exact `Blockers` match stays in and updates that row when retry-eligible.

Continue to the next fresh role immediately.
