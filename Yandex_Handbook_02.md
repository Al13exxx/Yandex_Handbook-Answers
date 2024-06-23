# Блок 2. Дескриптивный анализ данных. Введение в понятие данных и описательные статистики числовых данных
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Найдем максимальное и минимальное значение индекса счастья в 2019 году. Два ответа должны быть на разных строчках, используя print два раза.
```python
import pandas as pd
df = pd.read_csv('2019.csv')
print(df['Score'].max())
```
B. Найдем средний уровень счастья среди всех стран.
```python
import pandas as pd
df = pd.read_csv('2019.csv')
print(df['Score'].mean())
```
C. Найдем медианный уровень счастья среди всех стран.
```python
import pandas as pd
df = pd.read_csv('2019.csv')
print(df['Score'].median())
```
D. Найдем моду среди всех стран.
```python
import pandas as pd
df = pd.read_csv('2019.csv')
print(df['Score'].mode()[0])
```
E. Найдем стандартное отклонение среди всех стран.
```python
import pandas as pd
df=pd.read_csv('2019.csv')
print(df['Score'].std())
```
F. Найдем десять самых счастливых стран.
```python
import pandas as pd
df = pd.read_csv('2019.csv')
print(df['Country or region'].head(10).tolist())
```
G. Подсчитаем суммарный ВВП всех стран.
```python
import pandas as pd
df = pd.read_csv('2019.csv')
print(df['GDP per capita'].sum())
```
H. Подсчитаем суммарный ВВП первых десяти стран.
```python
import pandas as pd
df = pd.read_csv('2019.csv')
print(df['GDP per capita'].head(10).sum())
```