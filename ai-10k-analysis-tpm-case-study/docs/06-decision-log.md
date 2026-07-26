# Decision Log

## AI-Powered 10-K Analysis Platform

## 1. Purpose

This log records important product, architecture, security, quality, cost, and delivery decisions for the AI-Powered 10-K Analysis Platform.

The purpose is to preserve the context behind each decision, make trade-offs visible, prevent repeated discussions without new evidence, and track follow-up actions.

---

## 2. Decision Status Definitions

| Status     | Meaning                                                    |
| ---------- | ---------------------------------------------------------- |
| Proposed   | A recommendation has been prepared but is not yet approved |
| Approved   | The decision is final for the current program phase        |
| Deferred   | The decision has been intentionally postponed              |
| Reversed   | The original decision was changed based on new evidence    |
| Superseded | A later decision replaced this decision                    |

---

## 3. Decision Summary

| ID     | Decision                                                        | Owner                             | Status   |
| ------ | --------------------------------------------------------------- | --------------------------------- | -------- |
| DEC-01 | Focus the MVP on one primary user and one filing at a time      | Product Owner                     | Approved |
| DEC-02 | Support three 10-K sections in the first MVP                    | Product Owner                     | Approved |
| DEC-03 | Require source citations for important generated claims         | Product Owner and Quality Owner   | Approved |
| DEC-04 | Process only public-company filings in the MVP                  | Product Owner and Security Owner  | Approved |
| DEC-05 | Use a modular monolith for the initial application architecture | Engineering Lead                  | Proposed |
| DEC-06 | Keep the AI-service integration provider-independent            | Engineering Lead and AI/Data Lead | Proposed |
| DEC-07 | Use an asynchronous analysis workflow with visible status       | Engineering Lead                  | Proposed |
| DEC-08 | Avoid long-term storage of full filing content during the MVP   | Security Owner                    | Proposed |
| DEC-09 | Establish performance targets after baseline testing            | Engineering Lead and TPM          | Approved |
| DEC-10 | Defer company comparison and advanced table extraction          | Product Owner                     | Approved |

---

# 4. Detailed Decisions

## DEC-01: Define one primary MVP user

**Date:** Initial program-design phase
**Owner:** Product Owner
**Status:** Approved

### Problem

Potential users include students, investors, analysts, and corporate strategy professionals. Designing equally for every group would create unclear and competing requirements.

### Options Considered

1. Design for all potential financial users
2. Design primarily for professional investment analysts
3. Design primarily for MBA students and early-career analysts

### Decision

Design the first MVP primarily for an MBA student or early-career financial analyst reviewing a public-company 10-K.

### Criteria

* Clarity of user need
* Simplicity of the first workflow
* Ease of user testing
* Alignment with the project owner’s finance and MBA experience
* Ability to demonstrate value with a limited MVP

### Rationale

A clearly defined primary user produces more focused requirements and allows the MVP to test one core problem: reviewing selected 10-K sections efficiently while maintaining source traceability.

### Trade-off

The first MVP may not satisfy all requirements of senior investment professionals or enterprise research teams.

### Follow-Up

Evaluate secondary-user requirements after the primary workflow is validated.

---

## DEC-02: Limit the supported filing sections

**Date:** Initial program-design phase
**Owner:** Product Owner
**Status:** Approved

### Problem

A 10-K contains many sections, financial statements, tables, and notes. Supporting the entire filing in the first version would significantly increase extraction, testing, and quality complexity.

### Options Considered

1. Analyze the entire 10-K
2. Support only narrative sections
3. Support narrative sections and complex financial tables

### Decision

Support these three sections in the MVP:

* Business
* Risk Factors
* Management’s Discussion and Analysis

### Criteria

* User value
* Technical complexity
* Filing-format consistency
* Quality-validation effort
* MVP timeline

### Rationale

These sections provide meaningful business and risk information while avoiding the initial complexity of advanced financial-table extraction.

### Trade-off

The MVP will not provide complete financial-statement analysis.

### Follow-Up

Evaluate financial-table extraction as a later phase after the narrative workflow is stable.

