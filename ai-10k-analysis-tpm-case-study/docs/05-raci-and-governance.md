# RACI and Governance Model

## AI-Powered 10-K Analysis Platform

## 1. Purpose

This document defines proposed responsibilities, decision ownership, review forums, and escalation paths for the AI-Powered 10-K Analysis Platform.

The project is currently an independently executed portfolio case study. The roles below represent how responsibilities would be separated in a staffed technical program. During the independent prototype phase, the project owner temporarily performs several roles but documents decisions according to the appropriate role.

---

## 2. Proposed Program Roles

| Role              | Primary Responsibility                                                                                      |
| ----------------- | ----------------------------------------------------------------------------------------------------------- |
| Business Sponsor  | Approves business objective, budget, major scope changes, and business-risk acceptance                      |
| Product Owner     | Defines user needs, scope, feature priority, and acceptance criteria                                        |
| TPM               | Owns program planning, dependencies, risks, operating cadence, decision process, and readiness coordination |
| Engineering Lead  | Owns technical architecture, engineering quality, technical estimates, and technical readiness              |
| Software Engineer | Designs, implements, tests, and documents application components                                            |
| AI or Data Lead   | Owns document-processing, model-integration, prompt, citation, and quality approaches                       |
| Security Reviewer | Reviews secrets, access, data handling, logging, and security risks                                         |
| Quality Reviewer  | Validates functional requirements, citations, financial values, and known limitations                       |
| User Reviewer     | Evaluates workflow usability and summary usefulness                                                         |

---

## 3. RACI Matrix

| Activity or Decision                       | Business Sponsor | Product Owner | TPM | Engineering Lead | Software Engineer | AI/Data Lead | Security Reviewer | Quality Reviewer | User Reviewer |
| ------------------------------------------ | ---------------- | ------------- | --- | ---------------- | ----------------- | ------------ | ----------------- | ---------------- | ------------- |
| Approve business problem and objective     | A                | R             | C   | C                | I                 | I            | I                 | I                | C             |
| Define primary user and MVP scope          | C                | A/R           | C   | C                | I                 | C            | I                 | C                | C             |
| Define functional requirements             | I                | A             | R   | C                | C                 | C            | C                 | C                | C             |
| Define nonfunctional requirements          | I                | C             | R   | A                | C                 | C            | C                 | C                | I             |
| Approve technical architecture             | I                | C             | C   | A                | R                 | R            | C                 | C                | I             |
| Select filing-source approach              | I                | C             | R   | A                | C                 | C            | C                 | C                | I             |
| Select AI-service approach                 | I                | C             | R   | C                | C                 | A            | C                 | C                | I             |
| Define API contract                        | I                | C             | C   | A                | R                 | C            | C                 | C                | I             |
| Implement application components           | I                | I             | C   | A                | R                 | R            | C                 | C                | I             |
| Define security and data-handling controls | I                | C             | R   | C                | C                 | C            | A                 | C                | I             |
| Define testing and quality criteria        | I                | C             | R   | C                | C                 | C            | C                 | A                | C             |
| Validate citation and financial accuracy   | I                | I             | C   | C                | C                 | R            | I                 | A                | C             |
| Maintain program plan and milestones       | I                | C             | A/R | C                | I                 | I            | I                 | I                | I             |
| Maintain RAID and dependency logs          | I                | C             | A/R | C                | C                 | C            | C                 | C                | I             |
| Run weekly program review                  | I                | C             | A/R | C                | I                 | I            | I                 | I                | I             |
| Approve major scope change                 | A                | R             | C   | C                | I                 | I            | C                 | C                | I             |
| Confirm technical launch readiness         | I                | C             | R   | A                | C                 | C            | C                 | C                | I             |
| Accept remaining business risk             | A                | R             | C   | C                | I                 | I            | C                 | C                | I             |
| Make final MVP launch decision             | A                | R             | C   | C                | I                 | I            | C                 | C                | I             |
| Document decisions and follow-up actions   | I                | C             | A/R | C                | I                 | I            | I                 | I                | I             |

---

## 4. Current Independent-Project Model

