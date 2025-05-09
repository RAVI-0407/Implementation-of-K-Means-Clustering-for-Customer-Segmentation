# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import dataset and print head,info of the dataset
2. check for null values
3. Import kmeans and fit it to the dataset
4. Plot the graph using elbow method
5. Print the predicted array
6. Plot the customer segments


## Program and Output:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: RAVIPRASATH K
RegisterNumber:  212224230225 */
```
```
from google.colab import drive
drive.mount('/content/drive')
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("drive/MyDrive/ML/Mall_Customers.csv")
data.head()
```
![image](https://github.com/user-attachments/assets/0d69abe2-42e3-4850-8bb1-23cd03d4680c)
```
data.info()
```
![image](https://github.com/user-attachments/assets/ba578210-310b-4d96-83a9-d2f33fb1b6f5)
```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/523848e3-00bd-408a-afdd-e9db47f5214f)
```
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
![image](https://github.com/user-attachments/assets/9ea29deb-6dde-4cf9-8121-efc726c565f3)
```
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:, 3:])
y_pred
```
![image](https://github.com/user-attachments/assets/43b23af4-87e0-418c-82f2-c56aa940701b)
```
data["cluster"] = y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")
```
![image](https://github.com/user-attachments/assets/b7547afd-5d97-4d66-8fae-7ce992080938)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
