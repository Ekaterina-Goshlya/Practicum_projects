# Статистический анализ данных

## Описание проекта
Мы аналитики популярного сервиса аренды самокатов GoFast. Нам передали данные о некоторых пользователях из нескольких городов, а также об их поездках. 

Пользователи сервиса GoFast пользуются мобильным приложением. Сервисом можно пользоваться:
- без подписки
 - абонентская плата отсутствует;
 - стоимость одной минуты поездки — 8 рублей;
 - стоимость старта (начала поездки) — 50 рублей;
- с подпиской Ultra
 - абонентская плата — 199 рублей в месяц;
 - стоимость одной минуты поездки — 6 рублей;
 - стоимость старта — бесплатно.

## Задачи проекта 
Проанализируем данные и проверим некоторые гипотезы, которые могут помочь бизнесу вырасти.

## Выводы

**Исследовательский анализ данных**:

Частота встречаемости городов:
- Самое большое количество пользователей находятся в Пятигорске, а самое маленькое в Москве.

Соотношение пользователей с подпиской и без подписки:
- Количество пользователей без подписки (free) - 54%, превышает количество пользователей с подпиской (ultra) - 46%.

Возраст пользователей:
- Самые младшие пользователи - 12 лет.
- Самые старшие пользователи - 43 года.
- Средний возраст пользователей - 25 лет.

Расстояние, которое пользователь преодолел за одну поездку:
- Самая короткая дистанция - 0.86 км.
- Самая длинная - 7.2 км.
- В основном пользователи проезжают от 2.5 км до 4 км.
- Прослеживаются выбросы примерно в диапазоне <900 и >5800

Продолжительность поездок:
- Самые короткие поездки - по пол минуты. Значение странное, возможно техническая ошибка самоката или пользователь передумал ехать.
- Самая длинная поездка - 40 минут.
- В основном длительность поездки состовляет 13 - 22 минут.
- Прослеживаются выбросы примерно <2 и >34

**Объединение данных**:

- Объединили данные о пользователях, поездках и тарифах в один датафрейм - data.
- Создали два датафрейма на основе data:
data_free - с данными о пользователях без подписки.
data_ultra - с данными о пользователях с подпиской.

- Визуализировали информацию о расстоянии и времени для пользователей обеих категорий:

Для пользователей без подписки - время поездки составляет от 12 до 22 минут, и проезжают от 2 до 4 км.

Для пользователей с подпиской - время поездки составляет от 14 до 22 минут, пик расстояния приходится на 2 до 3,5 км.

Таким образом, можно сделать вывод, что пользователи без подписки в целом совершают более долгие поездки, а также проезжают большее расстояние, чем пользователи с подпиской.   


**Проверка гипотез**: 

- 6.1 Нулевая гипотеза отвергнута. Соответственно, пользователи с подпиской тратят больше времени на поездки, чем пользователи без подписки.
- 6.2 Не получилось отвергнуть нулевую гипотезу. Можно сделать вывод о том, что с большой долей вероятности пользователи с подпиской проезжают расстояние, не превышающее 3130 метров за одну поездку.
- 6.3 Нулевая гипотеза отвергнута, выручка пользователей с подпиской больше выручки пользователей без подписки.
- 6.4 Будем использовать гипотезу о равенстве средних для зависимых (парных) выборок. Метод, который нужно использовать при сравнении: scipy.stats.ttest_rel().
