# AI-Powered 10-K Analysis Platform  
### Technical Program Management Portfolio Case Study

## Overview

This project is an independent Technical Program Management case study for an AI-powered platform that helps users analyze public-company 10-K filings.

The proposed platform retrieves or accepts a 10-K filing, extracts important sections, summarizes financial and business trends, identifies major risks, and links generated insights back to the source text.

The project demonstrates how I approach an ambiguous technical program from initial problem definition through architecture, execution planning, risk management, and launch readiness.

## Problem

A 10-K filing can contain hundreds of pages of financial statements, risk disclosures, management commentary, and supporting notes. Reviewing the filing manually takes significant time, and important information may be spread across multiple sections.

Users need a faster way to identify key financial trends and business risks without losing access to the original source.

## Target Users

- MBA students
- Financial analysts
- Individual investors
- Corporate strategy teams
- Investment research professionals

## Proposed MVP

The first version will allow a user to:

1. Enter a public-company ticker or upload a 10-K filing.
2. Select the sections to analyze.
3. Extract relevant filing text.
4. Generate a structured summary.
5. Show supporting citations for important claims.
6. Display key risks, financial trends, and management commentary.

## In Scope

- Public 10-K filing retrieval or upload
- Filing text extraction
- Analysis of selected filing sections
- AI-generated summaries with source citations
- Basic results interface
- Error handling and monitoring
- Cost and usage tracking

## Out of Scope

- Investment recommendations
- Stock-price predictions
- Automated trading
- Analysis of confidential company documents
- Real-time portfolio management
- Production-scale enterprise deployment

## TPM Deliverables

This repository will include:

- [Program Charter](docs/01-program-charter.md)
- Requirements
- Architecture diagram
- Workstreams and milestones
- RAID log
- Decision log
- API design
- Security and data-handling plan
- Cost estimate
- Monitoring plan
- Launch-readiness checklist

## Proposed Architecture

User → Web Interface → Backend API → Filing Retrieval or Upload → Document Processing → AI Analysis → Citation Validation → Results Dashboard

Supporting components may include:

- Database for company, filing, and analysis metadata
- Object storage for temporary document handling
- Monitoring for errors, latency, usage, and cost
- Authentication for saved analyses in a later phase

## Success Measures

The initial MVP will be evaluated using:

- Percentage of major claims supported by citations
- Financial-number extraction accuracy
- Analysis completion rate
- Average and P95 response time
- Error and timeout rate
- Cost per analysis
- User review of summary usefulness

These are proposed targets and will be refined after prototype testing.

## Project Status

**Current phase:** Program design and MVP planning

The first deliverables are the program charter, requirements, architecture, workstream plan, and risk register. Prototype development will follow after the initial design is complete.

## My Role

This is an independent portfolio project. I am responsible for defining the problem, creating the program plan, evaluating technical options, documenting risks and decisions, and building or coordinating the MVP prototype.

This project should not be interpreted as a production launch or as management of a staffed engineering team.

## Planned Repository Structure

```text
ai-10k-analysis-tpm-case-study/
├── README.md
├── START-HERE.md
├── docs/
│   └── 01-program-charter.md
├── diagrams/
├── prototype/
└── screenshots/
```
