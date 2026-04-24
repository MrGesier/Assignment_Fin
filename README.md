# Finary Care Ops Case Study — Streamlit Analyzer

Interactive Streamlit app to analyze support tickets from the **Finary Care Ops case study** using a **rule-based opportunity scoring framework**.

The app helps turn raw support tickets into:
- prioritized **product / process opportunities**
- structured **evidence for Product & Engineering**
- clear **auditability / QA checks**
- reusable outputs for the **case study deliverable**

---

## Overview

This tool is designed to support **Part 2** of the case study:

> Review 300 support tickets, identify recurring themes, prioritize the top 3 product or process improvement opportunities, justify the prioritization, and explain how to surface them with Product and Engineering.

It also lays the groundwork for **Part 3**, by helping isolate one recurring case that can later be codified for scale.

---

## Main Features

### 1. Excel upload
Upload the support ticket Excel file directly in the app.

### 2. Rule-based classification
Each ticket is analyzed using a configurable rules engine based on:
- category
- subcategory
- subject
- description
- **tags** (last column is explicitly included)

### 3. Opportunity prioritization
Tickets are grouped into opportunity clusters such as:
- Account sync reliability
- Billing and subscription clarity
- Finary One service delivery and SLA
- Product bug stability
- Tax and reporting support complexity
- Security and account access friction

### 4. Adjustable scoring model
The scoring logic is customizable from the sidebar. You can modify the weight of each criterion:
- Volume
- Severity
- Premium / revenue exposure
- Virality / reputation risk
- Product dependency / escalation
- Operational burden
- Backlog / open tickets

### 5. Evidence-based outputs
The app generates:
- opportunity scoring table
- ticket-level classification audit trail
- top opportunity charts
- priority heatmap
- tag distribution analysis
- top 3 Product / Engineering reports

### 6. QA / coverage checks
Built-in checks help prove that the analysis is robust:
- total tickets loaded
- total tickets processed
- coverage rate
- uncategorized share
- rule-match coverage
- tag coverage
- missing subject / description checks
- duplicate ticket id checks

---

## Why this tool is useful for the case study

This app is not just a dashboard. It demonstrates an operational thinking process:

- transforming raw support demand into structured product insight
- prioritizing issues based on repeatability and business impact
- distinguishing support noise from roadmap signal
- creating a traceable, auditable method rather than a subjective opinion

That is exactly the kind of reasoning the case study is trying to assess.

---

## Scoring Logic

Each opportunity receives a composite score based on weighted criteria.

### Default dimensions
- **Volume** → how repeatable the issue is
- **Severity** → how painful / risky the issue appears
- **Premium exposure** → whether paying or high-value users are affected
- **Virality / reputation risk** → frustration signals that could damage brand trust
- **Product dependency** → whether support alone cannot solve it and Product / Engineering intervention is needed
- **Operational burden** → time / cost to resolve repeatedly
- **Backlog pressure** → whether many tickets remain open or pending

### Goal
The objective is **not** to rank only by raw ticket count.

The framework is designed to prioritize opportunities that combine:
- recurrence
- customer trust impact
- revenue exposure
- support burden
- product relevance

---

## Tags Handling

The **tags column is explicitly included** in the analysis.

Tags are used in two ways:

1. **Classification input**  
   Tags are part of the `evidence_text` used by the rule engine.

2. **Interpretation layer**  
   Tags are surfaced to show:
   - most frequent tags overall
   - top tags by opportunity
   - additional support for recurring patterns

This makes the analysis more defensible and closer to how a real Care Ops team would work.

---

## Outputs

The app produces several outputs directly in the UI.

### Core analysis
- Top opportunities table
- Ranked opportunity scores
- Opportunity-level breakdown

### Charts
- **Top Opportunity Scores**
- **Priority Heatmap by Opportunity**
- **Subscription Tier Mix — Top 3 Opportunities**
- **Top Tags / Tag distribution**

### Product & Engineering reports
For each top 3 opportunity, the app generates a structured summary with:
- opportunity name
- owner
- score
- evidence / ticket count
- user impact
- business impact
- examples
- recommendation / ask to Product & Engineering

Example structure:

```text
Opportunity: Bank sync reliability

Evidence:
- X tickets / 300
- Main patterns: bank sync failure, reconnection loop, missing transactions, balance mismatch
- High share of paid users impacted
- Long resolution time
- Many tickets escalated to Product

User impact:
Users lose trust because their balances / net worth are wrong.

Business impact:
Higher support load, lower trust, churn risk for paying users.

Ask to Product/Eng:
1. Add degraded-state messaging in-app
2. Improve reconnect flow
3. Create bank-level reliability dashboard
4. Proactive alert when sync is stale
