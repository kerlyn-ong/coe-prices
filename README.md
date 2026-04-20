# coe-prices
A project showing the trend of how COE prices change over the years. \
COE is introduced to implement an allocation mechanism for Singapore's vehicle quota to achieve zero-vehicle growth policy in order to manage traffic congestion in land-scarce country. \
COE prices fluctuate depending on prevailing demand and supply. In past year, as demand was strong, prices have increased. \
Aim to allow buyers to decide when they should bid for a car

# who are the users?
* High-Intent Strategic Car Buyers

# tables description
* dim_vehicle:
* dim_date: standard date table
* fact_coe_prices: premiums -- highest unsuccessful bid price plus $1


# possible metrics
For users who want to renew their COE, they can look into metric PQP
* Prevailing Quota Premium (PQP) (10 years) = Moving Avg of COE Price Premium in the last 3 months
* Prevailing Quota Premium (PQP) (5 years) = Moving Avg of COE Price Premium in the last 3 months

Executive Summary (KPIs - Top Row)
* Latest Premium - Current 'Spot' Price
* Current PQP - Renewal Price
* Market Heat Index - Subscription Rate

Main Trend (Middle)
* Price Gap Chart - Dual axis PQP (area), Premium Bids (circle)

Bidding Round Comparison (Buy in Bid 1 or 2)
* Bidding Prices in Round 1 vs Round 2 in a month

Success Probability Heatmap (Right Side)
* Heatmap (Months on x-axis, Bidding Round on Y-axis) - Subscription Rate for colour scale

Additional 
KPI - Quota Change %
Supply vs Price Scatter Plot - Proving zero growth policy impact


# Possible headers
* COE Bidding Optimizer: When to Strike?

Start with Global Parameters
KPIs
Middle
Bottom
