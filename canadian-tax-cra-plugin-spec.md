# Canadian Tax & CRA Compliance Plugin — Design Specification

**Version:** 0.1.0-draft
**Target User:** Small business owner (non-accountant)
**Author:** Srivatsa Kasagar
**Date:** March 2026

---

## Overview

A self-contained plugin that acts as a knowledgeable CRA compliance assistant for Canadian small business owners. It covers the four highest-impact tax obligations — GST/HST, payroll & remittances, corporate income tax (T2), and SR&ED/grants — and translates CRA rules into plain-language guidance, actionable checklists, calculations, and filing summaries.

**Design philosophy:** The plugin assumes the user is not a tax professional. Every output must be plain-language, specific to their situation, and honest about what requires a CPA or tax lawyer to finalize.

---

## Plugin Directory Structure

```
canadian-tax-cra/
├── README.md
├── CONNECTORS.md
├── skills/
│   ├── gst-hst-compliance/
│   │   └── SKILL.md
│   ├── payroll-remittances/
│   │   └── SKILL.md
│   ├── corporate-tax-t2/
│   │   └── SKILL.md
│   └── sred-grants/
│       └── SKILL.md
└── commands/
    ├── gst-filing.md
    ├── payroll-calc.md
    ├── cra-deadlines.md
    ├── sred-screen.md
    ├── grant-finder.md
    └── t2-checklist.md
```

---

## Skills (Background Knowledge — Auto-Activating)

Skills load automatically when the user asks about relevant topics. They encode deep regulatory knowledge and activate based on keyword triggers.

---

### Skill 1: `gst-hst-compliance`

**Trigger keywords:** GST, HST, PST, QST, input tax credit, ITC, sales tax, zero-rated, exempt supply, reporting period, net tax, quick method, simplified method, voluntary registration, small supplier, $30,000 threshold, CRA My Business Account

**What it knows:**

#### GST/HST Rate Reference (2026)

| Province | GST Rate | HST Rate | Provincial Component | PST (separate) |
|----------|----------|----------|----------------------|----------------|
| Alberta | 5% | — | — | None |
| British Columbia | 5% | — | — | 7% PST |
| Manitoba | 5% | — | — | 7% RST |
| New Brunswick | — | 15% | 10% | — |
| Newfoundland & Labrador | — | 15% | 10% | — |
| Nova Scotia | — | 15% | 10% | — |
| Ontario | — | 13% | 8% | — |
| PEI | — | 15% | 10% | — |
| Quebec | 5% | — | — | 9.975% QST |
| Saskatchewan | 5% | — | — | 6% PST |

#### Registration Thresholds

- **Mandatory registration:** Once taxable revenues exceed **$30,000** in a single calendar quarter OR in any four consecutive calendar quarters.
- **Voluntary registration:** Permitted at any revenue level. Recommended if the business has significant purchases (to claim ITCs) or if clients expect a GST/HST number.
- **Small supplier exemption:** Under $30,000 — registration optional; cannot charge or collect GST/HST but also cannot claim ITCs.

#### Reporting Periods

| Annual Revenue | Assigned Filing Period | Filing Deadline |
|----------------|----------------------|-----------------|
| $1.5M or less | Annual | 3 months after fiscal year-end |
| $1.5M – $6M | Quarterly | 1 month after quarter-end |
| Over $6M | Monthly | 1 month after month-end |

*Note: Annual filers with net tax of $3,000+ must make quarterly instalment payments.*

#### Input Tax Credits (ITCs)

ITCs allow the business to recover GST/HST paid on business expenses. Key rules:
- Only claimable on **business-use** purchases (not personal)
- Must have **supporting documentation** (invoices showing GST/HST registration number, amount, etc.)
- For purchases over $30: must show supplier's GST/HST number, date, total paid, tax paid/payable
- For purchases over $150: must also show purchaser's name or business name
- **Time limit:** 4 years from the date the return was due (2 years for financial institutions)
- **Partial ITC:** If an asset is used partly for business and partly for personal, claim only the business-use percentage

