# Mahalanobis Distance Difference in Platform Exploration

```python
# Outlier detection using Mahalanobis distance
from scipy.stats import chi2
X = np.array([[10, 10], [12, 12], [11, 11], [14, 14], [100, 100], [14, 14]])
# Calculate mean and covariance matrix

mean = np.mean(X, axis=0)
cov_matrix = np.cov(X.T)
inv_cov_matrix = np.linalg.inv(cov_matrix)
mahalanobis_distances = np.array([np.dot(np.dot((x - mean), inv_cov_matrix), (x - mean).T) for x in X])
critical_value = chi2.ppf((1-0.1), df=2)  # df is the number of dimensions
outliers = np.where(mahalanobis_distances > critical_value)

```

| Environment | Distance | BLAS Backend (Pending confirmation) |
|---|---|---|
| Apple conda (m4) | 5.227 | Accelerate (Apple) |
| Intel mac uv | 4.572 | OpenBLAS or MKL |
| Bootcamp WSL | 2.614 | OpenBLAS |
| Intel mac miniconda container | 2.614 | OpenBLAS |

