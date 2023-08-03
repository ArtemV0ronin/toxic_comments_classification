# Классификация токсичных комментариев
Ноутбук проекта находится в файле [toxic_comments_classification.ipynb](https://github.com/ArtemV0ronin/toxic_comments_classification/blob/main/toxic_comments_classification.ipynb)  
Альтернативная [ссылка](https://colab.research.google.com/drive/1uYcvDLjShoEVHigql75q5KGoulXm4gLK#offline=true&sandboxMode=true) на Google Collab.

## Задача проекта
Интернет-магазин «Викишоп» запускает новый сервис. В нём пользователи могут редактировать и дополнять описания товаров, как в вики-сообществах. Клиенты предлагают свои правки и комментируют изменения других. Магазину нужен инструмент, который будет искать токсичные комментарии и отправлять их на модерацию. В нашем распоряжении набор данных с разметкой о токсичности правок.

## Используемый стек
![Static Badge](https://img.shields.io/badge/BertModel-red)
![Static Badge](https://img.shields.io/badge/TfidfVectorizer-red)
![Static Badge](https://img.shields.io/badge/WordNetLemmatizer-red)
![Static Badge](https://img.shields.io/badge/re-red)
![Static Badge](https://img.shields.io/badge/nltk-red)
![Static Badge](https://img.shields.io/badge/torch-red)
![Static Badge](https://img.shields.io/badge/spacy-red)
![Static Badge](https://img.shields.io/badge/sklearn-red)
![Static Badge](https://img.shields.io/badge/LogisticRegression-red)
![Static Badge](https://img.shields.io/badge/DecisionTreeClassifier-red)
![Static Badge](https://img.shields.io/badge/CatBoostClassifier-red)
![Static Badge](https://img.shields.io/badge/Pipeline-red)
![Static Badge](https://img.shields.io/badge/GridSearchCV-red)
![Static Badge](https://img.shields.io/badge/matplotlib-red)
![Static Badge](https://img.shields.io/badge/pandas-red)
![Static Badge](https://img.shields.io/badge/numpy-red)
![Static Badge](https://img.shields.io/badge/tqdm-red)
![Static Badge](https://img.shields.io/badge/time-red)

---

## Итоги проекта

В результате работы были разработаны 2 модели классификации, определяющие токсичность текста.

1. <b>Модель 1</b>

Разработана на базе модели логистической регрессии. Данные на которых обучалась модель были заранее обработаны следующим образом:
- очистка - оставлены только символы английского алфавита в нижнем регистре
- лемматизация - выделены леммы слов с помощью spacy лемматайзера 
- векторизация - текст преобразован в численную форму с помощью TF-DF векторайзера

Всего было протестировано 3 алгоритма моделей машинного обучения. Метрика f1 моделей на кросс-валидации:

<table>
<tr>
  <th>Модель</th>
  <th>f1</th>
</tr>
<tr>
  <td>LogisticRegression</td>
  <td>0.76</td>
</tr>
<tr>
  <td>DecisionTreeClassifier</td>
  <td>0.716</td>
</tr>
<tr>
  <td>CatBoostClassifier</td>
  <td>0.714</td>
</tr>
</table>
<p style="margin-bottom: 30px"></p>

По итогу выбрана наилучшая модель - модель линейной регрессии. 

В результате тестирования метрика качества модели **f1 = 0.752**

<img src="https://drive.google.com/uc?export=view&id=1GA2_NVRbvH2VSFbf1KY42YT3oTsM8y9G">

2. <b>Модель 2</b>

Разработана на базе предобученной BERT модели. Данные заранее не обрабатывались.

Из-за ограниченной мощности ПК полноценно прогнать весь датасет в этой моделе не удалось, поэтому была взята только случайная выборка из 10000 объектов. На предобработанных данных была обучена модель линейной регрессии и найдены наилучшие гиперпараметры. 

В результате тестирования метрика качества модели <b>f1 = 0.705</b>.

<img src="https://drive.google.com/uc?export=view&id=1YLzut8T2-K6Q02KefUYyX31yhoToPCsy">
