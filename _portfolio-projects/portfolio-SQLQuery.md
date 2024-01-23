---
title: "SQL Data Queries"
date: 2024-01-16
excerpt: "Project walking through the use of SQL to query a relational database. <br/><img src='/images/SQL_Query/postgres-logo.png'>"
permalink:
layout: "single"
---

# Introduction

In a previous project I demonstrated my ability to design and implement a relational database (DB). However, I want to create a project where I focus solely on my ability to write efficient and effective SQL queries from a relational database. The Db I will be using is one that encompasses all the data that I accumulated for my Ph.D. dissertation research. The creation and details behind the DB can be found following this [link](https://ttoavs.github.io/portfolio-projects/portfolio-postgres/). The details around the data are not that important my goal here is to showcase my SQL technical abilities through data queries.

The relational DB is housed in a [PostgreSQL](https://www.postgresql.org) data base and I am interfacing with it on a local server using the program [DBeaver](https://dbeaver.io). Within this project I am going to go through 20 different prompts that I must accomplish by writing SQL code. The relative difficulty of the queries will increase throughout the document.

## Database Archetecture

Before jumping into the SQL code, I want to briefly go through the design of this database, which is more thoroughly covered in the before mentioned project.

The database originates from my published database CDFLOW, which consists of dissolved CO<sub>2</sub> estimates from flowing freshwaters across the US from 1990 through 2020. Additional tables related to spatial site data and add to the original data by including geographical reference data and additional environmental metrics. The layout of the relational DB can be seen in the below ER diagram, which also shows the primary and foreign keys for each table.

![Alt Text](/images/postgres_portfolio/ERD.png#center)

## Round 1 Prompts 1-10

The first round of queries will on involve querying data from a single table.

0\. (Preview prompt) Display a list of all the tables included in the DB.

![Alt Text](/images/SQL_Query/Q0_code.png)

![Alt Text](/images/SQL_Query/Q0_results.png)

0.5\. (Preview prompt) Display a list of all the columns in the CDFLOW table. (This table is the focus of most queries)

![Alt Text](/images/SQL_Query/Q.5_code.png)

![Alt Text](/images/SQL_Query/Q.5_results.png)

1\. Of the three spatial grouping features how many unique groups are represented?

![Alt Text](/images/SQL_Query/Q1_code.png)

![Alt Text](/images/SQL_Query/Q1_results.png)

2\. How many observations are available in each of the 49 states represented in the data? Which state has the least? (Washington D.C. is considered a state for this DB)

![Alt Text](/images/SQL_Query/Q2_code.png)

![Alt Text](/images/SQL_Query/Q2_results.png)

3\. What is the mean, max, and min *p*CO<sub>2</sub> value from each state?

![Alt Text](/images/SQL_Query/Q3_code.png)

![Alt Text](/images/SQL_Query/Q3_results.png)

4\. How many observations have pH values over 7?

![Alt Text](/images/SQL_Query/Q4_code.png)

![Alt Text](/images/SQL_Query/Q4_results.png)

5\. How many observations have above average pCO2 values?

![Alt Text](/images/SQL_Query/Q5_code.png)

![Alt Text](/images/SQL_Query/Q5_results.png)

6\. How many observations occur in each month?

![Alt Text](/images/SQL_Query/Q6_code.png)

![Alt Text](/images/SQL_Query/Q6_results.png)

7\. Compute a running count of observations by date in each COMID.

![Alt Text](/images/SQL_Query/Q7_code.png)

![Alt Text](/images/SQL_Query/Q7_results.png)

8\. Write a query to look at the difference between the most recent *p*CO<sub>2</sub> value from the last at a particular COMID.

![Alt Text](/images/SQL_Query/Q8_code.png)

![Alt Text](/images/SQL_Query/Q8_results.png)

9\. List COMIDS that have *p*CO<sub>2</sub> values with pH > 9, Alkalinity < 2500, and temperature > 25?

![Alt Text](/images/SQL_Query/Q9_code.png)

![Alt Text](/images/SQL_Query/Q9_results.png)

10\. What are the average HUC_12 pH values in Minnesota?

![Alt Text](/images/SQL_Query/Q10_code.png)

![Alt Text](/images/SQL_Query/Q10_results.png)

## Round 2 Prompts 11-15

The second round will involve more difficult queries which may include data from 2 or more tables.

11\. Query *p*CO<sub>2</sub> estimates with COMID_NHD table data.

![Alt Text](/images/SQL_Query/Q11_code.png)

![Alt Text](/images/SQL_Query/Q11_results.png)

12\. Query *p*CO<sub>2</sub> estimates where over 50% of the HUC8 is covered by water.

![Alt Text](/images/SQL_Query/Q12_code.png)

![Alt Text](/images/SQL_Query/Q12_results.png)

13\. Query the Average *p*CO<sub>2</sub> by state and join with the state spatial table so that geometry data is available.

![Alt Text](/images/SQL_Query/Q13_code.png)

![Alt Text](/images/SQL_Query/Q13_results.png)

14\. Similar to number 13, query the average *p*CO<sub>2</sub> by HUC2 and join with the HUC2 spatial table so that geometry data is available.

![Alt Text](/images/SQL_Query/Q14_code.png)

![Alt Text](/images/SQL_Query/Q14_results.png)

15\. Query *p*CO<sub>2</sub> estimates from HUC8s where at least 50 observations are available.

![Alt Text](/images/SQL_Query/Q15_code.png)

![Alt Text](/images/SQL_Query/Q15_results.png)

## Round 3 Prompts 16-20

The third and final round will include more advanced data queries.

16\. Query the average *p*CO<sub>2</sub> and percent urban landcover by HUC8, only include complete observations.

![Alt Text](/images/SQL_Query/Q16_code.png)

![Alt Text](/images/SQL_Query/Q16_results.png)

17\. Query the counts of *p*CO<sub>2</sub> data within each HUC2 for each state for every year available.

![Alt Text](/images/SQL_Query/Q17_code.png)

![Alt Text](/images/SQL_Query/Q17_results.png)

18\. Query *p*CO<sub>2</sub> estimates and percent cultivated land cover observations collected between the months of May and September. Additionally filter out observations where Alkalinity it not at least 1000.

![Alt Text](/images/SQL_Query/Q18_code.png)

![Alt Text](/images/SQL_Query/Q18_results.png)

19\. Query *p*CO<sub>2</sub> estimates where within each HUC8 COMIDs represent at least three different streamorder levels and each comid has at least 5 observation.

![Alt Text](/images/SQL_Query/Q19_code.png)

![Alt Text](/images/SQL_Query/Q19_results.png)

20\. Combine prompts number 18 and 19. (This is actually data I am interested in modeling for research)

![Alt Text](/images/SQL_Query/Q20_code.png)

![Alt Text](/images/SQL_Query/Q20_results.png)

# Conclusion

SQL is great for querying big and complex relational databases. Although, there may be a bit of a learning curve to writing complex queries, once learned Data Scientists' can cut through big data in no time at all.

Thanks for reading and I hope this showcases the SQL technical skill that I possess! Hopefully you even picked up a new skill or two.
