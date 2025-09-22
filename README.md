### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
python

import pandas as pd
df=pd.read_csv("/content/clustervisitor.csv")
df

cluster = {"Young":(df['Age']<=30),"Middle":((df['Age']>30) & (df['Age']<=50)),"Old":(df['Age']>50)}
print(cluster)

count=[]
for g,c in cluster.items():
  visitors=df[c]
  count.append(len(visitors))
  print(f"visitors in {g} Group")
  print(visitors)
  print(count)

import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.bar(cluster.keys(),count,color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()

```
### Output:
<img width="403" height="694" alt="image" src="https://github.com/user-attachments/assets/ed2d3d4b-a991-4c0c-87c1-444a1fd0ba8c" />

<img width="804" height="561" alt="image" src="https://github.com/user-attachments/assets/343ff1a1-c830-472e-9b1a-866773a25f6d" />


### Visualization:
```python
python

import pandas as pd
df=pd.read_csv("/content/clustervisitor (Salary).csv")
df

df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
df3

from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

kmeans=KMeans(n_clusters=3,random_state=42)
df3['cluster']=kmeans.fit_predict(df3)
df3

plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary')
plt.title('Clustered Data')
plt.show()

```
### Output:
<img width="133" height="616" alt="image" src="https://github.com/user-attachments/assets/09b037b1-5389-4736-9419-beb75527f57d" />
<img width="133" height="616" alt="image" src="https://github.com/user-attachments/assets/06d99c38-251f-4bdf-a110-d4d824ee3370" />



### Result:
The implement Cluster and Visitor Segmentation for Navigation patterns in Python is execute successfully.
