## Completed Assessment Document

The full Junior Data Analyst Assessment, including my responses to Parts 1–6, is available in Google Docs.

[View My Completed Tunda Box Assessment](https://docs.google.com/document/d/16JPZYd3hE99O3n7k2NwQlNIRME8a5mNaLY9cp85G7cs/edit?usp=sharing)

**Candidate:** Sharon Koina · [LinkedIn](https://linkedin.com/in/sharon-koina) · [GitHub](https://github.com/naisoisharonkarinoh)


## Repository contents
| File | What it is |
|---|---|
| `assessment.ipynb` | All SQL and Python solutions, run against the sample data |
| `data/` | The sample tables from the assessment, transcribed to CSV exactly as given |
| `requirements.txt` | Python packages needed to run the notebook |

## How to run
```bash
pip install -r requirements.txt
jupyter notebook assessment.ipynb
```
The notebook loads the CSVs into pandas and an in-memory SQLite database, so every SQL query runs as written.

## Assumptions
<!-- List each assumption you made, e.g. how you treated duplicates, NULLs, city spelling, refunds, the outlier, customer 999. -->

## Thought process
### Part 1 – Experience
### Part 2 – SQL and Python
<!-- For each question: what you were asked, how you approached it, the result. -->
### Part 3 – Data quality and spreadsheets
### Part 3 – Data Quality and Spreadsheets

#### D1. Audit the Data

The following data quality issues concern me:

1. **Duplicate orders:** Order ID 1006 appears twice. I would investigate and remove the duplicate if confirmed.
2. **Missing values:** Order 1009 has a NULL amount. I would check the original transaction records.
3. **Unusual amount:** Order 1013 has KES 185,000, which may be an incorrect entry. I would verify it.
4. **Inconsistent city names:** Nairobi appears with different capitalisation and extra spaces. I would standardise the city names.
5. **Invalid customer reference:** Order 1020 belongs to customer ID 999, who is not in the customers table. I would investigate the missing customer record.
6. **Order statuses:** Cancelled and refunded orders should not be included in completed revenue calculations.

I would clean and validate the data before sharing final reports.

#### D2. Spreadsheet Formulas

**1. Total completed M-Pesa revenue:**

```excel
=SUMIFS(E:E,D:D,"completed",F:F,"M-Pesa")
```

**2. Add each order's city from the customers sheet:**

```excel
=XLOOKUP(B2,customers!A:A,customers!B:B,"Not Found")
```

The first formula adds amounts for completed orders paid through M-Pesa. The second looks up the customer's ID and returns their city from the customers sheet.

#### D3. Mean or Median

I would use the median because the dataset contains an unusually high completed order of KES 185,000. This outlier can increase the mean and make it less representative of a typical order. The median is less affected by extreme values and gives a better picture of the typical completed order value.
### Part 4 – Statistics
### Part 5 – Business case
### Part 6 – Questions for the team

## What I'd do with more time

## Verified Assessment Results and Corrections

The following results were calculated from the supplied Tunda Box sample data.

### 1. Orders by Status (S1)

| Order Status | Number of Orders |
|---|---:|
| Completed | 16 |
| Cancelled | 2 |
| Refunded | 2 |

**Note:** I used distinct order IDs to avoid counting the duplicated order ID 1006 twice. The original data contains 17 completed rows, including the duplicate.
### 2. Completed Revenue by City (S2)

| City | Revenue (KES) |
|---|---:|
| Kisumu | 187,100 |
| Nairobi | 20,650 |
| Mombasa | 5,150 |
| Nakuru | 3,300 |

Kisumu has the highest completed-order revenue.

I removed duplicate orders, excluded missing amounts and standardised city names. Orders belonging to unmatched customer IDs were not included in the city totals.
### 3. Repeat Purchase Rate (S4)

### S4. Repeat Purchase Rate

**SQL Query:**

```sql
WITH unique_orders AS (
    SELECT DISTINCT ON (order_id) *
    FROM orders
    ORDER BY order_id
),
customer_orders AS (
    SELECT
        c.customer_id,
        COUNT(o.order_id) AS order_count
    FROM customers c
    LEFT JOIN unique_orders o
        ON c.customer_id = o.customer_id
        AND o.status = 'completed'
    GROUP BY c.customer_id
)
SELECT
    COUNT(*) FILTER (WHERE order_count >= 2) * 100.0
    / COUNT(*) AS repeat_purchase_rate
FROM customer_orders;

**Result:** 30%.

**Calculation:** 3 customers out of 10 have placed at least two distinct completed orders.

Repeat purchase rate = (3 / 10) × 100 = 30%.

I counted completed orders only and used distinct order IDs to avoid counting duplicates.

### 4. Month-on-Month Revenue (S5)

| Month | Completed Revenue (KES) | Percentage Change |
|---|---:|---:|
| June | 9,000 | N/A |
| July | 6,800 | -24.44% |
| August | 192,000 | 2,723.53% |
| September | 10,300 | -94.64% |

The unusually high August revenue is caused by an order worth KES 185,000, which requires verification.

### 5. Data Quality and Assumptions

During the analysis, I identified:

- Duplicate order ID 1006.
- Missing order amount for order 1009.
- An unusually high order amount of KES 185,000.
- Inconsistent city names and extra spaces.
- Customer ID 999 in the orders table, which does not exist in the customers table.

I used SQL queries to group, filter, join and aggregate the data. I also used distinct order IDs where necessary to avoid counting duplicate transactions twice.

### 6. Thought Process

My approach was to first understand the tables and identify the relationship between customers and orders. I then checked the data for missing values, duplicates, inconsistent entries and unusual amounts.

After cleaning and validating the data, I used SQL to calculate order counts, city revenue, repeat purchase rates and monthly revenue changes.

Finally, I interpreted the results in business terms and considered how the findings could support decision-making. I also documented assumptions and highlighted issues that require further investigation before presenting final business figures.

### 7. Completed Assessment Document

[View My Completed Tunda Box Assessment](https://docs.google.com/document/d/16JPZYd3hE99O3n7k2NwQlNIRME8a5mNaLY9cp85G7cs/edit?usp=sharing)
