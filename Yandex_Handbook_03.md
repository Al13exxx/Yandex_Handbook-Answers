# Блок 3. Парные сравнения числовых данных
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Выведем имя самого популярного писателя в наборе данных.
```python
import pandas as pd
df=pd.read_csv('books_prep.csv')
popular_author = df['Author'].describe()['top']
print(popular_author)
```
B. Выведем средний рейтинг для «дорогих» книг, округлив до 2 знаков после запятой.
```python
import pandas as pd
df=pd.read_csv('books_prep.csv')
print(df['User Rating'][df['Price (Above Average)']=='Yes'].mean().round(2))
```
C. Выведем средний рейтинг для «дешёвых» книг, округлив до 2 знаков после запятой.
```python
import pandas as pd
df=pd.read_csv('books_prep.csv')
print(df['User Rating'][df['Price (Above Average)']=='No'].mean().round(2))
```
D. Используя критерий Левене, выведем только значение p-value, округлив до 2 знаков после запятой.
```python
import pandas as pd
from scipy.stats import levene 
df=pd.read_csv('books_prep.csv')
df_yes = df[df['Price (Above Average)'] == 'Yes']['User Rating']
df_no = df[df['Price (Above Average)'] == 'No']['User Rating']
print(levene(df_yes, df_no).pvalue.round(2))
```
E. Используя ttest, выведем только значение p-value, округлив до 2 знаков после запятой.
```python
import pandas as pd
from scipy.stats import ttest_ind
df=pd.read_csv('books_prep.csv')
df_yes = df[df['Price (Above Average)'] == 'Yes']['User Rating']  
df_no = df[df['Price (Above Average)'] == 'No']['User Rating']  
import scipy 
from scipy.stats import levene  
print((ttest_ind(df_yes, df_no).pvalue).round(2))
```
F. Используя тест ANOVA, выведем только значение p-value, округлив до 2 знаков после запятой.
```python
from scipy.stats import f_oneway
import pandas as pd
df=pd.read_csv('books_prep.csv')
r_3 = df[df['User Rating (Round)'] == 3]['Reviews']
r_4 = df[df['User Rating (Round)'] == 4]['Reviews']
r_5 = df[df['User Rating (Round)'] == 5]['Reviews']
print(f_oneway(r_3, r_4, r_5).pvalue.round(2))
```