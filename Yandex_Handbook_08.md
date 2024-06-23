# Блок 8. Подготовка данных
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Выведем информацию о датасете.
```python
import pandas as pd
df=pd.read_csv('disney_title.csv')
print(df.info())
```
B. Поменяем тип переменной в колонке Date.
```python
import pandas as pd
df=pd.read_csv('disney_title.csv')
print(pd.to_datetime(df['Date']).dtype)
```
C. Выведем переменную с названиями десяти первых фильмов, вышедшие в промежутке с 1 января 2020 года по 1 января 2021 года.
```python
import pandas as pd
df=pd.read_csv('disney_title.csv')
df['Date']=pd.to_datetime(df['Date'])
df=df[(df['Date']>='2020-01-01')& (df['Date']<'2021-01-01')]
print(df['title'].head(10))
```
D. Удалим столбец из датасета 'release_year' и выведем название оставшихся столбцов.
```python
import pandas as pd
df=pd.read_csv('disney_title.csv')
df=df.drop(['release_year'],axis=1)
print(list(df))
```
E. Поменяем название переменных из 'disney_title.csv' на такие же названия написанные с большой буквы.
```python
import pandas as pd
df = pd.read_csv('disney_title.csv')
df.columns = df.columns.str.capitalize()
print(list(df.columns))
```
G. Выведем количество пропущенных значений по каждому стобцу.
```python
import pandas as pd
df=pd.read_csv('disney_title.csv')
print(df.isnull().sum())
```
H. Удалим пропущенные значения во всех столбцах и выведем количество пропущенных переменных по каждому столбцу.
```python
import pandas as pd
df=pd.read_csv('disney_title.csv')
df=df.dropna()
print(df.isnull().sum())
```
I. Выведем процент пропущенных значений относительно всех значений, результат округлим до сотых. 
```python
import pandas as pd
df=pd.read_csv('disney_title.csv')
print(round(df.isna().mean()*100, 2))
```
J. Заменим пропущенные значения в столбце 'country' на 'Country not specified' и выведем первые пять первых значений.
```python 
import pandas as pd
df=pd.read_csv('disney_title.csv')
df['country']=df['country'].fillna('Country not specified')
print(df['country'].head(5))
```