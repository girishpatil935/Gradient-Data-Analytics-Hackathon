# Olist E-Commerce Analytics & Business Intelligence Dashboard

An end-to-end data analytics and business intelligence project built on the **Olist Brazilian e-commerce dataset**. The project transforms raw transactional data into a validated, order-level analytical dataset and an interactive **Power BI** management dashboard focused on sales, customers, products, delivery performance, freight, and customer satisfaction.

---

## Project Overview

The objective of this project is to help Olist understand marketplace performance, customer behavior, operational efficiency, and customer experience through data-driven analysis.

The project follows a structured pipeline:

```
Raw E-Commerce Data
        ↓
Data Cleaning & Integration
        ↓
Feature Engineering
        ↓
Order-Level Master Dataset
        ↓
Data Validation
        ↓
Power BI Analysis
        ↓
Business Insights & Recommendations
```

The analysis is designed around a key data-modeling principle:

> **One row in the final master dataset represents one order.**

This prevents one-to-many relationships from products, payments, reviews, and other entities from unintentionally duplicating orders during analysis.

---

## Business Questions

The project focuses on answering key business questions around:

- How is Olist's marketplace performing over time?
- Which product categories generate the highest order volume and value?
- What characteristics distinguish higher-value customers?
- How strong is customer retention and repeat purchasing?
- How does delivery performance relate to customer satisfaction?
- Which categories experience greater freight-cost pressure?
- Where are the key opportunities for operational and customer-experience improvement?

---

## Dataset

The analysis uses the **Olist Brazilian E-Commerce dataset**, containing approximately 100,000 orders and information across multiple business dimensions, including:

- Orders
- Customers
- Products
- Sellers
- Payments
- Reviews
- Geographical information
- Product categories

The analyzed period covers approximately **September 2016 to October 2018**.

> Raw datasets are not included in this repository.

---

## Data Preparation & Feature Engineering

Python and Pandas were used to integrate the source datasets and create the final analytical master.

### Product & Category Features

The order-level dataset includes features such as:

- `item_count`
- `unique_products`
- `unique_sellers`
- `product_category_count`
- `primary_category`
- `product_categories`
- `avg_product_price`
- `min_product_price`
- `max_product_price`
- `avg_product_photos_qty`
- `avg_product_weight_g`
- `avg_product_volume_cm3`
- `has_multiple_categories`

### Spend-Weighted Category Features

Category spending was aggregated at the order level to create:

- `category_identified_spend`
- `category_spend_count`
- `top_spend_category`
- `top_category_spend`
- `top_category_spend_share`
- `category_spend_concentration`

### Customer Features

Customer behavior was analyzed using `customer_unique_id` to represent the actual customer across orders. Features include:

- `customer_order_count`
- `customer_total_spend`
- `customer_avg_order_value`
- `customer_avg_review_score`
- `customer_late_order_rate`
- `customer_avg_delivery_delay`
- `customer_category_diversity`
- `customer_repeat_purchase_indicator`

> Customer-level features were deliberately **not** assigned to records with unknown customer identifiers, avoiding misleading customer analytics.

---

## Data Validation

Before importing the final dataset into Power BI, multiple validation checks were performed.

### Final Master Dataset

| Metric | Result |
|---|---|
| Rows | 99,441 |
| Columns | 51 |
| Unique Order IDs | 99,441 |
| Duplicate Order IDs | 0 |
| One Row per Order | ✅ PASS |
| Unknown Customers with Customer Features | 0 |

Additional validation covered:

- Product count consistency
- Seller count consistency
- Category count consistency
- Category spend consistency
- Spend-share validity
- Multiple-category flags
- Delivery consistency
- Customer feature integrity

The final dataset therefore maintains the intended one-row-per-order analytical structure.

---

## Power BI Dashboard

The validated master dataset was used to build a **six-page interactive Power BI dashboard**.

### 01 — Executive Overview
High-level view of marketplace performance:
- Revenue
- Orders
- Customers
- Average order value
- Revenue trends
- Overall marketplace KPIs

### 02 — Sales & Orders
Purchasing and revenue patterns:
- Order volume
- Revenue by category
- Average order value
- Product/category performance
- Sales trends

### 03 — Customer Intelligence
Customer value and retention:
- Customer spending
- Repeat customers
- Repeat customer rate
- Average customer order value
- Customer behavior
- Category diversity

