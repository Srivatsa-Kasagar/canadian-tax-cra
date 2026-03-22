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

*Last updated: March 2026*
