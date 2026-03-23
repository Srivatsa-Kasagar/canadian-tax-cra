---
description: Generate a T2 preparation checklist tailored to your corporation's situation
argument-hint: "[province, fiscal year-end, income types, any special items: dividends/assets/shareholder loans/foreign income]"
---

The user wants a T2 preparation checklist for their corporation.
Their input (if any) is: $ARGUMENTS

## Step 1 — Collect inputs via AskUserQuestion

Check what is already in $ARGUMENTS. Collect all missing inputs in a single AskUserQuestion call.

**First call — corporation profile:**

Question 1: "Where is your corporation incorporated or primarily operating?"
Header: "Province"
Options:
- Ontario
- British Columbia
- Alberta
- Quebec
- Other province — I'll type it in

Question 2: "What is your fiscal year-end month?"
Header: "Year-end"
Options:
- December 31 (calendar year)
- March 31
- June 30
- Other — I'll type it in

Question 3: "What type of income does your corporation earn?"
Header: "Income type"
Options:
- Active business income only (consulting, services, products, etc.)
- Investment/passive income only (rental, dividends, interest)
- Both active and investment income

Question 4: "Did any of these occur this fiscal year? (Select all that apply)"
Header: "Special items"
multiSelect: true
Options:
- Dividends paid to shareholders
- Capital assets purchased or sold (equipment, vehicles, computers)
- Shareholder loans (money borrowed from or loaned to the corporation)
- Foreign income or non-resident transactions
- New employees hired for the first time
- SR&ED research and development work

Wait for answers. Then ask in plain text:
"Is your corporation a Canadian-Controlled Private Corporation (CCPC)? (Yes / No / Not sure)"

Once all inputs collected, proceed.

## Step 2 — Build the checklist

Generate a tailored T2 preparation checklist based on the profile.

### Base checklist (all corporations)

**Financial Statements:**
- [ ] Year-end income statement (profit & loss) — prepared by accountant or bookkeeper
- [ ] Year-end balance sheet — must agree to all supporting schedules
- [ ] Bank statements and reconciliations for all accounts (all 12 months)
- [ ] Credit card statements (business cards only)
- [ ] Loan statements showing opening balance, payments, and year-end balance

**Revenue & Expenses:**
- [ ] Categorized transaction listing from accounting software (QuickBooks, Xero, Wave, etc.)
- [ ] All sales invoices — especially large transactions and related-party transactions
- [ ] Receipts for all expense categories above $500 (CRA audit-ready)
- [ ] Home office expenses if applicable: sq footage of office vs. total home, annual utilities/rent

**Government Accounts:**
- [ ] Prior year T2 return and Notice of Assessment
- [ ] CRA My Business Account — confirm no outstanding balances or correspondence
- [ ] GST/HST returns filed during the fiscal year (all periods)
- [ ] Payroll remittance history if employees (PD7A summaries)

**Prior Year Items:**
- [ ] Copy of prior year T2 (for carryforward amounts: losses, ITCs, CCA UCC balances)
- [ ] Any CRA audit adjustments or reassessments since last filing

---

### Add if income type includes **active business income** (CCPC):

**Small Business Deduction planning:**
- [ ] Confirm active business income amount for SBD limit ($500K federal)
- [ ] If associated corporations exist: combined active business income across all
- [ ] Passive/investment income earned this year (if > $50K, SBD phase-out may apply)

---

### Add if income type includes **investment/passive income**:

- [ ] Interest income statements (T5s received)
- [ ] Dividend income received (from other Canadian corporations: T5 slips)
- [ ] Rental property: gross rents, mortgage interest, property tax, repairs, CCA
- [ ] RDTOH (Refundable Dividend Tax on Hand) balance from prior year T2
- [ ] GRIP (General Rate Income Pool) balance if eligible dividends were paid or planned

---

### Add if **dividends paid** this year:

- [ ] Amount and date of each dividend resolution
- [ ] Shareholders who received dividends and their ownership percentages (Schedule 50)
- [ ] Type of dividend: eligible or non-eligible (depends on whether GRIP balance exists)
- [ ] T5 slips issued to shareholders (deadline: February 28 of following year)

---

### Add if **capital assets purchased or sold**:

