# Canadian Tax & CRA Compliance Plugin

A plain-language CRA compliance assistant for Canadian small business owners. Covers GST/HST filing, payroll deductions, corporate income tax (T2), and SR&ED/government grants — no tax background required.

---

## Commands

| Command | What it does |
|---|---|
| `/gst-filing` | Calculate net GST/HST owing, ITC breakdown, Quick Method comparison, and filing summary |
| `/payroll-calc` | Calculate CPP, EI, income tax deductions, employer costs, net pay, and CRA remittance |
| `/cra-deadlines` | Generate a personalized 12-month CRA deadline calendar |
| `/sred-screen` | Screen a project for SR&ED tax credit eligibility (Green / Yellow / Red rating) |
| `/grant-finder` | Find applicable federal and provincial grant programs ranked by value |
| `/t2-checklist` | Generate a T2 corporate tax preparation checklist tailored to your corporation |

### Example Usage

```
/gst-filing Q2 2026 — Ontario business. Sales: $85,000 consulting + $15,000 product sales.
Expenses: rent $5,000, software $2,000, meals $1,200, professional fees $3,000.

/payroll-calc Ontario, bi-weekly, $3,500 gross, basic personal TD1 only

/cra-deadlines Ontario corporation, December 31 year-end, quarterly GST, 3 employees

/sred-screen We spent 8 months building a machine learning model to predict
equipment failures. Existing models didn't work on our sensor data so we
had to develop a custom architecture.

/grant-finder Ontario SaaS startup, 8 employees, $1.2M revenue, looking to
fund developer hiring and AI R&D work

/t2-checklist Ontario corporation, March 31 fiscal year-end, active business income,
purchased $40K in equipment, paid $50K dividend to sole shareholder
```

---

## Skills (Auto-Activating Knowledge)

These skills load automatically when you discuss relevant topics — no commands needed.

| Skill | Activates when you ask about |
|---|---|
| **GST/HST Compliance** | HST, GST, input tax credits, sales tax, Quick Method, $30K threshold, zero-rated, exempt |
| **Payroll & Remittances** | CPP, EI, T4, ROE, remittance deadlines, employee vs contractor, payroll setup |
| **Corporate Tax (T2)** | T2, corporate tax, CCPC, small business deduction, CCA, dividends, instalments |
| **SR&ED & Grants** | SR&ED, R&D credits, IRAP, CDAP, T661, innovation grants, government funding |

---

## Setup

No API connections or environment variables required. Fully self-contained.

**Recommended:** Open the included `canadian-tax-calculator.html` in any browser for an interactive GST/HST and payroll calculator that works alongside this plugin.

---

## Annual Maintenance

CRA updates rates each year. Update the following each November/February:

| What changes | When | Affected components |
|---|---|---|
| CPP rates & maximums | November | payroll-remittances skill, /payroll-calc |
| EI rates & maximums | November | payroll-remittances skill, /payroll-calc |
| Federal tax brackets | February (budget) | payroll-remittances skill, /payroll-calc |
| SR&ED rates / limits | February (budget) | sred-grants skill, /sred-screen |
| Grant program availability | Ongoing | sred-grants skill, /grant-finder |

---

## Important Disclaimer

This plugin provides general tax and CRA compliance information for educational purposes only. It is **not tax or legal advice**. Canadian tax rules are complex, change annually, and depend on your specific circumstances. Always have a CPA or tax professional review filings and material decisions.

---

**Version:** 0.3.0
**Author:** Srivatsa Kasagar
**Covers:** Federal obligations across all provinces and territories
