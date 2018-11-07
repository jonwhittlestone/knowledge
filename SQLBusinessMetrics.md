# SQL Analysing Business Metrics - CodeAcademy

https://www.codecademy.com/learn/sql-analyzing-business-metrics

## Advanced Aggregates

- https://www.codecademy.com/courses/sql-analyzing-business-metrics/lessons/advanced-aggregates/exercises/daily-sum | How much money speedy spoon made from orders each day
- https://goo.gl/K4x4D1 | get revenue per day
    
    select date(ordered_at), round(sum(order_items.amount_paid),2)
    from orders
        join order_items on
            orders.id = order_items.order_id
            group by 1
            order by 1;
         
- https://goo.gl/NbSiI0 | Working out that Kale Smoothies aren't brining in the money by caclulated what percentage of total revenue, the revenue of each item represents
- https://goo.gl/kPY5rn | Building categories, using group by with expressions
