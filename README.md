# SQL_in_Action

-- <<<<<<<<<<<<<<<<<<<<<< PROBLEM 11 >>>>>>>>>>>>>>>>>>>>>>>
-- <<<<<<<<<<<<<<<<<<<<<<< WRAP UP >>>>>>>>>>>>>>>>>>>>>>>>>
-- What do you think makes a successful AirBnB rental in this market? What factors seem to be at play the most?
-- Write a few sentences and include them with your project submission in the README file 

Based on reviews_per_month, for the top 10, 8 out of 10 are in manhattan, top two in Manhattan.  With regards to room type, 4 of top 5 are private rooms. There also seems to be a correlation with minimum required nights where top three are 1, 1, 2 respectively. Looking at the group as whole, the average price of top 10 is 109.5  If KPI for success is volume or reviews_per_month then driving factors are location, price and minimum night requirements.

SELECT id, neighbourhood_group, price, reviews_per_month, minimum_nights FROM intro_sql.final_airbnb order by reviews_per_month DESC limit 10;

Based on average revenue per month (reviews_per_month * price), for the top 10, 5 out Brooklyn and 5 out of Manhattan, top two out of Brooklyn.  9 out of ten are entire homes.  Top rentals 3 are  minimum 1 night rentals.  avg price is 297.3.   If KPI for success is average revenue per month, the driving factors could be rental type and minimum night requirements.

SELECT id, neighbourhood_group, room_type, minimum_nights, reviews_per_month, price, (reviews_per_month * price) AS avg_rev_month FROM intro_sql.final_airbnb order by avg_rev_month DESC limit 10;


Looking at comparisons within the neighborhoods the driving factors for highest volume is price.  In most cases, the highest volume listing was below the average price listings for that neighborhood.

*note* haven't quite figured this code out but believe it will take creating new tables for each neighborhood to do comparisons against the group


-- <<<<<<<<<<<<<<<<<<<<< ** BONUS ** >>>>>>>>>>>>>>>>>>>>>>>
-- Find the the percent above or below each listing is compared to the average price for all listings.

SELECT id, ((price / (SELECT avg(price) FROM intro_sql.final_airbnb)) - 1)* 100 as percent_above_below_avg FROM intro_sql.final_airbnb;


-- HINT: No hints! It's a bonus for a reason :)
