# Блок 10. Линейная регрессия
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Выведем информацию о датасете.
```python
import pandas as pd
df=pd.read_csv("Crimes_2015.csv")
print(df.info())
```
B. Выберем какая формулировка подходит к распределению на рисунке больше всего.
1. На графике представлено нормальное распределение.
2. Распределение напоминает нормальное, но оно смещено вправо.
3. Распределение напоминает нормальное, но они смещено влево.
4. Зависимая переменная распределена ненормально.

![](/images/10-B.png)
```python
print(1)
```
C. Выведем описательную статистику.
```python
import pandas as pd
df=pd.read_csv('Crimes_2015.csv')
print(df.describe())
```
D. Выведем названия переменных, p-value которых меньше 0,05.

![](/images/10-D.png)
```python
print('Primary Types', 'Domestic', 'Arrest')
```
E. Выберем один вариант ответа:
1. R2 квадрат не изменился, переменные 'Ward', 'District' не добавляли качество модели.
2. R2 квадрат изменился, переменные 'Ward', 'District' делали модель лучше.

![](/images/10-F.png)
```python
print(2)
```
F. Выберем модель, которая лучше предсказывает количество совершенных преступлений в Чикаго.
1. Первая модель содержала следующие независимые переменные: ['Ward', 'District', 'Primary Types', 'Domestic', 'Arrest'].
2. Вторая модель содержала следующие независимые пременные: ['Primary Types', 'Domestic', 'Arrest'].
```python
print(2)
```
G. Выберем названия всех независимых переменных, которые проходят проверку на мультиколлинеарность.
|  feature |  VIF |   
|---|---|
|  Primary Types  |  1.216226 |   
|  Domestic |  1.034569 |   
|  Arrest |  1.219746 | 
```python
print('Primary Types', 'Domestic', 'Arrest')
```