#### ITC Blocked Categories (cannot claim)

- Meals and entertainment: **50% only** (50% is blocked)
- Club memberships (golf, fitness, recreational)
- Personal use portion of a vehicle
- Life insurance premiums

#### Net Tax Calculation

```
Net Tax = GST/HST collected on sales
        − ITCs (GST/HST paid on business expenses)

If positive → remit to CRA
If negative → request refund or apply to future periods
```

#### Quick Method (Simplified Accounting)

Available to businesses with taxable revenues ≤ $400,000/year. Instead of tracking all ITCs, a flat remittance rate applies:

| Type of Business | Supply Made In | Quick Method Rate |
|-----------------|---------------|-------------------|
| Service business | Province with 5% GST | 3.6% |
| Service business | HST province (13%) | 8.8% |
| Service business | HST province (15%) | 10.4% |
| Retail/wholesale | Province with 5% GST | 1.8% |

*Under quick method, the business keeps the difference between what it charges customers and what it remits.*

---

### Skill 2: `payroll-remittances`

**Trigger keywords:** payroll, CPP, EI, income tax deduction, T4, ROE, Record of Employment, remittance, payroll deduction, employer contribution, new hire, employee vs contractor, payroll account, RP account, PD7A, accelerated remitter, payroll deadline

**What it knows:**

#### 2026 Payroll Deduction Rates

**CPP (Canada Pension Plan)**

| | Employee | Employer |
|--|---------|---------|
| Rate | 5.95% | 5.95% (matching) |
| Basic Exemption | $3,500/year | — |
| Maximum Pensionable Earnings | $68,500/year | — |
| Maximum Annual Contribution | ~$3,867/year | ~$3,867/year |

*CPP2 (second additional CPP): 4% on earnings between $68,500 and $73,200, up to additional max $188/year (employee and employer each).*

**EI (Employment Insurance)**

| | Employee | Employer |
|--|---------|---------|
| Rate | 1.66% | 1.66% × 1.4 = 2.32% |
| Maximum Insurable Earnings | $63,200/year | — |
| Maximum Annual Premium (employee) | ~$1,049/year | ~$1,468/year |

**Federal Income Tax:** Calculated using CRA withholding tables based on province of employment, pay period, and TD1 claim amounts.

#### Remittance Schedules

| Type | Criteria | Due Date |
|------|----------|----------|
| Regular remitter | New employers; average monthly withholding $1,000–$24,999 | 15th of month *following* payroll month |
| Quarterly | New employers with < $1,000/month average AND payroll compliance history | End of April, July, October, January |
| Accelerated (Threshold 1) | Average monthly withholding $25,000–$99,999 | Within 3 working days after 15th and end of month |
| Accelerated (Threshold 2) | Average monthly withholding $100,000+ | Within 3 working days after weekly payroll |

**Missing remittances** trigger penalties of 3%–10% per late day and interest at the prescribed rate.

#### T4 Preparation (Annual)

- **Deadline:** February 28 (or 29 in leap years) of the following year
- File T4 slip with CRA AND provide copy to employee
- Key boxes: Box 14 (employment income), Box 16 (employee CPP), Box 18 (employee EI), Box 22 (income tax deducted), Box 52 (pension adjustment if applicable)

#### Record of Employment (ROE)

- Must be issued within **5 calendar days** after an employee's interruption of earnings (layoff, termination, leave of absence, etc.)
- Filed electronically via ROE Web (if 26+ employees) or paper Form INS2120
- Determines EI eligibility and benefit amounts for the employee

#### Employee vs. Contractor Test (CRA's View)

CRA uses a multi-factor test. Contractor status requires **all or most** of:
- Worker controls how, when, and where work is performed
- Worker provides their own tools/equipment
- Worker has chance of profit and risk of loss
- Worker can subcontract or hire helpers
- Work is not integrated into the business's core operations

**Risk of misclassification:** CRA can reclassify contractors as employees, triggering retroactive CPP/EI + penalties. When in doubt, treat as employee.

