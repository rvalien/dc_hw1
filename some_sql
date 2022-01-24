select * from yellow_taxi_data
limit 10

select * from zones
where "Zone" = 'Central Park'
limit 10

select tip_amount, tpep_pickup_datetime::date from yellow_taxi_data
limit 10

--Question 3: Count records *
--How many taxi trips were there on January 15?
select count(*) from yellow_taxi_data where tpep_pickup_datetime::date = '2021-01-15'
select '2010-01-01 12:00:00'::timestamp::date

-- Question 4: Largest tip for each day *
-- On which day it was the largest tip in January? (note: it's not a typo, it's "tip", not "trip")
--2021-01-20 2021-01-04 2021-01-01 2021-01-21 
select max(tip_amount) as max_tip, tpep_pickup_datetime::date as day from yellow_taxi_data
where tpep_pickup_datetime::date in ('2021-01-01', '2021-01-04','2021-01-20',  '2021-01-21')
group by tpep_pickup_datetime::date
order by max(tip_amount) desc

--Question 5: Most popular destination *
--What was the most popular destination for passengers picked up in central park on January 14?
--Enter the zone name (not id). If the zone name is unknown (missing), write "Unknown"
select 
count(y."DOLocationID") as c, y."DOLocationID", z."Zone"
from yellow_taxi_data y
INNER JOIN zones z ON y."DOLocationID" = z."LocationID"
where tpep_pickup_datetime::date = '2021-01-14'
and "PULocationID" = (select "LocationID" from zones where "Zone" = 'Central Park')
group by "DOLocationID", "Zone"
order by count("DOLocationID") desc
limit 3

--Question 6: Most expensive route *
--What's the pickup-dropoff pair with the largest average price for a ride (calculated based on total_amount)?
--Enter two zone names separated by a slash For example:"Jamaica Bay / Clinton East"
--If any of the zone names are unknown (missing), write "Unknown". For example, "Unknown / Clinton East".

select y."PULocationID", y."DOLocationID", avg(total_amount) as att from yellow_taxi_data y
group by(y."PULocationID", y."DOLocationID") 
order by att desc
limit 1

select * from zones
where "LocationID" in (4, 265)
