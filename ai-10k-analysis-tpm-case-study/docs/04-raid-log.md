# RAID Log

## AI-Powered 10-K Analysis Platform

## 1. Purpose

This log tracks the major risks, assumptions, issues, and dependencies that may affect the MVP’s scope, schedule, quality, security, cost, or launch readiness.

The log will be reviewed during each weekly program review and updated when new evidence changes an item’s probability, impact, status, or response plan.

---

## 2. Status Definitions

| Status     | Meaning                                                                      |
| ---------- | ---------------------------------------------------------------------------- |
| Open       | Item requires monitoring or action                                           |
| Mitigating | Response actions are in progress                                             |
| Escalated  | The item requires a priority or decision outside the current execution level |
| Closed     | The item has been resolved, validated, accepted, or is no longer relevant    |

---

## 3. Risk Register

| ID   | Risk                                                                                                                                                | Probability | Impact   | Trigger                                                                             | Mitigation                                                                         | Contingency                                                               | Owner         | Status |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | -------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------- | ------ |
| R-01 | Because filing structures vary, the platform may fail to extract supported sections for some companies, reducing MVP coverage and delaying testing. | High        | High     | Fewer than three of five sample filings are extracted successfully                  | Test several filing structures early and separate extraction logic by section      | Limit the MVP to validated formats and document unsupported cases         | Project owner | Open   |
| R-02 | The AI may generate claims that are not supported by the source filing, creating accuracy and user-trust risk.                                      | Medium      | Critical | Unsupported-claim rate exceeds the MVP target during manual review                  | Require citations, use structured prompts, and validate claims against source text | Block or label unsupported outputs and narrow the summary scope           | Project owner | Open   |
| R-03 | Financial values may be extracted or summarized incorrectly, leading to misleading analysis.                                                        | Medium      | Critical | Generated numbers do not match the original filing during validation                | Add source comparison tests and avoid summarizing values without references        | Remove unreliable numerical summaries from the MVP until corrected        | Project owner | Open   |
| R-04 | Large filings or long AI inputs may increase response time and processing cost beyond the MVP budget.                                               | High        | Medium   | Cost per analysis or P95 response time exceeds the approved target                  | Process only selected sections, use text chunking, and track token usage           | Reduce section size, limit usage, or use a lower-cost processing approach | Project owner | Open   |
| R-05 | Dependence on external filing and AI services may cause timeouts or incomplete analyses.                                                            | Medium      | High     | Repeated external-service errors or timeout rate exceeds the target                 | Define timeout, retry, and error-handling behavior                                 | Return a clear failure state and allow the analysis to be retried later   | Project owner | Open   |
| R-06 | API credentials or uploaded content could be exposed through source control or logging.                                                             | Low         | Critical | Secrets appear in repository history or logs contain protected content              | Use environment variables, `.gitignore`, and minimal logging                       | Revoke exposed credentials, remove sensitive data, and rotate secrets     | Project owner | Open   |
| R-07 | Optional features may expand the MVP and delay the primary workflow.                                                                                | Medium      | High     | New features are added without removing scope or changing the timeline              | Maintain a must-have scope and use formal change assessment                        | Move noncritical features to a future-release backlog                     | Project owner | Open   |
| R-08 | A one-person project may face capacity constraints across design, development, testing, and documentation.                                          | High        | Medium   | Critical-path milestones repeatedly move or planned work exceeds available capacity | Limit concurrent work and prioritize the critical path                             | Reduce MVP scope or revise the delivery forecast                          | Project owner | Open   |

---

## 4. Assumption Log

| ID   | Assumption                                                                                                              | Validation Method                                                             | Validation Deadline                       | Impact if False                                                   | Owner         | Status |
| ---- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------- | ----------------------------------------------------------------- | ------------- | ------ |
| A-01 | Public 10-K filings will be accessible through a reliable public source.                                                | Compare filing-source options and retrieve sample filings                     | Before filing-development work begins     | Filing retrieval architecture and schedule must change            | Project owner | Open   |
| A-02 | The Business, Risk Factors, and MD&A sections can be identified consistently for the initial sample companies.          | Test section extraction across at least five filings                          | End of filing-processing proof of concept | MVP coverage must be narrowed or extraction logic expanded        | Project owner | Open   |
| A-03 | Important generated claims can be linked to supporting text at an acceptable quality level.                             | Manually review a defined sample of claims and citations                      | Before quality-readiness review           | The product’s core trust proposition may not be viable            | Project owner | Open   |
| A-04 | A modular application can support the MVP without requiring a microservices architecture.                               | Review scale, deployment, and component boundaries during architecture design | Before implementation begins              | Architecture may require greater complexity and additional effort | Project owner | Open   |
| A-05 | A limited development and monthly usage budget will be sufficient for prototype testing.                                | Estimate hosting and AI usage, then compare actual prototype costs            | Before end-to-end testing                 | Scope, model choice, or testing volume may need adjustment        | Project owner | Open   |
| A-06 | Users will find structured summaries with citations more useful than an unrestricted chat experience for the first MVP. | Conduct structured review with sample users or reviewers                      | Before MVP-readiness decision             | User interface and workflow may require redesign                  | Project owner | Open   |

