# Amazon Sales Analysis — Excel Cleaning + Power BI Dashboard

An end-to-end data analysis project on Amazon product data. The dataset was cleaned and feature-engineered in Excel, then analyzed and visualized in Power BI to extract insights about pricing, discounts, ratings, and product demand.

---

## Dataset

**Source:** https://www.kaggle.com/datasets/karkavelrajaj/amazon-sales-dataset

The dataset contains product-level information such as price, discount, ratings, review counts, and product categories.

---

## Project Structure

```
amazon-sales-analysis/
│
├── data/
│   ├── amazon_raw.csv
│   └── amazon_cleaned.xlsx
│
├── powerbi/
│   ├── project.pbix
│   └── screenshots/
│       ├── page1_product_overview.png
│       └── page2_performance_analysis.png
│
└── README.md
```

---

## Part 1 — Excel Data Cleaning

### Raw Data Issues

* Currency symbols present in numeric columns (₹ values)
* Discount values stored as text percentages (e.g., 64%)
* Category hierarchy combined into a single column
* Irrelevant fields adding noise

---

### Cleaning Steps

* Removed currency symbols and converted price columns to numeric
* Converted percentage values into decimal format (64% → 0.64)
* Removed unnecessary columns to reduce noise
* Standardized data types for compatibility with Power BI and SQL

---

### Feature Engineering

| Column                | Logic                                            | Purpose                            |
| --------------------- | ------------------------------------------------ | ---------------------------------- |
| `price_bucket`        | Low / Medium / High                              | Segment products by price          |
| `discount_percentage` | (actual_price - discounted_price) / actual_price | Normalize discount                 |
| `discount_bracket`    | Low / Medium / High                              | Simplify discount comparison       |
| `rating_bucket`       | Good / Average / Poor                            | Group product quality              |
| `popularity_flag`     | rating_count > 10000                             | Identify high-demand products      |
| `value_score`         | rating × rating_count / discounted_price         | Combine value, demand, and quality |

---

### Key Learnings from Cleaning

* Raw data requires transformation before analysis
* Feature engineering significantly improves insight quality
* Bucketing continuous variables improves interpretability
* Median is more reliable than average for skewed data like price

---

## Part 2 — Power BI Dashboard

### Page 1 — Product Overview

**Questions Answered:**

* How are products distributed across price segments?
* How are products distributed by quality?
* Which categories perform best in terms of ratings?
* Which categories have the highest engagement?

**KPIs:**

* Median Rating
* Median Discounted Price
* Total Products

---

### Page 2 — Performance Analysis

**Questions Answered:**

* Do higher discounts improve ratings?
* Do higher discounts increase demand?
* Are popular products better rated?
* Do popular products provide better value?
* What is the relationship between price and rating?

---

## Key Insights

* Majority of products fall into the **Good rating category**, indicating rating inflation or bias
* Medium and High price segments dominate the dataset
* Discounts do not significantly influence product ratings
* Popular products tend to have slightly higher ratings and significantly higher engagement
* Engagement is concentrated in a few categories, especially Electronics
* Price and rating show a weak relationship — higher price does not guarantee better ratings
* High value_score products are typically low-priced with high engagement and good ratings

---

## Conclusion

The analysis demonstrates that discounts influence visibility but not perceived quality. Product performance is more strongly driven by popularity and category. Price alone is not a reliable indicator of product rating or value.

---

## Tools Used

| Tool     | Purpose                                   |
| -------- | ----------------------------------------- |
| Excel    | Data cleaning and feature engineering     |
| Power BI | Data visualization and dashboard creation |

---

## Author

Arnav Heerakar
GitHub: https://github.com/arnav-is-op
LinkedIn: https://www.linkedin.com/in/arnav-is-op
