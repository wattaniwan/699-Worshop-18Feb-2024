## Workshop: 18 Feb. 2024 


### 1. Create dataset and table 
- Create dataset **data_ass6_xxx** in BigQuery via WebUI 

- Create table **data_employees** via WebUI upload data in  **"employees.json"** with auto detect 



### 2. Queries and view the RESULTS and JSON

```
SELECT 
    salary, address
FROM `ds-on-gcp-410303.data_ass6_xxx.Employee`,
UNNEST(address) as address
LIMIT 5;

```


```
SELECT 
    salary.current_salary, address.city
FROM `ds-on-gcp-410303.data_ass6_xxx.Employee`,
UNNEST(address) as address
LIMIT 5;

```


### 3.  Write Queries and save as view   in BigQuery. 

"EmployeeForViz"  

This makes it easier to access and visualize the data in Looker Studio.

```
SELECT 
    ...
FROM `ds-on-gcp-410303.data_ass6_xxx.Employee`,
    ...
LIMIT 5;
```


### 4. Visualize Data in Looker Studio (Page1: Employee-Demo)

Contain atleast 3 charts.


### 5. Explore Public Datasets in BigQuery 


```
SELECT * FROM `bigquery-public-data.google_analytics_sample.ga_sessions_20170801` 
LIMIT 1;
```

### 6.  Write Queries and save as view   in BigQuery. 

"GAanalyticsForViz"  

Example: (Do not use this example for your assignment)

```
SELECT
    fullVisitorId AS user_id,
    product.productSKU AS item_id,
    SUM(hits.hitNumber) AS total_interact_count
FROM
    `bigquery-public-data.google_analytics_sample.ga_sessions_20170801`,
    UNNEST(hits) AS hits,
    UNNEST(hits.product) AS product
WHERE
    product.productSKU IS NOT NULL
    AND ARRAY_LENGTH(hits.product) > 0
GROUP BY
    user_id,
    item_id
ORDER BY
    total_interact_count DESC;
```

### 7. Visualize Data in Looker Studio (Page2: GA-Demo)

Contain atleast 3 charts.