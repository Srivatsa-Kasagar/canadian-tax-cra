# 🍁 Canadian Tax & CRA Compliance — Claude Code Plugin

> A plain-language CRA compliance assistant for Canadian small business owners.
> No tax background required.

![Version](https://img.shields.io/badge/version-0.5.0-dc2626?style=flat-square)
![Rates](https://img.shields.io/badge/rates-2026%20CRA-0f172a?style=flat-square)
![Coverage](https://img.shields.io/badge/coverage-all%20provinces%20%26%20territories-1e3a5f?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-slate?style=flat-square)

---

Running a Canadian business means juggling GST/HST filings, payroll remittances, T2 corporate returns, and a calendar full of CRA deadlines — often without a tax team behind you. This plugin brings all of that into Claude Code as six slash commands and four auto-activating skills, so you can get accurate, plain-English guidance without leaving your editor.

Everything runs locally. No API keys, no external connections, no data leaves your machine.

---

## What's Included

| | |
|---|---|
| **8 slash commands** | On-demand calculations and checklists |
| **4 knowledge skills** | Auto-load when relevant topics come up |
| **Interactive calculator** | Browser-based GST/HST + payroll tool |
| **2026 CRA rates** | CPP, EI, federal + all provincial tax brackets |
| **All 13 jurisdictions** | Federal obligations across every province and territory |

---

## Commands

Type any of these directly in Claude Code:

| Command | What it does |
|---|---|
| `/gst-filing` | Calculate net GST/HST owing, ITC breakdown, Quick Method comparison, and a filing summary ready to submit |
| `/payroll-calc` | Calculate CPP, EI, and income tax deductions — plus employer costs, net pay, and your CRA remittance amount |
| `/cra-deadlines` | Generate a personalized 12-month CRA deadline calendar based on your business type, fiscal year-end, and filing frequency |
| `/sred-screen` | Screen a project for SR&ED tax credit eligibility and get a Green / Yellow / Red rating with reasoning |
| `/grant-finder` | Find applicable federal and provincial grant programs ranked by potential value for your situation |
| `/t2-checklist` | Generate a T2 corporate tax preparation checklist tailored to your province, fiscal year-end, and income type |
| `/salary-vs-dividend` | Compare salary vs dividends from your CCPC — after-tax income, RRSP room, CPP impact, and optimal mix recommendation |
| `/expense-optimizer` | Identify every CRA-allowable deduction, calculate write-off amounts, flag audit risks, and surface missed deductions including home office and vehicle |

### Example Prompts

```
/gst-filing Q2 2026 — Ontario business. Sales: $85,000 consulting + $15,000 product sales.
Expenses: rent $5,000, software $2,000, meals $1,200, professional fees $3,000.
```

```
/payroll-calc Ontario, bi-weekly, $3,500 gross, basic personal TD1 only
```

```
/cra-deadlines Ontario corporation, December 31 year-end, quarterly GST, 3 employees
```

```
/sred-screen We spent 8 months building a machine learning model to predict equipment
failures. Existing models didn't work on our sensor data so we had to develop a
custom architecture.
```

```
/grant-finder Ontario SaaS startup, 8 employees, $1.2M revenue, looking to fund
developer hiring and AI R&D work
```

```
/t2-checklist Ontario corporation, March 31 fiscal year-end, active business income,
purchased $40K in equipment, paid $50K dividend to sole shareholder
```

```
/salary-vs-dividend Ontario CCPC, $300K corporate net income, want to take out $120K
personally, RRSP priority high, under 65
```

---

## Skills (Auto-Activating)

These load automatically when you mention relevant topics — no command needed. Just ask naturally.

| Skill | Kicks in when you ask about |
|---|---|
| **GST/HST Compliance** | HST, GST, input tax credits, Quick Method, $30K threshold, zero-rated or exempt supplies |
| **Payroll & Remittances** | CPP, EI, T4s, ROEs, remittance deadlines, employee vs. contractor classification |
| **Corporate Tax (T2)** | T2 returns, CCPC status, small business deduction, CCA, dividends, tax instalments |
| **SR&ED & Grants** | SR&ED credits, IRAP, T661, innovation grants, government funding programs |

---

## Installation

**Step 1 — Clone the repo (one time)**

```bash
git clone https://github.com/Srivatsa-Kasagar/canadian-tax-cra.git
```

**Step 2 — Add a shell alias (one time, recommended)**

The `--plugin-dir` flag must be passed every session. An alias makes this automatic:

```bash
# zsh (macOS default)
echo "alias claude-tax='claude --plugin-dir ~/canadian-tax-cra/plugin'" >> ~/.zshrc && source ~/.zshrc

# bash
echo "alias claude-tax='claude --plugin-dir ~/canadian-tax-cra/plugin'" >> ~/.bashrc && source ~/.bashrc
```

**Step 3 — Launch**

```bash
claude-tax
```

All eight commands and four skills are immediately available. Prefer not to use an alias? Pass the flag manually each session: `claude --plugin-dir ./canadian-tax-cra/plugin`.

---

## Interactive Calculator

Open `canadian-tax-calculator.html` in any browser for a standalone tool that works alongside the plugin:

- **GST/HST tab** — add revenue and expense lines, toggle Quick Method, see net tax owing or refund
- **Payroll tab** — calculate CPP, EI, and provincial income tax deductions for any province with 2026 rates
- **Deadlines tab** — generate a visual CRA deadline calendar by fiscal year-end month

No server required — open the file directly from your filesystem.

---

## Keeping Rates Current

CRA updates rates on a predictable schedule. Here's what to refresh and when:

| What changes | Typically when | Where to update |
|---|---|---|
| CPP contribution rates & maximums | November | `skills/payroll-remittances/SKILL.md`, `/payroll-calc` command |
| EI premium rates & maximums | November | `skills/payroll-remittances/SKILL.md`, `/payroll-calc` command |
| Federal personal tax brackets | February (budget) | `skills/payroll-remittances/SKILL.md`, `/payroll-calc` command |
| SR&ED expenditure limits & rates | February (budget) | `skills/sred-grants/SKILL.md`, `/sred-screen` command |
| Grant program availability | Ongoing | `skills/sred-grants/SKILL.md`, `/grant-finder` command |

---

## Disclaimer

This plugin provides general CRA compliance information for **educational purposes only**. It is not tax advice or legal advice. Canadian tax rules are complex, change annually, and vary significantly based on your specific circumstances. Always have a CPA or qualified tax professional review your filings and any material decisions before acting on them.

---

<div align="center">

**v0.5.0** &nbsp;·&nbsp; 2026 CRA Rates &nbsp;·&nbsp; All Provinces & Territories &nbsp;·&nbsp; By [Srivatsa Kasagar](https://github.com/Srivatsa-Kasagar)

</div>
