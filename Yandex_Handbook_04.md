# Блок 4. Категориальные данные
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Выведем наиболее частый тип переменных встречаемый в датасете.
```python
import pandas as pd
df=pd.read_csv('COVID-19 SSR.csv')
print(df.dtypes.mode()[0])
```
B. Выведем пять первых значения переменной 'Rating of Online Class experience'.
```python
import pandas as pd
df=pd.read_csv('COVID-19 SSR.csv')
print(df['Rating of Online Class experience'].head(5).str.title())
```
C. Выведем количество учащихся, которые спят больше или меньше оптимального времени для сна.
```python
import pandas as pd
import numpy as np
df=pd.read_csv('COVID-19 Survey Student Responses.csv')
df['Sleep']=np.where((df['Time spent on sleep']<9) & (df['Time spent on sleep']>6.9),'normal','not normal')
print(len(df[df['Sleep']=='not normal']))
```
D. После обработки выведем тип переменной.
```python
import pandas as pd
df=pd.read_csv('COVID-19 Survey Student Responses.csv')
df['Time spent on TV'].replace(['N', 'n', 'No tv',' '], '0', inplace=True)
df['Time spent on TV'] = pd.to_numeric(df['Time spent on TV'])
print(df['Time spent on TV'].dtypes)
```
E. Перекодируем переменные, а затем выведем результат Хи-квадрата.
```python
import pandas as pd
from scipy.stats import chi2_contingency
df = pd.read_csv("COVID-19 Survey Student Responses.csv")

def encode_variable(value):
    if value >= 7:
        return 'normal'
    else:
        return 'not normal'

df['Sleep'] = df['Time spent on sleep'].apply(encode_variable)

def encode_media(valu):
    if valu < 2:
        return 'normal'
    else:
        return 'not normal'

df['Media'] = df['Time spent on social media'].apply(encode_media)
crosstab_result = pd.crosstab(df['Sleep'], df['Media'])
chi2, p, dof, expected = chi2_contingency(crosstab_result)
print(chi2)
```
F. Перекодировуем переменные, а затем воспользавшись результатом Хи-теста и Выведем результат Хи-квадрата.
```python
import pandas as pd
from scipy.stats import chi2_contingency
df = pd.read_csv("COVID-19 Survey Student Responses.csv")

def encode_variable_sleep(value):
    if value >= 7:
        return 'normal'
    else:
        return 'not normal'

def encode_variable_media(value):
    if value < 2:
        return 'normal'
    else:
        return 'not normal'

df['Sleep'] = df['Time spent on sleep'].apply(encode_variable_sleep)
df['Media'] = df['Time spent on social media'].apply(encode_variable_media)
crosstab_result = pd.crosstab(df['Sleep'], df['Media'])
chi2, p, dof, expected = chi2_contingency(crosstab_result)
print(p)
```
G. Перекодируем значения переменной 'Health issue during lockdown' на "1" и "0", выведем количество значений.
```python
import pandas as pd
df = pd.read_csv("COVID-19 Survey Student Responses.csv")
df['Health issue during lockdown'] = df['Health issue during lockdown'].map({'YES': 1, 'NO': 0})
print(df['Health issue during lockdown'].value_counts())
```
H. Выведем количество учащихся, которые используют книги в качестве профилактики борьбы со стрессом.
```python
import pandas as pd
df=pd.read_csv('COVID-19 Survey Student Responses.csv')
print(df['Stress busters'].str.contains('book').sum())
```
I. Отфильтруем пользователей, которые используют платформу для социальной сети и вычислить, в среднем сколько времени в день проводят в социальных медиа, результат округлим до сотых.
```python
import pandas as pd
df=pd.read_csv('COVID-19 Survey Student Responses.csv')
print(df[df['Prefered social media platform']=='Instagram']['Time spent on social media'].mean().round(2))
```
J. Определим платформу, в которой пользователи проводят больше всего времени в среднем. В начале укажим название предпочитаемой социальной сети, а затем среднее количество времени, затрачиваемое на пользование социальными сетями через пробел, результат округлим до сотых.
```python
import pandas as pd
df=pd.read_csv('COVID-19 Survey Student Responses.csv')
avg_time_per_platform = df.groupby('Prefered social media platform')['Time spent on social media'].mean()
preferred_platform = avg_time_per_platform.idxmax()
max_avg_time = round(avg_time_per_platform.max(), 2)
print(preferred_platform, max_avg_time)
```