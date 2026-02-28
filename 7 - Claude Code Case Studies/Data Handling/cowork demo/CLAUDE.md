# Project Context — Customer & Transaction Performance

## Overview
This project analyses customer and transaction data for an Indian retail business across 10 cities.
The primary deliverable is an executive-ready PowerPoint slide summarising business performance.

---

## Files

| File | Description |
|------|-------------|
| `Customer_Data_Start.xlsx` | Source data — two sheets: `Customer` (1,000 rows) and `TXN` (3,000 rows) |
| `Executive_Performance_Overview.pptx` | Output slide — single executive slide built from the source data |

### Data Schema

**Sheet: Customer** (columns A–G, 1,000 customers)
- `Customer_ID`, `Customer_Name`, `Customer_Email`, `Customer_Number`, `Age`, `Gender`, `Location`
- Cities: Mumbai, Chennai, Pune, Ahmedabad, Delhi, Jaipur, Hyderabad, Bangalore, Kolkata, Surat

**Sheet: TXN** (columns A–K, 3,000 transactions)
- `Transaction_ID`, `Date_of_Purchase`, `Customer_ID`, `Product_Category`, `Product_Name`
- `Units`, `Price`, `Discounts`, `Returned`, `Mode_of_Payment`, `Purchase_Channel`
- Date range: March 2021 – 2023 (2023 is a partial year)
- Revenue formula: `(Units × Price) − Discounts`

---

## Key Metrics (as of last analysis)

| Metric | Value |
|--------|-------|
| Total Revenue | ₹21.2L (₹21,17,112) |
| Total Customers | 1,000 |
| Total Transactions | 3,000 |
| Avg. Order Value | ₹706 |
| Total Discounts Given | ₹1,93,909 |
| Return Rate | **50.3%** ⚠ (needs attention) |

### Revenue by Category (₹ Thousands)
| Category | Revenue |
|----------|---------|
| Toys | 376 |
| Automotive | 373 |
| Electronics | 350 |
| Home | 350 |
| Fashion | 347 |
| Books | 322 |

### Revenue by Sales Channel
| Channel | Revenue | Share |
|---------|---------|-------|
| In-Store | ₹10.94L | 52% |
| Online | ₹10.23L | 48% |

### Year-on-Year Revenue (₹ Thousands)
| Year | Revenue | Notes |
|------|---------|-------|
| 2021 | 823 | Full year |
| 2022 | 1,062 | Full year (+29% YoY) |
| 2023 | 233 | Partial year |

### Payment Methods (transaction count)
- Credit Card: 616 | UPI: 608 | Debit Card: 595 | Net Banking: 599 | Cash: 582

### Top 5 Products by Revenue
1. Motor Oil — ₹91,261
2. Action Figure — ₹88,190
3. Laptop — ₹86,059
4. Board Game — ₹81,613
5. Bed Sheets — ₹81,317

---

## Executive Slide Design

**File:** `Executive_Performance_Overview.pptx`
**Tool used:** PptxGenJS (Node.js), built via `/sessions/relaxed-peaceful-gates/slide_work/build_slide.js`
**Layout:** Single 16:9 slide (10" × 5.625")

**Design choices:**
- Dark navy theme (`0B1B4D` background, `060E2E` header/footer bar)
- Accent colour: `38BDF8` (sky blue)
- Warning accent: `FCA5A5` (coral/red) for the return rate card
- Font: Calibri throughout
- 4 KPI cards in a row (top section)
- Left panel: Horizontal bar chart — Revenue by Category
- Right panel: Doughnut chart (channel split) + Column chart (YoY revenue)
- Footer: data source attribution + partial-year disclaimer

**To regenerate the slide:**
```bash
cd /sessions/relaxed-peaceful-gates/slide_work
node build_slide.js
```

---

## Key Insight for Executives
The **50.3% return rate** is the single most important flag in this dataset — roughly 1 in 2 transactions is returned, which severely impacts net revenue and operational costs. This should be the primary action item for leadership.
