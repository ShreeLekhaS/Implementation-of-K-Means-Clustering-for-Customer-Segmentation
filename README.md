# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement.

2. Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3. Import KMeans and use for loop to cluster the data.

4. Predict the cluster and plot data graphs.
5. 
6. Print the outputs and end the program

## Program and Output:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Shree Lekha.S
RegisterNumber: 212223110052
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv('Mall_Customers.csv')

data.head()

```
![image](https://github.com/user-attachments/assets/34d53e8d-2256-4904-bfc5-d1e31837426c)

```
data.info()
```
![image](https://github.com/user-attachments/assets/5022ff6a-95eb-40a7-9159-d012c67dedd1)

```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/f8cdf292-07b0-42e9-84d3-57f744b01cac)

```
from sklearn.cluster import KMeans
wcss = [] #Within-Cluster Sum of Square.
#It is the sum of squared distance between each point & the centroid in a cluster

for i in range(1,11):
    kmeans = KMeans(n_clusters = i, init = "k-means++")
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11), wcss)
plt.xlabel("Number of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

```
![image](https://github.com/user-attachments/assets/1d017afd-e2f9-4a7a-8cb0-a7f25d24b25f)
```
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
KMeans(n_clusters = 5)
```
![image](https://github.com/user-attachments/assets/b9c7c2a8-9046-459e-a1e1-0cbe9aba7b12)

```
y_pred = km.predict(data.iloc[:, 3:])
y_pred
```
![image](https://github.com/user-attachments/assets/a7251cb4-9d32-45e6-abde-140ec80dfb9f)

```
data["cluster"] = y_pred

df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")

```
![image](https://github.com/user-attachments/assets/c401f8dc-3ac4-4549-98fd-e58930320f2d)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
