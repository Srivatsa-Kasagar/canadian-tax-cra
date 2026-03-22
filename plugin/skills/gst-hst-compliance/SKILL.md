---
name: gst-hst-compliance
description: >
  This skill should be used when the user asks about "GST", "HST", "PST",
  "input tax credit", "ITC", "sales tax", "zero-rated", "exempt supply",
  "net tax", "Quick Method", "small supplier", "$30,000 threshold",
  "GST registration", "CRA My Business Account", "GST filing", or any
  question about Canadian sales tax obligations, rates, or filing.
version: 0.2.0
---

# GST/HST Compliance

Assist Canadian small business owners with GST/HST registration, filing, and input tax credit (ITC) recovery. Always give plain-language guidance — assume no tax background.

**Important:** Provide general guidance only. Always recommend the user verify amounts with a bookkeeper or CPA before filing. Tax rates and rules change annually.

## Tax Rates by Province (2026)

| Province/Territory | Tax | Rate | Notes |
|---|---|---|---|
| Alberta | GST | 5% | No provincial sales tax |
| British Columbia | GST | 5% | PST 7% separate (provincial) |
| Manitoba | GST | 5% | RST 7% separate (provincial) |
| New Brunswick | HST | 15% | 5% federal + 10% provincial |
| Newfoundland & Labrador | HST | 15% | 5% federal + 10% provincial |
| Nova Scotia | HST | 15% | 5% federal + 10% provincial |
| Northwest Territories | GST | 5% | No territorial sales tax |
| Nunavut | GST | 5% | No territorial sales tax |
| Ontario | HST | 13% | 5% federal + 8% provincial |
| Prince Edward Island | HST | 15% | 5% federal + 10% provincial |
| Quebec | GST | 5% | QST 9.975% separate (Revenu Québec) |
| Saskatchewan | GST | 5% | PST 6% separate (provincial) |
| Yukon | GST | 5% | No territorial sales tax |

## Registration

**Mandatory:** Once taxable revenues exceed **$30,000** in a single calendar quarter OR in any four consecutive calendar quarters.

**Voluntary:** Permitted below $30,000. Recommended if the business has significant purchases (to recover ITCs) or clients expect a GST/HST number.

**Small supplier:** Under $30,000 — registration optional. Cannot charge GST/HST, cannot claim ITCs.

## Reporting Periods

| Annual Revenue | Filing Period | Deadline |
|---|---|---|
| ≤ $1.5M | Annual | 3 months after fiscal year-end |
| $1.5M – $6M | Quarterly | 1 month after quarter-end |
| Over $6M | Monthly | 1 month after month-end |

Annual filers with net tax ≥ $3,000 must make quarterly instalment payments.

**Quarterly deadlines (calendar year filers):**
- Q1 (Jan–Mar): April 30
- Q2 (Apr–Jun): July 31
- Q3 (Jul–Sep): October 31
- Q4 (Oct–Dec): January 31 (following year)

## Net Tax Formula

```
Net Tax = GST/HST collected on taxable sales
        − Input Tax Credits (ITCs) on business expenses

Positive result → remit to CRA
Negative result → request refund or carry forward
```

## Input Tax Credits (ITCs)

ITCs recover GST/HST paid on business expenses.

**Key rules:**
- Only business-use expenses qualify — no personal use
- Supporting documentation required (invoice with supplier GST/HST number, date, amount, tax paid)
- Time limit: 4 years from the date the return was due
- Partial ITC: claim only the business-use % for mixed-use assets

**ITC rates by expense type:**

| Expense Category | ITC Claimable |
|---|---|
| Office rent, software, professional fees | 100% |
| Business travel, vehicle (business portion) | 100% of business % |
| Meals & entertainment | 50% only |
| Club memberships (golf, fitness, recreational) | 0% — blocked |
| Life insurance premiums | 0% — blocked |

## Supply Types

| Type | GST/HST Charged? | ITC on Inputs? | Examples |
|---|---|---|---|
| Taxable | Yes | Yes | Most goods and services |
| Zero-rated | No (0%) | Yes | Basic groceries, prescription drugs, exports |
| Exempt | No | No | Medical services, most financial services, residential rent |

## Quick Method (Simplified Accounting)

Available to businesses with taxable revenues ≤ $400,000/year. Remit a flat % of gross sales (including tax) instead of tracking individual ITCs.

**Remittance rates (service businesses):**
- 5% GST province: 3.6%
- 13% HST (Ontario): 8.8%
- 15% HST province: 10.4%

**Retail/wholesale businesses** use lower rates (1.8% / 5.0% / 6.0%).

Once elected, Quick Method must be used for a full fiscal year. To elect, file Form GST74 with CRA before the first day of the fiscal year for which you want Quick Method to apply. You can also elect on your first GST/HST return if you're a new registrant.

## Instalment Reconciliation (Annual Filers)

Annual filers with net tax ≥ $3,000 must make quarterly instalment payments during the year. At year-end filing, instalments are reconciled on the return:

```
Line 109  Net tax owing (GST/HST collected − ITCs)
Line 110  Less: instalments already paid during the year
Line 115  = Balance owing (or refund)
```

**Example:** Net tax = $9,600. You paid $2,400 × 4 quarterly instalments = $9,600 on Line 110. Line 115 balance = $0.

If you under-paid instalments, CRA charges instalment interest on the shortfall. If you over-paid, the excess is refunded or applied to your account.

## Common Filing Mistakes

1. **Missing ITC documentation** — invoice must show supplier's GST/HST number
2. **Claiming ITCs on exempt expenses** — insurance premiums, bank fees, residential rent paid to unregistered landlord
3. **Forgetting zero-rated sales** — exports are zero-rated; no HST charged but ITCs still claimable
4. **Late filing** — 1% of net tax + 0.25% per month, up to 12 months
5. **Not registering when required** — CRA can back-assess from the date the $30K threshold was crossed
