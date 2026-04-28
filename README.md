# FLO Customer Segmentation with Unsupervised Learning

## Overview

This project focuses on customer segmentation for FLO, an omnichannel retail company.  
The objective is to identify distinct customer groups based on historical shopping behavior and support more targeted, data-driven marketing strategies.

Two unsupervised learning approaches are used:

- K-Means Clustering  
- Hierarchical Clustering  

The emphasis is not only on building clustering models, but also on producing segments that are interpretable and actionable from a business perspective.

---

## Dataset

The dataset contains historical transaction data of FLO customers who made purchases in 2020–2021 across both online and offline channels.

- **Observations:** 19,945  
- **Variables:** 12  

### Key Variables

- `master_id`: Unique customer identifier  
- `order_channel`: Platform used for shopping  
- `first_order_date` / `last_order_date`: Customer lifecycle information  
- `order_num_total_ever_online` / `offline`: Purchase frequency  
- `customer_value_total_ever_online` / `offline`: Monetary value  
- `interested_in_categories_12`: Product category engagement  

---

## Feature Engineering

To better represent customer behavior, additional features were created:

- **Recency:** Days since last purchase  
- **Tenure:** Customer lifetime (days)  
- **Total Order Count:** Online + offline frequency  
- **Total Customer Value:** Combined spending  
- **Average Order Value:** Spending per transaction  

These features provide a more complete view of customer engagement and value.

---

## Methodology

### 1. Data Preprocessing

- Date variables converted to datetime format  
- Skewness analyzed for all numerical features  
- Log transformation applied to reduce right-skewness  
- Features standardized using `StandardScaler`  

---

### 2. K-Means Clustering

- Elbow Method used to evaluate WCSS across different cluster sizes  
- Silhouette Score used as an additional validation metric  

Although **k=2** produced the highest silhouette score, it resulted in overly broad customer groups.  
To achieve more granular and actionable segmentation, **k=7** was selected by considering:

- Elbow curve behavior  
- Silhouette scores  
- Business interpretability  

---

### 3. Hierarchical Clustering

- Ward linkage applied to minimize within-cluster variance  
- Dendrogram used to analyze cluster structure  
- Results compared with K-Means to validate segmentation consistency  

---

## Visualizations

### Distribution Before Transformation
![Before](outputs/before_transform.png)

### Distribution After Transformation
![After](outputs/after_transform.png)

### Elbow Method
![Elbow](outputs/elbow_method.png)

### Hierarchical Clustering Dendrogram
![Dendrogram](outputs/hierarchical_dendrogram.png)

---

## Key Insights

- **High Value Customers:**  
  High purchase frequency and spending → suitable for loyalty programs and premium campaigns  

- **Loyal Customers:**  
  Consistent engagement across channels → ideal for personalized recommendations  

- **High Basket Customers:**  
  Higher spending per transaction but lower frequency → potential for frequency-based campaigns  

- **Low Value Customers:**  
  Low engagement and spending → require cautious, cost-effective reactivation strategies  

- **New / Potential Customers:**  
  Lower tenure but growth potential → onboarding and engagement campaigns recommended  

---

## Model Comparison

K-Means produced clearer and more interpretable segments, making it more suitable for practical business applications.

Hierarchical Clustering supported the analysis by revealing the underlying structure and confirming segmentation tendencies.

---

## Key Takeaway

Customer segmentation should not rely solely on statistical metrics.

While metrics like Silhouette Score provide guidance, selecting the optimal number of clusters also requires considering interpretability and business usability.

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

Install dependencies:

```bash
pip install -r requirements.txt