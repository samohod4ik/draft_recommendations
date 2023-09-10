# Поиск наиболее подходящих товаров (draft recommendations).

## Описание проекта

В рамках проекта вы поработаете с реальными сырыми данными от одного из крупнейших маркетплейсов страны.
Вас ждет интересная задача сопоставления и поиска наиболее похожих товаров.
Сопоставление или “мэтчинг” (англ. matching - соответствия) - одна из базовых задач машинного обучения, которая встречается в информационном поиске, компьютерном зрении, рекомендательных системах и др.

Вы познакомитесь с алгоритмами приближённого поиска ближайщих соседей, научитесь создавать индексы в векторных базах данных и обучать ранжирующие модели. Эти навыки востребованы во многих сферах и позволят вам решать еще более интересные и сложные задачи.
А по завершению проекта вы сможете пополнить резюме ещё одним интересным кейсом в портфолио.

## Задача

- разработать алгоритм, который для всех товаров из validation.csv предложит несколько вариантов наиболее похожих товаров из base;
- оценить качество алгоритма по метрике accuracy@5

## Используемые библиотеки

- catboost
- imblearn
- matplotlib
- numpy
- pandas
- sklearn
- faiss-cpu

## Данные

base.csv - анонимизированный набор товаров. Каждый товар представлен как уникальный id (0-base, 1-base, 2-base) и вектор признаков размерностью 72.

train.csv - обучающий датасет. Каждая строчка - один товар, для которого известен уникальный id (0-query, 1-query, …) , вектор признаков И id товара из base.csv, который максимально похож на него (по мнению экспертов).

validation.csv - датасет с товарами (уникальный id и вектор признаков), для которых надо найти наиболее близкие товары из base.csv.

validation_answer.csv - правильные ответы к предыдущему файлу.

## Полезные ссылки

- https://habr.com/ru/companies/vk/articles/338360/
- https://scikit-learn.org/stable/modules/neighbors.html#unsupervised-neighbors
- Подкаст https://music.yandex.ru/album/17951713/track/116375860
- FAISS
    - https://engineering.fb.com/2017/03/29/data-infrastructure/faiss-a-library-for-efficient-similarity-search/
    - https://habr.com/ru/companies/okkamgroup/articles/509204/
    - https://evogeek.ru/articles/298310/
    - https://www.pinecone.io/learn/series/faiss/faiss-tutorial/
    - https://towardsdatascience.com/understanding-faiss-619bb6db2d1a
    - https://towardsdatascience.com/getting-started-with-faiss-93e19e887a0c
- Annoy
    - https://erikbern.com/2015/09/24/nearest-neighbor-methods-vector-models-part-1
    - https://erikbern.com/2015/10/01/nearest-neighbors-and-vector-models-part-2-how-to-search-in-high-dimensional-spaces.html
    - https://erikbern.com/2016/06/02/approximate-nearest-news.html
    - https://github.com/spotify/annoy
