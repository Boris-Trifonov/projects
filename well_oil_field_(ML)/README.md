# Выбор локации для нефтяной скважины

# Цель исследования:
- Построить модель, которая поможет определить регион, где добыча нефти принесёт наибольшую прибыль.

# Задачи
- Определить значения признаков для каждого месторождения в избранном регионе.
- Построить модель и оценить объём запасов.
- Выбрать месторождения с самым высокими оценками значений, в зависимости от бюджета компании и стоимости разработки одной скважины;
- Проанализировать возможную прибыль и риски техникой Bootstrap.

# Условия задачи:
- Для обучения модели подходит только линейная регрессия (остальные — недостаточно предсказуемые).
- При разведке региона исследуют 500 точек, из которых с помощью машинного обучения выбирают 200 лучших для разработки.
- Бюджет на разработку скважин в регионе — 10 млрд рублей.
- При нынешних ценах один баррель сырья приносит 450 рублей дохода. Доход с каждой единицы продукта составляет 450 тыс. рублей, поскольку объём указан в тысячах баррелей.
- После оценки рисков нужно оставить лишь те регионы, в которых вероятность убытков меньше 2.5%. Среди них выбирают регион с наибольшей средней прибылью.
- Данные синтетические.

# Используемые библиотеки:
pandas, seaborn, Matplotlib, numpy, sklearn.

# Основные выводы:
- Изучили данные:
  - Пропусков, дубликатов и выбросов в данных нет.
  - Признак f2 в df_1 имеет сильную прямую корреляцию с целевым признаком (1.0). По остальным признакам во всех датасетах корреляция слабая средняя или отсутствует.

- Подготовили данные: Стандартизировали численные признаки:
  - Данные разбиты на выборки и масштабированы.

- Модели обучены (LinearRegression) и проверены на валидационных выборках.
  - Посчитаны средние запасы предсказанного сырья и rmse для всех 3х регионов.
  - Наилучший прогноз у региона df_1 (RMSE модели: 0.89)
  - Предсказанные средние запасы сырья на валидационных выборках очень близки к истинным средним. Получили хорошую адекватную модель.

- Проведена подготовка к расчёту прибыли.
  - Ключевые значения для расчётов сохранины в отдельных переменных
  - Рассчитан достаточный объём сырья для безубыточной разработки новой скважины: 111 тыс баррелей.
  - Написали функцию для расчёта прибыли по выбранным 200 самым прибыльным скважинам и предсказаниям модели.
  - Прибыль для региона df_0: 3_320_826_043.14 руб.
  - Прибыль для региона df_1: 2_415_086_696.68 руб.
  - Прибыль для региона df_2: 2_710_349_963.60 руб.

- Рассчитали риски и прибыль для каждого региона:
  - Проведена процедура Bootstrap
  - Наилучшие показатели у региона df_1. Данный регион рекомендован для hазработки месторождения. Его показатели:
  - Средняя прибыль: 456_045_105.79 руб.
  - 0.025-й квантиль: 33_820_509.40 руб.
  - 0.975-й квантиль: 852_289_453.87 руб.
  - Вероятность убытков: 1.50%
