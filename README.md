# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv("/content/titanic_dataset.csv")

dt
```
<img width="1748" height="656" alt="image" src="https://github.com/user-attachments/assets/b4d5db47-d3f1-4477-be2e-7405b6000d10" />

```
dt.info()
```
<img width="1768" height="430" alt="image" src="https://github.com/user-attachments/assets/6495e7bd-5526-47b8-8949-c69cb63c50d4" />

```
dt.shape
```
<img width="1743" height="98" alt="image" src="https://github.com/user-attachments/assets/f8759f2d-5392-4411-860d-1b41c665a31b" />

```
dt.set_index("PassengerId", inplace=True)

dt.describe()
```
<img width="1751" height="413" alt="image" src="https://github.com/user-attachments/assets/e6be1454-406e-403b-8dc6-16a25ca18acd" />

```
dt.nunique()
```
<img width="1754" height="519" alt="image" src="https://github.com/user-attachments/assets/72db7e05-d01c-44e4-8b0c-db4ca3362d76" />

```
dt["Survived"].value_counts()
```
<img width="1748" height="245" alt="image" src="https://github.com/user-attachments/assets/3865671f-4ba1-4ec4-b8d3-1f0da4227057" />

```
per = (dt["Survived"].value_counts() / dt.shape[0] * 100).round(2)
per
```
<img width="1743" height="262" alt="image" src="https://github.com/user-attachments/assets/e7667f44-bd7f-4b9a-bccb-1528f90e54c8" />

```
sns.countplot(data=dt, x="Survived")
```

<img width="1740" height="578" alt="image" src="https://github.com/user-attachments/assets/ce6e5fa5-2deb-4114-92ba-0fb69151566f" />


```
dt
```

<img width="1751" height="590" alt="image" src="https://github.com/user-attachments/assets/6f6402fe-1d43-4f9d-b69b-3421f5f4844f" />


```
dt.Pclass.unique()
```

<img width="1747" height="75" alt="image" src="https://github.com/user-attachments/assets/7431e3a9-5291-41b5-bfd6-c232221dbb73" />

```
dt.rename(columns={"Sex": "Gender"}, inplace=True)
dt
```

<img width="1751" height="610" alt="image" src="https://github.com/user-attachments/assets/d733b612-47ec-4064-a9b7-8df46557f4c5" />

```
sns.catplot(
    x="Gender",
    col="Survived",
    kind="count",
    data=dt,
    height=5,
    aspect=0.7
)
```

<img width="1765" height="700" alt="image" src="https://github.com/user-attachments/assets/efde1a6b-25c4-4e07-9081-3b01286bad06" />

```
sns.scatterplot(x=dt["Age"], y=dt["Fare"])

```

<img width="1751" height="578" alt="image" src="https://github.com/user-attachments/assets/c18ab218-8c12-43d0-8406-a7c73682ee7d" />

```
sns.jointplot(x="Age", y="Fare", data=dt)

```
<img width="1770" height="678" alt="image" src="https://github.com/user-attachments/assets/33a5702d-fa4e-4947-9b8e-57d00edebf79" />

```
fig, ax1 = plt.subplots(figsize=(8, 5))
sns.boxplot(
    ax=ax1,
    x="Pclass",
    y="Age",
    hue="Gender",
    data=dt
)
```

<img width="1773" height="658" alt="image" src="https://github.com/user-attachments/assets/6fc923a8-c520-425e-8dda-3d3c90a124e1" />

```
sns.catplot(
    data=dt,
    col="Survived",
    x="Gender",
    hue="Pclass",
    kind="count"
)

```

<img width="1773" height="675" alt="image" src="https://github.com/user-attachments/assets/f174d068-5c9e-471f-a304-03790d147afe" />

```
corr = dt.select_dtypes(include=np.number).corr()
sns.heatmap(corr,annot=True)
```

<img width="630" height="487" alt="image" src="https://github.com/user-attachments/assets/292701bc-6575-4370-abde-1db80dd73845" />


```
sns.pairplot(dt)
```
<img width="1820" height="692" alt="image" src="https://github.com/user-attachments/assets/31da80f1-8996-41e9-88d3-2ac7399ce5b2" />

# RESULT
       Thus, Exploratory Data Analysis for the given dataset is done successfully.
