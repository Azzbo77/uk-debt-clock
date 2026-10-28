adme · MD
# 🇬🇧 UK Debt Clock
 
A live, browser-based debt clock for the United Kingdom — inspired by the US Debt Clock — displaying real-time estimates of the national debt and key public finance figures, updated every second directly in your browser.
 
No server required. No frameworks. Just a single HTML file.
 
---
 
## What It Shows
 
The clock uses published figures from the Office for National Statistics (ONS), the Office for Budget Responsibility (OBR), NHS England, and the House of Commons Library. It shows live estimates, not real-time government accounts.
 
### National Debt
The headline figure uses the latest ONS public sector net debt observation available from the API. As of 28 October 2026, the latest observation was **£3,005.0 billion at the end of September 2026**. The fallback is that same observation. The separate **£3,662 per second** rate annualizes the OBR March 2026 forecast of £115.5 billion borrowing for 2026-27; actual borrowing is uneven and should be checked against monthly ONS outturns.
 
### Government Finances
Pro-rated estimates against 2026-27 annual forecasts (the UK public-sector financial year starts 1 April) for:
- Annual borrowing forecast
- Total managed expenditure (~£1,421bn, OBR March 2026 forecast)
- Current receipts (~£1,304bn, OBR March 2026 forecast)
- Net debt interest (~£111bn, OBR March 2026 forecast)
- Welfare spending (£352.8bn, OBR March 2026 forecast)
- Pensioner spending (£169.2bn, OBR March 2026 forecast)
- NHS England Group and NHS providers revenue limit (£215.352bn, 2026-27 financial directions)
### Per Citizen & Per Taxpayer
Breakdowns of debt and annual borrowing per person and per taxpayer. The population base is ONS mid-2025 and the taxpayer divisor is HMRC's 2026-27 projection of 40.8 million income taxpayers; per-taxpayer figures are illustrative.
 
### Economy
Running GDP estimate for the fiscal year, plus nominal GDP per second, based on the OBR March 2026 2026-27 forecast of £3.164 trillion.
 
---
 
## Colour Coding
 
Figures are colour coded to give an at-a-glance sense of their nature:
 
| Colour | Meaning |
|--------|---------|
| 🔴 Red | Negative for the public finances — debt, deficit, interest payments, overspending |
| 🟡 Amber | Significant but neutral — welfare, NHS, population figures |
| 🟢 Green | Positive — government receipts and economic output |
 
---
 
## How Live Is It?
 
| What | How fresh |
|------|-----------|
| Debt base figure and debt-to-GDP ratio | ONS BKQK and HF6X series fetched on page load and hourly; September 2026 values are fallbacks |
| Borrowing rate (£3,662/sec) | OBR March 2026 2026-27 forecast, annualized; update after the October 2026 EFO |
| Spending, receipts, interest, welfare, and pensioner spending | OBR March 2026 2026-27 forecasts; update after the October 2026 EFO |
| NHS revenue limit | 2026-27 NHS England financial directions |
| Counter motion | Live in your browser — extrapolated in real time from the above figures |
 
The debt counter ticks in your browser. Finance cards are pro-rated shares of annual forecast totals, not actual year-to-date outturn. If the ONS API is unavailable, the page uses the September 2026 fallback or a more recent valid cached figure.
 
---
 
## Data Sources
 
