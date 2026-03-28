## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.

STEP 2:Clean the Data Set using Data Cleaning Process.

STEP 3:Apply Feature Encoding for the feature in the data set.

STEP 4:Apply Feature Transformation for the feature in the data set.

STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.

2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.

3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.

4. One Hot Encoding
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
df=pd.read_csv("C:\\Users\\G.POORNIMA DEVI\\Downloads\\data.csv")
df.isnull().sum(axis=0)
```
<img width="1380" height="269" alt="image" src="https://github.com/user-attachments/assets/898cb12e-40e4-4094-ac98-34ad7e131f66" />

```
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
le=LabelEncoder()
df["nom_0_encoded"]=le.fit_transform(df["nom_0"])
df
```

<img width="1152" height="574" alt="image" src="https://github.com/user-attachments/assets/5e58eac3-1d99-494e-9cd1-eba2a0c892cb" />

```
oe=OrdinalEncoder(categories=[['Cold','Warm','Hot']])
df["ord_2_encoded"]=oe.fit_transform(df[["ord_2"]])
df
```

<img width="1317" height="637" alt="image" src="https://github.com/user-attachments/assets/16674b58-80ff-4abb-8ed7-7cbaf9ea46e1" />

```
df_ohe_encoded=pd.get_dummies(data=df, columns=['bin_2'])
df_ohe_encoded
```

<img width="1256" height="670" alt="image" src="https://github.com/user-attachments/assets/406e6377-b379-4ead-8ad4-b8f70ecd84f6" />

```
import category_encoders as ce
be=ce.BinaryEncoder()
df_be_encoded=be.fit_transform(X=[df['bin_1'],df['bin_2']])
df_be_encoded
```

<img width="1173" height="217" alt="image" src="https://github.com/user-attachments/assets/d0239dc8-dcd0-479b-99f9-62fc78d65be8" />

```
import pandas as pd
import numpy as np
df=pd.read_csv("C:\\Users\\G.POORNIMA DEVI\\Downloads\\Data_to_Transform.csv")
df
```

<img width="952" height="590" alt="image" src="https://github.com/user-attachments/assets/79ec80f8-359b-4cbe-bb83-703dbd219bf2" />

```
df['log Tranformed MPS']=np.log1p(df['Moderate Positive Skew'])
df['Reciprocal HPS']=1/df['Highly Positive Skew']
df['Square Transformed MNS']=np.square(df['Moderate Negative Skew'])
df['Square Transformed HNS']=np.square(df['Highly Negative Skew'])
df
```

<img width="1365" height="675" alt="image" src="https://github.com/user-attachments/assets/e24ace5d-0dfc-406d-bbca-33c6e80aa825" />


```
from sklearn.preprocessing import PowerTransformer
pt=PowerTransformer(method='box-cox')
df['Power Transformed Box-Cox']=pt.fit_transform(df[['Moderate Positive Skew']])
df
```

<img width="1349" height="609" alt="image" src="https://github.com/user-attachments/assets/8d907aa1-6d7c-4bb7-9af0-2301391e1e1d" />

```
pt=PowerTransformer(method='yeo-johnson')
df['Power Transformed yeo-johnson']=pt.fit_transform(df[['Highly Negative Skew']])
df
```

<img width="1343" height="652" alt="image" src="https://github.com/user-attachments/assets/d8267f86-001e-49ab-964b-c2f6458e660a" />

```
import pandas as pd
df=pd.read_csv("C:\\Users\\G.POORNIMA DEVI\\Downloads\\Data_to_Transform.csv")
import matplotlib.pyplot as plt
import scipy.stats as stats
stats.probplot(df['Highly Negative Skew'], dist='norm', plot=plt)
plt.show()
```

<img width="1228" height="663" alt="image" src="https://github.com/user-attachments/assets/ca856d16-3950-46fb-8400-00db98aff9d0" />

```
import pandas as pd
from sklearn.preprocessing import PowerTransformer
df=pd.read_csv("C:\\Users\\G.POORNIMA DEVI\\Downloads\\Data_to_Transform.csv")
pt=PowerTransformer(method='yeo-johnson')
df['Power Transformed yeo-johnson']=pt.fit_transform(df[['Highly Negative Skew']])
import scipy.stats as stats
stats.probplot(df['Power Transformed yeo-johnson'],dist='norm',plot=plt)
plt.show()
```

<img width="1367" height="703" alt="image" src="https://github.com/user-attachments/assets/e948485e-8396-447c-ac83-232967480382" />


# RESULT:
Thus, the Python program for feature encoding and feature transformation are executed successfully.

       
