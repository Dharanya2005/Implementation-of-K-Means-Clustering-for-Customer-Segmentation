# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Data Preparation: Load data, handle missing values, and extract relevant features for clustering.

2.Determine Clusters: Use the Elbow Method to find optimal number of clusters based on WCSS.

3.K-Means Clustering: Fit the K-Means model with optimal clusters, predict cluster labels for data.

4.Visualization: Plot data points with distinct colors for each cluster to visualize clustering resultant.


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: DHARANYA N
RegisterNumber:  212223230044
*/
```

## Program & Output:
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()
```
![image](https://github.com/user-attachments/assets/010b2395-74ef-4883-98bf-79f0949f24fb)
```
data.info()
```
![image](https://github.com/user-attachments/assets/152e06e8-e55f-4990-be86-4f09a45c227e)
```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/90e48180-f475-4a58-abf3-8bd4b1b3253c)
```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
  kmeans = KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Metthod")
```
![image](https://github.com/user-attachments/assets/00faab21-e589-42f1-a8db-f255efddde70)
```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
![image](https://github.com/user-attachments/assets/439bb26f-cc77-4c8a-b306-bcb9d2c50302)
```
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
```
```
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segmets")
```
![image](https://github.com/user-attachments/assets/ad8f6c30-a9b1-43fb-af29-19f6e84c3790)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
