# Блок 9. Определение исследовательских гипотез
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Отобираем случайные 500 строк из датасета и выводим полученный размер.
```python
import pandas as pd
df = pd.read_csv("Patient Survival.csv")
random_sample = df.sample(n=500)
print(random_sample.shape)
```
B. Выберем случайное количество строк по 30 наблюдений из каждой группы, учитывая пять переменных: 'Patient_Age', 'Patient_Body_Mass_Index', 'Patient_Smoker', 'Diagnosed_Condition', 'Survived_1_year'`
```python
import pandas as pd
df = pd.read_csv('Patient Survival.csv')
df=df.groupby('Treated_with_drugs')
a = df[['Patient_Age', 'Patient_Body_Mass_Index', 'Patient_Smoker', 'Diagnosed_Condition', 'Survived_1_year']]
exp_sample1 = a.sample(30)
print(exp_sample1.shape)
```
C. Выберем правильное утверждение:

![](/images/C.png)
1. Наблюдаемые значения распределены не нормально.
2. Наблюдаемые значения распределены нормально.
```python
print(1)
```
D. Выберем правильное утверждение:

![](/images/D.png)
1. Разброс между курящими и не курящими группами пациентов отличается. У курильщиков меньший разброс, чем у группы не-курильщиков. Медианное значение отличается.
2. Разброс между курящими и не курящими группами пациентов отличается. У курильщиков больший разброс, чем у группы не-курильщиков. Медианное значение отличается.
```python
print(1)
```
E. Выберем правильное утверждение относительно графика:

![](/images/E.png)
1. Разброс диагностированного состояния в разных возрастных группах практически не отличается. Медианное значение примерно одинаково.
2. Разброс диагностированного состояния в разных возрастных группах отличается. Медианное значение примерно одинаково.
3. Разброс диагностированного состояния в разных возрастных группах значительно отличается. Медианное значение не одинаково.
```python
print(3)
```
F. Выберем правильный ответ:

![](/images/F.png)
1. Распределения возраста в группах разных лекарств различны. Медиана с поправкой на возраст среди принимаемых лекарств отличается. В другом графике, без поправки на возраст, медианы не имеют таких значительных различий.
2. Распределения возраста в группах разных лекарств различны. Медиана с поправкой на возраст среди принимаемых лекарств отличается. В другом графике, без поправки на возраст, медианы имеют различия.
3. Распределения возраста в группах разных лекарств не отличаются. Медиана с поправкой на возраст среди принимаемых лекарств не отличается. В другом графике, без поправки на возраст, медианы имеют значительные различия.
```python
print(2)
```
G. Выберем правильное утверждение:

![](/images/G.png)
1. Из графика видно, что в группе некурящих пациентов наибольшее количество людей, которые умерли после года лечения. Наименьшую пропорцию составляет группа некурящих пациентов, которые выжили после года лечения.
2. Из графика видно, что в группе некурящих пациентов наименьшее количество людей, которые умерли после года лечения. Наибольшую пропорцию составляет группа некурящих пациентов, которые выжили после года лечения.
```python
print(1)
```
H. Выберем правильное утверждение:

![](/images/H.png)
1. Коэффициент корреляции между этими переменными близок к 0, между ними почти нет статистически значимой связи.
2. Коэффициент корреляции между этими переменными близок к 50, между ними есть статистически значимая связь.
3. Коэффициент корреляции между этими переменными близок к 100, и между ними есть статистическая значимая связь.
```python
print(1)
```
I. Корреляция между переменными возраст и индекс массы тела составило 0.05369718182207669. Выберем правильное утверждение и выведите его в ответе:
1. Коэффициент корреляции между этими переменными близок к 0, между ними почти нет статистически значимой связи.
2. Коэффициент корреляции между этими переменными близок к 50, между ними есть статистически значимая связь.
3. Коэффициент корреляции между этими переменными близок к 100, и между ними есть статистическая значимая связь.
```python
print(2)
```