### 04 — Delivery Intelligence
Operational and logistics performance:
- On-time delivery
- Late delivery
- Delivery delays
- Delivery duration
- Estimated vs. actual delivery
- Operational reliability

### 05 — Product & Freight Intelligence
- Product categories
- Product pricing
- Freight costs
- Product value vs. freight
- Category-level performance
- Customer review performance

### 06 — Reviews & Satisfaction
Customer experience:
- Average review score
- Review performance by category
- Delivery performance vs. reviews
- Customer satisfaction patterns
- Management insights and recommendations

---

## Key Findings

**Marketplace Scale**
The final analytical dataset contains 99,441 orders, representing approximately **R$15.8 million** in order value across the analyzed period.

**Delivery Performance**
Approximately **91.9%** of delivered orders were classified as on time. While overall delivery performance is strong, late orders experienced an average delay of approximately **9.5 days**, making delivery reliability an important operational consideration.

**Category Differences**
Product categories vary considerably in order volume, product pricing, freight costs, and customer review scores — indicating that category-specific operational strategies can provide more targeted opportunities for improvement.

**Customer Retention**
Repeat customers represent a relatively small proportion of the customer base, highlighting an opportunity to strengthen customer retention and encourage additional purchases.

**Freight Cost**
Average freight cost is approximately **R$22.82**, representing a meaningful share of order value and making logistics efficiency an important area for further investigation.

> These findings represent observed patterns in the data. They should not be interpreted as proof of causal relationships.

---

## Business Recommendations

Based on the analysis, three key priorities emerge.

### 1. Improve Delivery Reliability
Identify categories, regions, and operational segments where delivery delays are concentrated. Olist can use these insights to investigate fulfillment and logistics bottlenecks and prioritize operational improvements.

### 2. Manage Freight-Cost Pressure
Investigate categories with higher freight costs and evaluate the potential contribution of:
- Product dimensions and weight
- Seller location
- Customer location
- Logistics distance

This can help identify opportunities to improve shipping efficiency.

### 3. Strengthen Customer Retention
The relatively low repeat-purchase share presents an opportunity to increase customer lifetime value through:
- Post-purchase engagement
- Personalized recommendations
- Category-based campaigns
- Retention initiatives
- Targeted customer offers

---

## Repository Structure

```
Olist-Ecommerce-Analytics/
│
├── Phase1_Olist_Analysis.ipynb
├── Olist_Ecommerce_Dashboard.pbix
└── README.md
```

| File | Description |
|---|---|
| `Phase1_Olist_Analysis.ipynb` | Python/Google Colab notebook containing data preparation, feature engineering, enrichment, and validation |
| `Olist_Ecommerce_Dashboard.pbix` | Interactive Power BI dashboard |
| `README.md` | Project documentation |

---

## Tools & Technologies

**Data Processing**
- Python
- Pandas
- Google Colab

**Business Intelligence**
- Microsoft Power BI
- DAX

**Data Formats**
- CSV
- Excel

---

## How to Reproduce

### Python Analysis
1. Open the notebook in Google Colab.
2. Provide the required Olist source dataset.
3. Run the notebook cells sequentially.
4. Review the enrichment and validation outputs.
5. Export the validated master dataset.

### Power BI
1. Open the `.pbix` file using Power BI Desktop.
2. Review the six dashboard pages.
3. Interact with filters and visuals to explore the analysis.

---

## Analytical Considerations

**One Row Per Order**
The final master dataset deliberately preserves one row per order to avoid duplication during analysis.

**Missing Values**
Missing values were retained where they represented unavailable information rather than automatically replacing them with zero. For example, an order that was not delivered may legitimately lack an actual delivery date.

**Customer Identification**
`customer_unique_id` was used for customer-level and repeat-purchase analysis because it represents the customer across multiple orders.

**Correlation vs. Causation**
The analysis identifies patterns and associations in historical observational data. It does not establish causal relationships.

---

## Project Outcome

This project converts fragmented e-commerce data into a validated analytical foundation and an interactive management dashboard.

The final solution enables stakeholders to move from:

**Data → Analysis → Insights → Business Decisions**

with a focus on:

**Marketplace Performance · Sales · Customers · Delivery · Products · Freight · Satisfaction**

---

## Authors

- Girish Patil
- Prathamesh Chaumwal

**Project:** Olist E-Commerce Analytics & Business Intelligence
**Type:** Data Analytics / Business Intelligence / E-Commerce Analytics
