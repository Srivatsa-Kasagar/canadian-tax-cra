---
description: Identify every CRA-allowable business expense deduction, calculate write-off amounts, flag audit risks, and surface missed deductions — with full work-from-home and vehicle guidance
argument-hint: "[business structure, province, industry, revenue, work-from-home, vehicle use]"
---

The user wants to optimize their business expense deductions under CRA rules.
Their input (if any) is: $ARGUMENTS

## Step 1 — Collect inputs via AskUserQuestion

Check what is already present in $ARGUMENTS. Collect all missing inputs in a single AskUserQuestion call.

**A. Business structure** — if not provided, ask:
Question: "What is your business structure?"
Header: "Structure"
Options:
- Corporation (T2) — CCPC
- Sole proprietor / partnership (T2125)

**B. Province** — if not provided, ask:
Question: "Which province is your business based in?"
Header: "Province"
Options:
- Ontario
- British Columbia
- Alberta
- Quebec
- Manitoba
- Saskatchewan
- Nova Scotia
- New Brunswick
- Other

**C. Industry** — if not provided, ask:
Question: "What best describes your business?"
Header: "Industry"
Options:
- Consulting / professional services
- Technology / SaaS / software
- Trades / contracting / construction
- Retail / e-commerce
- Health / wellness / medical
- Creative / media / marketing agency
- Other

**D. Annual revenue** — ask in plain text:
"What is your estimated annual business revenue? (Used to assess reasonableness of expense claims and flag any CRA risk ratios.)"

**E. Work from home** — if not provided, ask:
Question: "Do you work from home?"
Header: "Home office"
Options:
- Yes — home is my primary place of business
- Hybrid — I work from home several days a week
- No — I work entirely from a separate office or client site

If Yes or Hybrid, ask:
- "What percentage of your home is used exclusively or primarily for business? (Measure the office square footage ÷ total home square footage. Typical range: 10–25%.)"
- "What are your monthly home costs? Include: rent or mortgage interest, utilities (heat/hydro/water), home internet, property tax, and home insurance."

**F. Vehicle use** — if not provided, ask:
Question: "Do you use a personal or company vehicle for business?"
Header: "Vehicle"
Options:
- Yes — I track business kilometres
- Occasionally — rough estimate only
- No

If Yes or Occasionally, ask:
- "What percentage of your total kilometres driven are for business? (Typical range: 30–70%. A logbook is required to support any claim over 50%.)"
- "What are your total annual vehicle operating costs? Include: gas, insurance, maintenance/repairs, licensing."
- "What did the vehicle cost to purchase (or current book value)? (Used to check CRA's luxury vehicle cap of $38,000 for Class 10.1.)"

Once all inputs are collected, proceed to Step 2.

---

## Step 2 — Walk through expense categories

Ask the user to provide their annual spend for each applicable category. Present these as a single grouped question or series — do not ask one at a time.

**Categories:**
1. Salaries and wages (employees, not owner)
2. Owner salary / management fees paid to yourself
3. Subcontractors and consultants
4. Professional fees (accounting, legal, bookkeeping)
5. Software and subscriptions (SaaS tools, cloud services)
6. Computer and equipment purchases (this year)
7. Marketing, advertising, and website
8. Travel (flights, hotels, ground transport — business trips only)
9. Meals and entertainment (business-related)
10. Phone — business portion of monthly bill
11. Training, courses, and professional development
12. Office supplies and postage
13. Bank fees, interest on business loans
14. Business insurance (E&O, liability, commercial property)
15. Private Health Services Plan (PHSP) premiums
16. Other business expenses not listed above

---

## Step 3 — Apply CRA rules to each category

### Salaries, wages, and owner salary
- Fully deductible to the corporation or business
- Owner salary must be "reasonable" — comparable to market rate for the role
- Owner salary triggers CPP (both employee and employer portions)
- Tip: Salary creates RRSP contribution room; dividends do not

### Subcontractors and consultants
- Fully deductible
- Contractors paid over $500/year require a T4A slip
- CRA scrutinizes worker classification — misclassifying employees as contractors is a major audit trigger

### Professional fees
- Fully deductible
- Accounting and legal fees related to business operations: 100% deductible
- Legal fees for share issuance or capital transactions: capitalize, not expense

### Software and subscriptions
- Monthly SaaS tools (Slack, Notion, QuickBooks, etc.): fully deductible as current expenses
- Software purchased outright under $500 per item: Class 12 CCA — 100% in year of purchase (half-year rule: 50% in first year)
- Software purchased outright over $500: Class 10 or 12 depending on nature — apply CCA

