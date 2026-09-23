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
![Dashboard Overview](<img width="1365" height="718" alt="Screenshot 2026-09-23 223638" src="https://github.com/user-attachments/assets/6124a740-ea06-423a-bf94-86d7adf11c9a" />)


### 2. 📝 Measures & Fields Architecture:
![Measures List](<img width="1365" height="720" alt="Screenshot 2026-09-23 223655" src="https://github.com/user-attachments/assets/490f7e8c-2474-4031-bfaa-76097355b365" />)


### 3. 📅 Date Table Structure (`Dim_Date`):
![Dim Date Table](<img width="1365" height="723" alt="Screenshot 2026-09-23 223708" src="https://github.com/user-attachments/assets/1a43dacc-8984-4c70-bb29-bcf1093e7e25" />)


### 4. 🔄 Power Query ETL - Renamed Columns:
![ETL Renamed Columns](<img width="1365" height="719" alt="Screenshot 2026-09-23 223720" src="https://github.com/user-attachments/assets/93dade96-faf7-4f0e-b75f-2ce39132852f" />)


### 5. 🧹 Power Query ETL - Filtered Rows:
![ETL Filtered Rows](<img width="1365" height="721" alt="Screenshot 2026-09-23 223744" src="https://github.com/user-attachments/assets/b9d2485e-fbfe-46e3-8b2f-08657d31298b" />)


### 6. 🔤 Power Query ETL - Replaced Values:
![ETL Replaced Values](<img width="1365" height="718" alt="Screenshot 2026-09-23 223758" src="https://github.com/user-attachments/assets/c8e67469-4242-440d-88de-abc1cdc23025" />)


### 7. 🔀 Power Query ETL - Split Column:
![ETL Split Column](<img width="1365" height="719" alt="Screenshot 2026-09-23 223811" src="https://github.com/user-attachments/assets/081882f8-def3-458c-a3e4-45c9b2102c14" />)


### 8. 📈 Power Query ETL - Unpivoted Other Columns:
![ETL Unpivot]<img width="251" height="313" alt="Screenshot 2026-09-23 223908" src="https://github.com/user-attachments/assets/5baf5346-25f2-4142-a3ee-71a653b78a2d" />)



### 8. 📈 Power Query ETL - Unpivoted Other Columns:
![ETL Unpivot]<img width="254" height="375" alt="Screenshot 2026-09-23 223922" src="https://github.com/user-attachments/assets/5c061106-4ec3-4198-a43e-04b5b202b1ca" />)



### 8. 📈 Power Query ETL - Unpivoted Other Columns:
![ETL Unpivot](<img width="893" height="464" alt="Screenshot 2026-09-23 223554" src="https://github.com/user-attachments/assets/9b47fad0-170f-4d02-bfd3-6d81ad35ddbc" />)


### 9. 🏷️ Power Query ETL - Promoted Headers:
![ETL Promoted Headers](Screenshot%202026-09-23%20223655.png)

### 10. 📂 Raw CSV Source Preview:
![Raw Source Data](Screenshot%202026-09-23%20223638.png)