---

## DEC-03: Require citations for important claims

**Date:** Initial program-design phase
**Owner:** Product Owner and Quality Owner
**Status:** Approved

### Problem

AI-generated summaries may include claims that are incomplete, inaccurate, or unsupported by the original filing.

### Options Considered

1. Provide summaries without citations
2. Provide citations only when users request them
3. Require citations for important financial and business claims

### Decision

Important generated claims must include a reference to supporting source text.

### Criteria

* User trust
* Accuracy
* Traceability
* Quality-testing feasibility
* Financial-analysis risk

### Rationale

Source traceability is central to the product’s value and helps users verify generated analysis.

### Trade-off

Citation generation and validation add processing time, implementation complexity, and testing effort.

### Follow-Up

Define a manual citation-quality rubric before formal testing.

---

## DEC-04: Process only public filings

**Date:** Initial program-design phase
**Owner:** Product Owner and Security Owner
**Status:** Approved

### Problem

Allowing arbitrary document uploads may introduce confidential, copyrighted, sensitive, or unsupported content.

### Options Considered

1. Allow any uploaded financial document
2. Support public filings and private uploads
3. Restrict the first MVP to public-company filings

### Decision

The first MVP will process only publicly available 10-K filings.

### Criteria

* Security
* Privacy
* Legal and data-handling risk
* MVP simplicity
* Testing consistency

### Rationale

Restricting the MVP to public filings lowers privacy and security risk and provides a more consistent source for development and testing.

### Trade-off

Users cannot analyze private or internal company documents.

### Follow-Up

Revisit controlled uploads only after authentication, authorization, retention, and security requirements are designed.

---

## DEC-05: Use a modular monolith for the MVP

**Date:** Architecture-design phase
**Owner:** Engineering Lead
**Status:** Proposed

### Problem

The application needs logical separation between filing retrieval, document processing, AI analysis, result handling, and the user interface. However, the expected MVP scale is limited and the project is independently developed.

### Options Considered

1. Traditional monolith with tightly connected components
2. Modular monolith
3. Microservices
4. Multiple independent serverless functions

### Proposed Decision

Use a modular monolith for the initial MVP.

### Criteria

* Development speed
* Deployment simplicity
* Cost
* Maintainability
* Testing effort
* Expected scale
* Future ability to separate components

### Rationale

A modular monolith provides clear internal component boundaries without the deployment, networking, monitoring, and operational complexity of microservices.

### Trade-Off

Individual components cannot be scaled or deployed independently as easily as separate services.

### Follow-Up

Reevaluate the architecture if usage, team size, deployment frequency, or scaling needs increase materially.

---

## DEC-06: Keep AI-service integration provider-independent

**Date:** Architecture-design phase
**Owner:** Engineering Lead and AI/Data Lead
**Status:** Proposed

### Problem

The project needs an AI service, but model cost, quality, latency, availability, and capabilities may change during development.

### Options Considered

1. Connect application logic directly to one AI provider
2. Build an internal interface that separates application logic from the selected provider
3. Support multiple providers in the first MVP

### Proposed Decision

Create a simple internal analysis interface that separates the application’s business logic from the selected AI provider.

### Criteria

* Reversibility
* Testing
* Maintainability
* Provider cost
* Future model comparison
* MVP complexity

### Rationale

A provider-independent interface makes it easier to change or test models without redesigning the complete application.

### Trade-Off

The abstraction adds some initial development work and should remain simple to avoid unnecessary overengineering.

### Follow-Up

Select one provider for the first implementation and avoid building full multi-provider routing until it is needed.

---

## DEC-07: Use asynchronous analysis processing

**Date:** Architecture-design phase
**Owner:** Engineering Lead
**Status:** Proposed

### Problem

Retrieving a filing, extracting sections, calling an AI service, and validating results may take longer than a normal web request.

### Options Considered

1. Keep the browser request open until analysis finishes
2. Create an asynchronous analysis job and return a status identifier
3. Process the entire workflow manually during the prototype

### Proposed Decision

Use an asynchronous workflow:

