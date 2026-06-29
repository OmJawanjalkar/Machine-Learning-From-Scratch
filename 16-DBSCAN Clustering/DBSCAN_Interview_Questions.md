# Top 10 DBSCAN Interview Questions with Answers

---

# 1. What is DBSCAN?

### Answer

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) is an **unsupervised machine learning clustering algorithm** that groups together data points that are closely packed (high-density regions) while marking isolated points as **noise (outliers)**.

Unlike K-Means, DBSCAN does **not require the number of clusters (K) to be specified beforehand**.

### Key Points

- Density-based clustering algorithm
- Automatically detects the number of clusters
- Finds clusters of arbitrary shapes
- Identifies outliers automatically

---

# 2. What are the two important parameters in DBSCAN?

### Answer

DBSCAN uses two parameters:

### 1. Epsilon ($$\varepsilon$$)

The maximum distance between two points for them to be considered neighbors.

Mathematically,

$$
N_{\varepsilon}(p)=\{q \mid dist(p,q)\leq \varepsilon\}
$$

where

- $$N_{\varepsilon}(p)$$ = Neighborhood of point $$p$$
- $$\varepsilon$$ = Radius

---

### 2. MinPts

Minimum number of neighboring points required to form a dense region.

If

$$
|N_{\varepsilon}(p)|\geq MinPts
$$

then the point is called a **Core Point**.

---

# 3. What are Core, Border, and Noise points?

### Answer

### Core Point

A point having at least **MinPts** neighbors inside the epsilon radius.

Condition:

$$
|N_{\varepsilon}(p)|\geq MinPts
$$

---

### Border Point

A point having fewer than MinPts neighbors but lies within the neighborhood of a Core Point.

It belongs to the cluster but cannot expand it.

---

### Noise Point

A point that is neither a Core Point nor a Border Point.

It is treated as an **Outlier**.

---

# 4. How does DBSCAN work?

### Answer

The algorithm follows these steps:

1. Pick any unvisited point.
2. Find all neighboring points within $$\varepsilon$$.
3. If neighbors ≥ MinPts, create a new cluster.
4. Expand the cluster by recursively visiting neighboring Core Points.
5. Repeat until all points are visited.
6. Remaining points are labeled as Noise.

---

# 5. Why is DBSCAN called a Density-Based Algorithm?

### Answer

DBSCAN forms clusters based on **point density**.

Instead of calculating cluster centers, it checks whether enough points exist within a specified radius.

If the local density is high, a cluster is formed.

If the density is low, the point is treated as noise.

---

# 6. What are the advantages of DBSCAN?

### Answer

### Advantages

- No need to specify the number of clusters beforehand.
- Automatically detects outliers.
- Can find clusters of arbitrary (non-spherical) shapes.
- Works well when clusters are clearly separated.
- Not sensitive to the choice of initial centroids (because it does not use centroids).

---

# 7. What are the disadvantages of DBSCAN?

### Answer

### Disadvantages

- Choosing the correct $$\varepsilon$$ value is difficult.
- Performance decreases in high-dimensional datasets.
- Cannot handle clusters with significantly different densities.
- Sensitive to parameter selection.

---

# 8. DBSCAN vs K-Means

### Answer

| Feature | DBSCAN | K-Means |
|----------|---------|----------|
| Need K beforehand | ❌ No | ✅ Yes |
| Detects Outliers | ✅ Yes | ❌ No |
| Cluster Shape | Any Shape | Mostly Spherical |
| Uses Centroids | ❌ No | ✅ Yes |
| Handles Noise | ✅ Excellent | ❌ Poor |
| Initialization Required | ❌ No | ✅ Yes |
| Works on Density | ✅ Yes | ❌ No |

---

# 9. What is the Time Complexity of DBSCAN?

### Answer

Without indexing:

$$
O(n^2)
$$

With efficient indexing structures such as **KD-Tree** or **Ball Tree**:

$$
O(n\log n)
$$

where

$$
n
$$

is the number of data points.

---

# 10. When should you use DBSCAN?

### Answer

Use DBSCAN when:

- Number of clusters is unknown.
- Dataset contains outliers.
- Clusters have irregular shapes.
- Automatic noise detection is required.

Avoid DBSCAN when:

- Data has clusters with very different densities.
- Dataset is very high-dimensional.
- Choosing a suitable $$\varepsilon$$ is difficult.

---

# Bonus Interview Questions (Very Frequently Asked)

## 11. Why doesn't DBSCAN require the number of clusters beforehand?

Because it forms clusters based on **density**, not by dividing data into a predefined number of groups.

---

## 12. What distance metrics can DBSCAN use?

DBSCAN is not limited to Euclidean distance.

Common distance metrics include:

- Euclidean Distance
- Manhattan Distance
- Minkowski Distance
- Cosine Distance
- Hamming Distance (for categorical data)

---

## 13. How do you choose the epsilon ($$\varepsilon$$) value?

A common approach is using a **K-Distance Graph**.

1. Compute the distance to the k-th nearest neighbor for every point.
2. Sort these distances.
3. Plot them.
4. Choose the value at the "elbow" (knee) of the curve as $$\varepsilon$$.

---

## 14. Why does DBSCAN perform poorly in high-dimensional data?

As the number of dimensions increases, distances between points become more similar.

This phenomenon is called the **Curse of Dimensionality**, making density estimation less effective and reducing DBSCAN's performance.

---

## 15. What happens if epsilon is chosen incorrectly?

### If epsilon is too small:

- Many points become Noise.
- Clusters become fragmented.

### If epsilon is too large:

- Separate clusters merge into one.
- Outliers may incorrectly join clusters.

Therefore, choosing an appropriate $$\varepsilon$$ is crucial.

---

# Interview Tips

### Remember these five points:

- DBSCAN = Density-Based Clustering.
- Uses two parameters: $$\varepsilon$$ and **MinPts**.
- Three types of points: Core, Border, and Noise.
- Automatically finds the number of clusters.
- Excellent for detecting outliers and irregularly shaped clusters.

---

# One-Line Interview Answer

> **DBSCAN is a density-based clustering algorithm that groups closely packed data points into clusters while labeling isolated points as noise. It does not require the number of clusters in advance and is highly effective for datasets containing outliers and clusters of arbitrary shapes.**