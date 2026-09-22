# Application Plan

This file contains stable candidate facts and answer rules only. Execution belongs to `START_HERE_AUTOPILOT.md`; role filters to `RECENCY_PREFLIGHT.md`; tracker behavior to `TRACKER_SCHEMA.md`; recovery to `AUTOPILOT_BLOCKER_PLAYBOOK.md`.

## Canonical Files

| Use | File |
|---|---|
| AI resume | `AI_ROLES/Yaswanth_Muppalla_AI_Resume.pdf` |
| AI DOCX fallback | `AI_ROLES/Yaswanth_Muppalla_AI_Resume.docx` |
| AI text fallback | `AI_ROLES/Yaswanth_Muppalla_AI_Resume.txt` |
| SDE resume | `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.pdf` |
| SDE DOCX fallback | `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.docx` |
| SDE text fallback | `SDE_ROLES/Yaswanth_Muppalla_SDE_Resume.txt` |
| Private/form-only values | `PRIVATE_APPLICATION_FIELDS.md` |

Use PDF by default, DOCX when parsing is better or required, and text only when upload/parsing is unreliable. Verify the visible attached filename before submission.

## Resume Routing

- **AI resume:** AI systems are central—LLM/RAG/retrieval, agents/MCP/tooling, AI evaluation/serving/observability/platform, LLMOps/MLOps, data/AI pipelines, or backend-to-AI products.
- **SDE resume:** general backend APIs/services, Java/Python, distributed systems, cloud/platform/data infrastructure, reliability, or backend-heavy full stack is central and AI is peripheral.
- Assign exactly one lane and resume per requisition. The word `AI` in a title does not decide the lane; central responsibilities do.

## Candidate And Contact Sources

- Legal/resume name: Yaswanth Muppalla.
- Current city/state: Atlanta, GA.
- Use the selected canonical resume for current email, phone, LinkedIn, GitHub, and portfolio links.
- Use `PRIVATE_APPLICATION_FIELDS.md` only inside an official form for the full address, identity values, exact legal/private selections, or other values intentionally kept form-only.
- Never copy private/form-only values into trackers, public Markdown, logs, screenshots, summaries, browser notes, shell commands, or Git.

## Work Authorization

| Question | Answer |
|---|---|
| Legally authorized to work in the United States? | Yes. |
| Require sponsorship now or in the future? | Yes. |
| Visa support | H-1B transfer. |
| Can provide identity/employment authorization after hire? | Yes. |
| At least 18 years old? | Yes. |

Skip roles that explicitly provide no visa/immigration support, cannot transfer H-1B, require no current/future sponsorship, or require citizenship, permanent residency, U.S.-person status, incompatible export eligibility, or clearance.

## Location, Availability, And Work Preferences

- Current location: Atlanta, GA.
- Role search location comes only from the active `BATCH FILTERS`; if unspecified, use `RECENCY_PREFLIGHT.md`.
- Open to Remote US and to hybrid/onsite work only when the advertised role location passes the active batch.
- Open to relocation for a qualifying role in an allowed batch location.
- Willing to travel when the role requires reasonable business travel.
- Earliest start: two weeks after offer acceptance unless Yaswanth supplies a newer answer.
- Full-time employment preferred. Contract and contract-to-hire: No by default.

For an Atlanta requisition, `I am local to where the job is posted` is truthful. Never relabel an outside-location job as Atlanta or Remote because Yaswanth can relocate.

## Compensation Rules

The active salary filter determines whether a role is eligible. Desired compensation is a candidate preference; salary history is a material fact and must never be invented.

- Text field: `Open to discussing compensation based on the role level, scope, location, and posted range.`
- Required desired-base number with an applicable posted range: use the midpoint rounded to the nearest `$5,000`, clamped inside the range and strictly above the active batch minimum.
- If the midpoint is not above the minimum but the range still qualifies, use the smallest `$5,000` increment above the minimum that remains inside the range.
- If the role legitimately passed the salary gate through other official evidence but the form itself shows no range, use the active batch minimum plus `$10,000`, rounded to the nearest `$5,000`, as a negotiable desired-base preference—not as salary history.
- Never enter a number below the active batch floor merely to submit. Never claim an employer's undisclosed range.

