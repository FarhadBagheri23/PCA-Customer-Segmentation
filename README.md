<<<<<<< HEAD
# Customer Segmentation with PCA & Clustering

Dimensionality reduction and customer segmentation on credit card behavioral data using **Principal Component Analysis (PCA)**, **K-Means**, and **Hierarchical Clustering**.

---

## Overview

This project applies unsupervised machine learning techniques to segment credit card customers based on their spending behavior. The core goal is to evaluate whether reducing feature dimensionality with PCA leads to better and more meaningful customer clusters.

**Key questions answered:**
- How many meaningful customer segments exist in the data?
- Does PCA improve clustering quality?
- Which clustering algorithm performs better after dimensionality reduction?

---

## Dataset

- **Source:** Credit card customer behavioral dataset
- **Records:** ~8,950 customers
- **Features (17):** `BALANCE`, `PURCHASES`, `CASH_ADVANCE`, `CREDIT_LIMIT`, `PAYMENTS`, `MINIMUM_PAYMENTS`, `TENURE`, and more

---

## Project Pipeline

```
Raw Data → Preprocessing → Standardization → PCA → Clustering → Evaluation
```

### 1. Data Preprocessing
- Removed irrelevant columns (e.g., `CUST_ID`)
- Dropped rows with null `CREDIT_LIMIT` (< 0.01% of data)
- Imputed missing `MINIMUM_PAYMENTS` using **median** (chosen over mean via distribution comparison)
- Removed redundant features using a **correlation threshold of 0.8**

### 2. Standardization
- Applied `StandardScaler` (Z-score normalization) before PCA
- Compared `StandardScaler` vs `Normalizer` and justified the choice for PCA

### 3. Principal Component Analysis (PCA)
- Fitted PCA on all components to inspect the explained variance spectrum
- Selected optimal number of components based on the **cumulative explained variance** plot
- Verified **orthogonality** of principal components (zero off-diagonal correlation)

### 4. Clustering

| Algorithm | Applied On | Evaluation |
|---|---|---|
| K-Means | PCA-reduced data | Elbow method (WCSS) + Silhouette Score |
| Hierarchical | PCA-reduced data | Dendrogram + Separation Ratio |

- Used the **Elbow method** (programmatic detection) to find optimal K for K-Means
- Applied **complete linkage** Hierarchical Clustering with dendrogram visualization
- Optimized the dendrogram cut threshold via quantile search for better cluster quality

### 5. Final Evaluation
- Compared clustering results **before and after** threshold optimization
- Metrics used: **Silhouette Score**, **Separation Ratio**, **Cluster Size Balance**

---

## Tech Stack

| Library | Purpose |
|---|---|
| `pandas` | Data loading and manipulation |
| `numpy` | Numerical operations |
| `scikit-learn` | PCA, K-Means, StandardScaler, Silhouette Score |
| `scipy` | Hierarchical clustering, dendrogram |
| `matplotlib` | Plotting |
| `seaborn` | Correlation heatmap, pairplots |

---

## Files

```
├── Clustering-PCA.ipynb     # Main notebook with full analysis
├── data/
│   ├── Mall_customer.csv    # Raw input dataset
│   └── pca_output.csv       # PCA-transformed output
└── README.md
```

---

## Results

- PCA successfully reduced 17 features while retaining the majority of variance
- K-Means on PCA-reduced data produced well-separated, interpretable customer segments
- Hierarchical Clustering improved significantly after optimizing the dendrogram cut threshold
- Clustering quality metrics confirmed that PCA leads to better-defined customer groups

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/FarhadBagheri23/PCA-Customer-Segmentation.git
cd PCA-Customer-Segmentation

# Install dependencies
pip install pandas numpy scikit-learn scipy matplotlib seaborn jupyter

# Launch notebook
jupyter notebook Clustering-PCA.ipynb
```
=======
# PCA-Customer-Segmentation
Dimensionality reduction and customer segmentation using PCA, K-Means, and Hierarchical Clustering on credit card behavioral data. Compares clustering quality before and after PCA with silhouette scores and separation metrics.
>>>>>>> 9c35daf694005cc19bc7364a498875b45d0f14e7
