# Блок 11. Логистическая регрессия
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Построим бар чарт, отражающий распределение бинарной переменной.
```python
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("loan.csv")
df['Loan_Status'].value_counts().plot(kind='bar')
plt.savefig('result.png')
```
B. Визуализируем распределение заявителей по брачному статусу. 
```python
import pandas as pd
import matplotlib.pyplot as plt
loan = pd.read_csv("loan.csv")
loan['Married'].value_counts().plot(kind='bar')
plt.title('Распределение заявителей по брачному статусу')
plt.xlabel('Брачный статус')
plt.ylabel('Количество')
plt.savefig('result.png')
```
C. Построим график, распределение по наличию и отсутствию высшего образования.
```python
import pandas as pd
import matplotlib.pyplot as plt
loan = pd.read_csv("loan.csv")
loan['Education'].value_counts().plot(kind='bar')
plt.title('Распределение заявителей по образованию')
plt.xlabel('Образование')
plt.ylabel('Количество')
plt.savefig('result.png')
```
D. Посмотрим распределение количества запрашиваемых денег.
```python
import pandas as pd
import matplotlib.pyplot as plt
loan = pd.read_csv("loan.csv")
plt.hist(loan['LoanAmount'], bins=20, edgecolor='black')
plt.title('Распределение запрашиваемых сумм кредита')
plt.xlabel('Сумма кредита')
plt.ylabel('Частота')
plt.savefig('result.png')
```
E. Построим модель логистической регрессии и включим туда одну переменную.
```python
import pandas as pd
import numpy as np
import statsmodels.api as sm
from statsmodels.genmod.generalized_linear_model import GLM
from statsmodels.genmod import families
df = pd.read_csv("loan.csv")
model = sm.GLM(df['Loan_Status'], df['LoanAmount'], family=families.Binomial(),
).fit()
print(np.exp(model.params))
```
F. Добавим переменные брачного статуса и наличия высшего образования в лист с зависимыми переменными.
```python
import pandas as pd
import numpy as np
import statsmodels.api as sm
from statsmodels.genmod.generalized_linear_model import GLM
from statsmodels.genmod import families
df = pd.read_csv("loan.csv")
model = sm.GLM(df['Loan_Status'], df[['LoanAmount','Married','Education']], family=families.Binomial(),
).fit()
print(np.exp(model.params))
```
G. Проверим независимые переменные на мультиколлинеарность.
```python
import pandas as pd
from statsmodels.stats.outliers_influence import variance_inflation_factor
df = pd.read_csv("loan.csv")
X = df[['LoanAmount','Married','Education']]
vif_data = pd.DataFrame()
vif_data["feature"] = X.columns 
vif_data["VIF"] = [variance_inflation_factor(X.values, i) for i in range(len(X.columns))]
print(vif_data)
```
H. Построим график влиятельных отклонений.
```python
import statsmodels.api as sm
import pandas as pd
from statsmodels.genmod.generalized_linear_model import GLM
from statsmodels.genmod import families
import matplotlib.pyplot as plt
df = pd.read_csv("loan.csv")
model = sm.GLM(df['Loan_Status'], df[['LoanAmount','Married','Education']], family=families.Binomial(),
).fit()
infl = model.get_influence()
fig = infl.plot_index(y_var="cooks", threshold=2 * infl.cooks_distance[0].mean())
fig.tight_layout(pad=1.0)
plt.savefig('result.png')
```
I. Посмотрим, имеет ли наша модель предсказательную силу и хорошо ли она классифицирует данные.
```python
import statsmodels.api as sm
import matplotlib.pyplot as plt
import pandas as pd
import statsmodels.api as sm
from statsmodels.genmod.generalized_linear_model import GLM
from statsmodels.genmod import families
from sklearn.metrics import roc_auc_score
from sklearn.metrics import roc_curve
df = pd.read_csv("loan.csv")
model = sm.GLM(df['Loan_Status'], df[['LoanAmount','Married','Education']], family=families.Binomial(),
).fit()
prob_pred = model.predict()
roc_auc = roc_auc_score(df['Loan_Status'], prob_pred)
fpr, tpr, thresholds = roc_curve(pd.to_numeric(df['Loan_Status']), prob_pred)
plt.plot(fpr, tpr)
plt.savefig('result.png')
```