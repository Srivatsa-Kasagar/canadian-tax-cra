---
description: Screen a project for SR&ED tax credit eligibility
argument-hint: "[describe the technical project or work performed]"
---

The user wants to screen a project for SR&ED eligibility.
Their input (if any) is: $ARGUMENTS

## Step 1 — Collect inputs via AskUserQuestion

If the user has not described the project in enough detail, use AskUserQuestion to gather context. Collect all missing inputs in a single call.

**If no project description provided at all, ask:**

Question 1: "What type of technical work are you trying to claim SR&ED for?"
Header: "Work type"
Options:
- Software / AI / machine learning development
- Hardware or product engineering
- Process or manufacturing improvement
- Biotech, chemistry, or life sciences

Question 2: "How would you describe the core technical challenge?"
Header: "Challenge"
Options:
- We tried to solve something and existing approaches didn't work
- We built something entirely new with no known solution
- We improved an existing process but hit unexpected technical barriers
- We're not sure — I'll describe it in more detail

Question 3: "Roughly how much did the work cost? (Helps estimate the ITC value)"
Header: "Expenditures"
Options:
- Under $50,000
- $50,000 – $200,000
- $200,000 – $500,000
- Over $500,000

Question 4: "Is your business a Canadian-Controlled Private Corporation (CCPC)?"
Header: "Business type"
Options:
- Yes — Canadian private company, majority Canadian-owned (35% refundable ITC applies)
- No — public company or foreign-controlled (15% non-refundable ITC)
- Not sure

Wait for answers. Then ask in plain text:
"In 2–5 sentences, describe what technical problem you were trying to solve, why it was uncertain, and what you tried or tested."

Once you have the project description, proceed to the eligibility assessment.

## Step 2 — Apply the three-part test

Assess each criterion from the sred-grants skill explicitly and separately.

**Criterion 1 — Technological Uncertainty**
Was there genuine uncertainty that existing publicly available knowledge could not resolve?
- Did the challenge go beyond what a skilled practitioner could solve using known methods?
- Was it unclear HOW to achieve the result — not just whether the business goal would work?
- Did the uncertainty exist before the work began?

Rate: ✅ Clear / ⚠️ Weak / ❌ Not present. State why.

**Criterion 2 — Technological Advancement**
Did the work generate new knowledge in science or technology?
- Was it more than applying known techniques in a new business context?
- Would a knowledgeable peer in the field consider this an advancement?

Rate: ✅ Clear / ⚠️ Weak / ❌ Not present. State why.

**Criterion 3 — Systematic Investigation**
Was the work conducted through hypothesis, testing, observation, and conclusions?
- Were hypotheses explicitly formulated and tested?
- Were results documented as they happened?

Rate: ✅ Clear / ⚠️ Weak / ❌ Not present. State why.

## Step 3 — Overall rating

🟢 **GREEN** — All three criteria clearly met. Recommend filing T661.
🟡 **YELLOW** — One or more criteria is weak or ambiguous. Partial claim possible. Needs SR&ED consultant review.
🔴 **RED** — Work appears to be routine development, commercial deployment, or application of known technology. Does not qualify.

## Step 4 — Output

---
### SR&ED Eligibility Screen

**Project:** [brief description from user]
**Business type:** [CCPC / non-CCPC]
**Estimated expenditures:** [range]

#### Three-Part Test

| Criterion | Result | Reasoning |
|---|---|---|
| Technological Uncertainty | ✅ / ⚠️ / ❌ | [specific observation based on project description] |
| Technological Advancement | ✅ / ⚠️ / ❌ | [specific observation] |
| Systematic Investigation | ✅ / ⚠️ / ❌ | [specific observation] |

**Overall Rating: 🟢 GREEN / 🟡 YELLOW / 🔴 RED**

**Summary:** [2–3 plain-language sentences explaining the rating in terms of the user's actual project]

#### Questions CRA Would Ask
List 4–5 specific questions a CRA technical reviewer would ask about this project, based on the description. Helps the user prepare documentation.

#### Documentation Gaps
Flag what documentation should exist but was not mentioned:
- [ ] [specific gap, e.g., "Test logs showing failed iterations and what was learned"]
- [ ] [specific gap]

#### Estimated ITC Value (GREEN or YELLOW only)
Based on the expenditure range provided:
- Estimated eligible expenditures (salaries + 80% contractors + 55% overhead proxy)
- ITC at 35% (if CCPC): ~$X refundable
- ITC at 15% (if non-CCPC): ~$X non-refundable

Add: "A SR&ED consultant can optimize eligible expenditure identification and typically works on a success-fee basis."

#### Recommended Next Steps
- 🟢 GREEN: Engage a SR&ED consultant or CPA. Organize documentation now. File T661 with T2 return.
- 🟡 YELLOW: Book a call with a SR&ED specialist to identify the qualifying subset. Do not file without expert review.
- 🔴 RED: SR&ED does not apply to this work. Run `/grant-finder` to find alternative programs (IRAP, CDAP, etc.).

---

> ⚠️ This is a preliminary assessment only. SR&ED eligibility is determined by CRA reviewers based on a detailed technical and financial review. CRA audits approximately 30% of SR&ED claims. Always engage a qualified SR&ED consultant or tax advisor before filing a claim.
