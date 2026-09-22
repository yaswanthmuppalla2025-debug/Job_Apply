# Role Preflight

This file is the sole owner of role eligibility and ranking filters. Run it once before filling; do not re-litigate a passed role unless the live page reveals new evidence.

## Filter Precedence

A current user instruction or `BATCH FILTERS` block overrides only the dimensions it specifies. Unspecified dimensions use the defaults below. Old dated snapshots, earlier campaign filters, memory, and search history never override the current launch. A standing employer hard block remains active unless the current instruction explicitly reopens that employer; omission from an exclusion list is not reopening.

Batch filters cannot waive truthfulness, exact official-role verification, sponsorship/eligibility, duplicate protection, confirmation proof, or platform/security boundaries.

## Workspace Defaults

| Dimension | Default |
|---|---|
| Lane | The lane launched by the user: AI, SDE, or both. |
| Fit | `High` or `Strong` only. |
| Location | Atlanta metro or nationwide Remote US only. `Atlanta` does not mean all of Georgia unless the batch says Georgia. |
| Recency | Up to 120 days when the exact official role is still open and the fit gate passes; fresher roles rank higher. |
| Seniority | Hands-on senior engineering scope compatible with roughly 6+ years and a master's degree. Roles requiring 5-7 years are normal; mandatory 8+ years proceed only when the exact resume timeline supports it. Judge responsibilities, not title alone. |
| Salary | Advertised candidate-applicable base compensation above `$130,000`. |
| Sources | All reputable discovery sources; submit through the exact official company/ATS route. |
| Sponsorship | H-1B transfer compatible. Skip explicit no-sponsorship/incompatible eligibility. Silence is not an automatic rejection. |
| Employer | Direct quality employer; skip staffing/vendor/aggregator proxies. |

## One-Pass Eligibility Gate

A role passes only when every applicable item is true:

1. **Official and open:** exact requisition resolves to a live official company or ATS page accepting applications.
2. **Recency:** official or reliable dated evidence places it inside the active window. Give one quick verification attempt to an unknown date, then skip rather than researching indefinitely.
3. **Central-responsibility fit:** at least three primary JD responsibilities are supported by the selected resume, including the responsibility the hiring manager is chiefly filling. Required years/scope are credible and no hard must-have gap exists.
4. **Lane:** AI-enabled system delivery is central -> AI; general backend/platform delivery is central and AI is peripheral -> SDE.
5. **Seniority:** hands-on Senior, Senior II, Engineer III, Staff, Lead, or Architect scope may qualify when the years and ownership are credible. Skip people-management, executive, organization-wide principal ownership, or deep research/model-science mandates unsupported by the resume.
6. **Location:** use the requisition's advertised work location, not applicant location, employer headquarters, or generic relocation prose. Remote qualifies only when the role itself is open nationwide or explicitly includes Atlanta/Georgia.
7. **Salary:** apply the active batch threshold to advertised base pay that applies to Yaswanth's location. For `>$X`, a range qualifies when its upper bound is above `X`; a single amount must be above `X`. Do not treat bonus/equity/total compensation as base and do not invent missing salary.
8. **Sponsorship and legal eligibility:** skip explicit no-visa/no-transfer/no-current-or-future-sponsorship, citizen/green-card/U.S.-person-only, incompatible export-control, or clearance requirements. If policy is unstated and truthful sponsorship answers remain possible, the role may proceed.
9. **Employer quality:** direct employer role at a credible product, platform, enterprise, fintech, healthcare-tech, retail, transportation, infrastructure, or similar company. Skip recruiter/staffing/consulting/vendor/client-confidential/W2-only/aggregator-proxy postings.
10. **Duplicate:** use `TRACKER_SCHEMA.md`; exact official job ID or canonical requisition URL controls.

Use `High` when the central responsibility and at least four primary duties are directly resume-backed with no meaningful must-have gap. Use `Strong` when the central responsibility and at least three primary duties are directly backed and any remaining gaps are secondary, learnable, or explicitly preferred rather than required.

For AI, prioritize LLM/RAG/retrieval, agents/MCP/tooling, AI product/backend engineering, evaluation/serving/observability, AI platform/LLMOps/MLOps, and data/AI pipelines. Skip roles primarily owning model research, recommender/personalization science, distributed training, CV/speech/domain research, or unsupported model strategy.

For SDE, prioritize backend APIs/services, Java/Python, distributed systems, cloud/platform/data infrastructure, reliability, and backend-heavy full stack. AI keywords are not required.

## Ranking After Eligibility

Rank eligible roles by:

1. Central-responsibility fit and credible level.
2. Freshness and official application viability.
3. Sponsorship confidence and advertised salary strength.
4. Atlanta fit, then nationwide Remote US unless the active batch says otherwise.
5. Employer quality and company spread.

Company spread is a ranking signal, not an automatic rejection. Prefer fresh qualified employers when one company has produced repeated silence, but allow materially distinct High/Strong roles. Explicit company/ATS caps and current user cooldowns remain hard.

## Current Employer Hard Blocks

- Capital One: do not apply before `2027-01-07`.
- Cargill: do not apply during current autopilot batches unless Yaswanth explicitly reopens it. Its absence from a batch exclusion list does not reopen it.

Apply additional employer exclusions only when they appear in the current `BATCH FILTERS` or a newer direct user instruction.

## Source Rotation

Use aggregators and LinkedIn for discovery, then resolve to official company/ATS pages. Rotate among:

- Official company career searches and Workday/company-native portals.
- Greenhouse, Ashby, Lever, Workable, SmartRecruiters, iCIMS, Oracle/Taleo, Phenom/SuccessFactors, and similar public ATS boards.
- LinkedIn and reputable job portals using several title/technology query families.
- Targeted employer searches based on the active lane and location.

Do not wait for a broad pool before applying. As soon as one role passes, place it in the rolling pool and continue discovery while applications are executed.

## Measurable Source Exhaustion

The qualified source pool is genuinely exhausted only after all are true:

- At least four distinct source families above were searched for every active lane.
- At least three materially different query families were used per lane, covering title, responsibility, and core technology terms.
- Two consecutive tranches of at least ten exact official roles each produced no new eligible non-duplicate role.
- Active high/strong retry rows with a currently available distinct recovery path were checked.

Until then, rotate sources and continue. A single empty search, one exhausted company board, or a shortlist with only a few roles is not exhaustion.

## Fast Skip

Skip immediately and continue when the role is closed, outside the active date/location/salary boundary, explicit no-sponsorship/ineligible, low/medium/adjacent fit, inflated beyond credible scope, duplicate, staffing/vendor proxy, or unable to resolve to an exact official requisition. Do not log routine skip noise.
