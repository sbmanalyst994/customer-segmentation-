# Customer Segmentation with K-Means

This repository contains an exploratory data analysis and clustering project on the **Mall Customers** dataset, using **K-Means** clustering to segment customers based on their **Annual Income** and **Spending Score**.

The main goal is to identify meaningful customer segments (personas) that a mall or retail business can target with tailored marketing and product strategies.

---

## AUTHOR
- **NAME:** AJEBORIOGBON SAMUEL A.
- **EMAIL:** samuelajeboriogbon@student.oauife.edu.ng
- **TASK:** Powered by TS Academy

---

## Project Structure

- `Customer Segmentation with K-Means.pdf`  
  Full report / notebook export showing:
  - Data loading and cleaning
  - Exploratory Data Analysis (EDA)
  - K-Means clustering
  - Elbow and Silhouette analyses
  - Cluster interpretation and customer personas

- (Optional files you might have)
  - `Mall_Customers.csv` – Dataset used in the analysis
  - `Customer Segmentation with K-Means.ipynb` - Jupyter notebook version of the analysis 

---

## Dataset Description

The project uses the **Mall Customers** dataset. Each row represents a customer with the following columns:

- `CustomerID` – Unique customer identifier  
- `Gender` – Male / Female  
- `Age` – Age of the customer  
- `Annual Income (k$)` – Annual income in thousand dollars  
- `Spending Score (1-100)` – Score assigned by the mall based on customer behavior and spending nature

The segmentation focuses on:

- **Annual Income (k$)**
- **Spending Score (1–100)**

These features allow us to understand how much customers earn and how much they tend to spend.

---

## Objective

> **Perform customer segmentation using K-Means clustering** to group mall customers based on **Annual Income** and **Spending Score**.

Key questions addressed:

1. Can we identify distinct customer groups based on income and spending behavior?
2. What are the characteristics of each cluster?
3. How can these clusters be interpreted as **customer personas** that are useful for business decisions?

---

## Methodology Overview

The analysis *(documented in `Customer Segmentation with K-Means.pdf`)* follows these main steps:

### 1. Data Loading & Initial Checks

- Load the dataset into a pandas DataFrame.
- Inspect:
  - Shape and first few rows
  - Data types of each column
  - Missing values and basic statistics

*(See examples and summary tables on **pages 1–2** of the PDF.)*

### 2. Exploratory Data Analysis (EDA)

Key EDA steps include:

- Descriptive statistics for:
  - Age
  - Annual Income
  - Spending Score

- Distribution plots for:
  - Age
  - Annual Income (k$)
  - Spending Score (1–100)

  These histograms highlight:
  - Age is approximately normally distributed.
  - Annual income is slightly right-skewed with a concentration in the 30–35 k$ range.
  - Spending scores are relatively uniform with a slight skew.

- Scatter plots:
  - **Age vs Spending Score**
  - **Gender vs Spending Score**
  - **Annual Income vs Spending Score**

  These appear on **pages 3–5** and help visually spot emerging groups and patterns.

### 3. Feature Selection

For clustering, two features are used:

- `Annual Income (k$)`
- `Spending Score (1-100)`

These are combined into a `features` array for the K-Means algorithm.

### 4. Determining Optimal Number of Clusters

Two methods are applied:

#### a. Elbow Method

- K-Means is run for a range of cluster numbers (e.g., k = 1 to 10).
- For each k, the **inertia** (Within-Cluster Sum of Squares, WCSS) is calculated.
- The **Elbow Plot** (see **page 6**) shows where the rate of decrease in inertia changes noticeably.
- The “elbow” is observed around **k = 5**, suggesting that 5 clusters is a good choice.

#### b. Silhouette Score

- For each k, the **Silhouette Score** is calculated to measure how well-separated the clusters are.
- Scores are plotted vs. number of clusters (see **page 7**).
- The maximum silhouette score is observed at **k = 5**, reinforcing the choice from the Elbow Method.

> Conclusion: **5 clusters** provide a good balance between compactness and separation.

### 5. Building the Final K-Means Model

- K-Means is initialized with:
  - `n_clusters = 5`
  - `random_state` (for reproducibility)
- The model is fit on the selected features.
- Cluster labels (0–4) are assigned to each customer and added as a new column, `Cluster`, in the DataFrame.

Examples of output tables and label distributions are shown on **pages 7–8**.

### 6. Cluster Analysis

After clustering, we:

- Compute the number of customers per cluster.
- Calculate average values of:
  - Annual Income
  - Spending Score
  for each cluster (see the summary table on **page 8**).

Bar charts and plots on **pages 8–9** visualize how each cluster differs in terms of average income and spending.

---

## Customer Personas (Cluster Profiles)

Based on the cluster centroids and EDA, five main customer segments are identified. In the PDF (see **page 9**) they are interpreted as:

1. **Cluster 0 – The Cautious Mid-Level Group**
   - Medium income, medium spending.
   - Represents the “average” or balanced mall visitor profile.

2. **Cluster 1 – The Cautious / Low Spenders**
   - Lower to medium income, lower spending.
   - Price-sensitive, potentially conservative spenders.

3. **Cluster 2 – The Savers (High Income, Low Spending)**
   - High income, low spending.
   - Financially capable but spend cautiously; may focus on savings or investments.

4. **Cluster 3 – The Enthusiasts (Low Income, High Spending)**
   - Lower income, high spending.
   - Likely young, lifestyle-driven shoppers who spend a significant portion of income.

5. **Cluster 4 – The Big Spenders (High Income, High Spending)**
   - High income, high spending.
   - Prime target for premium services, loyalty programs, and personalized offers.

Demographic breakdowns by **age** for each cluster are further explored on **pages 9–11**, highlighting age distributions and helping refine each persona.

---

## 🛠️ Technologies Used

- **Python**
  - `pandas` – Data manipulation and analysis
  - `numpy` – Numerical operations
  - `matplotlib`, `seaborn` – Data visualization
  - `scikit-learn` – K-Means clustering, metrics (Elbow & Silhouette)

