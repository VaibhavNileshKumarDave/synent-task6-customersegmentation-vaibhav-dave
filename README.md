# Task 6 — Customer Segmentation
### Synent Technologies Data Analyst Internship

---

## Problem Statement

Businesses that treat all customers the same waste marketing budget and miss revenue opportunities. This project applies unsupervised machine learning (K-Means Clustering) to mall customer data to automatically group customers into distinct behavioral segments based on their income and spending patterns — enabling targeted, data-driven marketing strategies for each segment.

---

## Dataset Details

| Property | Value |
|---|---|
| File | `Mall_Customers.csv` |
| Source | Kaggle — Mall Customer Segmentation Data |
| Source Link  | https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python |
| Rows | 200 |
| Columns | 5 |

**Columns:**

| Column | Description |
|---|---|
| `CustomerID` | Unique customer identifier |
| `Gender` | Male / Female |
| `Age` | Customer age in years |
| `Annual Income (k$)` | Annual income in thousands of USD |
| `Spending Score (1-100)` | Mall-assigned score based on spending behavior |

This is a clean dataset with **no missing values and no duplicate rows**, requiring minimal preprocessing before modeling.

---

## Approach

```
1. Setup            →  Import libraries, load CSV
2. Preprocessing    →  Check nulls/duplicates, encode Gender,
                       rename columns, apply StandardScaler
3. Elbow Method     →  Run KMeans for K=1 to 10 on scaled features,
                       plot WCSS to find optimal K
4. KMeans Modeling  →  Fit KMeans with K=5, predict cluster labels,
                       verify assignments from cluster centroids
5. Visualization    →  Scatter plots and cluster size bar chart
6. Insights         →  Business interpretation per chart
```

**Libraries used:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`

**Why StandardScaler?**
KMeans is a distance-based algorithm. `Annual Income` ranges from 15–137k while `Spending Score` ranges from 1–100 — without scaling, income dominates the distance calculation and biases the clusters. StandardScaler brings both features to the same scale before fitting.

---

## Key Results

### Optimal Clusters — Elbow Method
The WCSS curve shows a clear elbow at **K = 5**, meaning 5 clusters best balance model simplicity and variance explanation. Adding more clusters beyond 5 gives diminishing returns.

### Customer Segments Identified

| Cluster | Segment Name | Income | Spending | Strategy |
|---|---|---|---|---|
| 0 | Standard Customers | Mid | Mid | Retention — bundle deals, loyalty points |
| 1 | Premium Customers | High | High | VIP programs, exclusive branding |
| 2 | Impulsive Buyers | Low | High | Flash sales, limited-time offers, social media |
| 3 | Conservative Savers | High | Low | Value messaging, practical utility focus |
| 4 | Budget Conscious | Low | Low | Discounts, budget-friendly product lines |

### Key Findings

**Age is the biggest spending barrier** — no customer above age 40 has a spending score above 60, regardless of income level. All premium marketing efforts should target the 18–39 age bracket.

**Two completely different high-value strategies** — Premium Customers (high income, high spend) need VIP loyalty programs, while Impulsive Buyers (low income, high spend) respond to FOMO-driven campaigns like flash sales and social media promotions. These are opposite personas requiring opposite approaches.

**Standard Customers are the volume backbone** — Cluster 0 is the largest segment with 80+ customers. While not the most exciting segment, they form the foundation of baseline revenue and need consistent retention strategies to prevent churn.

**Conservative Savers are an untapped opportunity** — high income but low spending means they have the capacity to spend more. The right value-focused messaging and trust-building campaigns could convert them into Premium Customers over time.

---

## Visualizations

| Chart | File | Purpose |
|---|---|---|
| Elbow Method | `outputs/elbow_method.png` | Determining optimal number of clusters |
| Income vs Spending (colored by cluster) | `outputs/customer_segmentation.png` | Primary segmentation view |
| Age vs Spending (colored by cluster) | `outputs/age_vs_spending.png` | Age-based spending behavior |
| Cluster Size Bar Chart | `outputs/customer_distribution_by_cluster.png` | Customer volume per segment |

---

## Repository Structure

```
synent-task6-customersegmentation-vaibhav-dave/
│
├── data/
│   └── Mall_Customers.csv
│
├── notebooks/
│   └── Mall_Customers.ipynb
│
├── outputs/
│   ├── elbow_method.png
│   ├── customer_segmentation.png
│   ├── age_vs_spending.png
│   └── customer_distribution_by_cluster.png
│
└── README.md
```

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/VaibhavNileshKumarDave/synent-task6-customersegmentation-vaibhav-dave

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

# 3. Place dataset in the data/ folder
Dataset: https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python

# 4. Open the notebook
jupyter notebook notebooks/customer_segmentation.ipynb
```

---

## Author

**Vaibhav** — Data Analyst Intern, Synent Technologies
B.Tech Computer Engineering, LDRP-ITR, Gandhinagar (2027)
Internship Submission — June 2026