### Computer and equipment
- Computers, tablets, monitors: Class 50 — 55% CCA rate (half-year rule applies)
- General office equipment, furniture: Class 8 — 20% CCA rate (half-year rule applies)
- Small tools under $500 each: Class 12 — 100% (half-year: 50% first year)
- Immediate expensing: CCPCs may be eligible to fully expense certain property acquired after Jan 1, 2022 — verify with CPA

Show first-year deductible amount under each applicable class.

### Marketing and advertising
- Fully deductible
- Canadian publications and broadcasters: 100%
- Foreign advertising directed at Canadian market (e.g. Facebook/Google): generally 100% deductible as business expense

### Travel
- Fully deductible if travel has a clear business purpose
- Keep receipts and document the business purpose for each trip
- Mixed personal/business trips: only business portion deductible
- Convention expenses: maximum 2 conventions per year deductible

### Meals and entertainment
- **50% deductible only** — ITA section 67.1
- Must have a clear business purpose and document who attended and why
- CRA scrutinizes meals claims that exceed ~1% of revenue
- Employee events (e.g. holiday party for all staff): 100% deductible — maximum 6 such events per year

### Phone
- Business portion of personal phone bill: deductible
- Reasonable method: % of calls that are business, or maintain separate business line (100%)
- Document calculation method in case of audit

### Training and professional development
- Fully deductible if directly related to maintaining or improving skills required for current business
- Not deductible if training is for a new career or business unrelated to current operations

### Office supplies
- Fully deductible — paper, printer ink, pens, postage, shipping costs

### Bank fees and interest
- Bank service charges: fully deductible
- Interest on business loans or lines of credit: fully deductible
- Interest on money borrowed to invest in corporation: deductible on personal return (not corporate)

### Business insurance
- Fully deductible — E&O, general liability, commercial property, cyber insurance
- Life insurance premiums: generally NOT deductible (common mistake)
- Exception: life insurance used as collateral for a business loan may have a limited deductible component — verify with CPA

### Private Health Services Plan (PHSP)
- Premiums paid by a corporation for employee health coverage are fully deductible
- This includes the owner-employee (shareholder-employee) of a CCPC
- PHSP is one of the most underused deductions for incorporated small business owners
- Covers dental, vision, paramedical (chiro, physio, massage), prescriptions
- Must be a legitimate group plan (e.g. through Chamber of Commerce, Chambers Plan, GroupHEALTH)
- CRA Form T4 benefit reporting may apply if plan exceeds defined limits — verify with CPA

---

## Step 4 — Work-from-home logic for corporations

**If business structure = Corporation AND work from home = Yes or Hybrid:**

Explain the key rule clearly:

> A corporation cannot directly deduct home office expenses as its own costs. The correct and CRA-compliant structure is for the shareholder-employee to charge the corporation rent for use of the home office space. The corporation deducts the rent; the owner reports rental income personally — but offsets it with the same home costs, resulting in near-zero net personal tax impact.

**Calculate the annual rent to charge the corporation:**

1. Total monthly home costs = rent/mortgage interest + utilities + internet + property tax + home insurance
2. Business-use percentage = office sq ft ÷ total home sq ft (user provided)
3. Monthly rent charged to corp = Total monthly costs × business-use %
4. Annual rent = monthly rent × 12

Show: This becomes a fully deductible corporate expense AND near-neutral on personal taxes.

**Document required:**
- Written lease agreement between owner (personally) and the corporation
- Monthly rent invoices or journal entries
- Floor plan or measurement documentation supporting the % claimed

**If sole proprietor:**
Apply standard T2125 home office deduction directly — no rent structure needed. Same % calculation applies. Deduct from business income directly.

---

## Step 5 — Vehicle calculation

If vehicle is used:

1. Total annual vehicle costs × business-use % = deductible operating costs
2. CCA on vehicle:
   - If vehicle cost ≤ $38,000: Class 10 — 30% CCA (half-year: 15% first year)
   - If vehicle cost > $38,000 (passenger vehicle): Class 10.1 — 30% on max $38,000 only (half-year applies)
   - First-year deductible CCA = vehicle cost (capped at $38,000) × 15% × business-use %

**Logbook requirement:**
- CRA requires a logbook documenting: date, destination, business purpose, kilometres for each business trip
- Without a logbook, CRA can deny the entire vehicle deduction
- Simplified logbook: keep a full logbook for one representative 3-month period, then extrapolate annually if consistent year-over-year