---

### Skill 3: `corporate-tax-t2`

**Trigger keywords:** T2, corporate tax, corporate income tax, CCPC, small business deduction, SBD, passive income, instalment payments, fiscal year end, Schedule 1, Schedule 8, CCA, capital cost allowance, dividend, eligible dividend, non-eligible dividend, RDTOH, GRIP, tax deferral, associated corporations, Part IV tax, loss carryforward, loss carryback

**What it knows:**

#### Key Filing Deadlines

| Event | Deadline |
|-------|----------|
| T2 return filing | **6 months** after fiscal year-end |
| Balance owing payment | **2 months** after fiscal year-end (3 months for eligible CCPCs) |
| Instalment payments | Monthly or quarterly (see below) |

#### Tax Rates (2025 — verify 2026)

| Type of Income | Federal Rate | Typical Combined Rate (ON) |
|----------------|-------------|--------------------------|
| Active business income ≤ SBD limit (CCPC) | 9% | ~12.2% |
| Active business income above SBD limit | 15% | ~26.5% |
| Investment/passive income | 38.67% (before RDTOH) | ~50.17% |
| Capital gains (50% inclusion) | 15% | ~13.25% |

#### Small Business Deduction (SBD)

- Available to **Canadian-Controlled Private Corporations (CCPCs)**
- Reduces federal corporate tax to **9%** on the first **$500,000** of active business income
- SBD limit is shared among associated corporations
- **Phase-out:** SBD reduces by $5 for every $1 of adjusted aggregate investment income (AAII) above $50,000
- Full SBD eliminated when AAII exceeds $150,000

#### Corporate Tax Instalment Payments

Required if the previous year's federal/provincial tax owing exceeded $3,000. Three methods:

1. **Prior year method:** Pay equal monthly instalments based on prior year's total tax
2. **Current year method:** Estimate current year's tax and pay accordingly
3. **First/second preceding year method:** First two instalments based on two years ago; remaining based on prior year

**Safe harbour:** Paying instalments equal to prior year's tax avoids interest even if current year is higher.

#### Capital Cost Allowance (CCA) — Common Classes

| CCA Class | Rate | What it covers |
|-----------|------|---------------|
| Class 1 | 4% | Buildings (most commercial) |
| Class 8 | 20% | Office furniture, equipment |
| Class 10 | 30% | Automobiles, trucks |
| Class 10.1 | 30% | Passenger vehicles > $37,000 (2024 limit) |
| Class 12 | 100% | Small tools, software (< $500) |
| Class 14.1 | 5% | Goodwill, customer lists, other eligible capital |
| Class 50 | 55% | General-purpose computer equipment |
| Class 53 | 50% | Manufacturing & processing equipment |

*Half-year rule:* In the year of acquisition, only 50% of the normal CCA rate is allowed (except for Classes 14.1, some enhanced property).

#### Dividend Types

| | Eligible Dividend | Non-Eligible Dividend |
|--|---|---|
| Source | Income taxed at general rate | Income taxed at SBD/small business rate |
| Gross-up for individual | 38% | 15% |
| Federal dividend tax credit | 20.73% of grossed-up amount | 9.03% of grossed-up amount |
| GRIP tracking required | Yes (corporations) | No |
| Net after-tax advantage | Higher — closer to capital gains treatment | Lower |

---

### Skill 4: `sred-grants`

**Trigger keywords:** SR&ED, scientific research, experimental development, R&D tax credit, T661, investment tax credit, ITC, eligible expenditure, technological uncertainty, technological advancement, IRAP, NRC, BDC, Canada Digital Adoption Program, CDAP, ISED, innovation grant, government funding, subsidy

**What it knows:**

#### SR&ED Program Overview

The Scientific Research & Experimental Development (SR&ED) program is Canada's largest federal tax incentive, delivering ~$3B+ annually to thousands of businesses. Administered by CRA.

