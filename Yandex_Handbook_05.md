# 5. Визуализация данных
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Визуализируем диапазон атаки покемонов, чтобы узнать пропорции «сильных» и «слабых». А также понять, какова примерная мода значений. В используемой базе данных переменная именуется Attack.Вместо plt.show() добавим в конец файла:
plt.savefig('result.png').
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
plt.hist(df['Attack'])
plt.savefig('result.png')
```
B. Попробуем отразить две шкалы на одном графике. Посмотрим, насколько сильно отличается распределения обычной атаки покемона и его специальной атаки. 
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
plt.hist(df['Attack'])
plt.hist(df['SpAtk'])
plt.savefig('result.png')
```
C. Для полного понимания происходящего исправим наш график. Сначала настроим прозрачность переменных.
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
plt.hist(df['Attack'],alpha=0.5)
plt.hist(df['SpAtk'],alpha=0.5)
plt.savefig('result.png')
```
D. В строках с переменными в функции plt.hist добавим аргументы label, чтобы присвоить переменной название, отражающееся в легенде. 
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
plt.hist(df['Attack'],label='Обычная атака',alpha=0.5)
plt.hist(df['SpAtk'],label='Специальная атака',alpha=0.5)
plt.legend()
plt.savefig('result.png')
```
E. Используя предыдущий график, подпишем оси графика с помощью команд plt.xlabel.
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
plt.hist(df['Attack'],label='Обычная атака',alpha=0.5)
plt.hist(df['SpAtk'],label='Специальная атака',alpha=0.5)
plt.legend()
plt.xlabel('Мощность атаки')
plt.ylabel('Количество покемонов')
plt.savefig('result.png')
```
F. Построим точечную диаграмму для проверки гипотезы, чем покемон сильнее, тем больше его защита.
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
plt.scatter(df['Attack'],df['SpAtk'],c='red')
plt.legend()
plt.savefig('result.png')
```
G. Cделаем точки прозрачнее, чтобы была видна кучность результато.
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
plt.scatter(df['Attack'],df['SpAtk'],c='red',alpha=0.3)
plt.legend()
plt.savefig('result.png')
```
H. Визуализируем частоту наблюдений по типам покемонов. Отразим частоту наблюдений по категориям с помощью столбчатой диаграммы.
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('PokemonData.csv')
df['Type1'].value_counts().plot(kind = 'bar')
plt.legend()
plt.savefig('result.png')
```
I. Теперь отобразить пропорцию легендарных и нелегендарных покемонов в каждом виде. И сделаем на одном барчарте.
```python
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("PokemonData.csv")
grouped = df.groupby('Legendary')['Type1'].value_counts().unstack(0).plot(kind='bar')
plt.savefig('result.png')
```
J. Внутри функции plot() переименуем оси и добавим название, чтобы было понятно, о чем наша визуализаци.
```python
import matplotlib.pyplot as plt
import pandas as pd
df=pd.read_csv('PokemonData.csv')
df.groupby('Legendary')['Type1'].value_counts().unstack(0).plot(kind='bar',xlabel='Тип покемонов',ylabel='Количество',title='Легендарные покемоны по типам в сравнении с обычными')
plt.savefig('result.png')
```