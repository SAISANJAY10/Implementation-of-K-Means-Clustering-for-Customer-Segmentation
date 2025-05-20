# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import Required Libraries
2. Load and Explore the Dataset
3. Select Features for Clustering
4. Calculate WCSS (Within-Cluster Sum of Squares)
5. Plot the Elbow Graph
6. Apply K-Means Clustering with Optimal Clusters
7. Segment Data Based on Clusters
8. Visualize the Clusters
9. Analyze and Interpret Results

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SAI SANJAY R
RegisterNumber: 212223040178
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
print(data.head())

data.info()

print(data.isnull().sum())

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:, 3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
plt.show()
y_pred = km.predict(data.iloc[:, 3:])
print(y_pred)

data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
![image](https://github.com/user-attachments/assets/37ff4e41-f20e-48fe-89a2-13eeeffff520)
![image](https://github.com/user-attachments/assets/2f562bab-160a-4c6e-82eb-e5d41ef17ade)
![image](https://github.com/user-attachments/assets/1e978673-f000-4624-96b3-80e3228e7e29)
![image](https://github.com/user-attachments/assets/297292fc-7492-48d6-8224-423d638a4a34)
![image](https://github.com/user-attachments/assets/b4bfcc94-7d61-4c36-952e-39c37567dbf7)
![image](https://github.com/user-attachments/assets/7a2a7542-d5ef-41b8-b1e6-9702b7e37121)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
