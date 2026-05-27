# 🇬🇧 UK Debt Clock
 
A live, browser-based debt clock for the United Kingdom — inspired by the US Debt Clock — displaying real-time estimates of the national debt and key public finance figures, updated every second directly in your browser.
 
No server required. No frameworks. Just a single HTML file.
 
---
 
## What It Shows
 
The clock pulls from published figures by the Office for National Statistics (ONS), the Office for Budget Responsibility (OBR), and the House of Commons Library, and extrapolates them in real time based on known rates of change.
 
### National Debt
The headline figure shows the UK's public sector net debt, currently around **£2.9 trillion**, rising at approximately **£4,186 every second** — derived from the 2025-26 annual deficit of ~£133 billion.
 
### Government Finances
Year-to-date running totals (from the start of the UK fiscal year, 6th April) for:
- Annual deficit
- Total government spending (~£1,368bn planned for 2025-26)
- Tax receipts (~£1,235bn expected for 2025-26)
- Debt interest payments (~£110bn — the third largest item of public expenditure)
- Welfare and social protection spending (~£333bn)
- NHS England budget (~£196bn)
### Per Citizen & Per Taxpayer
Breakdowns of the debt and annual borrowing on a per-person and per-taxpayer basis, based on ONS population figures and HMRC taxpayer data (~34 million taxpayers in 2024/25).
 
### Economy
Running GDP estimate for the fiscal year, plus GDP per second, based on a nominal UK GDP of approximately £3.1 trillion.
 
---
 
## Colour Coding
 
Figures are colour coded to give an at-a-glance sense of their nature:
 
| Colour | Meaning |
|--------|---------|
| 🔴 Red | Negative for the public finances — debt, deficit, interest payments, overspending |
| 🟡 Amber | Significant but neutral — welfare, NHS, population figures |
| 🟢 Green | Positive — tax receipts, GDP and economic output |
 
---
 
## Data Sources
 
| Figure | Source |
|--------|--------|
| National debt (£2,911bn at end of March 2026) | [House of Commons Library](https://commonslibrary.parliament.uk/research-briefings/cbp-10842/) |
| Debt growth rate (£4,186/sec) | Derived from OBR £133bn deficit forecast ÷ seconds in a year |
| Total spending & receipts | [OBR Brief Guide to Public Finances](https://obr.uk/forecasts-in-depth/brief-guides-and-explainers/public-finances/) |
| Welfare spending (£333bn) | OBR Annually Managed Expenditure forecast 2025-26 |
| NHS budget (£196bn) | [NHS England Financial Performance](https://www.england.nhs.uk/) |
| UK GDP (~£3.1tn nominal) | [ONS GDP Estimates](https://www.ons.gov.uk/economy/grossdomesticproductgdp) |
| Population (67.6m) | ONS mid-2024 estimate |
| Taxpayers (~34m) | HMRC 2024/25 |
 
All figures are approximate and based on the most recently published data at the time of writing. The clock is for **illustrative purposes** — it does not connect to a live data feed and should not be used for financial or academic research without cross-referencing the primary sources above.
 
---
 
## How It Works
 
Everything runs in the browser using vanilla JavaScript. On page load, the script:
 
1. Calculates how many seconds have elapsed since the start of the current UK fiscal year (6th April)
2. Multiplies that by the known per-second rates of change
3. Updates the displayed figures every second (hero debt counter updates every 100ms for a smooth ticker effect)
There are no external API calls, no cookies, no tracking, and no dependencies beyond two Google Fonts.
 
---
 
## Licence
 
Free to use, share, and modify. If you build on it, a credit back to this repo would be appreciated.
 
---
 
