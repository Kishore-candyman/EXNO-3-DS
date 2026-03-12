## EXNO-3-DS

### NAME: KISHORE M
### REG.NO: 212224040161

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1: Read the given Data.

STEP 2: Clean the Data Set using Data Cleaning Process.

STEP 3: Apply Feature Encoding for the feature in the data set.

STEP 4: Apply Feature Transformation for the feature in the data set.

STEP 5: Save the data to the file.

# FEATURE ENCODING:
**1. Ordinal Encoding:**
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.

**2. Label Encoding:**
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.

**3. Binary Encoding:**
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.

**4. One Hot Encoding:**
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation

• Reciprocal Transformation

• Square Root Transformation

• Square Transformation

  # 2. POWER TRANSFORMATION
• Boxcox method

• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df= pd.read_csv("Encoding Data.csv")
df
```

<img width="371" height="454" alt="image" src="https://github.com/user-attachments/assets/e0d18e37-081e-44a0-a29e-ac561e88f1c1" />

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm= ['Hot','Warm','Cold']
e1= OrdinalEncoder (categories=[pm])
e1.fit_transform (df[["ord_2"]])
```
<img width="207" height="240" alt="image" src="https://github.com/user-attachments/assets/fc770b66-6919-4857-a583-71877082bc41" />

```
df['bo2'] = e1.fit_transform (df[["ord_2"]])
df
```
<img width="450" height="447" alt="image" src="https://github.com/user-attachments/assets/d55b6b23-6a26-490d-a1c8-300581257be2" />

```
le = LabelEncoder()
dfc = df.copy()
dfc["ord_2"] = le.fit_transform(dfc['ord_2'])
dfc
```
<img width="406" height="443" alt="image" src="https://github.com/user-attachments/assets/41c496f8-ff69-4af7-af84-86206d000f9b" />

```
from sklearn.preprocessing import OneHotEncoder
ohe = OneHotEncoder(sparse_output=False)
df2 = df.copy()
enc = pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2 = pd.concat([df2,enc],axis = 1)
df2
```
<img width="563" height="447" alt="image" src="https://github.com/user-attachments/assets/d37139c2-7b35-4513-99d0-ff2afb52bb97" />

```
pd.get_dummies(df2,columns=["nom_0"])
```
<img width="845" height="449" alt="image" src="https://github.com/user-attachments/assets/e6aab7e0-6d8c-41d0-8da3-52ebcabf47d7" />

```
from category_encoders import BinaryEncoder
df= pd.read_csv("data.csv")
df
```
<img width="601" height="465" alt="image" src="https://github.com/user-attachments/assets/bbb9bcc7-6978-4157-b7d3-b220d655bc47" />

```
be= BinaryEncoder()
nd= be.fit_transform(df['Ord_2'])
df
```
<img width="620" height="450" alt="image" src="https://github.com/user-attachments/assets/b9710bd8-d0e5-40e3-baa5-fa14cbcda43a" />

```
dfb= pd.concat([df,nd],axis=1)
dfb
```
<img width="874" height="455" alt="image" src="https://github.com/user-attachments/assets/64e899a5-cab6-41b6-b30b-efae5629f9cc" />

```
from category_encoders import TargetEncoder
te= TargetEncoder()
CC= df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC= pd.concat([CC,new],axis=1)
CC
```
<img width="686" height="447" alt="image" src="https://github.com/user-attachments/assets/51b28c04-cc1a-4499-bfe3-6e5da84f63f8" />

```
import pandas as pd 
import numpy as np
from scipy import stats 
df= pd.read_csv("Data_to_Transform.csv")
df
```
<img width="890" height="536" alt="image" src="https://github.com/user-attachments/assets/42f0189f-507a-40a0-bbd1-4a960edd4bae" />

```
df.skew()
```
<img width="389" height="265" alt="image" src="https://github.com/user-attachments/assets/cf644779-7292-4e50-8e94-6ab4e2aad27b" />

```
np.log(df["Highly Positive Skew"])
```
<img width="345" height="563" alt="image" src="https://github.com/user-attachments/assets/e32ef8c0-c975-4da1-903a-dab763da06df" />

```
np.reciprocal(df["Moderate Positive Skew"])
```
<img width="357" height="570" alt="image" src="https://github.com/user-attachments/assets/f2ec765c-3439-4eae-9017-49c7f721d344" />

```
np.sqrt(df["Highly Positive Skew"])
```
<img width="384" height="565" alt="image" src="https://github.com/user-attachments/assets/3c59a439-ee65-4d6c-8cfa-9c26f778c4c7" />

```
np.square(df["Highly Positive Skew"])
```
<img width="355" height="584" alt="image" src="https://github.com/user-attachments/assets/a9ac4ccb-5896-416c-bb89-2c1970d3886c" />

```
df["Highly Positive Skew_boxcox"],parameters= stats.boxcox(df["Highly Positive Skew"])
df
```
<img width="884" height="536" alt="image" src="https://github.com/user-attachments/assets/2513cc9c-df88-4b0c-9b4a-983e0a332d10" />

```
df.skew()
```
<img width="406" height="290" alt="image" src="https://github.com/user-attachments/assets/bb7a3564-66c0-498e-999e-2c92f97a8554" />
```
df["Highly Negative Skew_yeojohnson"],parameters= stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
```

<img width="475" height="334" alt="image" src="https://github.com/user-attachments/assets/6824dbd4-4217-460a-a0f4-1f2a904151c5" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```

<img width="884" height="554" alt="image" src="https://github.com/user-attachments/assets/188eeb22-cf91-46ef-ac7b-06210a3dd955" />

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

<img width="749" height="560" alt="image" src="https://github.com/user-attachments/assets/7bc88a0b-c6b5-4d16-b72b-067d48594a5f" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```

<img width="732" height="552" alt="image" src="https://github.com/user-attachments/assets/8c1a04a8-3d7a-45f6-9d97-387ff0133a06" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

<img width="725" height="554" alt="image" src="https://github.com/user-attachments/assets/07564d40-15dd-4df3-8dd5-e5314cd39c98" />

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```

<img width="720" height="556" alt="image" src="https://github.com/user-attachments/assets/cbdab0d6-7c77-46aa-93f9-fe62dec7e3b5" />

```
dt=pd.read_csv("titanic_dataset.csv")
dt
dt=pd.read_csv("titanic_dataset.csv")
dt
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45') 
plt.show()
```

<img width="717" height="538" alt="image" src="https://github.com/user-attachments/assets/9745687a-3155-4458-8499-9ba3fa12c96a" />

```
sm.qqplot(df['Highly Negative Skew_1'],line='45')
plt.show()
```
<img width="720" height="540" alt="image" src="https://github.com/user-attachments/assets/8c9f37a8-8aba-4f1a-bded-362964264dab" />

# RESULT:

Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.
       
