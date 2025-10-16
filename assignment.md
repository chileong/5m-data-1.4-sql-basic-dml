# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
SELECT max(round(rfp.resale_price/rfp.floor_area_sqm)) AS max_price_sqm, 
min(round(rfp.resale_price/rfp.floor_area_sqm)) AS min_price_sqm
FROM main.resale_flat_prices_2017 rfp
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
SELECT rfp.town, round(avg(rfp.resale_price/rfp.floor_area_sqm)) AS price_sqm
FROM main.resale_flat_prices_2017 rfp
GROUP BY rfp.town
```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql
SELECT CASE WHEN rfp.resale_price < 400000 THEN 'Budget' 
WHEN rfp.resale_price between 400000 and 700000 THEN 'Mid-Range' 
ELSE 'Premium' END AS flat_category,
count(*) AS category_count
FROM main.resale_flat_prices_2017 rfp
GROUP BY flat_category
ORDER BY category_count DESC
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
SELECT rfp.town, count (*) AS flats_sold
FROM main.resale_flat_prices_2017 rfp
WHERE rfp.month in ('2017-01', '2017-02', '2017-03')
GROUP BY rfp.town
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
