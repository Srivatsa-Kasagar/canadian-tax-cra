# Connectors

This plugin does not require any external service connections. It is fully self-contained.

## Optional Future Connectors

| Connector | Use Case | Status |
|---|---|---|
| CRA My Business Account (OAuth) | Pre-fill filing periods, outstanding balances, remitter type | Not yet available via API/MCP |
| QuickBooks Online | Pull actuals for GST filing and payroll calc from accounting data | Future enhancement |
| Xero | Sync ledger data for GST/HST and payroll calculations | Future enhancement |
| Payworks / ADP | Sync payroll records for T4 generation and reconciliation | Future enhancement |
| Service Canada ROE Web | Submit Records of Employment electronically | Future enhancement |

## Notes

- CRA does not currently offer a public OAuth API for third-party integrations. All CRA interactions must be done manually through My Business Account at canada.ca/en/revenue-agency.
- QuickBooks and Xero both offer API access. A connector could export transaction data and pass it to `/gst-filing` and `/payroll-calc` automatically.
- Until connectors are built, users should export their data as CSV or copy figures manually into the plugin commands or the HTML calculator.
