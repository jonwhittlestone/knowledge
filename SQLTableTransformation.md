# SQL Table Transformation - Code Academy

https://www.codecademy.com/courses/sql-table-transformation

----

## Subqueries
non-correlated
    
    SELECT *
    FROM flights
    WHERE origin in (
            SELECT code
            FROM airports
            WHERE elevation < 2000
            );
            
    find the average total distance flown by day of week and month.
        SELECT a.dep_month,
        a.dep_day_of_week,
        AVG(a.flight_distance) AS average_distance
        FROM (
                SELECT dep_month,
                dep_day_of_week,
                dep_date,
                SUM(distance) AS flight_distance
                FROM flights
                GROUP BY 1,2,3

             ) a
        GROUP BY 1,2
        ORDER BY 1,2;
  
  Correlated sub-queries
    # echo row in subquery is processed (not independent of ourer query)
      SELECT id
        FROM flights AS f
        WHERE distance > (
                SELECT AVG(distance)
                FROM flights
                WHERE carrier = f.carrier);
    
 ## Set operations
 
 Merge two columns with a union (as opposed to merging two rows with JOIN)
 
 - https://goo.gl/psToQA | An inner join will combine rows from different tables if the join condition is true. Let's look at the syntax to see how it works. This differs to an outer join which only returns results where ```LEFT``` OR ````RIGHT``

-  https://goo.gl/FkZFNL | INTERSECT combines two SELECT statements and only returns rows from the first statement that are identical to the second. Similar to EXCEPT

    SELECT category FROM new_products
    INTERSECT
    SELECT category FROM legacy_products;
 
## Conditional Aggregates

Coniditional aggregates are aggregate functions that compute a result set based on a given set of conditions

Use ```IS NULL``` rather than ````= NULL``

- https://goo.gl/Q7Io4J | Case statements

    if we wanted to sum the total flight distance and compare that to the sum of flight distance from a particular airline (in this case, United Airlines) by origin airport
    
## Date, Time and String functions

- SELECT DATETIME(delivery_time) FROM baked_goods;

- https://goo.gl/khR8Km | Provide a date part, Imagine that each dessert in our baked_goods table is inspected 2 hours, 30 minutes, and 1 day after the manufacture time.'§'
- MAX, MIN
- String concatenation
    SELECT string1 || ' ' || string2;
-
 ----
 Additional from SQL / Code Academy
 
- Aggregate functions like SUM and COUNT compute a single result from a set of multiple values / from multiple values at a time
- https://github.com/laravel/framework/blob/5.1/composer.json#L37https://goo.gl/s4fYFL | GROUP BY is a clause in SQL that is only used with aggregate functions. It is used in collaboration with the SELECT statement to arrange identical data into groups.

    SELECT price, COUNT(*) FROM fake_apps
    GROUP BY price;
    
   
