# 📈 Investor Behavior & Psychology Dashboard (2020-2025)

> A comprehensive behavioral analysis of investors, exploring the relationships between demographics, risk appetite, and the choice of financial instruments.

<img width="1322" height="741" alt="image" src="https://github.com/user-attachments/assets/b65a677c-900f-475f-a267-793337b81fca" />


## 🎯 Business Case
Most financial reports focus on **how much** capital flows into the market. This project answers the question: **why** it flows there. The goal of this dashboard is to provide financial institutions and advisors with insights into investor psychology, enabling better product profiling and optimization of marketing strategies.

## 📊 Key Insights
Based on the data analysis, the following behavioral patterns were identified:
1. **Risk Premium (Greed vs. Safety):** Heatmap analysis proves that investors declaring a high risk appetite expect extremely high returns in exchange (around 30-40%). However, the majority of the market prefers safe returns at the 10-20% level.
2. **Motivations & Fixed Deposits:** The primary and undisputed reason for locking cash in safe assets is the desire for "Fixed Returns," which outclasses other reasons such as capital protection.
3. **Age vs. Investment Horizon:** The project debunks the myth of the "impatient Gen Z" – young investors are just as likely as older ones to opt for long-term capital building.

---

## 🏗️ Dashboard Architecture

The report was designed for maximum readability (UI/UX) and divided into 3 logical sections:

### 1. Executive Summary (Overview)
The main control panel utilizing the *Glassmorphism* trend and a *Neon Glow* effect. It includes:
* Investor demographics (Gender, Age).
* Ranking of the most popular instruments (Avenues).
* Daily portfolio checking index (Market stress).

### 2. Risk Analysis (Risk vs. Expected Returns)
An analytical section proving correlations.
* **Heatmap:** Verifying the relationship between declared risk and financial expectations.
* **Gauge Charts:** Showing the degree of market "overheating" and stock market participation.

### 3. Psychological Drivers (Goals & Reasons)
* A detailed breakdown of the reasons why investors choose the stock market (Equity) as opposed to safe havens (Fixed Deposits).

<img width="1320" height="738" alt="image" src="https://github.com/user-attachments/assets/038c565f-d3f1-4844-b50c-4beb4955753f" />


## 🛠️ Technologies & Skills Used
* **Power Query (M):** Data cleaning, type transformation, automatic Unpivot of instrument rating columns.
* **Data Modeling:** Building a relational Star Schema model (Facts and Dimensions).
* **DAX (Data Analysis Expressions):** Advanced analytical measures. Sample code from the project:
  ```dax
  % Fixed Deposits = 
  VAR FdUsers = CALCULATE(COUNTROWS('Dim_investor'), 'Dim_investor'[Avenue] = "Fixed Deposits")
  VAR TotalUsers = COUNTROWS('Dim_investor')
  RETURN DIVIDE(FdUsers, TotalUsers, 0)



