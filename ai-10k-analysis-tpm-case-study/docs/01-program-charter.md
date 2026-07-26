# Program Charter  
## AI-Powered 10-K Analysis Platform

### 1. Program Purpose

Design and develop an MVP that helps users review public-company 10-K filings more efficiently. The platform will extract selected filing sections, generate structured summaries, identify key financial and business risks, and provide citations to the source text.

### 2. Business Problem

MBA students, analysts, and individual investors spend significant time reviewing lengthy 10-K filings. Important financial trends, business risks, and management commentary are distributed across multiple sections, making manual analysis slow and increasing the chance that users miss important information.

### 3. Objective

Create an MVP that processes selected sections of a public-company 10-K filing and produces a structured summary of financial trends and business risks, with citations linking important claims to the original filing.

**4. Target Users**
**Primary User**

An MBA student or early-career financial analyst who needs to review a public company’s 10-K filing efficiently for company research or financial analysis.

**Secondary Users**
Individual investors
Corporate strategy professionals
Investment-research professionals
**5. Primary User Journey**
The user enters a public-company ticker.
The user selects an available 10-K filing.
The user selects the filing sections to analyze.
The platform retrieves and processes the selected filing.
The platform generates structured summaries of the selected sections.
The platform links important claims to supporting source text.
The user reviews and copies the results for further analysis.

**6. MVP Scope**
The first version will support:

One public company and one 10-K filing per analysis
Publicly available 10-K filings
Analysis of the Business, Risk Factors, and Management’s Discussion and Analysis sections
Structured summaries of important trends and risks
Citations linking important claims to the original filing
A basic user interface for submitting and reviewing an analysis
Clear error messages when a filing cannot be processed

Complex financial-table extraction, company comparison, investment recommendations, stock-price forecasting, and real-time market data are not included in the first MVP.

### 6. In Scope

- Retrieve or upload a public 10-K filing
- Extract text from selected sections
- Generate structured summaries
- Identify major financial trends and business risks
- Link important claims to supporting source text
- Display results through a simple interface
- Track errors, latency, usage, and estimated cost
- Document technical decisions, risks, and launch criteria

### 7. Out of Scope

- Investment advice or buy/sell recommendations
- Stock-price forecasting
- Automated trading
- Analysis of confidential company information
- Enterprise-scale multi-tenant deployment
- Mobile application development
- Real-time market-data integration

### 7. Proposed Timeline

| Phase | Duration | Main Deliverables |
|---|---:|---|
| Program design | Week 1 | Charter, requirements, architecture |
| Filing ingestion | Week 2 | Retrieval or upload and text extraction |
| AI analysis | Week 3 | Summaries and citation workflow |
| Application integration | Week 4 | Backend and basic user interface |
| Testing and readiness | Week 5 | Quality, security, monitoring, cost review |
| MVP release | Week 6 | Demonstration, documentation, retrospective |

### 8. Workstreams

1. Product definition and requirements  
2. Filing retrieval and document processing  
3. AI analysis and citation validation  
4. Backend API and data handling  
5. User interface  
6. Testing, monitoring, and launch readiness  

### 9. Success Criteria


The MVP will be evaluated using product, quality, technical, and cost measures. These are initial targets and may be refined after baseline prototype testing.

| Category     | Metric                                         | Initial MVP Target                                                          |
| ------------ | ---------------------------------------------- | --------------------------------------------------------------------------- |
| User outcome | Time required to review selected 10-K sections | Demonstrate a meaningful reduction compared with manual review              |
| Product      | Analysis completion rate                       | At least 90% for supported filings                                          |
| Product      | User usefulness rating                         | At least 4 out of 5 during structured review                                |
| Quality      | Citation coverage                              | At least 90% of important generated claims linked to supporting source text |
| Quality      | Unsupported-claim rate                         | Less than 5% during manual evaluation                                       |
| Quality      | Section-extraction accuracy                    | At least 90% for supported filing formats                                   |
| Quality      | Financial-number accuracy                      | At least 95% for numbers included in generated summaries                    |
| Performance  | Average analysis response time                 | Establish after baseline testing and improve during the MVP                 |
| Performance  | P95 analysis response time                     | Establish after baseline testing                                            |
| Reliability  | Analysis failure rate                          | Less than 5% for supported filings                                          |
| Cost         | Cost per completed analysis                    | Measured and maintained within the defined MVP budget                       |

The project will not be considered successful based only on application completion. It must demonstrate usable summaries, source traceability, acceptable reliability, and controlled processing cost.

### 10. Major Risks

| Risk | Potential Impact | Initial Response |
|---|---|---|
| Unsupported or inaccurate AI claims | User trust and quality risk | Require source citations and manual validation |
| Incorrect financial-number extraction | Misleading analysis | Test against known filing values |
| Filing-format differences | Processing failures | Test multiple companies and document unsupported formats |
| Large filing size | Higher latency and cost | Limit scope, chunk text, and monitor usage |
| External service failure | Incomplete analysis | Add timeouts, retries, and clear error handling |
| Sensitive uploaded documents | Privacy and security risk | Restrict project to public filings and minimize retention |
| Prototype scope growth | Timeline delay | Protect MVP scope and move enhancements to later phases |

### 11. Assumptions

- Public filings are available in readable formats.
- The MVP will initially support a limited set of filing structures.
- The project will use a limited development budget.
- A single project owner will manage product, program, and prototype activities.
- Generated analysis will be informational and will not replace professional investment research.

### 12. Dependencies

- Access to public 10-K filing data
- Document parsing capability
- AI model or language-model service
- Application hosting environment
- Development and testing tools

### 13. Constraints

- One-person portfolio project
- Limited implementation time
- Limited cloud and AI-service budget
- No dedicated engineering, security, or operations team
- No use of confidential company information

### 14. Governance and Decision Ownership

The project owner is accountable for scope, architecture, risk management, implementation priorities, and MVP readiness.

Major decisions will be documented in a decision log, including:

- Filing-source strategy
- Application architecture
- AI-processing approach
- Data-retention policy
- Cost controls
- Launch-readiness criteria

### 15. Launch Approach

The MVP will not be considered ready until:

- The primary workflow functions successfully
- Important claims include supporting citations
- Known failure cases are documented
- Basic monitoring is available
- Secrets and credentials are protected
- Cost and usage can be reviewed
- A demonstration and rollback or disablement plan exists

### 16. Current Status

**Status:** Green  
**Phase:** Program design  
**Next milestone:** Complete requirements and architecture documentation