**Two components:**
1. **Deduction:** SR&ED expenditures can be fully deducted from income in the year incurred (or carried forward indefinitely)
2. **Investment Tax Credit (ITC):** A percentage of eligible expenditures is credited against tax payable

#### ITC Rates

| Business Type | ITC Rate | Refundable? |
|---------------|----------|-------------|
| CCPC (active business) on first $3M of expenditures | **35%** | **Yes — fully refundable** |
| CCPC above $3M limit OR large corporation | 15% | No (non-refundable; applies against tax owing) |
| Other Canadian corporations | 15% | No |

*CCPC limit of $3M phases out between $500K and $800K of taxable capital.*

#### Eligibility — The Three-Part Test

Work qualifies for SR&ED if it meets **all three**:

1. **Scientific or technological uncertainty:** There was a genuine uncertainty that existing knowledge couldn't resolve — i.e., it wasn't obvious how to do it. The uncertainty must exist *before* the work begins.
2. **Scientific or technological advancement:** The work was performed to advance knowledge in science or technology — not just a business advancement (like implementing a known technology in a new business context).
3. **Systematic investigation:** The work was conducted through hypothesis, testing, analysis, and conclusions — a structured process, not trial-and-error or just trying things out.

**What does NOT qualify:**
- Commercial production or deployment of a known process
- Routine data collection or analysis
- Market research or customer testing
- Style changes, cosmetic changes
- Social science, arts, or humanities research
- Prospecting for minerals

#### Eligible Expenditures

