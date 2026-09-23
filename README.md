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

    ### 1. 🖥️ Executive Dashboard View:
![Dashboard Overview](Screenshot%202026-09-23%20223554.png)

### 2. 📝 Measures & Fields Architecture:
![Measures List](Screenshot%202026-09-23%20223922.png)

### 3. 📅 Date Table Structure (`Dim_Date`):
![Dim Date Table](Screenshot%202026-09-23%20223908.png)

### 4. 🔄 Power Query ETL - Renamed Columns:
![ETL Renamed Columns](Screenshot%202026-09-23%20223811.png)

### 5. 🧹 Power Query ETL - Filtered Rows:
![ETL Filtered Rows](Screenshot%202026-09-23%20223758.png)

### 6. 🔤 Power Query ETL - Replaced Values:
![ETL Replaced Values](Screenshot%202026-09-23%20223744.png)

### 7. 🔀 Power Query ETL - Split Column:
![ETL Split Column](Screenshot%202026-09-23%20223720.png)

### 8. 📈 Power Query ETL - Unpivoted Other Columns:
![ETL Unpivot](Screenshot%202026-09-23%20223708.png)

### 9. 🏷️ Power Query ETL - Promoted Headers:
![ETL Promoted Headers](Screenshot%202026-09-23%20223655.png)

### 10. 📂 Raw CSV Source Preview:
![Raw Source Data](Screenshot%202026-09-23%20223638.png)
