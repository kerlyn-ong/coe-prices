# coe-prices
A project showing the trend of how COE prices change over the years.
COE is introduced to implement an allocation mechanism for Singapore's vehicle quota to achieve zero-vehicle growth policy in order to manage traffic congestion in land-scarce country.
COE prices fluctuate depending on prevailing demand and supply. In past year, as demand was strong, prices have increased.

# who are the users?
Interested Car Buyers
Car Buyers who want to renew COE

# tables description
dim_vehicle:
dim_date: standard date table
fact_coe_prices: premiums -- highest unsuccessful bid price plus $1


# possible metrics
For users who want to renew their COE, they can look into metric PQP
Prevailing Quota Premium (PQP) (10 years) = Moving Avg of COE Price Premium in the last 3 months
Prevailing Quota Premium (PQP) (5 years) = Moving Avg of COE Price Premium in the last 3 months
