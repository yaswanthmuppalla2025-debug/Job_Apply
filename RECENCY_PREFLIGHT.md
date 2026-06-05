# Recency Preflight

Use this before spending time on a form. The goal is to save tokens and apply only to fresh, quality, non-duplicate roles.

## Rule

Autopilot applies only to roles verified as posted or genuinely reposted within the last 15 days.

- `0-7 days`: apply first.
- `8-15 days`: apply only when the resume/JD match is strong.
- `>15 days`: skip.
- Unknown date: skip unless reliable dated evidence proves the role is within 15 days.

Do not stop the run because a date is unavailable. Skip the role as unknown/stale and continue to fresher roles.

## Quality, Location, And Duplicate Gate

Before filling a form, run these quick checks after the recency check:

1. Quality: prefer direct employer roles at product, AI, SaaS, platform, cloud, fintech, enterprise, healthcare-tech, infrastructure, major-retail, transportation, or similar durable companies. Skip random staffing, consulting, vendor, recruiter, W2-only, client-confidential, and aggregator-proxy postings.
2. Location: prioritize Georgia/Atlanta, Dallas/Austin/Texas, Virginia, Texas, North Carolina, Tennessee, Florida, and Remote US. Treat SF/Bay Area/California as the last option unless the company and role are unusually strong.
3. Duplicate: scan the existing tracker `Role` columns before applying. If the same company has the same normalized role title already submitted/attempted, or the same official job id/application URL is already present, skip as duplicate or `Already Applied`. Do not block a different company just because it has a common title like `Senior Software Engineer`.

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
- `Posting Age Days`
- `Recency Bucket`
- `Recency Proof URL`
- `Open Checked At`

If any of these are not derivable quickly, leave them blank or `Unknown` unless they are needed for the hard gate. The goal is to keep moving, not to turn every metadata field into a blocker.

## Skip Cases

Skip and move on when:

- Posted date is older than 15 days.
- Official page is closed, expired, or no longer accepting applications.
- Recency is unknown and no reliable proof shows the role is within 15 days.
- Aggregator result does not resolve to an official open application page.
- The posting is a low-quality staffing/consulting/vendor/recruiter/aggregator-proxy role.
- The same company and normalized role title, official job id, or application URL is already present in the trackers.

Status mapping:

- Stale, closed, expired, no-sponsorship, fit-mismatch, staffing, consulting, vendor, recruiter, client-confidential, aggregator-proxy, or low-value location/source choices: skip without logging broad cache noise.
- Same-company same-role, same official job id, same application URL, or portal-proven prior submission: record `Already Applied` in the appropriate `AI` or `SDE` sheet when proof is clear; otherwise skip and continue.

Continue to the next fresh role immediately.
