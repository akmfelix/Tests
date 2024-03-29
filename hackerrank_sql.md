## 1 Revising the Select Query I
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

## 2 Revising the Select Query II
Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
~~~
SELECT name
FROM city
WHERE countrycode = 'USA' AND population > 120000;
~~~

## 3 Select All
Query all columns (attributes) for every row in the CITY table.
~~~
select * from city;
~~~

## 4 Select by ID
Query all columns for a city in CITY with the ID 1661.
~~~
select * from city where id=1661;
~~~

## 5 Japanese Cities' Attributes
Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
~~~
select * from city where countrycode='JPN';
~~~

## 6 Japanese Cities' Names
Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
~~~
select name from city where countrycode='JPN';
~~~

## 7 Weather Observation Station 1
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

