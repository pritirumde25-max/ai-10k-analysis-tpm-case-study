# Workstreams and Milestones

## AI-Powered 10-K Analysis Platform

## 1. Purpose

This document organizes the MVP into major workstreams, milestones, dependencies, and delivery checkpoints.

The proposed timeline is six weeks. Because this is an independent portfolio project, the timeline represents a planning baseline and may be updated as technical assumptions are tested.

---

## 2. Workstream Overview

| ID    | Workstream                              | Desired Outcome                                                               |
| ----- | --------------------------------------- | ----------------------------------------------------------------------------- |
| WS-01 | Product and Requirements                | Clear user problem, MVP scope, requirements, and success criteria             |
| WS-02 | Filing Retrieval and Processing         | Retrieve a supported 10-K and extract selected filing sections                |
| WS-03 | AI Analysis and Citations               | Generate structured summaries with supporting source references               |
| WS-04 | Backend API and Data Handling           | Connect filing processing, AI analysis, status tracking, and results          |
| WS-05 | User Interface                          | Allow a user to submit and review an analysis                                 |
| WS-06 | Quality, Security, and Launch Readiness | Validate quality, failures, security, monitoring, cost, and release readiness |

---

## 3. Workstream Details

### WS-01: Product and Requirements

**Objective:** Define the problem, users, scope, requirements, success metrics, and open questions.

**Major deliverables:**

* Program charter
* User journey
* Functional and nonfunctional requirements
* Success metrics
* Initial architecture decisions
* Prioritized MVP scope

**Completion criteria:**

* Primary user and core workflow are documented
* Must-have requirements are identifiable
* Out-of-scope capabilities are documented
* Major open questions have owners or decision dates

---

### WS-02: Filing Retrieval and Processing

**Objective:** Retrieve a public-company 10-K filing and extract the supported sections.

**Major deliverables:**

* Filing-source selection
* Ticker validation
* Filing-list retrieval
* 10-K content retrieval
* Business section extraction
* Risk Factors section extraction
* Management’s Discussion and Analysis extraction
* Processing-error handling

**Completion criteria:**

* The system retrieves supported filings for selected sample companies
* The three MVP sections are extracted successfully
* Unsupported formats generate a clear error or limitation message
* Processing results can be passed to the AI-analysis component

---

### WS-03: AI Analysis and Citations

**Objective:** Generate structured summaries while maintaining traceability to the source filing.

**Major deliverables:**

* Text-chunking approach
* Prompt or analysis instructions
* Structured summary format
* Citation-generation approach
* Citation-validation method
* Manual quality-review process

**Completion criteria:**

* The system creates summaries for the three supported sections
* Important claims include source references
* Unsupported claims can be identified during testing
* Financial values can be compared with the original filing

---

### WS-04: Backend API and Data Handling

**Objective:** Connect the user workflow, document processing, AI analysis, status handling, and results.

**Major deliverables:**

* Analysis-submission endpoint
* Analysis-status endpoint
* Results endpoint
* Error and timeout handling
* Analysis metadata model
* Configuration and secret handling
* External-service retry behavior

**Completion criteria:**

* A user request can start an analysis
* Processing status is visible
* Successful results are returned
* Failed requests return a clear error
* Credentials are separated from application code

---

### WS-05: User Interface

**Objective:** Provide a simple workflow for submitting and reviewing an analysis.

**Major deliverables:**

* Ticker input
* Filing selector
* Section selector
* Processing-status display
* Structured-results view
* Citation view
* Error-message display
* Copy-results capability

**Completion criteria:**

* A user can complete the primary journey without developer assistance
* Processing and failure states are visible
* Results clearly separate source content from generated analysis
* Citations are understandable and accessible

---

### WS-06: Quality, Security, and Launch Readiness

**Objective:** Determine whether the MVP is safe, reliable, understandable, and ready to demonstrate.

**Major deliverables:**

* Functional test plan
* Quality-evaluation approach
* Security and data-handling review
* Monitoring plan
* Cost model
* Known-limitations document
* Launch-readiness checklist
* Demonstration and disablement plan

**Completion criteria:**

* Must-have acceptance criteria pass
* No unresolved critical security issue exists
* Important claims are reviewed for citation support
* Errors, latency, and usage can be observed
* Cost per analysis can be estimated
* Known limitations are documented
* A go, conditional-go, or no-go recommendation can be made

---

## 4. Proposed Milestones

