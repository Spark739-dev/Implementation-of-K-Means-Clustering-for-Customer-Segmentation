# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary python libraries to initiate the program of clustering.
2. Use pandas as pd to read the csv file.
3. Use head(),info(),isnull().sum() to analysis the datasets to find errors if found use data preprocessing steps.
4. Use Kmeans to store the number of clusters for test cases by using for loop from range 1 to 11 before declare the empty list after storing use append() to append the datapoints into the list and use fit to train the test clusters.
5. Use matplotlib.pyplot to visualize the clusters using Elbow Method
6. Then use use KMeans to store the number of clusters for real use
7. Use fit to train the real clusters.
8. Use y_pred variable to store the predictions after printing it shows the array type which clusters it belongs to.
9. Create new feature called clusters to store the clusters of datapoints of y_pred variable and then apply to all features starting from Annual Income (k$) and Spending Score (1-100) feature.
10. Use matplotlib.pyplot to visualize the y_pred of different clusters values in those selected features. 

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: VESHWANTH. 
RegisterNumber: 212224230300  
*/
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
data=pd.read_csv("C:\\Users\\admin\\OneDrive\\Documents\\Mall_Customers.csv")
data.head
data.info()
data.isnull().sum()
wcss=[]
for i in range(1,11):
    kmeans=KMeans(n_clusters=i,init='k-means++')
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
plt.show()
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["clusters"]=y_pred
df0=data[data["clusters"]==0]
df1=data[data["clusters"]==1]
df2=data[data["clusters"]==2]
df3=data[data["clusters"]==3]
df4=data[data["clusters"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")  
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")  
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")  
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")  
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4") 
plt.legend()
plt.title("Customer Segments")
plt.show()
```

## Output:
![image](https://github.com/user-attachments/assets/c43424d6-2d6a-442d-a023-ab8d34615458)
![image](https://github.com/user-attachments/assets/bfa0c3bd-b9d0-42bf-ad11-3a5d6c995da3)
![image](https://github.com/user-attachments/assets/d445595b-6c74-4e51-b97c-5a86eb795f34)
![image](https://github.com/user-attachments/assets/238875a0-80f8-4b09-ab09-3509ea8aa54f)
![image](https://github.com/user-attachments/assets/9cc72f52-a094-4366-be88-f7fe365a0432)
![image](https://github.com/user-attachments/assets/40a20997-698c-4123-b532-12016c832fed)
![image](https://github.com/user-attachments/assets/229d7141-6c5b-4dd4-b2b4-8a8eb5743780)




## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
