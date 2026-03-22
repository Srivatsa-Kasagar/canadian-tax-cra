---
description: Calculate payroll deductions, net pay, and CRA remittance
argument-hint: "[province, pay period, gross pay, TD1 amounts]"
---

The user wants to calculate payroll deductions for an employee.
Their input (if any) is: $ARGUMENTS

## Step 1 — Collect inputs via AskUserQuestion

Check what is already present in $ARGUMENTS. Collect all missing inputs in a single AskUserQuestion call.

**A. Province of employment** — if not provided, ask:
Question: "Which province does this employee work in?"
Header: "Province"
Options:
- Ontario
- British Columbia
- Alberta
- Quebec (uses QPP, not CPP — different rules apply)

**B. Pay period frequency** — if not provided, ask:
Question: "How often do you run payroll for this employee?"
Header: "Pay period"
Options:
- Bi-weekly — every 2 weeks, 26 times/year (Recommended)
- Semi-monthly — twice a month, 24 times/year
- Monthly — once a month, 12 times/year
- Weekly — every week, 52 times/year

**C. Employee status** — if not provided, ask:
Question: "What is this employee's situation?"
Header: "Employee"
Options:
- Standard employee under 65 — CPP applies fully
- Employee aged 65–70 — CPP optional (CPT30 election)
- Employee aged 70 or older — CPP exempt

**D. TD1 claim amount** — if not provided, ask in plain text after AskUserQuestion:
"What is the employee's TD1 federal claim amount? (Default is $16,129 — the 2026 basic personal amount. Use this unless they have additional credits.)"

**E. Gross pay** — if not provided, ask in plain text:
"What is the employee's gross pay for this pay period? (Enter the amount before any deductions.)"

Once all inputs are collected, proceed to calculation.

## Step 2 — Calculate CPP

**2026 rates:**
- Employee rate: 5.95% | Employer rate: 5.95% (matching)
- Max pensionable earnings: $68,500/year | Basic exemption: $3,500/year
- Max annual contribution (each): ($68,500 − $3,500) × 5.95% = $3,867.50

Per-period exemption = $3,500 ÷ pay periods per year

Employee CPP this period:
= (gross pay − per-period exemption) × 5.95%
Capped at: $3,867.50 ÷ pay periods per year

**CPP2** — apply only if annualized gross exceeds $68,500:
= (annualized gross − $68,500) × 4%, capped at $188/year total
CPP2 per period = annual CPP2 ÷ pay periods

Skip CPP entirely if employee is 70+ or has filed CPT30.

## Step 3 — Calculate EI

**2026 rates:**
- Employee rate: 1.66% | Employer rate: employee × 1.4 = 2.324%
- Max insurable earnings: $63,200/year
- Max annual employee premium: $63,200 × 1.66% = $1,049.12

Employee EI this period = gross pay × 1.66%
Capped at: $1,049.12 ÷ pay periods per year

Employer EI this period = employee EI × 1.4

Note for Quebec employees: lower EI rate applies; QPP replaces CPP.

## Step 4 — Calculate income tax (annualized method)

Annualized gross = gross pay × pay periods per year

**Federal brackets 2026:**
- 15% on first $57,375
- 20.5% on $57,376–$114,750
- 26% on $114,751–$158,520
- 29% on $158,521–$220,000
- 33% above $220,000

Federal basic personal credit = TD1 federal claim × 15%
Annual federal tax = bracket calculation − federal basic personal credit

**Provincial tax — use province-specific rates:**
- Ontario: 5.05% / 9.15% / 11.16% / 12.16% / 13.16%
- BC: 5.06% / 7.7% / 10.5% / 12.29% / 14.7% / 16.8% / 20.5%
- Alberta: 10% / 12% / 13% / 14% / 15% (on $148,269 / $177,922 / $237,230 / $355,845 thresholds — 2025 values, verify for 2026)
- Quebec: 14% / 19% / 24% / 25.75% (QPP, not CPP)

Provincial basic personal credit = provincial TD1 amount × lowest provincial rate
Annual provincial tax = bracket calculation − provincial credit

Per-period tax = annual tax ÷ pay periods

## Step 5 — Build the payroll summary

Calculate:
- Total employee deductions = CPP + CPP2 + EI + federal tax + provincial tax
- Net pay = gross pay − total employee deductions
- Total CRA remittance = employee deductions + employer CPP + employer EI
- Total employer cost = gross pay + employer CPP + employer EI

## Step 6 — Output

---
### Payroll Summary — [Pay Period Type], [Province]
**Gross Pay:** $[amount] | **Pay Periods/Year:** [number]

#### Employee Deductions
| Deduction | Calculation | This Period |
|---|---|---|
| CPP | ($[gross] − $[exemption]) × 5.95% | $X |
| CPP2 | [if applicable] | $X |
| EI | $[gross] × 1.66% | $X |
| Federal Income Tax (est.) | Annualized brackets | $X |
| Provincial Tax — [prov] (est.) | Annualized brackets | $X |
| **Total Deductions** | | **$X** |
| **Net Pay to Employee** | | **$X** |

#### Employer Contributions
| Item | Amount |
|---|---|
| Employer CPP match | $X |
| Employer EI (employee × 1.4) | $X |
| **Total CRA Remittance Due** | **$X** |
| **Total Cost to Employer** | **$X** |

**Remittance deadline:** 15th of [following month] (regular remitters)

#### Annualized Snapshot
Show what these numbers look like across a full year (× pay periods), and flag when CPP and EI maximums will be reached based on current gross pay.

---

> ⚠️ Income tax amounts are estimates using simplified annualized calculations. Use CRA's Payroll Deductions Online Calculator (PDOC) at canada.ca/pdoc or T4032 tables for exact withholding before processing each pay run. CPP and EI maximums reset every January 1 and must be tracked year-to-date for each employee.
