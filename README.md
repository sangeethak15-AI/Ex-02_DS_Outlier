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
![Output](op1.png)

### AFTER REMOVING COLUMN -"Gender":
![Output](op2.png)

### GRAPH TO EXHIBIT OUTLIERS:
![Output](op3.png)

### USING Z-SCORE FUNCTION TO DETECT OUTLIERS:
![Output](op4.png)![Output](op5.png)

### GRAPH AFTER REMOVING OUTLIERS FROM COLUMN - "Height":
![Output](op6.png)

### FINAL DATASET:
![Output](op7.png)

## RESULT:
The Outliers are detected and removed from the Dataset.
