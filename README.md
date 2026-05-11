# Predictive COE Prices Dashboard

### Problem Statement
Singapore's COE bidding market is characterized by high volatility and psychological bidding. Buyers lack a consolidated tool to tell them if they should enter the market now or wait. Hence, I developed an end-to-end analytics solution to assist high-intent car buyers in navigating the volatile Singapore Certificate of Entitlement (COE) Market. This dashboard provides real-time market checks and recommendations whether to 'Buy/Wait'.

### Data Architecture and Tech Stack
Visualization: Tableau\
Data Processing: SQL/Python\
Data Modelling: Built a Star Schema from .xlsx file comprising of the 3 tables below
* dim_date: Date table
* dim_vehicle: Shows the different vehicle category type and description
* fact_coe_prices: Is a fact table that contains bidding rounds, premiums, quota data

### Core Features and Metrics
* Decision Signal: A sub-header that interprets price variance as 'Buy/Wait' signal. Price Variance is calculated by comparing Latest Premium against Prevailing Quota Premium of 3 months. If variance is negative, it represents an opportunity to 'Buy', and vice versa.
* Success Probability Logic: Calculated as Bids Success/Bids Received. This identifies the 'ease of entry' for a buyer.
* Market Heat: A demand-to-supply ratio calculation to identify and assess compeition of how many bids are available for every 1 available certificate.

### Assumptions & Methodology
* Calculation in one Vehicle Category does not affect the calculation of other categories within the same bidding window
* Calculations are based on historical performance of Bidding Round 1 vs Round 2
* Trends are shown based on previous 12 months

### Key Technical Challenges
* Syncing Vehicle Category across different sheets: Added boolean filter on every sheet to ensure final dashboard will be able to filter based on different categories
* Showing latest data: Make use of different formulaes to ensure that latest date data is able to show for the KPIs.

### Dashboard
[Tableau Link - COE Prices Dashboard](https://public.tableau.com/app/profile/kerlyn.ong/viz/COE_Prices/COEPricesDashboard)

The dashboard tells the audience to wait until an opportunity rises to buy mainly due to:
* Volatility Chart: Premium being higher than current Prevailing Quota Price

Other visuals are meant to be supporting and help drive buyers decisions
* Market Heat: Index > 1.5 means high competition
* Quote Change: A negative quota change means that there is high competition where supply is shrinking which will potentially push prices up
* Success Probability: The red cells means that competition is high and a high percentage means its easy to win the bid
* Bidding Round Comparison: Informs buyer which bidding rounds are premiums low and when to bid
* Scatter Plot: Good to enter market when the latest dot is in the bottom-right quadrant of the scatter plot when there is high supply and low price

<img width="1220" height="853" alt="image" src="https://github.com/user-attachments/assets/f292ab40-dc4e-40ae-b54a-8a0aa078682c" />


# Appendix
Key Metrics Formulaes:
* Prevailing Quota Price =  Moving Average of Premium over previous 3 months
* Market Heat = Bids Received / Bids Success
* Quota Change = (Current Quota - Previous Quota) / Previous Quota
* Success Probability = Bids Success / Bids Received
* Savings = Premium - Prevailing Quota Price

Basic Wireframe ([Figma Link](https://www.figma.com/design/wJvKpR8RvR9MFtLRxBFuPF/coe-prices?node-id=0-1&t=G4Z0hixaZENnKIfd-1))

<img width="1059" height="751" alt="image" src="https://github.com/user-attachments/assets/691c8a87-0d49-45e4-8b7c-8a2c58fbc0f4" />