- [ ] Purchase invoices for all capital additions with date, description, and amount
- [ ] CCA class for each asset (your accountant will classify — have invoices ready)
- [ ] For vehicles: personal vs. business use percentage, and whether cost exceeds the passenger vehicle limit
- [ ] For disposals: original cost, proceeds of disposition, and date of sale
- [ ] Schedule 8 from prior year T2 (shows opening UCC balances by class)
- [ ] Immediate expensing: eligible CCPC property acquired after Jan 1, 2022 may qualify for 100% deduction — flag for accountant

---

### Add if **shareholder loans**:

- [ ] Shareholder loan account balance at year-end (from balance sheet)
- [ ] Date each loan was advanced or repaid
- [ ] Purpose of each loan (housing loan, vehicle purchase, and general loans have different rules)
- [ ] Warning: loans not repaid within one year of the corporation's fiscal year-end are included in the shareholder's personal income. Confirm repayment dates with accountant.

---

### Add if **foreign income or non-resident transactions**:

- [ ] Details of all foreign income sources (country, type, amount in CAD)
- [ ] Foreign tax paid (for foreign tax credit — T2209)
- [ ] Any payments to non-residents (withholding tax obligations may apply)
- [ ] Transfer pricing documentation if transactions with related non-resident entities

---

### Add if **SR&ED work performed**:

- [ ] Technical project descriptions for each qualifying project
- [ ] Time sheets showing SR&ED hours by employee
- [ ] Lab notebooks, design docs, test logs, Git commit history
- [ ] Salary details for employees working on SR&ED projects
- [ ] Subcontractor invoices related to SR&ED work
- [ ] Form T661 (SR&ED Expenditures Claim) — prepared by SR&ED consultant
- [ ] Note: T661 deadline is 18 months after fiscal year-end — do not miss it
- [ ] Run `/sred-screen [project description]` if eligibility is not yet confirmed

---

### Add if **first employees hired this year**:

- [ ] RP (payroll) account registered with CRA
- [ ] T4 slips prepared for all employees (deadline: February 28)
- [ ] Confirm employee vs. contractor status for all workers (see payroll-remittances skill)

---

## Step 3 — Required T2 Schedules

Based on the profile, list the required schedules. Indicate what each one does so the user can tell their accountant.

**Always required:**
| Schedule | Purpose |
|---|---|
| Schedule 1 | Reconciles accounting income to taxable income (add-backs, deductions) |
| Schedule 100 | Balance sheet information |
| Schedule 125 | Income statement information |
| Schedule 141 | Notes checklist (type of financial statements provided) |

**Add based on profile:**
| Schedule | Required When |
|---|---|
| Schedule 3 | Dividends received from other Canadian corporations |
| Schedule 4 | Loss carryforward/carryback continuity |
| Schedule 6 | Summary of dispositions (assets sold) |
| Schedule 7 | Aggregate investment income and active business income (passive income) |
| Schedule 8 | Capital Cost Allowance (CCA) — always required if any fixed assets |
| Schedule 50 | Shareholder information (ownership %) — required for all private corporations |
| Schedule 63 | Return of fuel charges — if applicable |
| T2 SCH 200 | Small Business Deduction calculation (CCPC only) |

---

## Step 4 — Output

---
### T2 Preparation Checklist
**Corporation:** [province] | **Year-end:** [month/year] | **Income type:** [type]
**CCPC:** [yes/no/unknown] | **Special items:** [list]

#### Documents to Gather
[Full checklist from Step 2, formatted with checkboxes]

#### T2 Schedules Your Accountant Will Need
[Table from Step 3 filtered to this profile]

#### Common Errors to Avoid
List 4–5 errors most relevant to this profile. Examples:
- Forgetting to include all shareholder loans on the balance sheet
- Missing CCA on assets purchased in the final weeks of the fiscal year
- Not tracking GRIP balance when paying dividends from general-rate income
- Filing T4s late (missed February 28 deadline triggers penalties)
- Claiming SBD when passive income phase-out applies

#### Timeline
| Milestone | Suggested Date |
|---|---|
| Gather documents | Within 30 days of year-end |
| Deliver to accountant | 6–8 weeks after year-end |
| Review draft T2 | 10–12 weeks after year-end |
| File T2 return | By 6-month deadline |
| Pay balance owing | By 2-month deadline (3 months for eligible CCPCs) |

---

> ⚠️ This checklist is a guide to help you prepare for your accountant meeting — it is not a substitute for professional tax advice. T2 returns should always be prepared or reviewed by a qualified CPA. Tax rules change annually; have your accountant confirm current rates, limits, and schedules before filing.
