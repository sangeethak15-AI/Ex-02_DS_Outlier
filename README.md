# Ex-02_DS_Outlier
## AIM:

To detect and remove outliers from the given data and save the final data.

## EXPLANATION:

Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

## ALGORITHM:

### STEP1:
Import the packages(pandas,numpy)
### STEP2:
Upload and read the given csv file.
### STEP3:
Use drop function to remove a column "Gender" from the Dataframe.
### STEP4:
Apply Graphical Method "Box plot",which exhibits the Outliers.
### STEP5:
Apply Z-score function defined in scipy library to detect the outliers.
### STEP6:
Apply Statistical Method "Interquartile Range(IQR)" ,to remove the Outliers from the Dataset.

## PROGRAM:
```
import pandas as pd
df=pd.read_csv("weight.csv")
df
df.drop("Gender",axis=1)
df
df.drop("Gender",axis=1,inplace=True)
df
df.boxplot()
from scipy import stats
import numpy as np
z=np.abs(stats.zscore(df))
z
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1
df2 = df1.copy()
q1 = df2.quantile(0.25)
q3 = df2.quantile(0.75)
IQR = q3-q1
df3 = df2[((df2>=q1-1.5*IQR) & (df2>=q1-1.5*IQR)).all(axis =1)]
df3
df3.boxplot()
```
## OUTPUT:

### INITIAL DATA:
![op1](https://user-images.githubusercontent.com/93992063/161556771-dfd566b8-b32d-4e12-902e-dca478026db5.png)

### AFTER REMOVING COLUMN -"Gender":
![op2](https://user-images.githubusercontent.com/93992063/161557025-ece2e25c-4892-48ab-b542-95ba623d6b7f.png)

### GRAPH TO EXHIBIT OUTLIERS:
![op3](https://user-images.githubusercontent.com/93992063/161557241-a9c03880-fcb5-48c7-9a7e-8e6cffc686f7.png)

### USING Z-SCORE FUNCTION TO DETECT OUTLIERS:
![op4](https://user-images.githubusercontent.com/93992063/161557309-19f021de-8797-4b7e-b04d-7175560ad007.png)
![op5](https://user-images.githubusercontent.com/93992063/161557315-07ba4d69-d5c3-4e0c-98f9-883ea8cb5fda.png)

### GRAPH AFTER REMOVING OUTLIERS FROM COLUMN - "Height":
![op6](https://user-images.githubusercontent.com/93992063/161557468-1178f849-cf43-485e-baa7-ec8baddc3f4c.png)


### FINAL DATASET:
![op7](https://user-images.githubusercontent.com/93992063/161557473-e260eaa1-db12-4ef1-8cd2-4db03262ed37.png)


## RESULT:
The Outliers are detected and removed from the Dataset.