Flag if business-use % > 80%: CRA scrutinizes high business-use claims on personal vehicles. Ensure logbook supports this.

---

## Step 6 — Output

---
### Business Expense Optimizer — [Structure], [Province]
**Annual revenue:** $[X] | **Industry:** [type]

#### Deductible Expense Summary

| Expense Category | Annual Amount | Deductible % | Deductible Amount | Key CRA Rule |
|---|---|---|---|---|
| Home office rent (via corp) | $X | 100% | $X | Corp pays rent to owner |
| Vehicle — operating costs | $X | X% | $X | Business-use % — logbook required |
| Vehicle — CCA (first year) | $X | 15% × biz% | $X | Class 10/10.1 — half-year rule |
| Meals & entertainment | $X | 50% | $X | ITA s.67.1 |
| Equipment — CCA Class 50 | $X | 27.5% | $X | Computers — half-year |
| Equipment — CCA Class 8 | $X | 10% | $X | Furniture/equipment — half-year |
| Software under $500/item | $X | 50% | $X | Class 12 — half-year first year |
| Salaries (employees) | $X | 100% | $X | Reasonable compensation |
| Owner salary | $X | 100% | $X | Must be reasonable |
| Subcontractors | $X | 100% | $X | T4A required if >$500 |
| Professional fees | $X | 100% | $X | Business-related only |
| PHSP premiums | $X | 100% | $X | Group plan required |
| Software & subscriptions | $X | 100% | $X | Current expense |
| Marketing & advertising | $X | 100% | $X | Canadian media: 100% |
| Travel | $X | 100% | $X | Business purpose required |
| Phone (business %) | $X | X% | $X | Document calculation |
| Training | $X | 100% | $X | Current business only |
| Office supplies | $X | 100% | $X | |
| Bank fees & interest | $X | 100% | $X | Business loans only |
| Business insurance | $X | 100% | $X | NOT life insurance |
| Other | $X | 100% | $X | As described |
| **Total deductions** | **$X** | | **$X** | |

#### Estimated Tax Savings
- Total deductible expenses: $X
- Corporate tax rate (SBD, [province]): ~X%
- **Estimated tax saved this year: $X**

#### Home Office Summary (Corporation)
If applicable — show:
- Monthly home costs: $X
- Business-use %: X%
- Monthly rent to charge corporation: $X
- Annual corporate deduction: $X
- Required documentation: written lease, monthly invoices, floor plan

#### Red Flags — CRA Audit Triggers
Flag any of the following based on user inputs:
- Meals claim exceeds 1% of revenue → "CRA commonly audits this ratio"
- Vehicle business-use % > 80% → "Ensure logbook exists to support this"
- Home office % > 35% → "Anything above ~30–35% invites scrutiny without clear justification"
- Life insurance claimed as deductible → "Generally not deductible — remove unless specifically advised by CPA"
- No T4A planned for contractors paid >$500 → "T4A required by CRA filing deadline"
- Subcontractors who may be employees → "CRA worker classification risk — review against RC4110 factors"

#### What You May Be Missing
Based on inputs, suggest any unclaimed deductions:
- No PHSP claimed → "As a CCPC owner, PHSP premiums are fully deductible and convert non-deductible personal health costs into a corporate deduction. Worth setting up."
- No CCA claimed on equipment → "If you purchased computers or equipment this year, CCA applies and can reduce taxable income significantly."
- No home office claimed → "If you work from home at all, the rent-to-corporation structure may generate meaningful deductions."
- Technology company with no SR&ED → "/sred-screen your development work — you may qualify for refundable tax credits."

#### Documentation Checklist
For each claimed deduction, what CRA will want to see:

| Deduction | Required documentation |
|---|---|
| Home office rent | Lease agreement, monthly rent invoices, floor plan, home cost receipts |
| Vehicle | Mileage logbook (date, destination, purpose, km), all operating cost receipts |
| Meals & entertainment | Receipts showing amount, restaurant, date, names of attendees, business purpose |
| Travel | Itinerary, receipts, written record of business purpose for each trip |
| Subcontractors | Signed contracts, invoices, T4A slips filed |
| Equipment (CCA) | Purchase receipts, date placed in service, description |
| PHSP | Proof of group plan enrolment, premium payment receipts |
| Training | Receipts, description of course, connection to current business |

---

> ⚠️ This tool provides general guidance based on 2026 CRA rules. Exact deductibility depends on your specific facts, how expenses are documented, and how your CPA treats them. Have a CPA review your expense claims before filing — especially for home office, vehicle, and mixed-use items.
