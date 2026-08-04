# Customer Behavior Data Analytics Project

This repository documents my end-to-end customer behavior analytics project. The project demonstrates how raw retail customer data can be prepared, analyzed, stored in a relational database, and transformed into an interactive business intelligence dashboard.

The workflow combines **Python**, **PostgreSQL**, **SQL**, and **Power BI** to identify customer patterns, purchasing behavior, category performance, subscription trends, and other business-relevant insights.

## Dashboard Preview

![Customer Behavior Dashboard](assets/customer-behavior-dashboard.png)

## Project Overview

The objective of this project is to convert raw customer shopping data into clear and actionable business insights. The analysis covers the complete data workflow:

- Data import and inspection
- Data cleaning and transformation
- Exploratory data analysis
- Feature engineering
- Loading the prepared dataset into PostgreSQL
- SQL-based business analysis
- Power BI dashboard development
- Reporting and presentation of findings

## Business Objectives

This project was designed to answer questions such as:

- How many customers are included in the dataset?
- What is the average purchase amount?
- What is the average customer review rating?
- Which product categories generate the most revenue?
- Which categories have the highest sales volume?
- How does customer behavior differ across age groups?
- What percentage of customers have an active subscription?
- Which products have the highest average review ratings?
- Which products are most frequently purchased within each category?
- How can customers be segmented based on their previous purchases?

## Project Workflow

![Project Workflow](assets/project-workflow.png)

### 1. Data Preparation and Exploratory Analysis with Python

The dataset was imported into a Jupyter Notebook and analyzed using Python and pandas. The main tasks included:

- Inspecting the dataset structure and data types
- Identifying missing values and duplicates
- Standardizing column names
- Filling missing review ratings using category-level median values
- Creating customer age groups
- Converting purchase-frequency labels into approximate day intervals
- Removing unnecessary or redundant columns
- Validating the cleaned dataset before database loading

### 2. PostgreSQL Database Integration

The cleaned DataFrame was loaded into a PostgreSQL database using SQLAlchemy. PostgreSQL was used as the central data source for SQL analysis and Power BI reporting.

Example connection workflow:

```python
from sqlalchemy import create_engine

engine = create_engine(
    "postgresql+psycopg://postgres:YOUR_PASSWORD@localhost:5432/customer_behavior"
)

df.to_sql(
    "customer",
    engine,
    schema="public",
    if_exists="replace",
    index=False
)
```

> Replace `YOUR_PASSWORD` with your PostgreSQL password. Do not publish real credentials in the repository.

### 3. SQL Analysis

SQL queries were used to answer business questions and generate analytical summaries. The analysis included:

- Average purchase amount and review rating
- Revenue and sales by category
- Subscription distribution
- Top-rated products
- Discount usage by product
- Customer segmentation based on previous purchases
- Top products within each category using window functions
- Purchase behavior across customer groups

Example query:

```sql
SELECT
    item_purchased,
    ROUND(AVG(review_rating)::numeric, 2) AS average_rating
FROM customer
GROUP BY item_purchased
ORDER BY average_rating DESC
LIMIT 5;
```

### 4. Power BI Dashboard

The PostgreSQL database was connected directly to Power BI. The dashboard was designed to provide an interactive summary of customer behavior and business performance.

The dashboard includes:

- Total number of customers
- Average purchase amount
- Average review rating
- Subscription-status distribution
- Revenue by category
- Sales by category
- Revenue by age group
- Sales by age group
- Interactive filters for subscription status, gender, category, and shipping type

## Dashboard Highlights

The completed dashboard presents the following headline metrics:

- **3.9K customers**
- **$59.76 average purchase amount**
- **3.75 average review rating**
- Clothing as the leading category by both revenue and sales volume
- A larger share of non-subscribed customers compared with subscribed customers
- Comparable purchasing activity across the defined age groups

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Python | Data preparation, cleaning, transformation, and exploratory analysis |
| pandas | Data manipulation and feature engineering |
| Jupyter Notebook | Interactive Python development environment |
| PostgreSQL | Relational database and SQL analysis |
| pgAdmin 4 | PostgreSQL database administration |
| SQLAlchemy | Python-to-PostgreSQL connection |
| SQL | Business analysis and aggregation |
| Power BI | Interactive dashboard design and visualization |
| GitHub | Project documentation and version control |

## Repository Structure

```text
customer-behavior-project/
│
├── Customer_Shopping_Behavior_Analysis.ipynb
├── customer_behavior_sql_queries.sql
├── customer_behavior_dashboard.pbix
├── customer_shopping_behavior.csv
├── README.md
└── assets/
    ├── customer-behavior-dashboard.png
    └── project-workflow.png
```

## How to Run the Project

### 1. Clone the repository

```bash
git clone YOUR_REPOSITORY_URL
cd YOUR_REPOSITORY_NAME
```

### 2. Open the Jupyter Notebook

Open:

```text
Customer_Shopping_Behavior_Analysis.ipynb
```

Run the notebook cells to import, clean, transform, and validate the dataset.

### 3. Create the PostgreSQL database

Create a PostgreSQL database named:

```text
customer_behavior
```

Then update the database connection credentials in the notebook and load the DataFrame into the `customer` table.

### 4. Run the SQL analysis

Open:

```text
customer_behavior_sql_queries.sql
```

Run the queries in pgAdmin 4 against the `customer_behavior` database.

### 5. Open the Power BI dashboard

Open:

```text
customer_behavior_dashboard.pbix
```

Update the PostgreSQL credentials if required, refresh the data source, and interact with the dashboard filters and visuals.

## Skills Demonstrated

- Data cleaning and preprocessing
- Exploratory data analysis
- Feature engineering
- Relational database integration
- SQL aggregation and filtering
- Common table expressions
- Window functions and ranking
- Customer segmentation
- KPI development
- Dashboard design
- Business insight communication
- End-to-end analytics project documentation

## Project Outcome

This project demonstrates my ability to complete a full analytics workflow, from raw data preparation to database analysis and interactive reporting. It also shows how Python, SQL, PostgreSQL, and Power BI can be integrated to produce a clear and reusable business intelligence solution.

## Notes

- Database passwords and other credentials should not be committed to GitHub.
- Power BI users may need to update the PostgreSQL data-source credentials before refreshing the dashboard.
- File names and folder paths can be adjusted to match the final repository structure.
