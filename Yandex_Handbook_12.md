# Блок 12. Текстовые данные
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)


B. Выведем самый частотный тип именованных сущностей, который встречается в корпусе стихотворений.
```python
import spacy
import pandas as pd
load_model = spacy.load('ru_core_news_sm')
df = pd.read_csv('russian_poetry.csv')
entities = []
for text in df['text'].values:
    doc = load_model(text)
    for entity in doc.ents:
        entities.append((entity.text, entity.label_))
ents_data = pd.DataFrame(entities, columns=['text', 'label'])
top_entity_type = ents_data['label'].describe()['top']
print(top_entity_type)
```
C. Выведем наиболее встречаемую именованную сущность в тексте стихотворений.
```python
import spacy
import pandas as pd
load_model = spacy.load('ru_core_news_sm')
df = pd.read_csv('russian_poetry.csv')
entities = []
for text in df['text'].values:
    doc = load_model(text)
    for entity in doc.ents:
        entities.append((entity.text, entity.label_))
ents_data = pd.DataFrame(entities, columns=['text', 'label'])
top_entity_type = ents_data['text'].describe()['top']
print(top_entity_type)
```
D. Проведем анализ тональности для каждого стихотворения в корпусе выведем максимульно негативную оценку. 
```python
import pandas as pd
from dostoevsky.tokenization import RegexTokenizer
from dostoevsky.models import FastTextSocialNetworkModel
df = pd.read_csv("russian_poetry.csv")
tokenizer = RegexTokenizer()
model = FastTextSocialNetworkModel(tokenizer=tokenizer)
data1 = model.predict(df['text'], k=5)
negative_list = []
for sentiment in data1:
        negative_list.append(sentiment.get('negative'))
df['negative'] = negative_list
print(df['negative'].max())
```
E. Проведем анализ тональности для каждого стихотворения в корпусе выведем среднюю положительную оценку. 
```python
import pandas as pd
from dostoevsky.tokenization import RegexTokenizer
from dostoevsky.models import FastTextSocialNetworkModel
df = pd.read_csv("russian_poetry.csv")
tokenizer = RegexTokenizer()
model = FastTextSocialNetworkModel(tokenizer=tokenizer)
data1 = model.predict(df['text'], k=5)
positive_list = []
for sentiment in data1:
        positive_list.append(sentiment.get('positive'))
df['positive'] = positive_list
print(df['positive'].mean())
```