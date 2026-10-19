# Predictive COE Prices Dashboard

### Problem Statement
Singapore's COE bidding market is characterized by high volatility and psychological bidding. Buyers lack a consolidated tool to tell them if they should enter the market now or wait. Hence, I developed an end-to-end analytics solution to assist high-intent car buyers in navigating the volatile Singapore Certificate of Entitlement (COE) Market. This dashboard provides real-time market checks and recommendations whether to 'Buy/Wait'.

### Key Insights and Recommendation (as of April 2026)
#### Executive Recommendation: **WAIT**
Analysis of historical COE bidding cycles up to April 2026 shows an overheated, demand-driven market environment across all vehicle categories. The dashboard triggers a unified "WAIT" signal, advising buyers to **defer entry and wait** until premium valuations normalise against fair-value benchmarks. Across all categories, premiums are currently above their respective 3-Mth Prevailing Quota Price (~1-7%).

#### Category Highlights: Category A overheating
* Elevated Premiums: Category A shows the sharpest premium markup ($118,000), **~7% above** the 3-Mth Prevailing Quota Price ($110,072 average).
* Low Success Odds: A high Market Heat of **2.11** (>2 buyers competing for every 1 COE certificate) lowers bidders' success rates down to a **red 47%** in Bidding Round 1 for April.
* Increasing Demand: From the Premium against Quota Scatter Plot, there is high demand which drives the latest round for Category A (Low Supply = 1,265 / High Premium = 118,000) to be positioned in **extreme top left quadrant**. Although quota change is **+0.08%**, the quota supply remains fairly flat, further indicates that price spike is purely driven by buyer demand rather than supply constraints.

#### Strategic Entry Triggers for Buyers
To transition from **WAIT** to **BUY** signal, categories must satisfy two quantitative thresholds:
* **Primary Trigger - Premiums Normalisation**: Latest Premiums drop below the 3-Mth Prevailing Quota Price where vehicles become cheaper than baseline.
* **Secondary Indicator - Competition Heat Cooling**: Market Heat is at baseline levels (**< 1.5**) where there are fewer competing buyers per certificate.

### Dashboard
[Tableau Link - COE Prices Dashboard](https://public.tableau.com/app/profile/kerlyn.ong/viz/COE_Prices/COEPricesDashboard)

The dashboard - filtered by Category, tells the audience to wait until an opportunity rises to buy mainly due to:
* Volatility Chart: Premium being higher than current Prevailing Quota Price

Other visuals are meant to be supporting and help drive buyers decisions
* Market Heat: Index > 1.5 means high competition
* Quote Change: A negative quota change means that there is high competition where supply is shrinking which will potentially push prices up
* Success Probability: The red cells means that competition is high and a high percentage means its easy to win the bid
* Bidding Round Comparison: Informs buyer which bidding rounds are premiums low and when to bid
* Scatter Plot: Good to enter market when the latest dot is in the bottom-right quadrant of the scatter plot when there is high supply and low price

<img width="1035" height="785" alt="image" src="https://github.com/user-attachments/assets/8af2d0b5-e420-4c3a-b29e-85fa76fa5cee" />

### Data Architecture and Tech Stack
Visualization: Tableau\
Data Processing: SQL/Python (Pandas) via [Google Colab](https://github.com/kerlyn-ong/coe-prices/blob/6b49e9d40b6c96bd68dbd53334c60c234db09d4b/DataGovSG_COE_Dataset.ipynb)\
Data Modelling: Built a Star Schema from .xlsx file comprising of the 3 tables below
* dim_date: Date table
* dim_vehicle: Shows the different vehicle category type and description
* fact_coe_prices: Is a fact table that contains bidding rounds, premiums, quota data

### Core Features and Metrics
* Decision Signal: A sub-header that interprets price variance as 'Buy/Wait' signal. Price Variance is calculated by comparing Latest Premium against Prevailing Quota Premium of 3 months. If variance is negative, it represents below Fair Value and an opportunity to 'Buy', and vice versa.
* Market Heat: A demand-to-supply ratio calculation to identify and assess compeition of how many bids are available for every 1 available certificate.
* Success Probability Logic: Calculated as Bids Success/Bids Received. This identifies the 'ease of entry' for a buyer.

### Assumptions & Methodology
* Calculation in one Vehicle Category does not affect the calculation of other categories within the same bidding window
* Calculations are based on historical performance of Bidding Round 1 vs Round 2
* Trends are shown based on previous 8 months

### Key Technical Challenges
* Syncing Vehicle Category across different sheets: Added boolean filter on every sheet to ensure final dashboard will be able to filter based on different categories
* Showing latest data: Make use of different formulaes to ensure that latest date data is able to show for the KPIs.

<details>
<summary><h3> Click to Expand: Appendix </h3></summary>

# Appendix
Key Metrics Formulaes:
* Prevailing Quota Premium =  Moving Average of Premium over previous 3 months
* Market Heat = Bids Received / Bids Success
* Quota Change = (Current Quota - Previous Quota) / Previous Quota
* Success Probability = Bids Success / Bids Received
* Savings = Premium - Prevailing Quota Price

Basic Wireframe ([Figma Link](https://www.figma.com/design/wJvKpR8RvR9MFtLRxBFuPF/coe-prices?node-id=0-1&t=G4Z0hixaZENnKIfd-1))

<img width="1059" height="751" alt="image" src="https://github.com/user-attachments/assets/691c8a87-0d49-45e4-8b7c-8a2c58fbc0f4" />

</details>
