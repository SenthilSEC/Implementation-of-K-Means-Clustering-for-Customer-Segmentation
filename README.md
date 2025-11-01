# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load and preprocess data: Import data, inspect it, and handle missing values if any.
2. Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.
3. Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features.
4. Assign cluster labels to each data point.
5. Plot data points in a scatter plot, color-coded by cluster assignments for interpretation.

## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Senthil Arunachalam P
RegisterNumber: 212224240147
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
```
```
data.head()
```
```
data.info()
```
```
data.isnull().sum()
```
```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
```
```    
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
```
km = KMeans(n_clusters=5, n_init=10)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
```
```
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
```
```
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster5")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="639" height="250" alt="image" src="https://github.com/user-attachments/assets/9cbe1b85-0b43-4408-8c9c-29037295e9c5" />
<img width="517" height="243" alt="image" src="https://github.com/user-attachments/assets/4bb60043-2703-4ba8-9ce8-358bfb40c9cb" />
<img width="426" height="258" alt="image" src="https://github.com/user-attachments/assets/ffb89649-e706-4cdd-bfdb-5f44ea4eee75" />
<img width="658" height="446" alt="image" src="https://github.com/user-attachments/assets/de2c8d39-dfbe-419e-8aba-2a7df369dad2" />
<img width="624" height="178" alt="image" src="https://github.com/user-attachments/assets/a0f8711a-38a8-404f-bd2d-acded95db6e1" />
<img width="696" height="454" alt="image" src="https://github.com/user-attachments/assets/c4ac3131-ba46-4b48-9c69-aa6ff63b7e14" />




## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
