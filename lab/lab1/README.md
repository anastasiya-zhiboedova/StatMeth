# Лабораторная работа 1
## Алгоритм получения задания
1. Запустите скрипт get_lab.py.
2. Введите адрес своей электронной почты.
3. Программа вернет номера заданий, которые требуется выполнить.

**Важно:** 18 марта права на изменение репозитория должны быть у всех. Если доступ не был предоставлен, пишите на psad-2020@phystech.edu.

Проверка прав без изменения репозитория: https://stackoverflow.com/questions/22811045/how-can-i-check-write-access-to-a-remote-git-repository-can-i-push


## Cдача задания
1. Создать ветку вида  lab1/Ivanov.
2. В папку заливать ноутбуки (для задач 1, 3) и pdf-файлы с решением (для задач 2, 4).

## Основные критерии оценки за задание
* аккуратность оформления работы;
* наличие выводов;
* обоснованность выбора статистических критериев, учет поправки на множественность гипотез
* в случае работы с синтетическими данными: учет неточностей, связанных со случайным порождением данных
* в случае работы с реальными данными также учитывается предобработка
 
# Задание 1

## Задача 1.1
Проверить мощность и консервативность критериев Лиллиефорса, Харке-Бера, Шапиро-Улика для выборок из следующих распределений:
* Нормальное
* Лапласа
* Стьюдента
* Усеченное нормальное распределение (модуль каждого элемента выборки не превосходит 2)

## Задача 1.2
**Выборка**: [Ирисы Фишера](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_iris.html).

Задана выборка описаний 150 экземпляров ириса разных видов. Описание каждого ириса состоит из четырех признаков:
* Длина наружной доли околоцветника (англ. sepal length);
* Ширина наружной доли околоцветника (англ. sepal width);
* Длина внутренней доли околоцветника (англ. petal length);
* Ширина внутренней доли околоцветника (англ. petal width).

Требуется определить насколько в среднем различается каждая из этих характеристик между разными видами.

Для каждой из данных характеристик выбрать подходящий размер эффекта из https://en.wikipedia.org/wiki/Effect_size#Types.

Посчитать соответствующее значение.

## Задача 1.3
Проверить мощность и консервативность критерия Уликоксона о равенстве медиан для выборок вида: 
X1: ~ alpha * N(0,1) + (1-alpha) * N(2, 4);

X2: ~ alpha * N(0,1) + (1-alpha) * N(2, 4) + delta.

Здесь delta --- сдвиг, дающий возможность разделить выборки X1 и X2.


Изучить зависимость от alpha и delta.

