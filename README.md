# E-Commerce Funnel Analysis & Conversion Optimization

An end-to-end data analytics project analyzing 120,000 e-commerce sessions to identify funnel bottlenecks, evaluate customer conversion behavior, and uncover actionable business insights.

The project combines Python, SQL Server, statistical hypothesis testing, and Power BI to transform raw session-level data into an analytical and decision-support solution.

---

## 📌 Project Overview

E-commerce businesses generate large amounts of customer interaction data, but raw session data does not directly explain where customers are lost or which acquisition strategies generate the most value.

This project analyzes an e-commerce conversion funnel:
**Website Visit → Product View → Add to Cart → Checkout → Purchase**

The objective is to answer key business questions:
- Where do customers drop out of the funnel?
- Which funnel stage represents the largest bottleneck?
- Does device type significantly affect conversion?
- Do acquisition channels perform differently?
- Do campaign types significantly influence conversion?
- Which channels generate the most revenue?
- How can the business prioritize conversion optimization opportunities?

---

## 📊 Dataset

The project uses a Direct-to-Consumer E-Commerce Funnel dataset containing:
- 120,000 sessions
- 17 attributes
- Customer/session information, Acquisition channel, Campaign type, Device type, User type, Region, Funnel stage indicators, Order value, and Revenue.

**[Link to Dataset]** *(استبدل هذا النص برابط الداتا الحقيقي)*

### Funnel Stages

| Stage | Description |
|---|---|
| Website Visit | User visited the website |
| Product View | User viewed a product |
| Add to Cart | User added a product to cart |
| Checkout | User started checkout |
| Purchase | User completed a purchase |

---

## 🛠️ Tech Stack

### Python
**Libraries:** Pandas, NumPy, Matplotlib, Seaborn, SciPy, Statsmodels
- **Used for:** Data cleaning, Exploratory Data Analysis, Funnel analysis, Segmentation, Statistical hypothesis testing, and Data visualization.

### SQL Server
- **Used for:** Data validation and Funnel calculations.
- **Techniques:** CTEs, CASE statements, CAST / data type conversion, Aggregations, GROUP BY, Window Functions (LAG), Unpivot-style transformations, and Conditional calculations.

### Power BI
- **Used for:** Interactive Dashboard creation and Business Intelligence reporting.

---

## 🔬 Analysis Methodology & Findings

### 1. Data Validation
Before performing the analysis, the dataset was validated to ensure that the funnel logic and revenue data were internally consistent.

**Validation Results:**
- Total sessions: 120,000
- Duplicate sessions: 0
- Invalid funnel sequences: 0
- Purchases: 8,181
- Rows with positive revenue: 8,181
- Purchases with zero revenue: 0
- Non-purchases with positive revenue: 0

*This confirmed that the dataset was structurally consistent and suitable for further analysis.*

### 2. Exploratory Data Analysis (EDA)
The initial EDA examined dataset structure, missing values, numerical/categorical distributions, revenue behavior, and channel/device/campaign performance. **The dataset contained no missing values and no duplicate sessions.**

### 3. Overall Funnel Analysis

| Funnel Stage | Users | Overall Conversion |
|---|---|---|
| Website Visit | 120,000 | 100.00% |
| Product View | 77,870 | 64.89% |
| Add to Cart | 27,156 | 22.63% |
| Checkout | 16,234 | 13.53% |
| Purchase | 8,181 | 6.82% |

**Stage-to-Stage Conversion**

| Transition | Conversion | Drop-off |
|---|---|---|
| Visit → Product View | 64.89% | 35.11% |
| Product View → Cart | 34.87% | **65.13%** |
| Cart → Checkout | 59.78% | 40.22% |
| Checkout → Purchase | 50.39% | **49.61%** |

**Key Funnel Finding:**
- The largest funnel bottleneck occurs at **Product View → Add to Cart** (65.13% drop-off).
- A second important bottleneck occurs at **Checkout → Purchase** (49.61% drop-off).

### 4. Device Analysis
- **Mobile:** 84,006 Sessions | 5,693 Purchases | 6.78% Conversion
- **Desktop:** 35,994 Sessions | 2,488 Purchases | 6.91% Conversion

