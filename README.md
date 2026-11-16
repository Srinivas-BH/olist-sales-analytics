# 🛒 Olist E-commerce Sales Intelligence
### Data Cleaning • Exploratory Data Analysis • Customer & Revenue Insights

## 📌 Project Overview

The **Olist E-commerce Sales Intelligence** project focuses on analyzing Brazilian e-commerce transactional data to identify meaningful business insights related to sales performance, product categories, customer locations, and delivery operations.

The project uses the Brazilian E-Commerce Public Dataset by Olist to demonstrate an end-to-end data analytics workflow, starting from raw data inspection and cleaning to data integration, validation, exploratory data analysis (EDA), and business insight generation.

The primary objective is to transform raw e-commerce data into structured, reliable information that can help businesses understand sales trends, identify high-performing product categories, analyze regional order distribution, and evaluate delivery performance.

This project is developed using Python and its data analysis libraries, with an emphasis on practical data manipulation, analytical thinking, and business-oriented interpretation.

---

## 🎯 Project Objectives

- Understand the structure and relationships between multiple e-commerce datasets.
- Perform data inspection and identify missing values, duplicate records, and data inconsistencies.
- Clean and transform raw datasets to improve data quality.
- Integrate multiple datasets using appropriate relational joins.
- Validate data integrity and ensure that joins do not introduce unintended row duplication.
- Analyze monthly item sales performance.
- Identify the top-performing product categories based on item sales value.
- Examine the geographical distribution of orders across Brazilian states.
- Evaluate delivery duration and identify unusually long delivery times.
- Measure the proportion of delivered orders arriving later than their estimated delivery dates.
- Generate data-driven findings and translate them into meaningful business recommendations.

---

## 📂 Dataset Description

**Dataset:** Brazilian E-Commerce Public Dataset by Olist

The dataset contains information about orders, customers, products, sellers, payments, reviews, and delivery operations from an online marketplace in Brazil.

For this project, the following four primary datasets were used:

| Dataset | Description |
|---|---|
| `olist_orders_dataset.csv` | Order details, order status, purchase timestamps, and delivery timestamps. |
| `olist_order_items_dataset.csv` | Individual items purchased within each order, including product, seller, price, and freight information. |
| `olist_products_dataset.csv` | Product details and product category information. |
| `olist_customers_dataset.csv` | Customer identifiers and geographical information, including city and state. |

### Dataset Characteristics

| Dataset | Rows | Columns |
|---|---:|---:|
| Orders | 99,441 | 8 |
| Order Items | 112,650 | 7 |
| Products | 32,951 | 9 |
| Customers | 99,441 | 5 |

**Important:** The order items dataset operates at the order-item level. A single order can contain multiple items, so `order_id` is not unique in this table. The combination of `order_id` and `order_item_id` represents an individual order-item record.

**Dataset Source:** [Brazilian E-Commerce Public Dataset by Olist – Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

---

## 🛠️ Technologies and Tools

| Technology | Application |
|---|---|
| Python | Core programming and data analysis |
| Pandas | Data manipulation, cleaning, transformation, and aggregation |
| NumPy | Numerical operations and data processing |
| Matplotlib | Data visualization |
| Seaborn | Statistical and exploratory visualizations |
| JupyterLab | Interactive development and analysis environment |
| Git & GitHub | Version control and project management |

---

## ⚙️ Project Workflow

The project follows a structured workflow to ensure data quality, analytical accuracy, and reproducibility.

### Stage A: Environment Setup and Data Loading

- Created a dedicated Conda environment for the project.
- Installed and configured the required Python libraries.
- Organized the project directory.
- Loaded the four primary CSV datasets using Pandas.
- Examined dataset dimensions, column names, and data types.

### Stage B: Initial Data Inspection

- Inspected dataset structures using `.head()`, `.info()`, and `.describe()`.
- Identified missing values using `.isnull()` and `.isna()`.
- Examined order status distributions.
- Checked for duplicate records.
- Investigated the relationship between orders and order items.
- Identified the appropriate data grain for analysis.

### Stage C: Data Cleaning and Preprocessing

- Converted relevant timestamp columns into Pandas datetime format.
- Investigated missing values in delivery-related timestamps.
- Examined numerical fields such as product prices and freight values.
- Checked product category consistency.
- Investigated timestamp inconsistencies, including delivery dates preceding carrier handoff dates.
- Created clean working copies while preserving the original raw datasets.

### Stage D: Data Integration and Feature Creation

Integrated the datasets using relational joins:

1. Order items with product information.
2. Integrated item-product data with order information.
3. Integrated the resulting dataset with customer information.

Used left joins and merge validation to preserve the order-item grain and prevent unintended row multiplication.

Created additional analytical columns:

- `order_month` – Extracted the purchase month from the order purchase timestamp.
- `item_revenue` – Represents the product item price, excluding freight.
- `item_plus_freight` – Represents item price combined with freight value.

### Stage E: Data Validation

- Verified row counts before and after dataset integration.
- Checked for missing values in important identifier columns.
- Validated unique keys in the products, orders, and customers datasets.
- Examined repeated identifiers in the integrated order-item dataset.
- Verified calculations for item price and freight.
- Aggregated item-level sales values at the order level to validate analytical calculations.

### Stage F: Delivery Performance Analysis and Filtering

- Selected delivered orders with valid customer delivery timestamps.
- Calculated delivery duration in days.
- Created a `late_delivery` indicator by comparing actual delivery dates with estimated
