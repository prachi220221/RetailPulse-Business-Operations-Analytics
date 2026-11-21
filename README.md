# RetailPulse-Business-Operations-Analytics
End-to-end retail analytics project using SQL, Python, Pandas, and Power BI to analyse revenue, profitability, operational KPIs, and data quality through interactive dashboards and business insights.
# Retail Revenue & Operational Analytics

An end-to-end retail analytics and business intelligence project using **SQL, Python, Pandas, and Power BI** to explore e-commerce revenue, profitability, operational performance, and data quality.

## Project Overview

Retail businesses generate large volumes of transactional data. Analysing this information consistently is essential for monitoring business performance, identifying operational issues, and making informed decisions.

This project demonstrates an analytics workflow that transforms raw e-commerce data into structured reports, business insights, and interactive dashboards.

The project focuses on:

- Revenue and profitability analysis
- Operational KPI monitoring
- SQL-based data validation and quality checks
- Data cleaning and preprocessing using Python
- Business intelligence and dashboard development
- Stakeholder-oriented reporting

## Business Objectives

The main objectives are to:

1. Analyse revenue and profitability trends.
2. Identify high-performing product categories and regions.
3. Monitor sales, returns, and operational KPIs.
4. Detect missing values, duplicate records, and inconsistent data.
5. Develop interactive dashboards for business reporting.
6. Support data-driven operational and commercial decisions.

## Technology Stack

| Category | Technologies |
|---|---|
| Programming | Python |
| Data Analysis | Pandas, NumPy |
| Database | SQL |
| Data Visualization | Power BI |
| Data Processing | Data Cleaning, EDA |
| Business Intelligence | KPI Reporting, Revenue Analysis |
| Data Quality | SQL Validation, QA Checks |

## Project Structure

```text
Retail-Revenue-Operational-Analytics/
│
├── dashboard/       # Power BI dashboard screenshots
├── data/            # Raw and cleaned sample datasets
│   ├── README.md
│   ├── amazon_sale_raw_sample.csv
│   └── cleaned_ecommerce_sample.csv
│
├── issues/          # Data quality issue tracking
├── notebooks/       # Exploratory data analysis
├── python/          # Data cleaning and analytics scripts
├── reports/         # Business findings and summaries
├── sql/             # SQL queries and validation scripts
│
├── README.md
├── requirements.txt
└── data_dictionary.md
```

## Analytics Workflow

The project follows a structured analytics process:

1. **Data Collection:** Load raw e-commerce transaction data.
2. **Data Cleaning:** Handle missing values, duplicates, and inconsistent records using Python and Pandas.
3. **SQL Analysis:** Write queries to analyse revenue, profitability, and business KPIs.
4. **Data Validation:** Perform quality checks before reporting.
5. **Business Intelligence:** Create Power BI dashboards for interactive analysis.
6. **Reporting:** Summarise findings and provide business recommendations.

## SQL Analysis & Data Quality Validation

SQL is used to retrieve, analyse, and validate transactional data.

Validation checks include:

- Missing and NULL value detection
- Duplicate transaction identification
- Negative sales validation
- Customer ID validation
- Data consistency checks

**Example: Identify transactions with negative sales**

```sql
SELECT *
FROM orders
WHERE sales < 0;
```

**Example: Monthly revenue and growth analysis**

```sql
WITH monthly_sales AS (
    SELECT
        DATE_TRUNC('month', order_date) AS month,
        SUM(sales) AS revenue
    FROM orders
    GROUP BY 1
)

SELECT
    month,
    revenue,
    LAG(revenue) OVER (ORDER BY month) AS previous_month,
    ROUND(
        (
            (revenue - LAG(revenue) OVER (ORDER BY month))
            / NULLIF(LAG(revenue) OVER (ORDER BY month), 0)
        ) * 100,
        2
    ) AS growth_percentage
FROM monthly_sales;
```

*Note: The date functions may need adjustment depending on the SQL database used.*

## Python & Pandas Analysis

Python and Pandas are used for:

- Data cleaning and preprocessing
- Missing value treatment
- Duplicate record handling
- Date formatting and transformation
- Revenue and profitability calculations
- Category-wise and regional analysis
- Exploratory data analysis

## Power BI Dashboard

The Power BI dashboard is designed to provide a business-focused view of retail performance.

Dashboard sections include:

- Executive Dashboard
- Sales Performance Overview
- Product Category Analysis
- Regional Sales Analysis
- Return and Profitability Analysis

Key dashboard features:

- Interactive KPI cards
- Sales trend monitoring
- Regional drill-down analysis
- Product category filtering
- Revenue and profitability comparisons
- Business performance visualisation

## Key Business Insights

The analysis explores business questions such as:

- Which product categories contribute the most revenue?
- Which regions generate stronger sales and profitability?
- How do discounts affect profit margins?
- What patterns can be observed in product returns?
- Which data quality issues may affect reporting accuracy?

Potential business recommendations include:

- Review excessive discounting in low-margin categories.
- Improve data validation before dashboard reporting.
- Monitor regional and category-level performance.
- Track return-related trends.
- Strengthen KPI-based operational reporting.

## Dataset Information

The repository contains sample e-commerce datasets for demonstration and analysis.

| Dataset | Description |
|---|---|
| `amazon_sale_raw_sample.csv` | Raw sample transaction data |
| `cleaned_ecommerce_sample.csv` | Cleaned dataset used in the analytics workflow |

Refer to `data_dictionary.md` for additional dataset information.

## Future Enhancements

- Automated reporting workflows
- Predictive sales forecasting
- Customer segmentation
- Advanced operational KPI monitoring
- Automated data quality checks
- Enhanced Power BI dashboards
- Python-based reporting automation

## Skills Demonstrated

**SQL | Python | Pandas | Power BI | Data Cleaning | Data Validation | KPI Reporting | Business Intelligence | Revenue Analysis | Operational Analytics | Data Visualization**

## Project Attribution

This repository is maintained as a learning and portfolio project. It is based on an existing project and has been adapted for further learning, exploration, and development.

Original Repository: [Add the original GitHub repository URL here]

Please refer to the original repository's licence and attribution requirements.

---

**Project Focus:** Retail Analytics | Business Intelligence | Operational Reporting | Data Quality

**Author:** Prachi Dhumal
