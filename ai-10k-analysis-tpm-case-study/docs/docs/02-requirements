# Product Requirements

## AI-Powered 10-K Analysis Platform

### 1. Purpose

This document defines the functional and nonfunctional requirements for the first MVP of the AI-Powered 10-K Analysis Platform.

The MVP is designed for an MBA student or early-career financial analyst who needs to review selected sections of a public-company 10-K filing efficiently.

---

## 2. Primary User Need

The user needs a faster way to identify important financial trends, business risks, and management commentary while maintaining traceability to the original filing.

---

## 3. MVP User Journey

1. The user enters a public-company ticker.
2. The system displays available 10-K filings.
3. The user selects one filing.
4. The user selects the filing sections to analyze.
5. The system retrieves and processes the filing.
6. The system generates structured summaries.
7. The system displays citations to supporting source text.
8. The user reviews and copies the results.

---

## 4. Functional Requirements

| ID    | Requirement                                                                                                              | Priority       |
| ----- | ------------------------------------------------------------------------------------------------------------------------ | -------------- |
| FR-01 | The system shall allow the user to enter a public-company ticker.                                                        | Must have      |
| FR-02 | The system shall validate whether the ticker is supported.                                                               | Must have      |
| FR-03 | The system shall display available 10-K filings for the selected company.                                                | Must have      |
| FR-04 | The system shall allow the user to select one 10-K filing for analysis.                                                  | Must have      |
| FR-05 | The system shall allow the user to select the Business, Risk Factors, and Management’s Discussion and Analysis sections. | Must have      |
| FR-06 | The system shall retrieve and extract text from the selected filing sections.                                            | Must have      |
| FR-07 | The system shall generate a structured summary of the selected sections.                                                 | Must have      |
| FR-08 | The system shall link important generated claims to supporting source text.                                              | Must have      |
| FR-09 | The system shall distinguish generated interpretation from original filing content.                                      | Must have      |
| FR-10 | The system shall display the analysis status as submitted, processing, completed, or failed.                             | Must have      |
| FR-11 | The system shall display a clear error message when a filing cannot be retrieved or processed.                           | Must have      |
| FR-12 | The system shall allow the user to copy the generated results.                                                           | Should have    |
| FR-13 | The system should record basic analysis metadata, including company, filing year, status, and completion time.           | Should have    |
| FR-14 | The system could allow the user to download the results as a report.                                                     | Could have     |
| FR-15 | The MVP will not provide investment recommendations, stock-price predictions, or automated trading.                      | Won’t have now |

---

## 5. Nonfunctional Requirements

### 5.1 Quality

| ID     | Requirement                                                                                         | Priority  |
| ------ | --------------------------------------------------------------------------------------------------- | --------- |
| NFR-01 | Important generated claims shall include supporting citations.                                      | Must have |
| NFR-02 | The system shall track unsupported claims during manual quality testing.                            | Must have |
| NFR-03 | Financial values included in summaries shall be validated against the source filing during testing. | Must have |
| NFR-04 | The system shall document unsupported filing structures and known limitations.                      | Must have |

### 5.2 Performance

| ID     | Requirement                                                                             | Priority  |
| ------ | --------------------------------------------------------------------------------------- | --------- |
| NFR-05 | The system shall measure average and P95 analysis response time.                        | Must have |
| NFR-06 | Final response-time targets shall be established after baseline prototype testing.      | Must have |
| NFR-07 | The interface shall provide visible status information while an analysis is processing. | Must have |

### 5.3 Reliability

| ID     | Requirement                                                                                                         | Priority  |
| ------ | ------------------------------------------------------------------------------------------------------------------- | --------- |
| NFR-08 | The system shall handle filing-source and AI-service failures without exposing internal technical details to users. | Must have |
| NFR-09 | The system shall record analysis failures for troubleshooting.                                                      | Must have |
| NFR-10 | The system shall define timeout and retry behavior for external service calls.                                      | Must have |

### 5.4 Security and Privacy

| ID     | Requirement                                                                | Priority    |
| ------ | -------------------------------------------------------------------------- | ----------- |
| NFR-11 | API keys and credentials shall not be stored in source control.            | Must have   |
| NFR-12 | The MVP shall process only public-company filings.                         | Must have   |
| NFR-13 | Logs shall avoid storing unnecessary filing content or credentials.        | Must have   |
| NFR-14 | Any future saved analyses shall be accessible only to the authorized user. | Should have |
| NFR-15 | The system shall display an informational-use disclaimer.                  | Must have   |

### 5.5 Cost

| ID     | Requirement                                                                    | Priority  |
| ------ | ------------------------------------------------------------------------------ | --------- |
| NFR-16 | The system shall track estimated AI-service usage per analysis.                | Must have |
| NFR-17 | The system shall calculate an estimated cost per completed analysis.           | Must have |
| NFR-18 | The MVP shall operate within the defined development and monthly usage budget. | Must have |

### 5.6 Maintainability

| ID     | Requirement                                                                                                                       | Priority    |
| ------ | --------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| NFR-19 | Filing retrieval, document processing, AI analysis, and result presentation should be implemented as separate logical components. | Should have |
| NFR-20 | Configuration values and credentials shall be separated from application code.                                                    | Must have   |
| NFR-21 | Major technical decisions and known limitations shall be documented.                                                              | Must have   |

---

## 6. Acceptance Criteria

### AC-01: Valid ticker

**Given** the user enters a supported public-company ticker,
**when** the user submits the ticker,
**then** the system displays available 10-K filings.

### AC-02: Invalid ticker

**Given** the user enters an invalid or unsupported ticker,
**when** the user submits the ticker,
**then** the system displays a clear validation message.

### AC-03: Filing analysis

**Given** the user selects a filing and at least one supported section,
**when** the user starts the analysis,
**then** the system processes the filing and displays the analysis status.

### AC-04: Completed summary

**Given** the filing is processed successfully,
**when** the analysis completes,
**then** the system displays a structured summary for each selected section.

### AC-05: Citation traceability

**Given** the summary contains an important financial or business claim,
**when** the user views that claim,
**then** the system displays supporting source text or a source reference.

### AC-06: Processing failure

**Given** the filing source or AI service is unavailable,
**when** the analysis fails,
**then** the system displays a clear error message and records the failure for troubleshooting.

---

## 7. Out-of-Scope Requirements

The following capabilities are not included in the first MVP:

* Analysis of forms other than 10-K filings
* Real-time market data
* Stock-price forecasting
* Investment recommendations
* Automated trading
* Multi-company comparison
* Advanced financial-table extraction
* Enterprise-scale user management
* Mobile application support

---

## 8. Open Questions

| ID    | Question                                                                  | Needed Before           |
| ----- | ------------------------------------------------------------------------- | ----------------------- |
| OQ-01 | Which public filing source will the MVP use?                              | Architecture completion |
| OQ-02 | Will the prototype support direct upload in addition to filing retrieval? | MVP design              |
| OQ-03 | Which AI model or service will be used?                                   | Prototype development   |
| OQ-04 | What response-time target is realistic after baseline testing?            | Performance testing     |
| OQ-05 | How will citation quality be evaluated consistently?                      | Test-plan completion    |
| OQ-06 | How long, if at all, should analysis results be retained?                 | Security review         |