During the portfolio phase, the project owner currently performs the following responsibilities:

| Role              | Current Assignment                                                            |
| ----------------- | ----------------------------------------------------------------------------- |
| Business Sponsor  | Project owner                                                                 |
| Product Owner     | Project owner                                                                 |
| TPM               | Project owner                                                                 |
| Engineering Lead  | Project owner, with external technical review where available                 |
| Software Engineer | Project owner                                                                 |
| AI/Data Lead      | Project owner                                                                 |
| Security Reviewer | Self-review using documented controls; external review may be requested later |
| Quality Reviewer  | Project owner using a structured test rubric                                  |
| User Reviewer     | Sample reviewers may be invited after the prototype is usable                 |

This structure does not imply that the project currently has a staffed engineering team. It separates responsibilities so that decisions can be evaluated from the correct business, product, technical, security, and quality perspectives.

---

## 5. Decision Ownership Principles

### 5.1 TPM ownership

The TPM is accountable for:

* Maintaining the decision process
* Identifying the decision owner
* Defining the decision deadline
* Gathering required evidence
* Documenting options and trade-offs
* Recording the final decision
* Tracking follow-up actions
* Escalating when a decision threatens the critical path

The TPM is not automatically accountable for the technical or business decision itself.

### 5.2 Technical ownership

The engineering lead is accountable for:

* Architecture
* Technical feasibility
* Engineering quality
* Reliability
* Performance
* Maintainability
* Technical readiness

### 5.3 Product and business ownership

The product owner and business sponsor are accountable for:

* User value
* Scope priority
* Budget
* Customer commitments
* Business-risk acceptance
* Final launch strategy

### 5.4 Security ownership

The security reviewer is accountable for approving whether security risks and controls are acceptable within the defined review scope.

---

## 6. Governance Cadence

### Weekly Program Review

**Purpose:** Review progress, risks, dependencies, decisions, and forecast.

**Participants:**

* TPM
* Product owner
* Engineering lead
* Workstream owners as needed

**Agenda:**

1. Overall status
2. Milestone progress
3. Critical-path status
4. Top risks and issues
5. Dependency changes
6. Decisions needed
7. Scope or forecast changes
8. Actions, owners, and due dates

---

### Technical Decision Review

**Purpose:** Resolve architecture or implementation decisions that affect multiple components, risks, costs, or milestones.

**Participants:**

* Engineering lead
* Relevant engineers
* AI/data lead where applicable
* Security reviewer where applicable
* TPM

**Required inputs:**

* Problem statement
* Options considered
* Decision criteria
* Technical and business trade-offs
* Recommendation
* Decision deadline

---

### Quality and Readiness Review

**Purpose:** Determine whether the MVP is ready for demonstration or release.

**Participants:**

* TPM
* Engineering lead
* Product owner
* Security reviewer
* Quality reviewer
* Business sponsor for final risk acceptance

**Review areas:**

* Functional requirements
* Citation and financial accuracy
* Performance
* Reliability
* Security
* Monitoring
* Cost
* Known limitations
* Support and disablement plan

---

## 7. Escalation Path

The proposed escalation path is:

1. Workstream owner attempts resolution.
2. TPM coordinates cross-workstream resolution.
3. Engineering or product lead resolves functional priority conflicts.
4. Business sponsor resolves scope, budget, timeline, or business-risk conflicts.

Escalation should include:

* Confirmed problem
* Business or customer impact
* Critical-path impact
* Actions already attempted
* Options and trade-offs
* TPM recommendation
* Decision owner
* Decision deadline

---

## 8. Decision-Meeting Output

Every decision meeting should end with:

* Final decision
* Accountable owner
* Decision date
* Reason and trade-offs
* Actions
* Action owners
* Due dates
* Remaining risks
* Conditions that would cause the decision to be revisited

Silence or lack of objection should not be treated as formal approval.

---

## 9. Current Governance Status

**Current execution model:** Independent project

**Current accountable owner:** Project owner

**Next governance action:** Complete the initial architecture review and document the filing-source, application-architecture, and AI-service decisions.
