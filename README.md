# Cопоставление и поиск наиболее похожих товаров

## Задача

- разработать алгоритм, который для всех товаров из validation.csv предложит несколько вариантов наиболее похожих товаров из base;
- оценить качество алгоритма по метрике accuracy@5
- *деплой: разработать REST API сервис, который по предложенным данным будем предлагать несколько похожих товаров.

В рамках проекта вы поработаете с реальными сырыми данными от одного из крупнейших маркетплейсов страны.
Вас ждет интересная задача сопоставления и поиска наиболее похожих товаров.
Сопоставление или “мэтчинг” (англ. matching - соответствия) - одна из базовых задач машинного обучения, которая встречается в информационном поиске, компьютерном зрении, рекомендательных системах и др.

Вы познакомитесь с алгоритмами приближённого поиска ближайщих соседей, научитесь создавать индексы в векторных базах данных и обучать ранжирующие модели. Эти навыки востребованы во многих сферах и позволят вам решать еще более интересные и сложные задачи.
А по завершению проекта вы сможете пополнить резюме ещё одним интересным кейсом в портфолио.

## Используемые библиотеки

pandas, numpy, faiss, datetime, adjdatatools, sklearn, catboost

## Данные

base.csv - анонимизированный набор товаров. Каждый товар представлен как уникальный id (0-base, 1-base, 2-base) и вектор признаков размерностью 72.

train.csv - обучающий датасет. Каждая строчка - один товар, для которого известен уникальный id (0-query, 1-query, …) , вектор признаков И id товара из base.csv, который максимально похож на него (по мнению экспертов).

validation.csv - датасет с товарами (уникальный id и вектор признаков), для которых надо найти наиболее близкие товары из base.csv.

validation_answer.csv - правильные ответы к предыдущему файлу.

## Результаты

Предварительный анализ данных
-----------------------------

Все три набора данных зашифрованы. Для каждого образца товара имеется **72 характеристики**, все представляют собой дробные числа. Пропусков и дубликатов нет ни в одном наборе. Данные ненормированные – диапазоны их значений отличаются.

**Характер распределений** для каждого признака одинаков по всем трем датасетам. 61 признак из 72 имеет распределение, близкое к нормальному. Распределения 11 признаков отличаются: либо имеют несколько самых популярных значений, либо их можно разбить на несколько групп. Графики распредений признаков хранятся в папке charts.

Предобработка данных
---------------------

**Проведена нормализация данных**. В результате диапазоны значений всех признаков лежат внутри отрезка [-1, 1]. Медианное значение приравнено к нулю в базовом датасете, в остальных незначительно отклоняется от нуля.

Поиск рекомендуемых товаров
---------------------------

Осуществляется в **два шага**.

На первом **отбираются 10** наиболее вероятных кандидатов с помощью библиотеки **FAISS**. **accuracy@10** на этом этапе составляет **58 %**.

На втором этапе с помощью модели машинного обучения **CatBoost из 10 кандидатов для каждого запроса отбирается 5**.

**accuracy@5** модели составляет **29,5 %**