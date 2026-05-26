# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement.
2. Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().
3. Import KMeans and use for loop to cluster the data and Predict the cluster and plot data graphs.
4. Print the outputs and end the program.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: HARSHANA M V
RegisterNumber:  212224240053
*/
```
```
import os
os.environ["OMP_NUM_THREADS"] = "1"  
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans


data = pd.read_csv("Mall_Customers.csv")
print(data.head())
data.info()
print(data.isnull().sum())


wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++", n_init=10, random_state=42)  
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()


km = KMeans(n_clusters=5, init="k-means++", n_init=10, random_state=42)  # n_init fix
y_pred = km.fit_predict(data.iloc[:, 3:])  
data["clusters"] = y_pred


df0 = data[data["clusters"] == 0]
df1 = data[data["clusters"] == 1]
df2 = data[data["clusters"] == 2]
df3 = data[data["clusters"] == 3]
df4 = data[data["clusters"] == 4]


plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red",    label="Careful (Low Income, Low Spend)")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="pink",   label="Standard")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="green",  label="Target (High Income, High Spend)")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="blue",   label="Spenders (Low Income, High Spend)")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="black",  label="Conservative (High Income, Low Spend)")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.legend()
plt.title("Customer Segments")
plt.show()


```
## Output:
<img width="1058" height="619" alt="image" src="https://github.com/user-attachments/assets/c9b13189-4aec-4425-8852-70b0b534c5c1" />
<img width="509" height="564" alt="image" src="https://github.com/user-attachments/assets/2a0017a4-26ea-4a16-9e79-41c608c8eb49" />
<img width="815" height="705" alt="image" src="https://github.com/user-attachments/assets/f4bfe1b5-55f9-43c1-8493-9a8e21b299d3" />
<img width="768" height="525" alt="image" src="https://github.com/user-attachments/assets/282e04a0-50d3-43fe-8827-1708e00f63cb" />





## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