| Category | Eligible | Notes |
|----------|----------|-------|
| Salaries & wages of SR&ED employees | Yes (80% for employees who spend < 90% on SR&ED) | Must track time allocation |
| Subcontractor costs | Yes (80% of amount paid to arm's-length contractors) | |
| Materials consumed or transformed | Yes | |
| Overhead (proxy method) | Yes (55% of eligible salaries) | Most small businesses use proxy method |
| Capital expenditures | No (eliminated in 2014) | |
| Lease costs for SR&ED equipment | Limited | |

#### Filing Requirements

- **Form T661** (SR&ED Expenditures Claim) filed with the T2 return
- **Deadline:** 12 months after the T2 return due date (18 months after year-end total)
- **Documentation:** CRA requires contemporaneous records — lab notebooks, design documents, test logs, meeting minutes, time sheets, revision histories

**Critical:** Document as you go. Reconstructing records after the fact is a major red flag in CRA reviews.

#### Federal Grant Programs for Small Businesses

| Program | Administering Body | What It Funds | Amount |
|---------|-------------------|---------------|--------|
| IRAP (Industrial Research Assistance Program) | NRC | Salary costs for R&D and commercialization projects | Up to $50K–$500K+ |
| Canada Digital Adoption Program (CDAP) | ISED | Adoption of digital technologies | Up to $15K grant + $100K loan |
| Canada Job Grant | ESDC (via provinces) | Employee training and upskilling | Up to 2/3 of training costs |
| Export Expansion Program | EDC | Export growth initiatives | Variable |
| Women Entrepreneurship Strategy (WES) | ISED | Women-owned businesses | Various streams |
| CEBA successor programs | BDC/ISED | Various | Check current availability |
| Provincial innovation grants | Various (OCE, Invest Ottawa, etc.) | Province-specific | Varies widely |

---

## Commands (User-Invoked Workflows)

Commands are explicit actions the user triggers, usually producing a structured output document.

---

### Command 1: `/gst-filing`

**Argument hint:** `[reporting period, total sales, total GST/HST collected, list of business expenses with GST/HST paid]`

**What it produces:**
- Net tax calculation (HST collected − ITCs)
- Breakdown of allowable vs. blocked ITCs
- Whether Quick Method would have been more advantageous
- Filing deadline for the period
- Line-by-line summary ready to reference when filing on CRA My Business Account
- Flag if any amounts seem unusual (e.g., ITC > collected, which triggers a refund)

**Example usage:**
```
/gst-filing Q1 2026 — Ontario business. Sales: $85,000 (13% HST).
Expenses: rent $5,000 + HST, software $2,000 + HST, meals $1,200 + HST,
office supplies $400 + HST
```

---

### Command 2: `/payroll-calc`

**Argument hint:** `[employee name/type, pay period, gross pay, province of employment, TD1 amount]`

**What it produces:**
- CPP deduction (employee)
- EI deduction (employee)
- Federal and provincial income tax deduction
- Employer's matching CPP and EI contributions
- Net pay to employee
- Total remittance amount due to CRA
- Remittance due date based on remitter type

**Example usage:**
```
/payroll-calc Ontario employee, bi-weekly pay, $3,500 gross,
basic personal amount only on TD1
```

---

### Command 3: `/cra-deadlines`

**Argument hint:** `[business type (sole prop / corporation / partnership), fiscal year-end, province, registered for GST/HST, employees: yes/no]`

**What it produces:**
- A 12-month personalized CRA deadline calendar
- Covers: GST/HST filing, payroll remittances, T4/T5 filing, corporate tax instalment, T2 balance due, T2 filing, SR&ED deadline (if applicable)
- Flags the three highest-risk dates (most penalties occur here)
- CRA My Business Account links for each filing type

**Example usage:**
```
/cra-deadlines Ontario corporation, December 31 fiscal year-end,
quarterly GST filer, 3 employees
```

---

### Command 4: `/sred-screen`

**Argument hint:** `[describe the project or work performed in 2–5 sentences]`

**What it produces:**
- Eligibility assessment against the three-part test (Uncertainty / Advancement / Systematic Investigation)
- Traffic light rating: GREEN (strong claim), YELLOW (partial claim likely), RED (unlikely to qualify)
- Specific questions CRA would ask — answered from the project description
- List of what documentation should have been kept (or needs to be created now)
- Estimated ITC range if eligible (requires rough expenditure input)
- Recommendation on whether to engage a SR&ED consultant

**Example usage:**
```
/sred-screen We built a machine learning model to predict equipment failures
in our manufacturing line. We spent 6 months trying different architectures
because existing models didn't generalize to our sensor data.
```

---

### Command 5: `/grant-finder`

**Argument hint:** `[business description: sector, size, province, what you want to fund (hiring/training/equipment/export/R&D/digital)]`

**What it produces:**
- Ranked list of applicable federal and provincial grant programs
- For each: funding amount range, eligibility summary, application deadline (if known), and direct link to program page
- Note on SR&ED applicability (since it's often the highest-value program)
- Realistic expectation-setting (approval rates, timing, effort required)

**Example usage:**
```
/grant-finder Ontario SaaS startup, 8 employees, looking to fund
developer hiring and AI R&D work
```

---

### Command 6: `/t2-checklist`

**Argument hint:** `[incorporated in (province), fiscal year-end, type of income (active business / investment / both), any special items: dividends paid / assets acquired / loans to shareholders / foreign income]`

**What it produces:**
- T2 preparation checklist organized by schedule
- Key schedules required for their situation (Schedule 1, 3, 4, 6, 7, 8, 50, etc.)
- Common errors and omissions checklist
- Documents to gather before meeting the accountant
- Estimated timeline (T2 typically prepared by accountant — this command is for prep, not DIY filing)

**Example usage:**
```
/t2-checklist Ontario corporation, March 31 fiscal year-end,
active business income, purchased $40K in equipment this year,
paid $50K dividend to sole shareholder
```

---

## README.md (Plugin Documentation)

```markdown
# Canadian Tax & CRA Compliance Plugin

A plain-language CRA compliance assistant for Canadian small business owners.
Covers GST/HST, payroll & remittances, corporate income tax (T2),
and SR&ED/government grants.

No tax background required.

---

## Commands

| Command | What it does |
|---------|-------------|
| `/gst-filing [period + sales/expense details]` | Calculates net GST/HST owing, ITC breakdown, and filing summary |
| `/payroll-calc [employee + pay details]` | Calculates CPP, EI, tax deductions, employer costs, and net pay |
| `/cra-deadlines [business type + year-end]` | Generates a personalized 12-month CRA deadline calendar |
| `/sred-screen [project description]` | Screens a project for SR&ED tax credit eligibility |
| `/grant-finder [business description + funding goal]` | Finds applicable federal/provincial grants and funding programs |
| `/t2-checklist [business details]` | Generates a T2 preparation checklist for your accountant meeting |

---

## Skills (Auto-Activating Knowledge)

| Skill | Activates when you ask about |
|-------|----------------------------|
| GST/HST Compliance | HST, GST, input tax credits, sales tax, Quick Method, $30K threshold |
| Payroll & Remittances | CPP, EI, T4, ROE, remittance deadlines, employee vs contractor |
| Corporate Tax (T2) | T2, corporate tax, CCPC, small business deduction, CCA, dividends |
| SR&ED & Grants | SR&ED, R&D credits, IRAP, CDAP, innovation funding, T661 |

---

## Important Disclaimer

This plugin provides general tax and CRA compliance information for educational
purposes. It is **not tax or legal advice**. Tax rules are complex, change
annually (rates, thresholds, and forms), and depend on your specific situation.
Always have a CPA or tax lawyer review filings and material decisions.

---

## Setup

No API connections required. Fully self-contained.

Recommended: Update rate tables annually each March/April after CRA publishes
the current year's payroll deduction tables and contribution rates.
```

---

## CONNECTORS.md

```markdown
# Connectors

This plugin does not require any external service connections.

## Optional Future Connectors

| Connector | Use Case | Status |
|-----------|----------|--------|
| CRA My Business Account (OAuth) | Pre-fill filing periods, outstanding balances | Not yet available via MCP |
| QuickBooks / Xero | Pull actuals for GST filing and payroll calc | Future enhancement |
| Payworks / ADP | Sync payroll records for T4 generation | Future enhancement |
```

---

## Build Phases

### Phase 1 — MVP (Build Now)
- [ ] All 4 skills with rate tables and regulatory knowledge
- [ ] `/cra-deadlines` command (highest value, zero calculation risk)
- [ ] `/sred-screen` command (qualitative — no math)
- [ ] `/grant-finder` command (research-based)

### Phase 2 — Calculation Features (Build After MVP Validation)
- [ ] `/gst-filing` command (requires validation of math outputs)
- [ ] `/payroll-calc` command (requires annual rate table updates)

### Phase 3 — Advanced Features
- [ ] `/t2-checklist` command
- [ ] Annual rate table update workflow (each March/April)
- [ ] QuickBooks/Xero connector integration

---

## Annual Maintenance Requirements

CRA updates the following each year — the plugin must be updated accordingly:

| What changes | When CRA publishes | Affected skills/commands |
|---|---|---|
| CPP contribution rates & maximums | November (for following year) | payroll-remittances, /payroll-calc |
| EI premium rates & maximums | November (for following year) | payroll-remittances, /payroll-calc |
| Federal/provincial tax brackets | February (federal budget) | payroll-remittances, /payroll-calc |
| CCA class limits (e.g., passenger vehicle limit) | Federal budget | corporate-tax-t2, /t2-checklist |
| SR&ED ITC rates / expenditure limits | Federal budget | sred-grants, /sred-screen |
| Grant program availability | Ongoing | sred-grants, /grant-finder |

---

## Risk & Disclaimer Framework

Every output from this plugin must include a tailored disclaimer calibrated to the risk level of the output:

| Output Type | Required Disclaimer Level |
|---|---|
| General information (rates, thresholds, how-to) | Brief footer: "Verify current rates with CRA." |
| Calculation (GST net tax, payroll deductions) | Mid-level: "This is an estimate. Have your bookkeeper or CPA verify before filing." |
| Eligibility determination (SR&ED, grants) | Strong: "Eligibility depends on facts and CRA interpretation. Engage a SR&ED consultant or tax advisor before claiming." |
| Filing deadlines | Always include: "Confirm deadlines with CRA or a tax professional, as special circumstances can affect due dates." |
```