1. User submits an analysis
2. System returns an analysis identifier
3. System processes the filing
4. User interface checks the analysis status
5. Results are displayed when processing completes

### Criteria

* Timeout risk
* User experience
* Reliability
* Retry behavior
* Observability
* Implementation complexity

### Rationale

An asynchronous process reduces the risk of request timeouts and allows the system to display submitted, processing, completed, or failed states.

### Trade-Off

The design requires status tracking and additional backend logic.

### Follow-Up

Measure prototype processing time. A simpler synchronous workflow may be used temporarily if baseline processing is consistently short.

---

## DEC-08: Minimize filing-content retention

**Date:** Security-design phase
**Owner:** Security Owner
**Status:** Proposed

### Problem

Storing full document content increases storage, privacy, security, and retention responsibilities.

### Options Considered

1. Store all filing content permanently
2. Store filing content for a limited period
3. Process content temporarily and retain only required metadata and results

### Proposed Decision

Avoid long-term storage of full filing content during the initial MVP. Retain only information required for testing, traceability, and result display.

### Criteria

* Security
* Privacy
* Storage cost
* Reprocessing cost
* Citation requirements
* Operational simplicity

### Rationale

Public filings can be retrieved again when needed, while minimizing stored content reduces security and storage obligations.

### Trade-Off

Repeated analyses may require retrieving and processing the same filing again, increasing latency and processing cost.

### Follow-Up

Define the exact data-retention period after the filing source and citation design are finalized.

---

## DEC-09: Establish performance targets after baseline testing

**Date:** Requirements phase
**Owner:** Engineering Lead and TPM
**Status:** Approved

### Problem

The team does not yet have evidence about filing sizes, processing time, model latency, or infrastructure performance.

### Options Considered

1. Select an arbitrary response-time target immediately
2. Avoid defining performance targets
3. Measure a baseline and then approve realistic targets

### Decision

Measure average and P95 response time during prototype testing and establish the final MVP performance target using baseline evidence.

### Criteria

* Accuracy of planning
* User experience
* Technical feasibility
* Cost
* Testability

### Rationale

Targets should be measurable and evidence-based rather than invented before the architecture and processing workflow are known.

### Trade-Off

The final response-time SLO cannot be approved during the earliest design phase.

### Follow-Up

Complete baseline performance testing before the quality and launch-readiness review.

---

## DEC-10: Defer company comparison and advanced table extraction

**Date:** Initial program-design phase
**Owner:** Product Owner
**Status:** Approved

### Problem

Company comparison and advanced financial-table extraction would add data normalization, extraction, user-interface, and quality complexity.

### Options Considered

1. Include both capabilities in the first MVP
2. Include only company comparison
3. Include only financial tables
4. Defer both capabilities

### Decision

Defer company comparison and advanced table extraction until after the primary filing-summary workflow is validated.

### Criteria

* MVP timeline
* Critical-path impact
* User value
* Quality risk
* Engineering capacity

### Rationale

Neither capability is necessary to prove the core value of producing structured, source-supported summaries.

### Trade-Off

The first MVP will provide narrower analytical functionality.

### Follow-Up

Add both capabilities to the future-release backlog and reassess them using user feedback.

---

# 5. Decision Review Rules

A decision may be revisited when:

* New technical evidence appears
* A key assumption becomes false
* User testing changes the product requirement
* Cost or performance differs materially from the baseline
* A security or quality risk changes
* Program scale or team structure changes

A decision should not be reopened only because someone prefers another option.

---

# 6. Decision Meeting Template

Every major decision review should answer:

1. What problem requires a decision?
2. Who is accountable for the decision?
3. When is the decision needed?
4. What options were evaluated?
5. What criteria were used?
6. What is the recommendation?
7. What trade-off are we accepting?
8. What actions follow the decision?
9. What evidence would cause us to revisit it?

---

# 7. Current Decisions Requiring Validation

Before implementation begins, validate:

* DEC-05: Modular monolith architecture
* DEC-06: Provider-independent AI-service interface
* DEC-07: Asynchronous processing workflow
* DEC-08: Filing-content retention approach
