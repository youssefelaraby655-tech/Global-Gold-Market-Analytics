# 🪙 Global Gold Market & Historical Analytics (1979 - 2021) 📈

An executive-level Business Intelligence dashboard built using **Power BI**, designed to analyze historical gold prices across multiple global currencies and countries spanning over 40 years. 🌟

---

## 📊 Project Overview
This project provides deep insights into gold price trends, market volatility, and currency fluctuations from 1979 to 2021. It transforms complex multi-currency financial datasets into interactive, actionable visual stories tailored for stakeholders and financial analysts. 💼

---

## 🚀 Key Features & UI/UX Design
* 🎨 **Executive Dark Theme UI:** Designed with a professional dark background and gold accents to reduce eye strain and highlight financial data.
* 🏷️ **Dynamic Title & Summary Cards:** Custom DAX measures that adapt dynamically based on user selections (Global overview vs. Country-specific drill-downs).
* 🌐 **Multi-Country & Multi-Currency Support:** Implemented robust ETL pipelines in Power Query (Unpivoting wide datasets) to seamlessly handle international price comparisons.
* 📐 **Advanced Financial Metrics:** 
  * 📉 Gold Price Volatility & Percentage %
  * 📊 Min/Max Annual Price tracking
  * 🔄 Dynamic Year-over-Year (YoY) analysis

---

## 🛠️ Data Modeling & ETL Process (Power Query)
1. 📂 **Source Data:** Historical monthly gold prices (1979–2021).
2. 🔄 **Unpivoting:** Transformed wide-format country columns into a clean, normalized relational structure (`Country`, `Currency`, `Price`).
3. 📅 **Date Table (`Dim_Date`):** Created a dedicated calendar table for advanced time-intelligence calculations and yearly/monthly aggregations[cite: 10].

---

## 📈 DAX Measures Implemented

```dax
AVG Price = AVERAGE('Gold Prices'[Price])

Max price = CALCULATE(MAX('Gold Prices'[Price]), ALLEXCEPT('Gold Prices', 'Gold Prices'[Year], 'Gold Prices'[Country]))

Min price = CALCULATE(MIN('Gold Prices'[Price]), ALLEXCEPT('Gold Prices', 'Gold Prices'[Year], 'Gold Prices'[Country]))

Gold Price Volatility = STDEV.S('Gold Prices'[Price])

Volatility Percentage % = DIVIDE([Gold Price Volatility], [AVG Price], 0)

Selected Country Summary = 
VAR CurrentCountry = SELECTEDVALUE('Gold Prices'[Country], "Global Market")
RETURN
    IF(
        ISFILTERED('Gold Prices'[Country]),
        "Gold Prices & Historical Analytics for: " & CurrentCountry,
        "Global Gold Market Overview & Historical Performance (1979 - 2000)"
    )
