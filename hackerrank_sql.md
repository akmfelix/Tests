### 1 Revising the Select Query I
Query all columns for all American cities in the **CITY** table with populations larger than 100000. The **CountryCode** for America is USA. The CITY table is described as follows.

| Field  | Type  |
|---|---|
| ID  | NUMBER  |
| NAME  | VARCHAR2(17)  |
| COUNTRYCODE  | VARCHAR2(3)  |
| DISTRICT  | VARCHAR2(20)  |
| POPULATION  | NUMBER  |

~~~
select * from city where population>100000 and countrycode='USA'
~~~

### 2 Revising the Select Query II
Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
~~~
SELECT name
FROM city
WHERE countrycode = 'USA' AND population > 120000;
~~~

### 3 Select All
Query all columns (attributes) for every row in the CITY table.
~~~
select * from city;
~~~

### 4 Select by ID
Query all columns for a city in CITY with the ID 1661.
~~~
select * from city where id=1661;
~~~

### 5 Japanese Cities' Attributes
Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
~~~
select * from city where countrycode='JPN';
~~~

### 6 Japanese Cities' Names
Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
~~~
select name from city where countrycode='JPN';
~~~

### 7 Weather Observation Station 1
Query a list of CITY and STATE from the STATION table.
The STATION table is described as follows: STATION
| Field  | Type  |
|---|---|
| ID  | NUMBER  |
| CITY  | VARCHAR2(21)  |
| STATE  | VARCHAR2(2)  |
| LAT_N  | NUMBER  |
| LONG_W  | NUMBER  |
~~~
select city, state from station;
~~~

### 8 Weather Observation Station 3 !!!!!
Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
~~~
select distinct city from station where mod(id,2)=0;
~~~

### 9 Weather Observation Station 4
Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table. where LAT_N is the northern latitude and LONG_W is the western longitude.\
For example, if there are three records in the table with CITY values 'New York', 'New York', 'Bengalaru', there are 2 different city names: 'New York' and 'Bengalaru'. The query returns 1, because total_number_of_records-number_of_unique_city_names=3-2=1
~~~
select count(city)-count(distinct city) from station
~~~

### 10 Weather Observation Station 5
Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
~~~
(select city, length(city)
from station
order by length(city) asc, city asc
limit 1)
union
(select city, length(city)
from station
order by length(city) desc, city asc
limit 1);
~~~

### 11 Weather Observation Station 6
Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.
~~~
select distinct city 
from station 
where regexp_like(lower(city),'^[aeiou]');
~~~

### 12 Weather Observation Station 7
Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
~~~
select distinct city 
from station
where regexp_like(lower(city), '[aeiou]$');
~~~

### 13 Weather Observation Station 8
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
~~~
select distinct city 
from station
where regexp_like(lower(city),'^[aeiou]')
and regexp_like(lower(city),'[aeiou]$');
~~~

### 14 Weather Observation Station 9
Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
~~~
select distinct city 
from station
where regexp_like(lower(city), '^[^aeiou]');
~~~

### 15 Weather Observation Station 10
Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.
~~~
select distinct city 
from station
where regexp_like(lower(city), '[^aeiou]$');
~~~

### 16 Weather Observation Station 11
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
~~~
select distinct city
from station
where regexp_like(lower(city), '^[^aeiou]') 
  or regexp_like(lower(city), '[^aeiou]$');
~~~

### 17 Weather Observation Station 12
Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
~~~
select distinct city
from station
where regexp_like(lower(city), '^[^aeiou]') 
  and regexp_like(lower(city), '[^aeiou]$');
~~~

### 18 Higher Than 75 Marks
Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
~~~
select name 
from students
where marks>75
order by substr(name, -3) asc, id asc;
~~~
