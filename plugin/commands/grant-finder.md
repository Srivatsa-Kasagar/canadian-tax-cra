---
description: Find applicable federal and provincial grants for your business
argument-hint: "[sector, province, company size, what you want to fund]"
---

The user wants to find applicable government grants and funding programs.
Their input (if any) is: $ARGUMENTS

## Step 1 — Collect inputs via AskUserQuestion

Check what is already in $ARGUMENTS. Collect all missing inputs in a single AskUserQuestion call.

**First call — business profile:**

Question 1: "What province is your business based in?"
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
- Other province or territory — I'll type it in

Question 2: "What sector best describes your business?"
Header: "Sector"
Options:
- Technology / software / SaaS
- Manufacturing or hardware
- Professional services (consulting, legal, accounting, etc.)
- Retail, food, or consumer goods

Question 3: "What do you primarily want to fund? (List all that apply, separated by commas)"
Header: "Funding goal"
Options:
- Hiring new employees
- R&D or technical innovation
- Employee training and upskilling
- Digital tools or technology adoption
- Exporting to new markets

Question 4: "What is your company's approximate annual revenue?"
Header: "Revenue"
Options:
- Under $500K (startup / early stage)
- $500K – $2M (growing small business)
- $2M – $10M (established SME)
- Over $10M

Wait for answers. Then ask in plain text:
"Does your business have any special ownership characteristics? (e.g. women-owned, Indigenous-owned, founder under 40, recent immigrant, or none of these — just type your answer)"

Once all inputs are collected, proceed to matching.

## Step 2 — Match programs

Using the sred-grants skill, identify all programs that match the profile.

**Always evaluate first:**
- **SR&ED** — if R&D/technical innovation is in scope, this is almost always the highest-value program. Flag it prominently.
- **IRAP** — for companies doing R&D with growth ambitions. Check if they have or could get an NRC advisor.
- **Canada Job Grant** — if hiring or training is in the funding goal.
- **Digital adoption** — CDAP was wound down in 2024. If digital tools adoption is in scope, note this and suggest checking canada.ca/ISED for any current successor programs or provincial equivalents (e.g. Ontario's Digital Main Street for retail/service businesses).

**Province-specific programs to consider:**
- Ontario: Ontario Made Manufacturing Investment Tax Credit, OCE SmartStart, Invest Ottawa, Ontario Business Improvement Area grants
- BC: Innovate BC, BC Tech Fund, CleanBC Industry Fund, BCIC New Ventures
- Alberta: Alberta Innovates, Emissions Reduction Alberta, AITF
- Quebec: Investissement Québec, PROMPT, CRIAQ (aerospace), CRSNG industrial partnerships
- Manitoba: Manitoba SEED, Manitoba Technology Accelerator, MITT training grants
- Saskatchewan: Saskatchewan Technology Startup Incentive (STSI), Innovation Saskatchewan
- Nova Scotia: Innovacorp, NSBI, Nova Scotia Business Fund
- Other provinces/territories: Check regional development agencies (ACOA for Atlantic Canada, WD for Western Canada, FedNor for Northern Ontario, PacifiCan for BC)

**Ownership-based programs (check user's answer):**
- Women Entrepreneurship Strategy (WES Ecosystem Fund) — women-owned/led
- Indigenous Business Development — NACCA, BDC Indigenous, FNBO
- Futurpreneur — founders aged 18–39
- Black Entrepreneurship Program — Black-owned businesses

**Export programs (if export is a funding goal):**
- CanExport SMEs — up to $50K, 50% cost-share for export market development
- EDC Export Expansion — various

## Step 3 — Rank and format

Rank programs by: estimated value × likelihood of eligibility × ease of application.

For each program present:
- Name and funder
- What it funds (1 sentence)
- Typical amount range
- Key eligibility criteria (2–3 bullet points)
- Application type: rolling / competitive / annual intake
- Estimated effort: Low / Medium / High
- One specific insight for this user's profile

## Step 4 — Output

---
### Government Grant & Funding Finder
**Business:** [sector, province] | **Revenue:** [range] | **Funding goal:** [goals]

#### Recommended Programs (ranked by value)

[For each matching program:]
**[Rank]. [Program Name]** — [Funder]
- **Funds:** [what it covers]
- **Amount:** [range]
- **Eligibility:** [key criteria]
- **Apply:** [rolling/competitive] | [program URL or where to find it]
- **Effort:** [Low/Medium/High]
- 💡 **For you:** [one specific insight based on their profile]

---

#### SR&ED — Your Likely Highest-Value Program
Always include this section if any R&D is in scope:
> SR&ED is non-competitive — you don't apply, you just file with your T2 return. A CCPC gets 35% of eligible R&D expenditures back as a **cash refund**, even with no taxes owing. Run `/sred-screen [project description]` to check if your work qualifies.

#### Realistic Expectations
- Most grants are competitive — typical approval rates 20–50%
- Application to funding: 3–9 months on average
- Most programs reimburse costs, not advance them — budget for upfront spend
- Hiring a grant writer improves success rates for competitive programs by 15–30%
- SR&ED is the most reliable: non-competitive, self-assessed, and stackable with most grants

#### Quick Wins
Highlight 1–2 programs the user can act on immediately with low effort.

---

> ⚠️ Grant program availability, intake dates, and eligibility criteria change frequently. Verify current program status directly with the administering organization before investing time in an application. This list reflects programs available as of early 2026.