---

## 5. Issue Log

There are currently no confirmed execution issues. The program is in the design phase.

An item will be added here only when a problem is actively occurring and requires resolution.

| ID | Issue            | Impact | Recovery Action | Owner | Target Resolution | Status |
| -- | ---------------- | ------ | --------------- | ----- | ----------------- | ------ |
| —  | No active issues | —      | —               | —     | —                 | —      |

---

## 6. Dependency Log

| ID   | Dependency                   | Provider                        | Consumer                         | Committed Date  | Needed-By Date                  | Impact if Late                                                 | Mitigation                                            | Owner         | Status |
| ---- | ---------------------------- | ------------------------------- | -------------------------------- | --------------- | ------------------------------- | -------------------------------------------------------------- | ----------------------------------------------------- | ------------- | ------ |
| D-01 | Filing-source decision       | Project owner                   | Filing-processing workstream     | To be confirmed | Before retrieval development    | Development cannot begin with a stable integration approach    | Compare options during architecture planning          | Project owner | Open   |
| D-02 | Extracted filing sections    | Filing-processing workstream    | AI-analysis workstream           | To be confirmed | Before end-to-end AI testing    | Summary and citation testing will be blocked                   | Use saved public sample text for early AI experiments | Project owner | Open   |
| D-03 | AI-service decision          | Project owner                   | AI-analysis and cost workstreams | To be confirmed | Before prototype implementation | Prompt, integration, and cost testing cannot be finalized      | Define a provider-independent analysis interface      | Project owner | Open   |
| D-04 | Section-output data contract | Filing-processing workstream    | Backend and AI workstreams       | To be confirmed | Before integration              | Components may produce incompatible formats                    | Define a temporary JSON contract early                | Project owner | Open   |
| D-05 | Backend API contract         | Backend workstream              | User-interface workstream        | To be confirmed | Before UI integration           | Frontend integration may be delayed                            | Develop the interface with mock responses             | Project owner | Open   |
| D-06 | Quality-review criteria      | Product and quality workstreams | Launch-readiness review          | To be confirmed | Before formal testing           | Accuracy and citation quality cannot be evaluated consistently | Define a manual review rubric before testing          | Project owner | Open   |
| D-07 | Monitoring and usage data    | Backend workstream              | Cost and readiness workstreams   | To be confirmed | Before final readiness review   | Reliability and cost decisions will lack evidence              | Add basic metrics during initial implementation       | Project owner | Open   |

---

## 7. Escalation Rules

An item should be escalated when:

* A critical-path dependency has no committed date
* A high-impact risk trigger occurs
* A critical security or accuracy risk cannot be mitigated within the current plan
* The scope, budget, or MVP date requires a decision
* The same issue remains unresolved through two review cycles
* A contingency plan must be activated

Because this is an independent project, escalation means making and documenting a conscious scope, architecture, budget, or timeline decision rather than silently continuing with an unrealistic plan.

---

## 8. Review Cadence

The RAID log will be reviewed:

* During weekly planning
* At each milestone review
* Before major architecture decisions
* Before end-to-end testing
* During launch readiness
* Whenever a risk trigger occurs

Each review should confirm:

* Whether probability or impact changed
* Whether mitigation actions are working
* Whether assumptions have been validated
* Whether a risk became an issue
* Whether dependency dates remain realistic
* Whether escalation or contingency is required

---

## 9. Current Summary

**Top risks:**

1. Unsupported or inaccurate AI-generated claims
2. Filing-format variability
3. Incorrect financial-value extraction
4. Scope expansion
5. One-person capacity constraints

**Current active issues:** None

**Critical open dependencies:**

1. Filing-source selection
2. AI-service selection
3. Section-output data contract
4. Quality-review criteria
