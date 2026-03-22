---
description: Generate a personalized 12-month CRA deadline calendar
argument-hint: "[business type, province, fiscal year-end, GST frequency, employees yes/no]"
---

The user wants a personalized CRA deadline calendar.
Their input (if any) is: $ARGUMENTS

## Step 1 — Collect inputs via AskUserQuestion

Check what is already in $ARGUMENTS. Collect all missing inputs in a single AskUserQuestion call — maximum 4 questions per call.

**First call — business structure (if not provided):**

Question 1: "What type of business entity are you?"
Header: "Business type"
Options:
- Corporation (T2 filer)
- Sole proprietor or partnership (T1 filer)

Question 2: "How often do you file GST/HST returns?"
Header: "GST filing"
Options:
- Quarterly (most common for small businesses)
- Monthly
- Annual
- Not registered for GST/HST

Question 3: "Do you have employees on payroll?"
Header: "Employees"
Options:
- Yes — I run payroll and remit CPP/EI
- No employees

Question 4: "What is your fiscal year-end month?"
Header: "Year-end"
Options:
- December 31 (calendar year)
- March 31
- June 30
- Other — I'll type it in

Wait for answers. Then if business type is corporation and province not yet known, ask:
"Which province is the corporation incorporated or primarily operating in?"
Options: Ontario / British Columbia / Alberta / Quebec

Once all inputs collected, proceed.

## Step 2 — Build the deadline calendar

Generate all applicable deadlines for the current calendar year (2026 unless otherwise specified).
List every deadline chronologically.

**GST/HST deadlines:**

Quarterly (calendar year):
- Q1: April 30
- Q2: July 31
- Q3: October 31
- Q4: January 31 of following year

Monthly: Last day of each following month (list all 12)

Annual: 3 months after fiscal year-end

**Corporate tax deadlines (corporations only):**

T2 balance owing:
- 2 months after fiscal year-end (most corporations)
- 3 months after fiscal year-end (eligible CCPCs — note this distinction)

T2 return filing: 6 months after fiscal year-end

Corporate instalments (if prior-year tax > $3,000):
- Quarterly: March 15, June 15, September 15, December 15
- Monthly: 15th of each month (higher-revenue corporations)

**Personal tax deadlines (sole proprietors only):**

- April 30: Personal income tax balance owing
- June 15: T1 return filing deadline (self-employed)
- Instalments (if prior-year tax > $3,000): March 15, June 15, September 15, December 15

**Payroll deadlines (if has employees):**

- 15th of each following month: Payroll remittance (regular remitters — list all 12 dates)
- February 28 (or 29 in a leap year) of the year following the calendar year: T4 slips issued to employees AND filed with CRA. For 2026 payroll, the deadline is February 28, 2027.
- Ongoing: ROE within 5 days of any interruption of earnings

**SR&ED deadline:**

- 18 months after fiscal year-end: T661 SR&ED claim filing deadline

## Step 3 — Output

---
### Your CRA Deadline Calendar — 2026
**Business:** [type] | **Year-End:** [month] | **Province:** [prov]
**GST/HST:** [frequency] | **Employees:** [yes/no]

#### All Deadlines — Chronological

| Date | Obligation | Type | Action |
|---|---|---|---|
| [date] | [description] | [GST / Payroll / T2 / T1 / SR&ED] | [what to do] |
| ... | | | |

#### ⚠️ Three Highest-Risk Deadlines

List the 3 deadlines carrying the biggest penalty risk for this business profile. For each:
- Date and obligation
- Penalty if missed (specific amount or formula)
- One-line tip to avoid missing it

#### Setup Checklist (one-time)
- [ ] Register for CRA My Business Account at canada.ca/en/revenue-agency
- [ ] Enable email notifications for CRA correspondence
- [ ] Add all deadlines to your calendar with a 2-week advance reminder
- [ ] Confirm your GST remitter type and payroll remitter type in My Business Account

---

> ⚠️ When a deadline falls on a weekend or statutory holiday, it extends to the next business day. This calendar covers federal CRA obligations — provincial tax deadlines (e.g. Ontario corporate minimum tax, BC PST) may differ. Always verify in CRA My Business Account.