**Statistical Test (Two-proportion Z-test):**
`p-value = 0.3939` (p > 0.05). There is insufficient statistical evidence that device type affects overall conversion.

### 5. Channel Analysis

| Channel | Revenue | Purchases | AOV |
|---|---|---|---|
| Paid Ads | $7,536,147.08 | 3,619 | $2,082.38 |
| Organic | $5,090,708.45 | 2,448 | $2,079.54 |
| Social | $2,578,443.31 | 1,230 | $2,096.30 |
| Email | $1,811,300.31 | 884 | $2,048.98 |

**Statistical Test (Chi-Square):** `p-value: 0.1375`. The observed differences between channels are not statistically strong enough to conclude that acquisition channel significantly affects purchase conversion.

### 6. Campaign Analysis

| Campaign | Sessions | Purchases | Conversion | Revenue | AOV |
|---|---|---|---|---|---|
| Discount | 60,121 | 4,107 | 6.83% | $8.53M | $2,076.11 |
| New Launch | 36,064 | 2,448 | 6.79% | $5.12M | $2,092.61 |
| Influencer | 23,815 | 1,626 | 6.83% | $3.37M | $2,070.92 |

**Statistical Test (Chi-Square):** `p-value: 0.96498` for overall conversion. Campaign type does not show a statistically significant effect on conversion.

---

## 🗄️ SQL Analytics Layer
SQL Server was used to transform the raw dataset into reusable analytical views for Power BI.
**Key views include:**
- `vw_overall_kpis`
- `vw_funnel_summary_advanced`
- `vw_funnel_segment`
- `vw_segment_performance`
- `vw_monthly_performance`
- `vw_funnel_segmentation`
- `vw_revenue_scenario_analysis`

---

## 📈 Power BI Dashboard
The final Power BI dashboard transforms the analytical results into an interactive decision-support interface allowing users to move from high-level business KPIs to detailed funnel and segment analysis.

![Power BI Dashboard Screenshot] *(استبدل هذا النص برابط أو مسار صورة الداشبورد)*

---

## 💡 Business Insights & Recommendations

### Insights
1. **Product Engagement is the Main Bottleneck:** Only 34.87% of product viewers add to cart.
2. **Checkout is the Second Major Leakage Point:** 50.39% of checkout starters fail to complete a purchase.
3. **Device Type Is Not a Significant Conversion Driver:** Optimization decisions should not be based solely on device-level conversion differences.
4. **Paid Ads Drive the Most Revenue:** Generated $7.54M, though conversion differences across channels are not statistically significant.
5. **Campaign Conversion Is Highly Consistent:** Hovering around 6.8% across all campaigns.

### Recommendations
1. **Priority 1 — Optimize Product Pages:** Improve product descriptions, imagery, pricing visibility, and stronger CTAs.
2. **Priority 2 — Reduce Checkout Abandonment:** Simplify checkout, reduce form fields, improve payment experience, and make shipping costs clearer.
3. **Priority 3 — Prioritize Revenue-Generating Channels:** Evaluate channels based on Revenue, AOV, and Acquisition Cost rather than traffic volume alone.
4. **Priority 4 — Use Experimentation:** Run A/B testing for product pages, CTA placement, and checkout flow to validate causal impacts.

---

## ⚠️ Project Limitations
- The analysis is observational and based on historical session-level data. Statistical association does not necessarily imply causation.
- The dataset lacks data on Customer Acquisition Cost (CAC), Marketing Spend, Error Logs, Payment Methods, and Customer Lifetime Value (CLV).

---

## 🔄 Final Conclusion
This project demonstrates an end-to-end analytics workflow:
`Python EDA` → `Funnel & Segmentation Analysis` → `Statistical Testing` → `SQL Server Analytics Layer` → `Power BI Dashboard` → `Actionable Business Recommendations`.

---

## 👨‍💻 Author
**Abdalrahman Mohamed Mahmoud**
Data Analyst | Python | SQL | Power BI

🔗 [LinkedIn](رابط_حسابك_هنا) | 🔗 [GitHub](رابط_حسابك_هنا)
