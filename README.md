# FLO Customer Segmentation with Unsupervised Learning

## Overview

This project focuses on segmenting FLO customers based on their historical shopping behavior using unsupervised learning techniques.

The main objective is to move beyond raw transactional data and create meaningful, interpretable customer groups that can be directly used in marketing and business decision-making.

Two clustering approaches are applied:

- K-Means Clustering  
- Hierarchical Clustering  

The emphasis of the project is not only on clustering performance but also on producing **actionable and business-relevant segments**.

---

## Dataset

The dataset contains customer transaction data from FLO, covering purchases made in 2020–2021 across both online and offline channels.

- **Observations:** 19,945  
- **Variables:** 12  

### Key Variables

- `order_num_total_ever_online` / `offline`: Purchase frequency  
- `customer_value_total_ever_online` / `offline`: Monetary value  
- `first_order_date` / `last_order_date`: Customer lifecycle  
- `interested_in_categories_12`: Product category engagement  

---

## Feature Engineering

To better represent customer behavior, several additional features were created:

- **Recency** → Days since last purchase  
- **Tenure** → Customer lifetime  
- **Total Order Count** → Overall purchase frequency  
- **Total Customer Value** → Total spending  
- **Average Order Value** → Spending per transaction  

These features provide a more complete behavioral representation compared to raw variables.

---

## Data Preparation

Customer-related variables showed significant right-skewness, especially monetary features.

### Before Transformation

![Before](outputs/before_transform.png)

- Strong right skew is visible  
- A small number of customers dominate spending  
- Raw data is not suitable for distance-based clustering  

---

### After Log Transformation

![After](outputs/after_transform.png)

- Distributions become more symmetric  
- Extreme values are compressed  
- Data becomes more suitable for clustering  

---

## Clustering Strategy

### Elbow Method

![Elbow](outputs/elbow_method.png)

- WCSS decreases rapidly until **k ≈ 6–7**  
- After that point, improvement slows down  
- This indicates diminishing returns in adding more clusters  

---

### Silhouette Score

- Highest score observed at **k=2**  
- However, this creates overly broad and non-actionable segments  

---

### Final Decision

Instead of relying purely on mathematical metrics:

> **k = 7 was selected to balance model performance and business interpretability**

This allows:

- More granular segmentation  
- Better marketing usability  
- More realistic customer grouping  

---

## K-Means Segmentation Results

The final segmentation reveals clear behavioral differences across customer groups.

### High Value Customers
- Highest total spending and purchase frequency  
- Represent the core revenue-driving segment  
- **Strategy:** loyalty programs, VIP campaigns, premium offers  

---

### Loyal Customers
- Consistent purchasing behavior across channels  
- High engagement over time  
- **Strategy:** personalized recommendations, retention campaigns  

---

### High Basket Customers
- High average order value but lower frequency  
- Spend more per transaction  
- **Strategy:** increase purchase frequency (reminders, promotions)  

---

### Mid Value Customers
- Moderate frequency and spending  
- Growth potential exists  
- **Strategy:** cross-sell and basket expansion  

---

### New Customers
- Low tenure and lower frequency  
- Early stage in lifecycle  
- **Strategy:** onboarding and engagement campaigns  

---

### Low Value Customers
- Low spending and low engagement  
- Limited short-term ROI  
- **Strategy:** low-cost reactivation campaigns  

---

## Hierarchical Clustering

![Dendrogram](outputs/hierarchical_dendrogram.png)

- Dendrogram confirms natural grouping structure  
- Supports the segmentation tendency observed in K-Means  
- Provides additional validation of cluster formation  

---

## Model Comparison

- **K-Means** → clearer, more scalable, easier to interpret  
- **Hierarchical Clustering** → useful for structural validation  

K-Means is selected as the primary model due to its practicality in real-world applications.

---

## Key Takeaway

Customer segmentation should not rely solely on statistical metrics.

While methods like Silhouette Score provide guidance,  
the final decision must also consider:

- Interpretability  
- Business usability  
- Actionability  

---

## Technologies Used

- Python  
- Pandas  
- NumPy  
- Matplotlib & Seaborn  
- SciPy  
- Scikit-learn  

---

## How to Run

```bash
pip install -r requirements.txt