| ID   | Target        | Milestone                                   | Completion Evidence                                                                |
| ---- | ------------- | ------------------------------------------- | ---------------------------------------------------------------------------------- |
| M-01 | End of Week 1 | Program definition complete                 | Charter, requirements, scope, success metrics, and initial architecture documented |
| M-02 | End of Week 2 | Filing-processing proof of concept complete | Supported filing retrieved and three sections extracted for sample companies       |
| M-03 | End of Week 3 | AI-analysis proof of concept complete       | Structured summaries and source references generated for extracted sections        |
| M-04 | End of Week 4 | End-to-end workflow connected               | User request moves through filing processing, AI analysis, and result display      |
| M-05 | End of Week 5 | Quality and readiness review complete       | Testing, security, monitoring, cost, and known limitations reviewed                |
| M-06 | End of Week 6 | MVP demonstration ready                     | Primary workflow demonstrated with launch-readiness decision documented            |

---

## 5. Major Dependencies

| ID     | Dependency                     | Provider                            | Consumer                     | Needed Before           | Impact if Late                           | Initial Mitigation                                            |
| ------ | ------------------------------ | ----------------------------------- | ---------------------------- | ----------------------- | ---------------------------------------- | ------------------------------------------------------------- |
| DEP-01 | Public filing-source selection | Project owner                       | Filing-processing workstream | Filing retrieval begins | Retrieval implementation cannot start    | Compare available filing-source options early                 |
| DEP-02 | Supported filing content       | Filing-processing workstream        | AI-analysis workstream       | End-to-end AI testing   | Summary testing is blocked               | Use saved public sample text temporarily                      |
| DEP-03 | AI-service selection           | Project owner                       | AI-analysis workstream       | Summary implementation  | Prompt and cost testing cannot finish    | Create a service-independent interface                        |
| DEP-04 | Extracted section structure    | Filing-processing workstream        | Backend and AI workstreams   | Integration begins      | Data contracts may change                | Define an initial section-output format early                 |
| DEP-05 | API contracts                  | Backend workstream                  | User-interface workstream    | Frontend integration    | UI integration may be delayed            | Use mock API responses during UI development                  |
| DEP-06 | Quality criteria               | Product and requirements workstream | Testing workstream           | Readiness review        | Quality cannot be evaluated consistently | Define citation and accuracy review criteria before testing   |
| DEP-07 | Monitoring approach            | Backend and launch workstreams      | Readiness review             | MVP demonstration       | Failures and cost may not be visible     | Add basic logging and usage tracking before final integration |

---

## 6. Critical Path

The initial critical path is:

1. Complete MVP requirements and architecture decisions
2. Select the filing source
3. Retrieve and extract supported filing sections
4. Generate summaries and citations
5. Connect the backend workflow
6. Complete end-to-end testing
7. Resolve launch-critical defects
8. Complete the readiness review
9. Prepare the MVP demonstration

A delay in any of these activities may move the MVP demonstration date.

---

## 7. Parallel Work

The following work can begin while critical-path development continues:

* User-interface mockups
* README and portfolio documentation
* Security-requirement review
* Test-case preparation
* Sample-filing selection
* Monitoring-metric definition
* Cost-model design
* Known-limitations documentation

Parallel work should not depend on unconfirmed final technical details where significant rework would result.

---

## 8. Delivery Cadence

### Weekly planning

Review:

* Current milestone
* Planned deliverables
* New risks and dependencies
* Decisions needed
* Available project capacity

### Midweek checkpoint

Review:

* Critical-path progress
* Blockers
* Technical findings
* Changes to assumptions
* Recovery actions

### End-of-week review

Review:

* Completed milestone evidence
* Target versus forecast
* Open defects
* Decisions made
* Plan for the following week

---

## 9. Schedule Management Rules

* Dates are planning targets until technical baselines are established.
* A milestone is complete only when its completion evidence exists.
* New requirements must be assessed for scope, timeline, quality, and cost impact.
* Critical-path delays must update the forecast.
* Optional features should not displace launch-critical work without an approved decision.
* Quality and source traceability will not be reduced only to preserve the target date.

---

## 10. Current Program Status

**Overall status:** Green

**Current phase:** Program definition

**Completed:**

* Business problem
* MVP objective
* Primary user
* User journey
* MVP scope
* Success metrics
* Functional and nonfunctional requirements

**Next milestone:**

Complete the initial architecture and resolve the filing-source and AI-service open questions.
