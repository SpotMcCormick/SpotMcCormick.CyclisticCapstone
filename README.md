# SpotMcCormick.CyclisticCapstone
Here is my capstone for the Coursera Data Analytics Course. 

When I recieve the data the first thing I had to do was examine it and clean it. The first thing I did was to format all the data to the correct type so I can analyze. I used the CAST function to do this and the code looked like this 

*"SELECT cast(rideable_type AS string) as rideable_type, cast( started_at AS time) as started_at, cast(ended_at AS time) as ended_at, cast(member_casual as string) as member_casual, cast(time_start as time) as start_time, cast(end_time AS time) as end_time, cast(start_day AS int) as start_day, cast(end_day as int) as end_day, minutes_per_ride
 FROM `dulcet-hulling-375416.cyclistic.clean_data` limit 1000*
 
 After that I decided to UNION all the data together so I could work on one table to figure out my descriptive statistics. The code consisted of this 
 
 *######Union all start. cleaning data from over a year to figure our evening hours for casuals vs. members*

*SELECT started_at, ended_at, member_casual, cast(started_at AS time) as time_start, cast(ended_at As time) as end_time 
 FROM `dulcet-hulling-375416.cyclistic.dec_2022` `dulcet-hulling-375416.cyclistic.nov_2022` 
 union all
SELECT started_at, ended_at, member_casual, cast(started_at AS time) as time_start, cast(ended_at As time) as end_time 
 from `dulcet-hulling-375416.cyclistic.oct_2022` `dulcet-hulling-375416.cyclistic.sep_2022` 
 union all
 SELECT started_at, ended_at, member_casual, cast(started_at AS time) as time_start, cast(ended_at As time) as end_time 
 from `dulcet-hulling-375416.cyclistic.aug_2022` `dulcet-hulling-375416.cyclistic.july_2022`
 union all 
 SELECT started_at, ended_at, member_casual, cast(started_at AS time) as time_start, cast(ended_at As time) as end_time 
 from `dulcet-hulling-375416.cyclistic.june_2022` `dulcet-hulling-375416.cyclistic.may_2022`
 union all
 SELECT started_at, ended_at, member_casual, cast(started_at AS time) as time_start, cast(ended_at As time) as end_time 
 from `dulcet-hulling-375416.cyclistic.april_2022`
 `dulcet-hulling-375416.cyclistic.march_2022`
 union all
SELECT started_at, ended_at, member_casual, cast(started_at AS time) as start_time, cast(ended_at As time) as end_time 
  from `dulcet-hulling-375416.cyclistic.feb_2022` `dulcet-hulling-375416.cyclistic.jan_2022`*
  
  *########end of union all"*
  
  
Then to find the average I wrote this 
  
*select avg(difference_in_time) as average
from `dulcet-hulling-375416.cyclistic.days_2022`,
(
SELECT  ended_at-started_at as difference_in_time
FROM `dulcet-hulling-375416.cyclistic.days_2022` limit 1000
)*
 
 Which was 23:52 for all overall riders
 
 Then I wanted to figure out the average of each type of rider so I wrote this code,

*select avg(difference_in_time) as average
from `dulcet-hulling-375416.cyclistic.days_2022`,
 where member_casual = "member" limit 1000
(
SELECT  ended_at-started_at as difference_in_time
FROM `dulcet-hulling-375416.cyclistic.days_2022`  limit 1000
)*

AND

*select avg(difference_in_time) as average
from `dulcet-hulling-375416.cyclistic.days_2022`,
 where member_casual = "casual" limit 1000
(
SELECT  ended_at-started_at as difference_in_time
FROM `dulcet-hulling-375416.cyclistic.days_2022`  limit 1000
)*


Where I found out casuals had and avearge ride time of 10:18 and members had a ride time of 26:32
 
From there I used the WEEKDAY function in excel to extract the day of each timestamp because I felt that was valuable data. 
 
After I gathered all the information I needed I built a dashbaord on tableau to prevent my findings to stakeholders. 

 
![Dashboard 1 (2)](https://github.com/SpotMcCormick/SpotMcCormick.CyclisticCapstone/assets/132832823/5c79a15b-77af-4311-97af-9567048a1269)


Hope you enjoyed!


 
