# Tunda Box Junior Data Analyst Assessment

**Candidate:** Sharon Koina  
**Assessment:** Junior Data Analyst Assessment

## Completed Assessment Document

The full Junior Data Analyst Assessment, including my responses to Parts 1–6, is available in Google Docs.

[View My Completed Tunda Box Assessment](https://docs.google.com/document/d/16JPZYd3hE99O3n7k2NwQlNIRME8a5mNaLY9cp85G7cs/edit?usp=sharing)

## Repository Contents

| File | Description |
|---|---|
| `README.md` | Assessment responses, findings and thought process |
| `assessment.ipynb` | SQL and Python solutions |
| `requirements.txt` | Python packages required for the notebook |

## How to Run

Install the required packages:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook assessment.ipynb
```

## Part 1 – Experience and Problem Solving

### Relevant Experience

I have developed practical data analysis skills through my Power Learn Project training and my Supermarket Sales Capstone project. I have worked with Python, SQL and data visualisation to clean, analyse and interpret data.

In my capstone project, I analysed supermarket sales data to understand revenue performance, compare branches and examine payment methods. This helped me develop skills in data cleaning, exploratory data analysis and communicating findings.

### Handling Different Results

If a colleague and I obtain different results from the same dataset, I would first check whether we used the same data, filters, date ranges and calculation methods. I would review the SQL queries, check for duplicates and missing values, and compare the results step by step.

I would discuss the differences with my colleague, agree on the correct definitions and document the final approach to ensure accurate reporting.

## Part 2 – SQL and Python

I used SQL and Python to explore the supplied customer and orders data.

My analysis involved:

- Counting orders by status.
- Joining customers and orders tables.
- Calculating completed revenue by city.
- Identifying customers who had never placed an order.
- Calculating the repeat purchase rate.
- Analysing monthly revenue and percentage changes.
- Identifying duplicates, missing values and unusual records.

The SQL and Python solutions are included in `assessment.ipynb`.

## Part 3 – Data Quality and Spreadsheets

### D1. Audit the Data

The following data quality issues concern me:

1. **Duplicate orders:** Order ID 1006 appears twice. I would investigate and remove the duplicate if confirmed.
2. **Missing values:** Order 1009 has a NULL amount. I would check the original transaction records.
3. **Unusual amount:** Order 1013 has KES 185,000, which may be an incorrect entry. I would verify it.
4. **Inconsistent city names:** Nairobi appears with different capitalisation and extra spaces. I would standardise the city names.
5. **Invalid customer reference:** Order 1020 belongs to customer ID 999, who is not in the customers table. I would investigate the missing customer record.
6. **Order statuses:** Cancelled and refunded orders should not be included in completed revenue calculations.

I would clean and validate the data before sharing final reports.

### D2. Spreadsheet Formulas

**1. Total completed M-Pesa revenue:**

```excel
=SUMIFS(E:E,D:D,"completed",F:F,"M-Pesa")
```

This formula adds amounts for completed orders paid through M-Pesa.

**2. Add each order's city from the customers sheet:**

```excel
=XLOOKUP(B2,customers!A:A,customers!B:B,"Not Found")
```

This formula looks up the customer's ID and returns their city from the customers sheet.

### D3. Mean or Median

I would use the median because the dataset contains an unusually high completed order of KES 185,000. This outlier can increase the mean and make it less representative of a typical order. The median is less affected by extreme values and gives a better picture of the typical completed order value.

## Part 4 – Statistics

### Understanding a P-value

A p-value helps us assess whether an observed result could reasonably have happened by chance if there were no real effect. A small p-value, such as 0.05 or below, provides evidence against the assumption that there is no effect. It does not prove that a result is correct or that there is a 95% probability that the hypothesis is true.

### Correlation and Causation

Correlation does not necessarily mean causation. Two variables may change together without one directly causing the other. For example, an increase in SMS messages and sales does not automatically mean that the messages caused the increase.

I would recommend a randomised experiment to test whether SMS messages have a direct effect on sales.

### A/B Testing

The current conversion rate is:

50 / 1,000 × 100 = **5%**

The new conversion rate is:

60 / 1,000 × 100 = **6%**

The absolute improvement is **1 percentage point**, while the relative improvement is **20%**.

I would not immediately recommend launching the new version based only on these figures. I would first check statistical significance, test duration and possible factors that could influence the results.

## Part 5 – Business Case: Marketing Conversion Analysis

### September

| Channel | Visitors | Conversions | Conversion Rate |
|---|---:|---:|---:|
| Organic | 40,000 | 2,400 | 6.00% |
| Paid Social | 10,000 | 200 | 2.00% |
| **Total** | **50,000** | **2,600** | **5.20%** |

### October

| Channel | Visitors | Conversions | Conversion Rate |
|---|---:|---:|---:|
| Organic | 38,000 | 2,318 | 6.10% |
| Paid Social | 30,000 | 630 | 2.10% |
| **Total** | **68,000** | **2,948** | **4.34%** |

### Interpretation and Recommendation

The overall conversion rate decreased from 5.20% in September to approximately 4.34% in October.

However, both organic and paid social conversion rates improved slightly. The overall decrease was mainly caused by a change in traffic mix: paid social attracted a much larger share of visitors, but its conversion rate was lower than organic traffic.

I would investigate paid social campaign targeting, audience quality, devices, landing pages and visitor behaviour. I would not immediately stop the paid campaigns. Instead, I would identify areas for improvement and optimise the campaigns using the findings.

## Part 6 – Questions for the Team

### 1. What would my responsibilities be?

I would expect to support data collection, cleaning, analysis, reporting and visualisation, while helping the team turn data into useful business insights.

### 2. Which tools and technologies would I use?

I would be interested in working with SQL, Python, Excel or Google Sheets, and data visualisation tools such as Power BI or Looker Studio.

### 3. What learning and mentorship opportunities are available?

I would like to learn from experienced analysts through practical projects, feedback, mentorship and opportunities to work with real business data.

### 4. How would success be measured in the first three months?

I would aim to understand the company's data and reporting processes, complete assigned analysis tasks accurately, communicate findings clearly and contribute useful insights to the team.

## Verified Assessment Results and Corrections

The following results were calculated from the supplied Tunda Box sample data.

### S1. Orders by Status

| Order Status | Number of Orders |
|---|---:|
| Completed | 16 |
| Cancelled | 2 |
| Refunded | 2 |

I used distinct order IDs to avoid counting the duplicated order ID 1006 twice. The original data contains 17 completed rows, including the duplicate.

### S2. Completed Revenue by City

| City | Revenue (KES) |
|---|---:|
| Kisumu | 187,100 |
| Nairobi | 20,650 |
| Mombasa | 5,150 |
| Nakuru | 3,300 |

Kisumu has the highest completed-order revenue.

I removed duplicate orders, excluded missing amounts and standardised city names. Orders belonging to unmatched customer IDs were not included in the city totals.

### S3. Customers Who Never Placed an Order

The customers who never placed an order are:

- Customer 109 – Eldoret
- Customer 110 – Kisumu

### S4. Repeat Purchase Rate

Three out of ten customers placed at least two distinct completed orders.

Repeat purchase rate:

(3 / 10) × 100 = **30%**

I counted completed orders only and used distinct order IDs to avoid counting duplicates.

### S5. Month-on-Month Revenue

| Month | Completed Revenue (KES) | Percentage Change |
|---|---:|---:|
| June | 9,000 | N/A |
| July | 6,800 | -24.44% |
| August | 192,000 | 2,723t/d/16JPZYd3hE99O3n7k2NwQlNIRME8a5mNaLY9cp85G7cs/edit?usp=sharing)
