# Amazon Sales Analysis — Excel Cleaning + Power BI Dashboard

End-to-end data analysis of Amazon product listings. Data preprocessing and feature engineering were performed in Excel, followed by analytical modeling and visualization in Power BI to evaluate pricing behavior, discount strategies, product quality, and demand patterns.

---

## Dataset

**Source:**  
https://www.kaggle.com/datasets/karkavelrajaj/amazon-sales-dataset  

Contains product-level attributes including pricing, discounts, ratings, review counts, and categorical hierarchies.

---

## Project Structure
 
```
amazon-sales-analysis/
│
├── data/
│   ├── amazon_raw.csv            ← Original Kaggle dataset (unmodified)
│   └── amazon_cleaned.xlsx       ← Cleaned and feature-engineered dataset
│
├── powerbi/
│   ├── project.pbix              ← Power BI report file
│   └── screenshots/
│       ├── page1_product_overview.png
│       └── page2_performance_analysis.png
│
└── README.md
```
 
---

---


---

## Part 1 — Excel Data Cleaning

### Raw Data Issues

- Currency symbols embedded in numeric columns (₹)
- Discount values stored as string percentages (e.g., "64%")
- Hierarchical category data compressed into a single column
- Presence of irrelevant or redundant fields
- Inconsistent data types affecting downstream analysis

---

### Cleaning Operations

- Stripped currency symbols and converted price fields to numeric format
- Transformed percentage strings into decimal representation (`64% → 0.64`)
- Removed non-informative columns to reduce dimensional noise
- Standardized data types for compatibility with Power BI and analytical workflows
- Ensured consistency across all numeric and categorical fields

---

### Feature Engineering

| Column                | Logic                                            | Purpose                                      |
|---------------------|--------------------------------------------------|----------------------------------------------|
| `price_bucket`       | Low / Medium / High                              | Segment products by pricing tiers            |
| `discount_percentage`| (actual_price - discounted_price) / actual_price | Normalize discount magnitude                 |
| `discount_bracket`   | Low / Medium / High                              | Enable categorical comparison of discounts   |
| `rating_bucket`      | Good / Average / Poor                            | Group product quality levels                 |
| `popularity_flag`    | rating_count > 10000                             | Identify high-engagement products            |
| `value_score`        | (rating × rating_count) / discounted_price       | Composite metric: quality × demand ÷ price   |

---

## Excel Output Preview

![Excel Cleaned Data](images/excel_cleaned_preview.png)

---

## Part 2 — Power BI Dashboard

### Page 1 — Product Overview

![Product Overview Dashboard](images/dashboard_product_overview.png)

**Analytical Focus:**

- Distribution of products across price segments
- Distribution across rating categories
- Category-level performance in ratings
- Category-level engagement (rating counts)

**Key Metrics:**

- Median Rating  
- Median Discounted Price  
- Total Product Count  

---

### Page 2 — Performance Analysis

![Performance Analysis Dashboard](images/dashboard_performance_analysis.png)

**Analytical Focus:**

- Relationship between discount magnitude and ratings
- Impact of discounts on demand (rating_count)
- Comparison of popular vs non-popular products
- Relationship between price and perceived quality
- Evaluation of composite value (`value_score`)

---

## Key Insights

- Rating distribution is heavily skewed toward the “Good” category, indicating possible rating inflation
- Mid and high-priced products dominate the dataset composition
- Discount magnitude shows negligible correlation with product ratings
- High-engagement products exhibit marginally higher ratings but disproportionately higher visibility
- Engagement is concentrated within specific categories, primarily Electronics
- Price does not exhibit strong predictive power for rating quality
- High `value_score` products are typically low-cost, high-engagement, and well-rated

---

## Conclusion

Discounting impacts visibility but does not materially influence perceived product quality. Product performance is primarily driven by category dynamics and user engagement rather than pricing. Value emerges from the interaction of demand, rating, and affordability—not price alone.

---

## Tools Used

| Tool     | Role                                           |
|----------|-----------------------------------------------|
| Excel    | Data cleaning, transformation, feature creation |
| Power BI | Data modeling, visualization, dashboarding     |

---

## Notes

### Excel Reference Notes

https://colab.research.google.com/drive/1ulSG0WTP4DlBuCfiNp8EQBUkVLn-budP#scrollTo=9R2K9sNJ8tL8

---

## Author

Arnav Heerakar
