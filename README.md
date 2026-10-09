# E-commerce Customer Analytics & Segmentation

A real-world e-commerce analytics project using anonymized order data from an e-commerce business.

## Project Objective

The project investigates:

> **What characteristics distinguish repeat and high-value customers from one-time customers?**

The analysis combines exploratory data analysis (EDA), RFM analysis, and K-Means clustering to identify meaningful customer segments and translate them into business insights.

## Dataset & Privacy

The original business order export contained customer and order information. For privacy, personally identifiable information (PII) was removed/anonymized before analysis.

The raw customer-level dataset is **not included in this public repository**.

The repository contains aggregate results, visualizations, and the analysis notebook structure needed to understand the methodology.

## Project Workflow

1. Data cleaning and validation
2. Exploratory Data Analysis
3. Revenue and channel analysis
4. Customer-level RFM analysis
5. Log transformation and feature scaling
6. K-Means clustering
7. Elbow and silhouette analysis
8. Customer segment profiling
9. Business recommendations

## Key Metrics

The validated working dataset contained:

- **905** reliable order-line records
- **624** unique orders
- **561** unique customers
- **₹14.18 lakh** total revenue
- **₹2,271.89** average order value
- **10.3%** repeat-customer rate

Because the source was extracted from a PDF export, some records were excluded where fields could not be reliably interpreted. No values were invented to fill those gaps.

## RFM Methodology

For every customer:

- **Recency:** days since the customer's latest purchase
- **Frequency:** number of unique orders
- **Monetary:** total revenue generated

The RFM variables were log-transformed and standardized before clustering.

## Clustering

K-Means was evaluated across multiple values of `k` using silhouette scores.

A six-cluster solution was selected for the final business segmentation because it provided a strong clustering score while producing a useful level of business interpretability. The analysis also showed that some alternative values of `k` had comparable or slightly higher scores, so the choice of six clusters is treated as a practical segmentation decision rather than a claim that six is mathematically unique.

## Final Customer Segments

| Segment | Customers | Avg. Orders | Avg. Spending |
|---|---:|---:|---:|
| High-value one-time | 73 | 1.00 | ₹11,533.67 |
| Repeat purchasers | 56 | 2.13 | ₹3,745.98 |
| Recent potential | 150 | 1.00 | ₹865.47 |
| Very recent | 45 | 1.02 | ₹2,579.18 |
| Older low-value | 149 | 1.00 | ₹778.63 |
| Minimal-value | 88 | 1.01 | ₹45.75 |

## Main Business Insight

The most important finding is that a relatively small group of **73 high-value one-time customers generated about 59% of total revenue** in the analyzed data.

This suggests an important retention opportunity: customers who make a high-value first purchase could be targeted for repeat-purchase and retention campaigns.

The **56 repeat purchasers** form another strategically important group because they demonstrate existing repeat-buying behaviour.

## Recommended Business Actions

### 1. High-value one-time customers
- Post-purchase follow-up
- Cross-sell complementary products
- Personalized repeat-purchase offers

### 2. Repeat purchasers
- Loyalty/rewards program
- Early access to products
- Referral incentives

### 3. Recent potential customers
- Second-purchase campaign
- Product recommendations
- Reminder/retargeting campaigns

### 4. Older low-value customers
- Low-cost reactivation campaigns
- Carefully controlled discounts

### 5. Minimal-value customers
- Avoid excessive acquisition/retention spending
- Focus on low-cost automated communication

## Limitations

- The source data was available as a PDF rather than a clean database/CSV export.
- Some PDF rows were malformed or incomplete and were excluded from reliable analysis.
- The observation period is relatively short, so long-term customer lifetime behaviour cannot be inferred.
- Customer segments describe observed purchasing behaviour; they do not prove why customers behave that way.
- The cluster labels are business interpretations, not supervised classes.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- RFM Analysis
- K-Means Clustering
- Data Visualization
- Exploratory Data Analysis

## Repository Structure

```text
e-commerce-customer-analytics/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── 01_customer_analytics.ipynb
├── data/
│   └── README.md
├── results/
│   ├── 01_monthly_revenue.png
│   ├── 02_channel_revenue.png
│   ├── 03_order_status.png
│   ├── 04_elbow_curve.png
│   ├── 05_silhouette_scores.png
│   ├── 06_customer_segments.png
│   ├── 07_cluster_revenue_share.png
│   ├── project1_eda_summary.csv
│   ├── monthly_performance.csv
│   ├── channel_performance.csv
│   ├── payment_performance.csv
│   ├── rfm_cluster_profiles.csv
│   └── rfm_k_selection.csv
└── docs/
    └── project_summary.md
```

## Author

**Meenaz Khan**

BCA | Python | Data Analytics | Machine Learning

GitHub: `meenazashrafkhan-cpu`
