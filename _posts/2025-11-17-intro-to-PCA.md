
#  Understanding PCA (Principal Component Analysis)

When working with datasets containing many features, we often face **redundant or correlated information**.  
**Principal Component Analysis (PCA)** helps us reduce the number of features while preserving as much **important information (variance)** as possible.

---

##  What Does PCA Do?

PCA transforms the data into a **new coordinate system** where:

- The **first axis (Principal Component 1)** captures the **maximum possible variance** in the data.  
- The **second axis (Principal Component 2)** captures the **next most variance**, **uncorrelated** to the first one.  
- This continues for however many components you choose to keep.

So instead of looking at 100 original features, you might only need 2 or 3 **principal components** that summarize most of the structure of your data.

---

##  Why Keep the Components Uncorrelated?

We want each component to capture **unique** information.  
If two components are correlated, they describe overlapping patterns — that’s redundancy.

By keeping them uncorrelated (orthogonal), PCA ensures:
- Each new axis explains a **distinct source of variation**.  
- There’s **no double-counting of variance**.  
- The transformed data becomes easier to interpret and model.

---

##  How PCA Reduces Dimensionality

1. **Compute the covariance matrix** of features.  
2. **Find eigenvectors (directions)** and **eigenvalues (amount of variance)**.  
3. **Sort** them by descending variance.  
4. **Keep only the top *k*** components that explain, for example, 95% of total variance.  
5. **Project** the data onto these top *k* components — now you have a lower-dimensional version of your dataset.

---

##  Intuitive Example (2D → 1D)

Imagine a dataset with two features — height and weight.  
They’re strongly correlated: tall people usually weigh more.  

PCA finds a **new axis (PC1)** along the line where data varies the most — roughly the “height–weight trend.”  
By projecting points onto this line, you effectively **summarize two features into one** (1D) while keeping most of the information.

---

##  PCA in Action (Python Example)

Let’s see PCA on a real dataset.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.decomposition import PCA
from sklearn.datasets import load_iris

# Load example dataset
data = load_iris()
X = data.data
y = data.target

print("Original shape:", X.shape)  # (150, 4)

# Apply PCA - reduce to 2 dimensions
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X)

print("Reduced shape:", X_pca.shape)  # (150, 2)

# Variance explained by each component
print("Explained variance ratio:", pca.explained_variance_ratio_)

# Plot results
plt.figure(figsize=(8,6))
plt.scatter(X_pca[:,0], X_pca[:,1], c=y, cmap='viridis')
plt.xlabel("Principal Component 1")
plt.ylabel("Principal Component 2")
plt.title("PCA: Iris Dataset (4D → 2D)")
plt.colorbar(label="Target Classes")
plt.show()
