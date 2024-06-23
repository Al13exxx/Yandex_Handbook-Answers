# Блок 7. Сбор и очистка данных
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

A. Будем работать с сохраненными страницами из Кинопоиска в HTML-формате. Выведем название страницы, которую собираемся парсить.
```python
from bs4 import BeautifulSoup as BS
with open('kinopoisk.html', 'r', encoding='utf-8') as file: 
    html_content = file.read()
soup = BS(html_content)
print (soup.title.text)
```
B. Выведем название фильма.
```python
from bs4 import BeautifulSoup as BS
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
a=soup.find('h1', class_='styles_title__65Zwx styles_root__l9kHe styles_root__5sqsd styles_rootInLight__juoEZ')
print(a.text)
```
C. Выведем имя режиссера.
```python
from bs4 import BeautifulSoup as BS
import requests
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
director_elements = soup.find_all('div', class_='styles_rowDark__ucbcz')

for director_element in director_elements:
    title_element = director_element.find('div', class_='styles_titleDark___tfMR')
    if title_element and title_element.text.strip() == 'Режиссер':
        director_value_element = director_element.find('div', class_='styles_valueDark__BCk93')
        if director_value_element:
            director_name = director_value_element.text
            print(director_name)
```
D. Выведем описание фильма.
```python
from bs4 import BeautifulSoup as BS
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
a=soup.find('p', class_="styles_paragraph__wEGPz")
print(a.text)
```
E. В разделе описания фильма выведем слова, написанные с большой буквы.
```python
from bs4 import BeautifulSoup as BS
import re
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
a=soup.find('p', class_="styles_paragraph__wEGPz")
words = re.findall(r'\b[А-ЯЁ][а-яё]+\b', a.text)
print(words)
```
F. Выведем количество актёров, которые находятся на странице.
```python
from bs4 import BeautifulSoup as BS
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
a=soup.find_all(class_='styles_root__vKDSE styles_rootInLight__EFZzH')
print(len(a))
```
G. Выведем список актёров и актёров озвучания.
```python
from bs4 import BeautifulSoup as BS
import requests
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
a=soup.find_all(class_="styles_root__vKDSE styles_rootInLight__EFZzH")
for i in a:
  print(i.text)
```
H. Выведем количество тегов 'а'.
```python
from bs4 import BeautifulSoup as BS
import re
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
a=soup.find_all('a')
print(len(a))
```
I. Найдем все теги 'a', затем извлечем все атрибуты.
```python
from bs4 import BeautifulSoup as BS
import requests
with open('kinopoisk.html', 'r', encoding='utf-8') as file:
    html_content = file.read()
soup = BS(html_content,'html.parser')
a=soup.find_all('a')
for i in a:
  print(i.get('href'))
```