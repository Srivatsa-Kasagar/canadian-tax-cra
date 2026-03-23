---
description: Identify every CRA-allowable business expense deduction, calculate write-off amounts, flag audit risks, and surface missed deductions — with work-from-home and vehicle guidance
argument-hint: "[business structure, province, work-from-home, vehicle use, expense amounts]"
---

The user wants to optimize their business expense deductions under CRA rules.
Their input (if any) is: $ARGUMENTS

---

## Interaction 1 — Core profile (AskUserQuestion)

Check $ARGUMENTS. If structure, province, or WFH status are missing, ask all three in one AskUserQuestion call:

**Business structure:**
Question: "What is your business structure?"
Options:
- Corporation (CCPC / T2)
- Sole proprietor or partnership (T2125)

**Province:**
Question: "Which province is your business based in?"
Options: Ontario · British Columbia · Alberta · Quebec · Manitoba · Saskatchewan · Nova Scotia · New Brunswick · Other

**Work from home?**
Question: "Do you work from home?"
Options:
- Yes — home is my primary place of business
- Hybrid — some days at home
- No — separate office only

---

## Interaction 2 — Vehicle (conditional AskUserQuestion)

Only ask if not already provided in $ARGUMENTS:

Question: "Do you use a vehicle for business?"
Options:
- Yes — I track business kilometres
- No

If Yes, follow up in plain text (single message):
> "Please provide: (a) business-use % of total km driven, (b) total annual vehicle operating costs (gas + insurance + maintenance + licensing), (c) vehicle purchase price."

---

## Interaction 3 — All expenses at once (plain text)

Send this as a single message — do not split into separate questions:

> "Almost done! Please fill in your **annual amounts** for any of the following that apply to your business. Leave blank or write $0 for anything that doesn't apply.
>
> **Payroll & People**
> - Salaries & wages (employees, not yourself): $
> - Owner salary / management fees: $
> - Subcontractors & consultants: $
>
> **Home & Vehicle** *(skip if already provided)*
> - Home office % of home sq ft: %
> - Monthly home costs (rent/mortgage interest + utilities + internet + property tax + insurance): $
> - Vehicle operating costs (annual): $
> - Vehicle purchase price: $
> - Vehicle business-use %: %
>
> **Operations**
> - Professional fees (accounting, legal): $
> - Software & SaaS subscriptions: $
> - Computer & equipment purchased this year: $
> - Office furniture purchased this year: $
> - Small tools / software items under $500 each: $
> - Marketing & advertising: $
> - Business travel (flights, hotels, transport): $
> - Meals & entertainment (business-related): $
> - Phone — business portion: $
> - Training & professional development: $
> - Office supplies & postage: $
> - Bank fees & business loan interest: $
> - Business insurance (E&O, liability, property): $
> - Private Health Services Plan (PHSP) premiums: $
> - Annual revenue (for audit ratio checks): $
> - Other business expenses: $"

---

## CRA Rules Reference (apply when calculating output)

### Home office

**Corporation:** Cannot deduct home office costs directly. Owner charges the corp rent equal to home costs × business-use %. Corp deducts the rent; owner reports rental income but offsets with same home costs — net personal tax ≈ zero.
- Monthly rent to corp = monthly home costs × business-use %
- Docs required: written lease, monthly invoices, floor plan

**Sole proprietor:** Deduct home costs × business-use % directly on T2125.

Flag if business-use % > 35%.

### Vehicle

- Operating costs deductible = total annual costs × business-use %
- CCA (first year):
  - Vehicle cost ≤ Class 10.1 prescribed limit → Class 10: 30% × 50% half-year = 15% first year × business-use %
  - Vehicle cost > prescribed limit → Class 10.1: cap at prescribed limit, same 15% × business-use %
  - ⚠️ Class 10.1 limit is indexed annually — confirm current limit with CRA before filing
- Logbook required for any vehicle claim; scrutinized above 80% business use

### Meals & entertainment
- 50% deductible only (ITA s.67.1)
- Flag if claim > 1% of revenue

### Equipment CCA (first year, half-year rule)
- Computers / tablets (Class 50): 55% × 50% = **27.5%** first year
- Office furniture / equipment (Class 8): 20% × 50% = **10%** first year
- Small tools / software under $500/item (Class 12): 100% × 50% = **50%** first year
- Immediate expensing may apply to CCPCs for eligible property — verify with CPA

### Everything else
- Salaries, owner salary, subcontractors, professional fees, software subscriptions, marketing, travel, phone (business portion), training, supplies, bank fees, business insurance, PHSP: **100% deductible**
- Life insurance premiums: generally **NOT deductible** — flag if claimed
- T4A required for contractors paid > $500/year

---

## Output

---
### Business Expense Optimizer — [Structure], [Province]

#### Deductible Expense Summary

| Expense | Annual Amount | Deductible % | Deductible Amount | CRA Rule |
|---|---|---|---|---|
| Home office [rent to corp / T2125] | $X | 100% | $X | [Corp rent or direct T2125] |
| Vehicle — operating | $X | X% | $X | Business-use % — logbook |
| Vehicle — CCA year 1 | $X | X% | $X | Class 10/10.1 — half-year |
| Meals & entertainment | $X | 50% | $X | ITA s.67.1 |
| Computers (Class 50) | $X | 27.5% | $X | Half-year rule |
| Furniture (Class 8) | $X | 10% | $X | Half-year rule |
| Small tools (Class 12) | $X | 50% | $X | Half-year rule |
| [All 100% items] | $X | 100% | $X | Fully deductible |
| **Total deductions** | **$X** | | **$X** | |

#### Estimated Tax Savings
- Total deductible expenses: **$X**
- Corporate SBD rate ([province]): ~X%
- **Estimated tax saved: $X**

#### Home Office Detail (if applicable)
Show the monthly rent calculation, annual corporate deduction, and documentation checklist.

#### Red Flags
Only flag items that actually apply based on user inputs:
- Meals > 1% of revenue
- Vehicle business-use > 80% without logbook note
- Home office % > 35%
- Life insurance claimed
- Contractors paid > $500 with no T4A planned

#### Deductions You May Be Missing
Only suggest items the user left blank that are relevant to their situation:
- No PHSP → "PHSP premiums are fully deductible for CCPC owners and convert personal health costs into a corporate deduction."
- No equipment CCA → "If you bought computers or equipment this year, CCA applies."
- No home office → "If you work from home at all, the rent-to-corp structure can generate a meaningful deduction."
- Tech business with no SR&ED → "Run /sred-screen — you may qualify for refundable R&D credits."

#### Documentation Checklist
List only what applies to claimed deductions: lease + invoices + floor plan (home office), logbook (vehicle), receipts + attendees (meals), itinerary + purpose (travel), contracts + T4A (contractors), purchase receipts (CCA), plan enrolment (PHSP).

---

> ⚠️ General guidance based on CRA rules. Exact deductibility depends on documentation and specific facts. Have a CPA review before filing — especially home office, vehicle, and mixed-use items.
