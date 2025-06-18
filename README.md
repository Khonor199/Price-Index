# Price-Index
 The report shows a comparison of the purchase price of an article with the minimum price of competitors in accordance with the sales region.
 
# 📊 Price Monitoring Dashboard: Market vs Procurement Prices

## 🧾 Task Description

This query compares **internal marketplace prices** with **external market prices** parsed from third-party websites.

The goal is to:
- Identify price discrepancies between the internal system and external sources.
- Detect anomalies ("outliers") where internal prices are significantly higher or lower than market ones.
- Provide actionable insights for procurement optimization.

---

## 🛠️ Technical Implementation

- **Main Data Sources:**
  - `order_service.order_item`: internal order data with actual prices paid
  - `price_parsing`: scraped prices from external sites
  - Dictionary tables (`pim_catalog_model_dict`, `client_service_business_entities_dict`, etc.)

- **Key Features Used:**
  - Common Table Expressions (`WITH`)
  - Date filtering using `today()`
  - `ROW_NUMBER()` to select the lowest price per model/region
  - `dictGet()` for dictionary-based lookups
  - Conditional classification (`CASE WHEN`) for business rules
  - Parameterized filters (for BI integration)

---

## 📌 Key Metrics

| Metric | Description |
|-------|-------------|
| `unit_price` | Internal procurement price per unit (without VAT) |
| `least` | Lowest parsed price from external sources (without VAT) |
| `diff_percent` | Percentage difference between internal and external prices |
| `GMV` | Gross Merchandise Value (quantity × unit price) |
| `Comment` | Classification of price comparison result |
| `Выброс` | Flag indicating if the price difference is an anomaly |

---

## 🔍 Business Insights

This query helps answer the following questions:

- Where are we paying more than the market price?
- Are there categories or clients with significant pricing issues?
- Which regions show the biggest discrepancies?
- Can we optimize procurement based on current market rates?

---

## 🖥️ Sample Output

![image](https://github.com/user-attachments/assets/9a760f20-76bf-4f2e-9942-81474bc27375)


![image](https://github.com/user-attachments/assets/abefc22c-13db-4a3b-bf4c-334c3b5adb89)