| Figure | Source |
|--------|--------|
| National debt base figure | [ONS series BKQK](https://www.ons.gov.uk/economy/governmentpublicsectorandtaxes/publicsectorfinance/timeseries/bkqk), latest available observation |
| Debt-to-GDP ratio (94.0% in September 2026) | [ONS series HF6X](https://www.ons.gov.uk/economy/governmentpublicsectorandtaxes/publicsectorfinance/timeseries/hf6x), latest available observation |
| 2026-27 borrowing forecast (£115.5bn) | [OBR Economic and Fiscal Outlook, March 2026](https://obr.uk/efo/economic-and-fiscal-outlook-march-2026/) |
| Total managed expenditure, receipts, interest, welfare, and pensioner spending | OBR March 2026 forecast tables; annual cash amounts rounded where shown |
| NHS England Group and NHS providers revenue limit (£215.352bn) | [2026-27 NHS England financial directions](https://www.gov.uk/government/publications/2026-to-2027-financial-directions-to-nhs-england/2026-to-2027-financial-directions-to-nhs-england) |
| Defence outturn (£62.0bn) | Ministry of Defence 2025-26 actual, as summarized by the [House of Commons Library](https://commonslibrary.parliament.uk/research-briefings/cbp-8175/) |
| Real GDP growth in 2025 (+1.2%) | [ONS GDP quarterly national accounts, April to June 2026](https://www.ons.gov.uk/economy/grossdomesticproductgdp/bulletins/quarterlynationalaccounts/apriltojune2026) |
| UK population (69,483,900) | [ONS mid-2025 estimate](https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/bulletins/annualmidyearpopulationestimates/mid2025) |
| Taxpayer denominator (40.8m) | [HMRC Income Tax Liabilities Statistics, July 2026](https://www.gov.uk/government/statistics/income-tax-liabilities-statistics-tax-year-2023-to-2024-to-tax-year-2026-to-2027/bulletin-commentary) |
 
All figures are approximate and based on the most recently published data at the time of writing. The clock is for **illustrative purposes** and should not be used for financial or academic research without cross-referencing the primary sources above.
 
---
 
## How It Works
 
Everything runs in the browser using vanilla JavaScript. On page load, the script:
 
1. Fetches the latest public sector net debt figure from the ONS API (series BKQK) and uses it as the base
2. Falls back to hardcoded figures if the API is unavailable
3. Calculates how many seconds have elapsed since the start of the current public-sector financial year (1 April)
4. Pro-rates the annual OBR forecast totals across the year; these are not actual ONS year-to-date outturns
5. Updates the displayed figures every second (hero debt counter updates every 100ms for a smooth ticker effect)
There are no third-party dependencies beyond two Google Fonts. No cookies, no tracking.
 
---
 
## Maintaining the Data
 
The ONS debt base figure updates automatically on page load and hourly. Forecast assumptions are controlled by constants near the top of the `<script>` section in `index.html` and require a manual update when new OBR forecasts are published. At this refresh, the October 2026 forecast was not yet present in the OBR publication archive.
 
### Maintenance Calendar
 
Put these three dates in your calendar each year:
 
| Date | Event | Action required |
|------|-------|----------------|
| **March** | OBR Spring Forecast | Minor revisions — check and update forecasts if materially changed |
| **October / November** | Autumn Budget | Main update of the year — update all spending and deficit constants |
| **1st April** | UK public-sector financial year rollover | Roll `FISCAL_YEAR_START` forward one year |
 
In practice the **Autumn Budget** is the most important update. The Spring Forecast often only makes minor revisions and may not need any changes.
 
### What to Update and Where to Find the New Figures
 
All constants are at the top of the `<script>` block in `index.html`. Open the file, search for `FALLBACK constants` and you will find them grouped together.
 
| Constant | What it is | Where to find the new figure |
|----------|-----------|------------------------------|
| `FISCAL_YEAR_START` | Start date of the current UK public-sector financial year | Always `new Date('YYYY-04-01T00:00:00Z')` — just increment the year each April |
| `FALLBACK_DEBT` | Debt base figure used if the ONS API is unavailable | [ONS BKQK series](https://www.ons.gov.uk/economy/governmentpublicsectorandtaxes/publicsectorfinance/timeseries/bkqk) — latest monthly figure in £m × 1,000,000 |
| `DEBT_PER_SEC` | Annualized borrowing forecast per second | OBR annual borrowing forecast ÷ seconds in the fiscal year |
| `SPENDING_ANNUAL` | Total managed expenditure | OBR forecast tables |
| `TAX_ANNUAL` | Current receipts | OBR forecast tables |
| `INTEREST_ANNUAL` | Net debt interest | OBR forecast tables |
| `WELFARE_ANNUAL` | Welfare spending | OBR forecast tables |
| `PENSION_ANNUAL` | Pensioner spending, not State Pension alone | OBR forecast tables |
| `NHS_ANNUAL` | NHS England Group and providers revenue limit | DHSC financial directions |
| `GDP_ANNUAL` | Nominal GDP forecast | OBR forecast tables |
 
### Worked Example — Calculating DEBT_PER_SEC
 
After each Budget, the OBR publishes a new borrowing forecast. To convert it to an annualized per-second rate:
 
```
New borrowing forecast (e.g. £120 billion) ÷ 31,536,000 seconds in a year = £3,806 per second
```
 
So in `index.html` you would update:
```javascript
const DEBT_PER_SEC = 3806;  // £120bn borrowing forecast ÷ 31,536,000 sec
```
 
Update the displayed rate and annual forecast together. Prefer deriving the rate from the annual forecast rather than maintaining duplicate strings.
### Don't Forget the Ticker and Display Labels
 
After updating the constants, also update these hardcoded display strings in the HTML (search for the old figures):
 
| Location | What to update |
|----------|---------------|
| Hero section | Borrowing forecast and annualized per-second estimate |
| Speed bar | The per-second rate displayed |
| Deficit card | The `▲ £X,XXX/sec` badge |
| Ticker tape | Borrowing forecast and annualized debt growth entries |
| Freshness panel | The "Extrapolated at £X,XXX/sec" note |
| README | This file — update figures to match |
 
---
 
## Licence
 
Free to use, share, and modify. If you build on it, a credit back to this repo would be appreciated.
 
---
 
*Data last reviewed: 28 October 2026. OBR figures use the March 2026 forecast because the October forecast was not yet published at review time.*
