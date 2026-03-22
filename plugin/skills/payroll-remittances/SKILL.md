---
name: payroll-remittances
description: >
  This skill should be used when the user asks about "payroll", "CPP",
  "EI", "income tax deduction", "T4", "ROE", "Record of Employment",
  "remittance", "payroll deduction", "employer contribution", "PD7A",
  "accelerated remitter", "employee vs contractor", "payroll deadline",
  "RP account", "hiring an employee", or any question about Canadian
  payroll obligations and CRA remittance requirements.
version: 0.2.0
---

# Payroll & Remittances

Guide Canadian small business owners through payroll deductions, employer contributions, remittance schedules, and year-end reporting obligations.

**Important:** Payroll calculations must be verified using CRA's Payroll Deductions Online Calculator (PDOC) or T4032 tables before each pay run. Rates change annually each January.

## 2026 Deduction Rates

### CPP (Canada Pension Plan)

| | Rate | Annual Maximum |
|---|---|---|
| Employee contribution | 5.95% | ~$3,867 |
| Employer matching | 5.95% | ~$3,867 |
| Basic exemption | — | $3,500/year |
| Maximum pensionable earnings | — | $68,500/year |

**CPP2 (Second Additional CPP):** 4% on earnings between $68,500 and $73,200 (~$188 max each for employee and employer).

Employees aged 70+ are exempt from CPP. Ages 65–69 may opt out with CPT30 form.

### EI (Employment Insurance)

| | Rate | Annual Maximum |
|---|---|---|
| Employee premium | 1.66% | ~$1,049 |
| Employer premium | 2.32% (1.4× employee) | ~$1,468 |
| Maximum insurable earnings | — | $63,200/year |

Quebec employees pay a lower EI rate and contribute separately to QPIP.

### Alberta Provincial Income Tax

Alberta uses a **graduated bracket system** (not a flat rate). 2025 brackets (verify 2026 indexed values with CRA T4032 Alberta tables):

| Taxable Income | Rate |
|---|---|
| First $148,269 | 10% |
| $148,269 – $177,922 | 12% |
| $177,922 – $237,230 | 13% |
| $237,230 – $355,845 | 14% |
| Over $355,845 | 15% |

Alberta personal amount: $21,003 (2025 — verify for 2026).

### Federal Income Tax

Calculated using CRA T4032 Payroll Deductions Tables based on:
- Province of employment
- Pay period frequency
- TD1 Personal Tax Credits Return (federal and provincial)
- Year-to-date earnings

Always use the TD1 amount the employee submitted. Default to basic personal amount if no TD1 received.

## Remittance Schedules

| Remitter Type | Criteria | Due Date |
|---|---|---|
| New employer / Regular | Average monthly withholding < $25,000 | 15th of the following month |
| Quarterly | New employer, < $1,000/month average, clean history | End of Apr, Jul, Oct, Jan |
| Accelerated — Threshold 1 | Monthly withholding $25,000–$99,999 | Within 3 working days after 15th AND end of month |
| Accelerated — Threshold 2 | Monthly withholding $100,000+ | Within 3 working days after each weekly payroll |

**Remittance = employee CPP + employee EI + income tax withheld + employer CPP + employer EI**

Late penalties: 3% (1–3 days late), 5% (4–5 days), 7% (6–7 days), 10% (8+ days), 20% (repeat offender).

## T4 Slips — Annual Filing

**Deadline:** February 28 (or 29 in leap year) of the following year.

File T4 slip with CRA AND deliver to employee.

Key T4 boxes:
| Box | Field |
|---|---|
| 14 | Employment income |
| 16 | Employee CPP contributions |
| 17 | Employee CPP2 contributions |
| 18 | Employee EI premiums |
| 22 | Income tax deducted |
| 24 | EI insurable earnings |
| 26 | CPP/QPP pensionable earnings |

File T4 Summary (totals across all employees) with the slips.

## Record of Employment (ROE)

Issue within **5 calendar days** of any interruption of earnings:
- Termination or layoff
- Leave of absence (parental, medical, compassionate care)
- Reduction in hours below 40% of normal

File electronically via Service Canada ROE Web (mandatory for 26+ employees; recommended for all).

ROE determines EI benefit eligibility — incorrect ROEs can harm or delay employee claims.

## Employee vs. Contractor — CRA's Test

Misclassifying an employee as a contractor triggers retroactive CPP/EI + penalties + interest.

**Indicators of employment (all or most present = likely employee):**
- Employer controls how, when, and where work is done
- Worker uses employer's tools and equipment
- No chance of profit / risk of loss
- Cannot subcontract or hire helpers
- Work is integral to the business's operations

**When uncertain:** Use CRA's Worker Classification questionnaire (RC4110) or request a ruling (CPT1 form). When in doubt, treat as employee.

## Payroll Setup Checklist

- [ ] Register for a payroll (RP) account with CRA (can be done via My Business Account)
- [ ] Collect TD1 Federal and provincial TD1 from each new employee
- [ ] Set up direct deposit remittance to CRA via My Payment or financial institution
- [ ] Determine remitter type after first 12 months of operation
- [ ] Set calendar reminders for remittance due dates

## Common Payroll Mistakes

1. **Late remittances** — penalties start immediately; set up auto-reminders
2. **Wrong remitter type** — CRA assigns type based on prior year; check annually
3. **Forgetting employer portions** — remittance includes both employee deductions AND employer CPP/EI match
4. **Not issuing ROE on time** — employee cannot apply for EI without it
5. **Using stale rates** — CPP/EI maximums reset every January 1
