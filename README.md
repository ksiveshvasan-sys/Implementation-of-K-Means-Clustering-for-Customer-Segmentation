# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Read the CSV dataset and display the dataset details such as first five rows, shape, and column names.
2. Select the features Annual Income and Spending Score for customer segmentation and get the number of clusters K.
3. Create and train the K-Means model using the selected features.
4. Assign each customer to a cluster and display the cluster centers and customer segmentation results.
5. Plot the clusters along with their cluster centers using a scatter plot.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Sivesh vasan K
RegisterNumber: 212225060268
*/
```
```
# AIM:
# To write a program to implement K-Means Clustering
# for Customer Segmentation.

import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

# Get CSV file name
file_name = input("Enter the CSV file name: ")

# Read CSV file
data = pd.read_csv(file_name)

# Display first 5 rows
print("\nFirst 5 rows of the dataset:")
print(data.head())

# Display dataset shape
print("\nDataset Shape:")
print(data.shape)

# Display column names
print("\nColumn Names:")
print(data.columns)

# Select features for customer segmentation
X = data[['Annual Income (k$)', 'Spending Score (1-100)']]

# Get number of clusters
k = int(input("\nEnter the number of clusters: "))

# Create K-Means model
kmeans = KMeans(n_clusters=k, random_state=42, n_init=10)

# Train the model
kmeans.fit(X)

# Add cluster number to dataset
data['Cluster'] = kmeans.labels_

# Display cluster centers
print("\nCluster Centers:")
print(kmeans.cluster_centers_)

# Display customer segmentation
print("\nCustomer Segmentation:")
print(data[['CustomerID',
            'Annual Income (k$)',
            'Spending Score (1-100)',
            'Cluster']])

# Plot the clusters
plt.figure(figsize=(10, 6))

plt.scatter(
    X['Annual Income (k$)'],
    X['Spending Score (1-100)'],
    c=data['Cluster'],
    s=50
)

# Plot cluster centers
plt.scatter(
    kmeans.cluster_centers_[:, 0],
    kmeans.cluster_centers_[:, 1],
    s=200,
    marker='X'
)

plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.title('K-Means Clustering for Customer Segmentation')

plt.show()
```
## Output:
<img width="1041" height="479" alt="image" src="https://github.com/user-attachments/assets/b58bec74-6edf-4cf5-a916-5113cc7a556f" />
<img width="880" height="608" alt="image" src="https://github.com/user-attachments/assets/a7fa4213-27ea-4fc1-8de0-7d94b7c61fd9" />
<img width="1027" height="652" alt="image" src="https://github.com/user-attachments/assets/f42d8866-a143-4b57-a33d-6685fa6ca53d" />


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