**Важно:** распределение является гауссовой смесью, это не сумма гауссовых величин [пример как сэмплировать](https://stackoverflow.com/questions/49106806/how-to-do-a-simple-gaussian-mixture-sampling-and-pdf-plotting-with-numpy-scipy)

## Задача 1.4

Частота распределения слов в языке описывается [законом Ципфа](https://en.wikipedia.org/wiki/Zipf%27s_law).

Проверить, что он действительно описывает частоту слов (через формальный критерий) на основе анализа двух документов: [Анны Карениной](http://az.lib.ru/t/tolstoj_lew_nikolaewich/text_0080.shtml) и [новостного корпуса](https://object.pouta.csc.fi/OPUS-WMT-News/v2019/mono/ru.txt.gz). Можно ли утверждать, что параметры закона Ципфа для этих двух корпусов совпадают?

**Пояснение по закону Ципфа:** закон Ципфа утверждает, что в выборке из N элементов частота (вероятность) встретить элемент с рангом K равняется:
const / K^a, где a --- параметр распределения.  [Подробнее можно посмотреть здесь](https://statweb.stanford.edu/~owen/courses/306a/ZipfByHera.pdf).

# Задание 2
Все переходы должны быть полностью описаны. Все выкладки и преобразования должны быть явно посчитаны.

## Задача 2.1

Пусть задано две вектора ответов: y — истинный вектор ответов для некоторой выборки, а также есть вектор ответов \hat{y} --- некоторой предсказательной модели. Наблюдатель хочет проверить гипотезу о том, что ровно в 25% случаев модель дает заниженные оценки. 
Предложите метод проверки данной гипотезы: запишите задачу формально, 
предложите статистику для решения данной задачи на уровне значимости alpha = 0.05.
Также найдите зависимость мощности данного критерия в зависимости от истинного
процента заниженных ответов.

## Задача 2.2

Рассмотрим фирму, которая занимается продажей лотерейных билетов. Правила лотереи следующее: все билеты являются выигрышными с вероятностью p. Билеты продаются до тех пор, пока хоть один человек не выиграет (гарантируется, что как только билет купили и он выигрышный, больше билетов не продают).
Из-за вспышки коронавируса все заводы закрылись, а с ними и знание заветного p также пропало. Фирма хочет восстановить p, имея отчет о продажах билетов за
последнии 5 месяцев: 8 билетов, 12 билетов, 7 билетов, 6 билетов и 12 билетов.


**Требуется:**

1. Оцените методом максимального правдоподобия параметр p0.

Теперь фирма нашла на складе несколько ящиков из билетами, которые вы можете использовать для проверки гипотезы о том, что истинное p равняется p0 — оценке
максимального правдоподобия из предыдущего пункта. Для проверки был предложен
следующий эксперимент: последовательно вскрываются n = 100 билетов, и проводился подсчет: сколько выигрышных билетов было из данных N штук. Данный эксперимент проводился 10 раз и были получены следующие результаты: 13, 8, 11, 10, 11, 12,
7, 9, 10, 9.

2. записать задачу формально;
3. предложить статистику для решения данной задачи;
4. получить приближенно нулевое распределение данной статистики;
5. записать явно правило принятия решения на основе статистики и нулевого распределения для обеспечения уровня значимости α = 0.05;
6. проверить гипотезу по записанному критерию, для данных из условия. Противоречат ли они гипотезу?

## Задача 2.3 

Известно, что электричка "Вашингтон-Петушки" аварийно останавливается раз в несколько дней.
Аналитики РЖД проанализировали, сколько дней электричка едет без поломок, и составили выборку:
x = (3, 22, 13, 6, 18, 5, 6, 10, 7, 15).

РЖД хочет проверить гипотезу, что дисперсия распределения равна 9 против правосторонней альтернативы.

**Требуется**:
1. Ввести предположение, каким распределением описывается данная выборка.
2. Записать задачу формально.
3. Предложить критерий для оценки дисперсии распределения.
4. Проверить гипотезу о значении дисперсии распределения для уровня значимости alpha = 0.05 аналитически.
5. Вывести и получить доверительный интервал для значения дисперсии при alpha = 0.05.

## Задача 2.4 
Одеяла с электрообогревом применяются в хирургии для восстановления температуры тела пациента после операции. 
Имеются два вида одеял: стандартный (b0) и экспериментальный (b1). 

Для 14 пациентов известно время, за которое нормальная температура тела восстанавливается при использовании одеяла каждого из видов.

Как понять, отличаются ли экспериментальные одеяла от стандартного?

**Требуется:**
1. Записать задачу формально в виде проверяемой гипотезы и альтернативы.
2. Предложить не менее 2-х критериев и соответствующих статистик для проверки
этой гипотезы и описать:
    * при каких дополнительных условиях (если они есть) стоит применять тот
или иной критерий
    * в чём преимущества/недостатки того или иного критерия
3. Аналитически выразить достигаемый уровень значимости каждого критерия на
выборке или опишите, как его получить с помощью табличных данных.

# Задание 3

## Задача 3.1

Изучить поведение FDR для эксперимента из лекции. Рассмотреть случаи, когда количество объектов m варьируется от 200 от 100000 для следующих поправок:
* Без поправок
* Метод Холма
* Метод Бенджамини-Хохберга

## Задача 3.2 
Дана [статистика бросков для игроков NBA](data/nba.csv)

Выборка представляет собой статистику бросков для различных игроков NBA. Для каждого игрока известны:

* количество успешных бросков в домашних играх (score_home)
* количество бросков в домашних играх (atm_home)
* количество успешных бросков в гостевых играх (score_away)
* количество бросков в гостевых играх (atm_away)

Требуется определить, есть ли разница в успехе бросков у игроков в домашних и гостевых играх.

У какого процента игроков разница в успехе существенна?

## Задача 3.3 
Выборка: [Wine](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html).

Предложить метод выбора наиболее важных признаков для логистической регрессии на основе изученных методов прикладной статистики.
Осуществить выбор.

## Задача 3.4
Даны [результаты работы двух машинных переводчиков на небольших выборках переводов для разных языковых пар](data/mt).

Стандартная оценка качества перевода производится с использованием специальной метрики [BLEU](https://en.wikipedia.org/wiki/BLEU). (Реализовано [здесь](https://www.nltk.org/_modules/nltk/translate/bleu_score.html)).


Требуется опеделить:
* превосходит ли один переводчик в среднем по парам второй переводчик по переводу
* связано ли качество перевода для разных языковых пар для двх переводчиков?

При подсчете BLEU учитывать только слова, регистр не учитывать. 

**Формат данных**

Названиие файлов имеет формат lang1_lang2_<translator_id>.txt:

lang_1, lang_2 --- языки (перевод с lang_1 на lang_2).

gold - эталонный вариант, с которым сравнивается перевод от систем машинного перевода.

# Задание 4
Все переходы должны быть полностью описаны. Все выкладки и преобразования должны быть явно посчитаны.

## Задача 4.1
Рассмотрим данные из [табллицы 1](data/corona.csv) по числу заболевших и выздоровевших от короновируса
в разных странах. Требуется проверить гипотезу о тому, что число выздоровевших
людей в странах не зависит от числа заболевших в стране. 

**Требуется:**
1. записать задачу формально;
2. предложить статистику для решения данной задачи;
3. записать приближенно нулевое распределение данной статистики;
4. записать явно правило принятия решения на основе статистики и нулевого распределения для обеспечения уровня значимости alpha = 0.05;
5. проверить гипотезу по записанному критерию, для данных из условия. Противоречат ли они гипотезу?
6. на уровне значимости alpha = 0.05 найти зависимость мощности критерия в зависимости от истинного значения статистики.

## Задача 4.2
Рассмотрим некоторую задачу классификации. Пусть задано качество 4 моделей a1, a2, a3, a4.
Качество полученных моделей показано в [таблице](data/classifiers.csv). 

Исследователю требуется выбрать наилучшую модель. Для выбора лучшей модели исследовать
требуется попарно сравнить среднее значение качества всех моделей. Может ли исследователь утверждать что какая-то из моделей лучше другой?

**Требуется:**
1. записать задачу формально;
2. предложить статистику для решения данной задачи;
3. записать нулевое распределение данной статистики;
4. записать явно правило принятия решения на основе статистики и нулевого распределения для обеспечения уровня значимости alpha = 0.05;
5. проверить гипотезу по записанному критерию, для данных из условия. Противоречат ли они гипотезе?

## Задача 4.3
Правительство города М. испытывает систему обнаружения нежелаемых лиц по камерам в метро. В качестве демонстрации работоспособности системы была поставлена цель: найти и задержать опасного рецидивиста по имени Николай Вальный, а также его соучастников. Была собрана выборка из 5000 снимков лица, для которых была проверена гипотеза о несовпадении этого снимка с лицами участников команды Н. Вального. Для 100 фотографий нулевая гипотеза была отвергнута на уровне значимости alpha = 0.05.

**Требуется:**
1. Определить, в чем недостаток данного подхода и как можно его улучшить.
2. Предложить наилучший, на ваш взгляд, способ для повышения качества данного решения. 
3. Какую меру качества контролирует данный способ? Какие гарантии
он предоставляет? 
4. В чём недостатки данного способа?
5. Как изменилась мощность при использовании предложенного вами способа относительно изначальной процедуры проверки?
6. Известно, что все 5000 фотографий были сделаны для разных людей, и правительство хочет, чтобы система ни в коем случае не упустила преступников. Ответьте на те же вопросы из пунктов 2-4.
7. Как изменилась мощность при использовании предложенного вами способа относительно предыдущего способа?

