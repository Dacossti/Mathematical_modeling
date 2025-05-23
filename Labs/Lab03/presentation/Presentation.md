---
## Front matter
title: "Презентация по лабораторной работе №3"
subtitle: "Модель боевых действий"
author: "Озьяс Стев Икнэль Дани"

## Generic otions
lang: ru-RU

## Formatting
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

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Озьяс Стев Икнэль Дани
  * студент группы НКНбд-01-21
  * Российский университет дружбы народов
  * <https://github.com/Dacossti>

:::
::: {.column width="30%"}

![](./image/ava.jpg)

:::
::::::::::::::

# Цели и задачи работы

## Цель лабораторной работы
 
Рассматривать 2 случая ведения боевых действий по модели Ланчестера:
1. Боевые действия между регулярными войсками
2. Боевые действия с участием регулярных войск и партизанских отрядов

## Задание к лабораторной работе

1. Изучать модель Ланчестера
2. Построить графики для обеих армий
3. Определить кто из них победитель

# Процесс выполнения лабораторной работы

## Теоретический материал 

Будем рассматривать 2 случая ведения боевых действий: 
1. Боевые действия между регулярными войсками 
2. Боевые действия с участием регулярных войск и партизанских отрядов 

В первом случае численность регулярных войск определяется тремя факторами:

1. скорость уменьшения численности войск из-за причин, не связанных с боевыми действиями (болезни, травмы, дезертирство);
2. скорость потерь, обусловленных боевыми действиями противоборствующих сторон (что связанно с качеством стратегии, уровнем вооружения, профессионализмом солдат и т.п.);
3. скорость поступления подкрепления (задаётся некоторой функцией от времени). 

## Теоретический материал 

В этом случае модель боевых действий между регулярными войсками описывается следующим образом

$$
 \begin{cases}
	\frac{dx}{dt}= -a(t)x(t) - b(t)y(t) + P(t)
	\\   
	\frac{dy}{dt}= -c(t)x(t) - h(t)y(t) + Q(t)
 \end{cases}
$$

Потери, не связанные с боевыми действиями, описывают члены $–a(t)x(t)$ и $–h(t)y(t)$, члены $–b(t)y(t)$ и $–c(t)x(t)$ отражают потери на поле боя. Коэффициенты $b(t)$, $c(t)$ указывают на эффективность боевых действий со стороны $y$ и $x$ соответственно, $a(t)$,$h(t)$  - величины, характеризующие степень влияния различных факторов на потери. Функции $P(t)$,$Q(t)$  учитывают возможность подхода подкрепления к войскам $X$ и $Y$ в течение одного дня. 

## Теоретический материал 

Во втором случае в борьбу добавляются партизанские отряды. Нерегулярные войска в отличии от постоянной армии менее уязвимы, так как действуют скрытно, в этом случае сопернику приходится действовать неизбирательно, по площадям, занимаемым партизанами. Поэтому считается, что темп потерь партизан, проводящих свои операции в разных местах на некоторой известной территории, пропорционален не только численности армейских соединений, но и численности самих партизан. В результате модель принимает вид:

$$
 \begin{cases}
	\frac{dx}{dt}= -a(t)x(t) - b(t)y(t) + P(t)
	\\   
	\frac{dy}{dt}= -c(t)x(t)y(t) - h(t)y(t) + Q(t)
 \end{cases}
$$

## Решение

Между страной $X$ и страной $Y$ идет война. Численность состава войск исчисляется от начала войны, и являются временными функциями $x(t)$ и $y(t)$
В начальный момент времени страна $X$ имеет армию численностью 88000 человек, 
а в распоряжении страны $Y$ армия численностью в 99000 человек.
Для упрощения модели считаем, что коэффициенты $a, b, c, h$ постоянны. 
Также считаем $P(t), Q(t)$ непрерывные функции

## Решение

Постройте графики изменения численности войск армии $X$ и армии $Y$ для следующих случаев:

1. Модель боевых действий между регулярными войсками

$$
 \begin{cases}
	\frac{dx}{dt}= -0.45x(t) - 0.55y(t) + sin(t + 15)
	\\   
	\frac{dy}{dt}= -0.58x(t) - 0.45y(t) + cos(t + 3)
 \end{cases}
$$

![График изменения численности в случае 1 (Julia)](image/image1.png){ #fig:003 width=70% height=70% }

По решению модели Ланчестера оказывается что армия $Y$ - победитель.

## Решение

2. Модель ведение боевых действий с участием регулярных войск и партизанских отрядов

$$
 \begin{cases}
	\frac{dx}{dt}= -0.37(t) - 0.67y(t) + sin(7t) + 1
	\\   
	\frac{dy}{dt}= -0.57x(t)y(t) - 0.39y(t) + cos(8t) + 1
 \end{cases}
$$

![График изменения численности в случае 2 (Julia)](image/image2.png){ #fig:005 width=70% height=70% }

По решению модели Ланчестера оказывается что армия $X$ - победитель.

# Выводы по проделанной работе

## Вывод

В результате проделанной лабораторной работы мы познакомились с моделями Ланчестнера. 
Проверили, как работает модель в различных ситуациях, построили графики $x(t)$ и $y(t)$ в рассматриваемых случаях.