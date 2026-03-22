# Future Plan — Canadian Tax & CRA Compliance Plugin

---

## Enhancements

### High Priority — Build Next

| Enhancement | Why it matters |
|---|---|
| `/hst-reconciliation` | Reconcile GST/HST collected vs remitted across quarters — common pain point at year-end |
| `/t4-generator` | Generate T4 slip summaries from payroll inputs; currently `/payroll-calc` stops at deductions |
| `/holdco-checklist` | Holding company + opco structure is extremely common for Canadian owner-operators |
| `/salary-vs-dividend` | The #1 question every CCPC owner asks — optimal mix calculator with 2026 rates |
| Province depth | Most examples default to Ontario; add BC/AB/QC-specific nuances (QST, WSIB/WCB variants) |

### Medium Priority

- **CSV import for GST filing** — paste a QuickBooks/Wave export directly into `/gst-filing`
- **`/installment-calc`** — corporate tax instalment schedules (March/June/September/December) with no-penalty thresholds
- **Multi-year rate archive** — 2024/2025 brackets alongside 2026 for amended returns
- **`/roe-wizard`** — Record of Employment walkthrough (reason codes, insurable hours, Box 15C)

### Low Effort, High Polish

- Add a `CHANGELOG.md` to track annual rate updates
- Show "Last updated: Jan 2026" in the calculator UI so users know rates are current
- Add a copy-to-clipboard button on calculator results

---

## Marketing

### Where the Audience Already Is

- **Reddit** — post in r/PersonalFinanceCanada, r/canadasmallbusiness, r/canadaentrepreneur. Lead with a problem ("tired of Googling CPP rates every payroll run?") not a product pitch.
- **Claude.ai community / Anthropic forums** — early plugin ecosystem, low competition right now
- **LinkedIn** — target Canadian accountants, bookkeepers, and startup founders. A short demo video of `/payroll-calc` in action would perform well.
- **X / Twitter** — Canadian fintech and indie hacker circles (#buildinpublic, #canadatech)

### Content That Markets Itself

- Write a short post: *"I built a free Claude plugin that calculates GST/HST — here's how it works"* — dev.to or Medium, then cross-post
- Create a 60-second screen recording of the calculator being used — embed in the GitHub README as a GIF
- Submit to **Product Hunt** on a Tuesday/Wednesday — tag as "developer tools" + "finance"

### Credibility Builders

- Add a "Used by X businesses" stat once early users are onboarded (even 10 is credible at launch)
- Reach out to Canadian bookkeeping communities (CPA Canada member forums, local BNI chapters)
- Partner with a CPA to review and endorse — even a LinkedIn quote adds trust given the disclaimer

### SEO (GitHub Pages already indexed)

- Add an `og:image` social card to `index.html` for link previews when shared
- Blog post targeting "CRA GST/HST calculator 2026" or "Canadian payroll deductions calculator" — real search volume

---

## Top Two Picks to Start

1. **`/salary-vs-dividend` command** — highest utility, directly answers the most Googled question for CCPC owners
2. **Product Hunt launch** — best single channel for initial visibility

---

*Last updated: March 2026*
