---
description: Calculate net GST/HST owing and produce a filing summary
argument-hint: "[province, reporting period, sales details, expense details]"
---

The user wants to calculate their GST/HST net tax and produce a filing summary.
Their input (if any) is: $ARGUMENTS

## Step 1 — Collect inputs via AskUserQuestion

Check if the following are already present in $ARGUMENTS. For each piece of information that is missing, use AskUserQuestion to ask the user. Ask all missing questions in a single AskUserQuestion call — do not ask one at a time.

**Required inputs:**

**A. Province** — if not already provided, ask:
Question: "Which province or territory does your business operate in?"
Header: "Province"
Options:
- Ontario (13% HST)
- Alberta (5% GST)
- British Columbia (5% GST)
- Other province — I'll type it in

**B. Reporting period** — if not already provided, ask:
Question: "Which reporting period are you filing for?"
Header: "Period"
Options:
- Q1 (January – March)
- Q2 (April – June)
- Q3 (July – September)
- Q4 (October – December)

**C. Filing year** — if not already provided, ask:
Question: "Which year is this filing for?"
Header: "Year"
Options:
- 2026
- 2025

**D. Revenue details** — if sales amounts are not provided, ask the user in plain text:
"Please share your sales for the period — describe each revenue stream and the amount (e.g. 'Consulting $65,000, Product sales $22,000, US export $8,000')."

**E. Expense details** — if expense amounts are not provided, ask the user in plain text:
"List your main business expenses for the period with amounts (e.g. 'Rent $4,500, Software $1,800, Meals $1,400, Legal fees $2,500'). Skip personal expenses."

**F. Instalments already paid** — after collecting expense details, ask in plain text:
"Have you already made any GST/HST instalment payments for this reporting period? If yes, enter the total amount paid (or type 'none')."

Once all inputs are collected, proceed to calculation.

## Step 2 — Identify the tax rate

From the gst-hst-compliance skill, look up the rate for the selected province:
- 5% GST: AB, BC, MB, NT, NU, QC, SK, YT
- 13% HST: ON
- 15% HST: NB, NL, NS, PE

Note if PST / QST applies separately — those are outside scope of this CRA filing.

## Step 3 — Classify revenue by supply type

Apply these rules from the gst-hst-compliance skill:
- **Taxable supply:** charge GST/HST — most goods and services sold in Canada
- **Zero-rated supply (0%):** no GST/HST charged, but ITCs still claimable — exports, basic groceries, prescription drugs
- **Exempt supply:** no GST/HST charged and no ITCs on related inputs — residential rent received, most financial services, medical services

Classify each revenue line. Ask the user if classification is ambiguous (e.g. mixed domestic/export sales).

## Step 4 — Calculate HST/GST collected

For each taxable revenue line: amount × provincial rate = tax collected
Zero-rated and exempt lines: $0 tax collected

## Step 5 — Calculate Input Tax Credits (ITCs)

For each expense, apply ITC rules from the gst-hst-compliance skill:

| Expense type | ITC rate |
|---|---|
| Office rent, software, professional fees, equipment | 100% of tax paid |
| Business vehicle (business use portion only) | 100% of business % |
| Meals & entertainment | 50% of tax paid |
| Club memberships, life insurance | 0% — blocked |
| Personal expenses | 0% — not eligible |

ITC per line = expense amount × provincial tax rate × ITC %

Flag any expense where the user hasn't paid HST (e.g. landlord not registered, paying a non-registered supplier under $30K) — no ITC available in those cases.

## Step 6 — Quick Method comparison

If the user's annualized revenue is ≤ $400,000 AND they are not already on Quick Method:

Calculate Quick Method tax:
- Service business rate: 3.6% (5% GST province) / 8.8% (13% HST) / 10.4% (15% HST)
- Retail/wholesale rate: 1.8% / 5.0% / 6.0%
- Apply to: total taxable sales × (1 + tax rate)
- Deduct 1% credit on first $30,000 of taxable supplies incl. tax

Compare to standard method and show the difference. Add note:
"Quick Method must be elected at the start of a fiscal year — consult your CPA before switching."

## Step 7 — Output

Produce the complete filing summary in this format:

---
### GST/HST Filing Summary
**Province:** [province] | **Period:** [period year] | **Rate:** [rate]
**Filing Deadline:** [date]

#### Revenue
| Description | Amount | Supply Type | Tax Collected |
|---|---|---|---|
| [lines] | | | |
| **Total (Line 101)** | **$X** | | **$X (Line 105)** |

#### Input Tax Credits
| Expense | Amount | ITC Type | ITC Claimable |
|---|---|---|---|
| [lines] | | | |
| **Total ITCs (Line 108)** | | | **$X** |

#### Net Tax
| | Amount |
|---|---|
| HST/GST Collected (Line 105) | $X |
| Less: ITCs (Line 108) | −$X |
| **Net Tax (Line 109)** | **$X** |
| Less: Instalments Paid (Line 110) | −$X |
| **Balance Owing / Refund (Line 115)** | **$X** |

If no instalments were paid, Line 110 = $0 and Line 115 = Line 109.

[Quick Method comparison table if eligible]

#### What to Enter in CRA My Business Account
Line 101 · Line 105 · Line 108 · Line 109 · Line 110 · Line 115 — with exact amounts

#### Next Steps
Step-by-step instructions for filing online.

---

> ⚠️ This summary is an estimate for planning purposes. Verify all amounts with your bookkeeper or CPA before filing. Confirm your filing deadline and account status in CRA My Business Account at canada.ca/en/revenue-agency.
