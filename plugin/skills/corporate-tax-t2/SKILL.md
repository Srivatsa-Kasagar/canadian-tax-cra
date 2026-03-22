---
name: corporate-tax-t2
description: >
  This skill should be used when the user asks about "T2", "corporate tax",
  "corporate income tax", "CCPC", "small business deduction", "SBD",
  "passive income", "instalment payments", "fiscal year end", "CCA",
  "capital cost allowance", "dividend", "eligible dividend", "RDTOH",
  "loss carryforward", "associated corporations", "Schedule 1", "Schedule 8",
  or any question about Canadian corporate income tax filing and planning.
version: 0.2.0
---

# Corporate Tax (T2)

Help Canadian small business owners understand their corporate income tax obligations, filing deadlines, and key tax concepts. Always clarify that T2 returns should be prepared by a CPA — this skill helps owners prepare, not file independently.

## Key Filing Deadlines

| Obligation | Deadline |
|---|---|
| T2 return filing | 6 months after fiscal year-end |
| Balance owing (most corporations) | 2 months after fiscal year-end |
| Balance owing (eligible CCPCs) | 3 months after fiscal year-end |
| Corporate tax instalments | Monthly or quarterly (see below) |
| SR&ED claim (T661) | 18 months after fiscal year-end |

**Eligible CCPC for 3-month balance:** Canadian-Controlled Private Corporation with taxable income ≤ small business deduction limit in the current or prior year, and combined taxable capital ≤ $10M.

## Tax Rates (2026 — confirm with CPA)

| Income Type | Federal Rate | Combined (Ontario example) |
|---|---|---|
| Active business — SBD eligible (first $500K) | 9% | ~12.2% |
| Active business — above SBD limit | 15% | ~26.5% |
| Investment / passive income | 38.67% (before RDTOH) | ~50.17% |
| Capital gains | 7.5%–16.5% | varies — ⚠️ inclusion rate subject to legislative change; confirm with CPA |

## Small Business Deduction (SBD)

- Reduces federal rate to **9%** on first **$500,000** of active business income
- Available to **Canadian-Controlled Private Corporations (CCPCs)** only
- $500K limit shared among **associated corporations**
- **Phase-out:** SBD reduced $5 for every $1 of adjusted aggregate investment income (AAII) above $50,000; eliminated when AAII > $150,000

## Corporate Tax Instalment Payments

Required if prior year tax owing > $3,000. Three safe-harbour methods:

1. **Prior year method:** Equal monthly instalments = prior year total tax ÷ 12
2. **Current year method:** Estimate current year tax; pay accordingly
3. **First/second preceding year method:** First 2 instalments based on 2 years ago; remainder based on prior year

Paying instalments equal to prior year tax avoids arrears interest even if current year is higher.

## Capital Cost Allowance (CCA) — Common Classes

| Class | Rate | What it covers |
|---|---|---|
| 1 | 4% | Commercial buildings |
| 8 | 20% | Office furniture, equipment |
| 10 | 30% | Automobiles, trucks |
| 10.1 | 30% | Passenger vehicles over the prescribed cost limit (indexed annually — verify current limit with CRA or your CPA) |
| 12 | 100% | Small tools, software < $500 |
| 14.1 | 5% | Goodwill, customer lists |
| 50 | 55% | General-purpose computers |
| 53 | 50% | Manufacturing & processing equipment |

**Half-year rule:** In the acquisition year, only 50% of the normal CCA rate applies (exceptions for certain eligible property).

**Immediate expensing:** CCPCs (and individuals) may be eligible to fully expense certain depreciable property acquired after January 1, 2022. Confirm eligibility with CPA.

## Dividend Types

| | Eligible Dividend | Non-Eligible Dividend |
|---|---|---|
| Sourced from | Income taxed at general (non-SBD) rate | Income taxed at SBD/small business rate |
| Individual gross-up | 38% | 15% |
| Federal dividend tax credit | 20.73% of grossed-up amount | 9.03% of grossed-up amount |
| Net tax advantage for shareholder | Higher — approaching capital gains treatment | Lower |
| GRIP tracking required | Yes | No |

## Shareholder Loans

Loans from a corporation to a shareholder must be repaid within **one year after the corporation's fiscal year-end** in which the loan was made — or the full amount is included in the shareholder's personal income.

Exceptions: bona fide loans with repayment schedule, housing loans, vehicle purchase loans (specific conditions apply).

## Common T2 Schedules

| Schedule | Purpose |
|---|---|
| Schedule 1 | Net income for tax purposes (reconcile accounting to tax income) |
| Schedule 3 | Dividends received |
| Schedule 4 | Corporation loss continuity |
| Schedule 6 | Summary of dispositions |
| Schedule 7 | Aggregate investment income and active business income |
| Schedule 8 | CCA calculation |
| Schedule 50 | Shareholder information (ownership %) |
| Schedule 100/125/141 | Balance sheet / income statement / notes checklist |

## Documents to Gather Before Meeting Your Accountant

- Financial statements (income statement + balance sheet)
- Bank statements and reconciliations
- Fixed asset additions/disposals with purchase invoices
- Shareholder loan balance
- Prior year T2 return and notice of assessment
- Any government correspondence from CRA
- Dividends paid (amounts and dates)
- GST/HST returns filed during the year
