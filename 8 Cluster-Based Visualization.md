📊 Experiment: Cluster-Based Data Visualization using K-Means
🎯 Aim

To perform cluster-based data visualization using the K-Means algorithm and analyze the clustering performance.

⚙️ Procedure

Import required libraries (NumPy, Pandas, Matplotlib, Scikit-learn).
Generate a synthetic dataset using make_blobs.
Convert the dataset into a Pandas DataFrame.
Standardize the data using StandardScaler.
Apply K-Means clustering with a specified number of clusters.
Assign cluster labels to each data point.
Visualize the clusters using a scatter plot.
Analyze clustering performance based on visualization.

import os
os.environ["OMP_NUM_THREADS"] = "2"

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.datasets import make_blobs

# Generate dataset
X, y = make_blobs(n_samples=300, centers=4, random_state=42)

# Create DataFrame
data = pd.DataFrame(X, columns=['Feature1', 'Feature2'])
print(data.head())

# Standardize data
scaler = StandardScaler()
X_scaled = scaler.fit_transform(data)

# Apply K-Means
kmeans = KMeans(n_clusters=4, random_state=42)
kmeans.fit(X_scaled)

# Predict clusters
clusters = kmeans.predict(X_scaled)
data['Cluster'] = clusters

print(data.head())

# Visualization
plt.figure(figsize=(8,6))
plt.scatter(data['Feature1'], data['Feature2'],
            c=data['Cluster'], cmap='viridis')

plt.title("K-Means Clustering Visualization - 7097")
plt.xlabel("Feature1")
plt.ylabel("Feature2")
plt.show()

✅ Result

The dataset was successfully clustered using the K-Means algorithm, and the clusters were visualized using a scatter plot.

The clustering results clearly show distinct groupings, demonstrating the effectiveness of K-Means in identifying patterns within data.
