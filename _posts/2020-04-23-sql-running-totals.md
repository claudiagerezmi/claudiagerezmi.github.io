---
title: SQL Practice - Understanding Running Totals
date: 2020-04-23
author: Claudia
layout: post
image: '/images/posts/main/20200423-sql-running-totals.jpg'
tags: [learning]
---

Introduction
------------

I got an interesting exercise to work on using SQL. Since the data was
available in a data frame format, I thought I could use SQL within R to
solve it.

To run SQL in R, I use the
[`sqldf package`](https://www.rdocumentation.org/packages/sqldf/versions/0.4-11).

The sqldf package is very simple to use. The main function is `sqldf()`,
and what it does is to set up a database, it imports the data frame into
the database, it performs the SQL select or other statement passed to
the function, and returns the result using a heuristic to determine
which class to assign to each column of the returned data frame.

All my SQL statements will be wrapped up by `sqldf()`.

Preparing the data
------------------

This exercise uses a simple table containing info about
purchase\_revenue and purchase\_date by customer\_id. Here is the code I
use to prepare the data.

    # Load required packages
    library(tidyverse)
    library(sqldf)
    library(lubridate)
    library(knitr)
    library(tictoc)

    # I chose to work with a SQLite DBMS
    options(sqldf.driver = "SQLite")

    # Create the columns of the data frame
    customer_id <- c(1, 2, 3, 2, 2, 3, 1, 3, 2)
    purchase_date <- c("2015-01-01 14:32:51", "2015-01-02 12:14:51", "2015-01-02 18:08:21", "2015-03-02 23:42:21", "2015-04-02 23:42:21", "2015-07-03 22:07:11", "2015-09-03 21:02:41", "2015-10-03 05:15:24", "2015-10-03 07:11:56")
    purchase_revenue <- c(25.34, 34.34, 37.15, 47.24, 54.12, 65.21, 74.60, 11.30, 22.45)

    # Create the data frame "test_orders"
    test_orders <- data.frame(customer_id, purchase_date, purchase_revenue)

    # Make sure the purchase_date column has a date format
    test_orders$purchase_date <- ymd_hms(test_orders$purchase_date)

<table>
<caption>Test Orders Table</caption>
<thead>
<tr class="header">
<th style="text-align: right;">customer_id</th>
<th style="text-align: left;">purchase_date</th>
<th style="text-align: right;">purchase_revenue</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">1</td>
<td style="text-align: left;">2015-01-01 14:32:51</td>
<td style="text-align: right;">25.34</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: left;">2015-01-02 12:14:51</td>
<td style="text-align: right;">34.34</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: left;">2015-01-02 18:08:21</td>
<td style="text-align: right;">37.15</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: left;">2015-03-02 23:42:21</td>
<td style="text-align: right;">47.24</td>
</tr>
<tr class="odd">
<td style="text-align: right;">2</td>
<td style="text-align: left;">2015-04-02 23:42:21</td>
<td style="text-align: right;">54.12</td>
</tr>
<tr class="even">
<td style="text-align: right;">3</td>
<td style="text-align: left;">2015-07-03 22:07:11</td>
<td style="text-align: right;">65.21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">1</td>
<td style="text-align: left;">2015-09-03 21:02:41</td>
<td style="text-align: right;">74.60</td>
</tr>
<tr class="even">
<td style="text-align: right;">3</td>
<td style="text-align: left;">2015-10-03 05:15:24</td>
<td style="text-align: right;">11.30</td>
</tr>
<tr class="odd">
<td style="text-align: right;">2</td>
<td style="text-align: left;">2015-10-03 07:11:56</td>
<td style="text-align: right;">22.45</td>
</tr>
</tbody>
</table>

Calculating running totals
--------------------------

The problem at hand asks to calculate the first date (YYYY-MM-DD) on
which a customer’s cumulative purchase\_revenue has reached $100 using
the test\_orders table.

Like with most SQL problems, there are multiple ways you can solve this.
Here I’m going to explain two ways:

1.  Using a window function
2.  Using a self join

### Using a window function

It would be simple to write a SQL query returning the cumulative revenue
for all customers.

    sqldf('SELECT SUM(purchase_revenue) as cumulative_revenue
    FROM test_orders
          ')

    ##   cumulative_revenue
    ## 1             371.75

Aggregate functions like `SUM`, perform calculations across a set of
rows and return a single output row.

Similar to an aggregate function, a window function calculates on a set
of rows, but unlike an aggregate function, a window function does not
cause rows to become grouped into a single output row.

    sqldf('SELECT customer_id
        ,purchase_date
        ,purchase_revenue
        ,SUM(purchase_revenue) OVER () cumulative_revenue
    FROM test_orders
          ')

    ##   customer_id       purchase_date purchase_revenue cumulative_revenue
    ## 1           1 2015-01-01 09:32:51            25.34             371.75
    ## 2           2 2015-01-02 07:14:51            34.34             371.75
    ## 3           3 2015-01-02 13:08:21            37.15             371.75
    ## 4           2 2015-03-02 18:42:21            47.24             371.75
    ## 5           2 2015-04-02 19:42:21            54.12             371.75
    ## 6           3 2015-07-03 18:07:11            65.21             371.75
    ## 7           1 2015-09-03 17:02:41            74.60             371.75
    ## 8           3 2015-10-03 01:15:24            11.30             371.75
    ## 9           2 2015-10-03 03:11:56            22.45             371.75

The syntax of a windows function is as follows:

    window_function (expression) OVER
         ( [ PARTITION BY expression_list ]
           [ ORDER BY order_list ]
           [ ROWS frame_clause ])

Window functions are initiated with the `OVER` clause, and are
configured using three concepts:

*window partition (`PARTITION BY`) - groups rows into partitions *window
ordering (`ORDER BY`) - defines the order or sequence of rows within
each partition \*window frame (`ROWS`) - defines the window by use of an
offset from the specified row

Definitions:

-   expression\_list: Comma separated list of expressions. They can only
    refer to column names derived by the FROM clause. The expressions in
    the list cannot refer to expressions or aliases in the select list.
    If you omit the PARTITION BY clause, the whole result set is treated
    as a single partition.
-   order\_list: Comma separated list of expressions. They can only
    refer to column names derived by the FROM clause.
-   frame\_clause: Define the offset using `CURRENT ROW`,
    `_value_ PRECEDING`, `UNBOUNDED PRECEDING`, `_value_ FOLLOWING`,
    `UNBOUNDED FOLLOWING`

The documentation on the `OVER` clause for a SQL Server can be found
[here](https://docs.microsoft.com/en-us/sql/t-sql/queries/select-over-clause-transact-sql?view=sql-server-2017).

Going back to the exercise.

Let’s say we want to calculate the cumulative\_revenue by customer\_id.
One familiar way to do this is using `GROUP BY`.

    sqldf('SELECT customer_id
        ,SUM(purchase_revenue) AS cumulative_purchase
    FROM test_orders
    GROUP BY customer_id
          ')

    ##   customer_id cumulative_purchase
    ## 1           1               99.94
    ## 2           2              158.15
    ## 3           3              113.66

The query above returns three rows because we are grouping by
customer\_id and we have three distinct customers.

The `GROUP BY` clause is used often used in conjunction with an
aggregate function, in this case, `SUM()`. The `GROUP BY` clause reduces
the number of rows returned by rolling them up and calculating the sums
for each group.

Now let’s calculate the cumulative\_revenue by customer\_id using the
`PARTITION BY` clause.

    sqldf('SELECT customer_id
        ,purchase_date
        ,purchase_revenue
        ,SUM(purchase_revenue) OVER (PARTITION BY customer_id) AS cummulative_revenue
    FROM test_orders
    ORDER BY customer_id
          ')

    ##   customer_id       purchase_date purchase_revenue cummulative_revenue
    ## 1           1 2015-01-01 09:32:51            25.34               99.94
    ## 2           1 2015-09-03 17:02:41            74.60               99.94
    ## 3           2 2015-01-02 07:14:51            34.34              158.15
    ## 4           2 2015-03-02 18:42:21            47.24              158.15
    ## 5           2 2015-04-02 19:42:21            54.12              158.15
    ## 6           2 2015-10-03 03:11:56            22.45              158.15
    ## 7           3 2015-01-02 13:08:21            37.15              113.66
    ## 8           3 2015-07-03 18:07:11            65.21              113.66
    ## 9           3 2015-10-03 01:15:24            11.30              113.66

The `PARTITION BY` clause divides the rows into partitions given by the
customer\_id column, the `SUM()` function is applied to each partition.

As we can see, the `PARTITION BY` clause does not reduce the number of
rows returned.

Now, what we really want to find is the running total per customer. That
is a cummulative sum of the purchase\_revenue by date.

We want to sum the revenue by customer\_id and we want to do that by
date (from the oldest to newest), so we need to divide the data by
customer\_id and add up the purchase\_revenue ordering the rows by
purchase\_date. We use `ORDER BY` in the `OVER` clause.

    sqldf('SELECT customer_id
        ,purchase_date
        ,purchase_revenue
        ,SUM(purchase_revenue) OVER (
            PARTITION BY customer_id 
            ORDER BY purchase_date
            ) AS running_total
    FROM test_orders
    ORDER BY customer_id
          ')

    ##   customer_id       purchase_date purchase_revenue running_total
    ## 1           1 2015-01-01 09:32:51            25.34         25.34
    ## 2           1 2015-09-03 17:02:41            74.60         99.94
    ## 3           2 2015-01-02 07:14:51            34.34         34.34
    ## 4           2 2015-03-02 18:42:21            47.24         81.58
    ## 5           2 2015-04-02 19:42:21            54.12        135.70
    ## 6           2 2015-10-03 03:11:56            22.45        158.15
    ## 7           3 2015-01-02 13:08:21            37.15         37.15
    ## 8           3 2015-07-03 18:07:11            65.21        102.36
    ## 9           3 2015-10-03 01:15:24            11.30        113.66

To get the first date (YYYY-MM-DD) on which a customer’s cumulative
purchase\_revenue has reached $100, we add a filter.

    sqldf(' SELECT customer_id
        ,purchase_date
        ,running_total
    FROM (
        SELECT customer_id
            ,purchase_date
            ,purchase_revenue
            ,SUM(purchase_revenue) OVER (
                PARTITION BY customer_id 
                ORDER BY purchase_date
                ) AS running_total
        FROM test_orders
        )
    WHERE running_total >= 100
    GROUP BY customer_id
          ')

    ##   customer_id       purchase_date running_total
    ## 1           2 2015-04-02 19:42:21        135.70
    ## 2           3 2015-07-03 18:07:11        102.36

*Note: Here I’m using a group-by trick to get the first ocurrence of a
value higher than $100. MySQL allows you to not aggregate the
non-grouped-by columns (other databases would throw a syntax error), in
which case it outputs only the first occurrence of each group-by
value(s). Note though that this won’t guarantee the way in which the
“first” occurrence is determined (it will be just how the rows are read
in). If you want a particular first occurrence, sort first, then apply
the group-by trick.*

### Using an self join

A self join is a query that compares a table to itself. In this case,
we’re comparing each date to any date less than or equal to it in order
to calculate the running total.

More especifically, we take the sum of purchase\_revenue in the second
table over every row that has a date less than or equal to the date
coming from the first table.

    sqldf('SELECT t1.customer_id
        ,t1.purchase_revenue
        ,SUM(t2.purchase_revenue) AS running_total
    FROM test_orders t1
        ,test_orders t2
    WHERE t1.purchase_date >= t2.purchase_date
        AND t1.customer_id = t2.customer_id
    GROUP BY t2.customer_id
        ,t1.purchase_date
          ')

    ##   customer_id purchase_revenue running_total
    ## 1           1            25.34         25.34
    ## 2           1            74.60         99.94
    ## 3           2            34.34         34.34
    ## 4           2            47.24         81.58
    ## 5           2            54.12        135.70
    ## 6           2            22.45        158.15
    ## 7           3            37.15         37.15
    ## 8           3            65.21        102.36
    ## 9           3            11.30        113.66

Which is the same as using the JOIN function

    sqldf('SELECT t1.customer_id
        ,t1.purchase_date
        ,t1.purchase_revenue
        ,SUM(t2.purchase_revenue) AS running_total
    FROM test_orders t1
    INNER JOIN test_orders t2 ON t1.purchase_date >= t2.purchase_date
        AND t1.customer_id = t2.customer_id
    GROUP BY t2.customer_id
        ,t1.purchase_date
          ')

    ##   customer_id       purchase_date purchase_revenue running_total
    ## 1           1 2015-01-01 09:32:51            25.34         25.34
    ## 2           1 2015-09-03 17:02:41            74.60         99.94
    ## 3           2 2015-01-02 07:14:51            34.34         34.34
    ## 4           2 2015-03-02 18:42:21            47.24         81.58
    ## 5           2 2015-04-02 19:42:21            54.12        135.70
    ## 6           2 2015-10-03 03:11:56            22.45        158.15
    ## 7           3 2015-01-02 13:08:21            37.15         37.15
    ## 8           3 2015-07-03 18:07:11            65.21        102.36
    ## 9           3 2015-10-03 01:15:24            11.30        113.66

Filtering for the dates (YYYY-MM-DD) on which a customer’s cumulative
purchase\_revenue has reached or surpassed $100.

    sqldf('SELECT t1.customer_id
        ,t1.purchase_date
        ,t1.purchase_revenue
        ,SUM(t2.purchase_revenue) AS running_total
    FROM test_orders t1
    INNER JOIN test_orders t2 ON t1.purchase_date >= t2.purchase_date
        AND t1.customer_id = t2.customer_id
    GROUP BY t2.customer_id
        ,t1.purchase_date
    HAVING SUM(t2.purchase_revenue) >= 100
          ')

    ##   customer_id       purchase_date purchase_revenue running_total
    ## 1           2 2015-04-02 19:42:21            54.12        135.70
    ## 2           2 2015-10-03 03:11:56            22.45        158.15
    ## 3           3 2015-07-03 18:07:11            65.21        102.36
    ## 4           3 2015-10-03 01:15:24            11.30        113.66

I will have to make more research on how to get only the first date on
which a customer’s cumulative purchase\_revenue has reached $100. All I
can come out with now is an outer filter.

    sqldf('SELECT customer_id
        ,DATE(
            MIN(purchase_date)
            ,"unixepoch"
            ) AS purchase_date
        ,running_total
    FROM (
        SELECT t1.customer_id
            ,t1.purchase_date
            ,t1.purchase_revenue
            ,SUM(t2.purchase_revenue) AS running_total
        FROM test_orders t1
        INNER JOIN test_orders t2 ON t1.purchase_date >= t2.purchase_date
            AND t1.customer_id = t2.customer_id
        GROUP BY t2.customer_id
            ,t1.purchase_date
        HAVING SUM(t2.purchase_revenue) >= 100
        )
    GROUP BY customer_id
          ')

    ## Warning in structure(as.numeric(x), class = c("POSIXct", "POSIXt")): NAs
    ## introduced by coercion

    ##   customer_id purchase_date running_total
    ## 1           2          <NA>        135.70
    ## 2           3          <NA>        102.36

### Comparing the window function method vs. the self-join method

So, which method is faster? 

A quick way to check on execution time in R
is using system.time() which returns the CPU (and other) times that the
expression used.

The elapsed time is the wall clock time taken to execute the function
sqldf. The “user CPU time” gives the CPU time spent by the current
process (i.e., the current R session) and “system CPU time” gives the
CPU time spent by the kernel (the operating system) on behalf of the
current process.

##### Self-Join execution time

    ##    user  system elapsed 
    ##   0.015   0.004   0.019

#### Window function execution time.

    ##    user  system elapsed 
    ##    0.02    0.00    0.02

The window function has an elapsed time about 10% faster than the self
join function. Plus I believe it’s easier to write.
