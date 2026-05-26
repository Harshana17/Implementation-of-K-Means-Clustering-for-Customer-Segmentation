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
import pandas as pd 
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
display(data.head())
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    Kmeans=KMeans (n_clusters = i, init ="k-means++")
    Kmeans.fit(d.iloc[:,3:])
    wcss.append(Kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Metthod")
km=KMeans(n_clusters=5)
km.fit(d.iloc[:,3:])
y_pred = km.predict(d.iloc[:,3:])
y_pred
d["clusters"]=y_pred
df0=d[d["clusters"]==0]
df1=d[d["clusters"]==1]
df2=d[d["clusters"]==2]
df3=d[d["clusters"]==3]
df4=d[d["clusters"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="clusters0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="clusters1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="clusters2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="clusters3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="black",label="clusters4")
plt.legend()
plt.title("Customer Segments")

```
## Output:
<img width="1058" height="619" alt="image" src="https://github.com/user-attachments/assets/c9b13189-4aec-4425-8852-70b0b534c5c1" />
<img width="509" height="564" alt="image" src="https://github.com/user-attachments/assets/2a0017a4-26ea-4a16-9e79-41c608c8eb49" />
<img width="815" height="705" alt="image" src="https://github.com/user-attachments/assets/f4bfe1b5-55f9-43c1-8493-9a8e21b299d3" />
<img width="768" height="525" alt="image" src="https://github.com/user-attachments/assets/282e04a0-50d3-43fe-8827-1708e00f63cb" />





## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
