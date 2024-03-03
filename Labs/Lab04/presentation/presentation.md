---
## Front matter
lang: ru-RU
title: Модель гармонических колебаний
author: |
         Озьяс Стев Икнэль Дани

institute: |
         Российский Университет Дружбы Народов

date: 24 февраля, 2024, Москва, Россия

## Formatting
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true
---

# Цели и задачи работы

## Цель лабораторной работы
 
Построить фазовый портрет гармонического осциллятора и решение уравнения гармонического осциллятора для следующих случаев:
1. Колебания гармонического осциллятора без затуханий и без действий внешнейсилы
2. Колебания гармонического осциллятора c затуханием и без действий внешнейсилы
3. Колебания гармонического осциллятора c затуханием и под действием внешнейсилы

## Задание к лабораторной работе

1. Изучать модель гармонических колебаний
2. Построить фазовый портрет гармонического осциллятора и решение уравнениягармонического осциллятора

# Процесс выполнения лабораторной работы

## Теоретический материал 

Движение грузика на пружинке, маятника, заряда в электрическом контуре, а
также эволюция во времени многих систем в физике, химии, биологии и других
науках при определенных предположениях можно описать одним и тем же
дифференциальным уравнением, которое в теории колебаний выступает в качестве
основной модели. Эта модель называется линейным гармоническим осциллятором.
Уравнение свободных колебаний гармонического осциллятора имеет
следующий вид:		

x'' + 2 g x' + w^2 x = 0

где x – переменная, описывающая состояние системы (смещение грузика, заряд конденсатора и т.д.),  – параметр, характеризующий потери энергии (трение в механической системе, сопротивление в контуре), w – собственная частота колебаний, t – время.


## Решение

Постройте фазовый портрет гармонического осциллятора и решение уравнения гармонического осциллятора для следующих случаев:

1. Колебания гармонического осциллятора без затуханий и без действий внешней силы
x'' + 9 x = 0

![Фазовый портрет №1 (Julia)](image/image1.png){ #fig:003 width=70% height=70% }

2. Колебания гармонического осциллятора c затуханием и без действий внешней силы
x'' + 5.5 x' + 4.4 x = 0

![Фазовый портрет №2 (Julia)](image/image1.png){ #fig:003 width=70% height=70% }

3. Колебания гармонического осциллятора c затуханием и под действием внешней силы
x'' + x' + 6 x = 0

![Фазовый портрет №3 (Julia)](image/image1.png){ #fig:003 width=70% height=70% }

# Выводы по проделанной работе

## Вывод

В результате проделанной лабораторной работы мы познакомились с моделем гармонических колебаний. 
Проверили, как работает модель в различных ситуациях, построили фазовые портреты в рассматриваемых случаях.

# Список литературы

1. [Гармонические_колебания](https://ru.wikipedia.org/wiki/Гармонические_колебания)