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
### Part 4 – Statistics
### Part 5 – Business case
### Part 6 – Questions for the team

## What I'd do with more time

## Verified Assessment Results and Corrections

The following results were calculated from the supplied Tunda Box sample data.

### 1. Orders by Status (S1)

| Order Status | Number of Orders |
|---|---:|
| Completed | 17 |
| Cancelled | 2 |
| Refunded | 2 |

Note: The counts include the duplicated order ID 1006 in the original data.

### 2. Completed Revenue by City (S2)

| City | Revenue (KES) |
|---|---:|
| Kisumu | 187,100 |
| Nairobi | 22,150 |
| Nakuru | 3,300 |
| Mombasa | 2,800 |
| Eldoret | 2,350 |

Kisumu has the highest completed-order revenue.

### 3. Repeat Purchase Rate (S4)

**Result: 30%**

- Total customers: 10
- Customers with at least two distinct completed orders: 3

Calculation:

(3 / 10) × 100 = 30%

I counted distinct completed order IDs and excluded cancelled and refunded orders. The duplicated order ID 1006 was counted only once.

### 4. Month-on-Month Revenue (S5)

| Month | Completed Revenue (KES) | Percentage Change |
|---|---:|---:|
| June | 9,000 | N/A |
| July | 8,300 | -7.78% |
| August | 192,000 | 2,213.25% |
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
