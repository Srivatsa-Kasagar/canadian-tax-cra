# Product Hunt Launch — Canadian Tax & CRA Plugin

---

## Listing Copy

**Name**
Canadian Tax & CRA Compliance Plugin

**Tagline** *(60 chars max)*
```
CRA compliance for Canadian small businesses — in Claude
```

**Short Description** *(260 chars max)*
```
A free Claude Code plugin with 7 slash commands covering GST/HST filing,
payroll deductions, T2 corporate tax, SR&ED credits, grant finding, and
salary vs dividend optimization. Interactive browser calculator included.
Built for Canadian small business owners. 2026 CRA rates.
```

**Topics / Tags**
- Developer Tools
- Finance
- Productivity
- Small Business
- Artificial Intelligence

---

## Full Description

Running a Canadian business means keeping up with GST/HST filings, payroll remittances, T2 returns, SR&ED claims, and a never-ending calendar of CRA deadlines — often without a dedicated tax team.

**Canadian Tax & CRA Compliance** is a free Claude Code plugin that puts all of this into your editor as seven slash commands and four auto-activating knowledge skills.

**What it does:**

- `/gst-filing` — Calculate net GST/HST owing, ITC breakdown, Quick Method comparison, and a filing summary
- `/payroll-calc` — CPP, EI, and income tax deductions with 2026 rates for all provinces
- `/cra-deadlines` — A personalized 12-month CRA deadline calendar for your business type
- `/sred-screen` — Screen a project for SR&ED eligibility with a Green/Yellow/Red rating
- `/grant-finder` — Find federal and provincial grant programs ranked by value
- `/t2-checklist` — A T2 preparation checklist tailored to your corporation
- `/salary-vs-dividend` — Find the optimal salary + dividend mix from your CCPC with side-by-side after-tax comparison

**Also included:** A standalone browser-based calculator with four tabs — GST/HST, payroll deductions, CRA deadlines, and the salary vs dividend optimizer. Open the HTML file in any browser, no server required.

Everything runs locally. No API keys, no external connections.

---

## Maker's First Comment

Hey PH! 👋

I built this after watching Canadian founder friends spend hours manually looking up CPP rates, GST filing rules, and SR&ED eligibility every quarter. The information is all out there — but it's scattered across CRA guides, T4032 tables, and provincial legislation. Getting a plain-language answer to "should I pay myself salary or dividends this year?" shouldn't require a 2-hour research session.

This plugin brings 2026 CRA rates, all 13 provinces and territories, and plain-English explanations directly into Claude Code. The `/salary-vs-dividend` optimizer is the piece I'm most excited about — it's the #1 question Canadian CCPC owners ask their accountants every year and the answer is rarely obvious.

It's completely free, fully self-contained, and open source. I'd love to hear what other CRA compliance pain points you'd want to see covered — drop them in the comments!

---

## Gallery — Screenshots to Capture

Capture these five screenshots before launch:

| # | What to show | File name suggestion |
|---|---|---|
| 1 | Landing page (index.html) hero — dark nav + stat cards | `01-landing-hero.png` |
| 2 | `/salary-vs-dividend` tab in calculator with Ontario $300K results | `02-salary-vs-dividend.png` |
| 3 | `/gst-filing` command output in Claude — filing summary with ITC breakdown | `03-gst-filing-output.png` |
| 4 | `/payroll-calc` command output — deductions table with employer cost | `04-payroll-calc-output.png` |
| 5 | CRA Deadlines tab showing the deadline grid | `05-cra-deadlines-grid.png` |

**Thumbnail:** Use the landing page hero (`01-landing-hero.png`) — dark background reads well as a small card on PH.

---

## Launch Day Checklist

**Before launch:**
- [ ] Push all code to GitHub (`git push -u origin main`)
- [ ] Enable GitHub Pages (repo Settings → Pages → main branch / root)
- [ ] Verify `index.html` loads correctly on the GitHub Pages URL
- [ ] Verify `canadian-tax-calculator.html` opens in Chrome/Safari without errors — especially the new Salary vs Dividend tab
- [ ] Take all 5 screenshots
- [ ] Create Product Hunt account if not already set up
- [ ] Schedule launch for Tuesday or Wednesday, 12:01 AM PST (highest traffic window)

**At launch:**
- [ ] Submit listing with all 5 gallery images
- [ ] Post maker's first comment within the first hour
- [ ] Share on LinkedIn with a short demo description
- [ ] Post in r/PersonalFinanceCanada and r/canadasmallbusiness (check self-promotion rules — frame as a free resource, not a launch announcement)
- [ ] Share in any Slack/Discord communities for Canadian founders or indie hackers you're in

**First 48 hours:**
- [ ] Reply to every comment on Product Hunt
- [ ] Note any feature requests — add them to FUTURE-PLAN.md
- [ ] Update README star count goal once you have a baseline

---

*Last updated: March 2026*