## Education

| Field | Answer |
|---|---|
| Highest degree | Master of Science, Computer Science |
| Graduate school | State University of New York, New Paltz |
| Graduate completion | May 2020 |
| Graduate GPA | 3.6/4.0 |
| Bachelor degree | Bachelor of Technology |
| Bachelor school | JNTUK |
| Bachelor completion | 2018 |
| Bachelor CGPA | 8.5/10 |

If an ATS lacks `Bachelor of Technology`, `Bachelor of Engineering` is the closest truthful option. Leave an undocumented bachelor field of study blank or `No Response` rather than inventing one.

## Experience And Skills

| Field | Answer |
|---|---|
| Professional software experience | 6+ years from the visible resume timeline; do not claim 7+ without newer confirmation. |
| Python | 4+ years. |
| Java/Spring | 3+ years. |
| AWS | 5+ years. |
| AI/LLM/RAG | 2+ years based on OmInsights from January 2024; do not extend earlier without evidence. |
| Angular/TypeScript | 1+ years. |
| Data engineering | 5+ years. |
| Management | Technical/project leadership only; do not claim people management. |
| Open source/portfolio | OmInsights GitHub/portfolio project; use only visible evidence for numeric contribution fields. |

Do not inflate years, skills, titles, leadership, certifications, or metrics to match a JD.

## OmInsights Classification

OmInsights is a personal technical portfolio/learning project. It is not an employer, active company/product business, client-serving business, consulting/advisory role, revenue activity, secondary employment, or outside work Yaswanth is committing to continue after joining.

Agents may use OmInsights as technical evidence for backend-to-AI platform engineering, RAG, Context Engine orchestration, MCP/tool execution, source-backed answers, and AWS-style deployment patterns.

For ordinary compliance questions caused only by OmInsights:

| Pattern | Answer |
|---|---|
| Continue OmInsights as outside work after joining? | No. |
| Outside business activity or secondary employment? | No; it is a personal learning/portfolio project. |
| Active founder/adviser/board/business ownership role? | No. |
| Pre-existing project/IP disclosure with explanation allowed? | Pre-existing personal technical portfolio project for learning and skill demonstration, with no customers, revenue, or employer confidential information. |

Use manual review only when a form forces a materially different personal legal certification that cannot be answered from authorized facts.

## Ordinary Form Defaults

| Field | Default |
|---|---|
| Discovery source | Use the truthful source: LinkedIn, company careers page, Indeed, referral, or other visible source. Never invent a referral. |
| Consent to process application data | Yes. |
| Job-related SMS recruiting messages | Yes when job-related; No for unrelated marketing. |
| AI-assisted application review | Yes. |
| Talent community | Yes unless it creates unrelated marketing burden. |
| Cover letter | Create a concise tailored letter only when required or clearly useful. |

For EEO, disability, veteran, citizenship, conflicts, relationships, disciplinary history, criminal history, employer-client relationships, agreements, identity values, and other legal/private fields, use a materially identical documented answer from `PRIVATE_APPLICATION_FIELDS.md`. Do not generalize company-specific wording or infer from absence.

References, referrals, licenses, and certifications require real documented names/evidence. Never invent them.

## Answer Rule

Use the single ladder in `AGENTS.md`: newest identical confirmed answer -> documented profile/private answer -> objective resume/JD/company inference -> conservative candidate-aligned default for a required non-material preference -> blank/`N/A` when allowed.

Tailor short prose from `ANSWER_BANK.md` without asking for approval. If an employer explicitly prohibits AI assistance or requires an applicant-authored response, fill objective fields and park only that response while continuing the batch.
