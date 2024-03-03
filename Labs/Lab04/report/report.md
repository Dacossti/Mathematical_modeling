---
# Front matter
lang: ru-RU
title: "Отчет по Лабораторной Работе №4"
subtitle: "Модель гармонических колебаний - Вариант 27"
author: "Озьяс Стев Икнэль Дани"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the υalue makes tex try to haυe fewer lines in the paragraph.
  - \interlinepenalty=0 # υalue of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Построить фазовый портрет гармонического осциллятора и решение уравнения гармонического осциллятора для следующих случаев:
1. Колебания гармонического осциллятора без затуханий и без действий внешнейсилы
2. Колебания гармонического осциллятора c затуханием и без действий внешнейсилы
3. Колебания гармонического осциллятора c затуханием и под действием внешнейсилы

# Задание

1. Изучать модель гармонических колебаний
2. Построить фазовый портрет гармонического осциллятора и решение уравнениягармонического осциллятора

# Выполнение лабораторной работы

## Теоретические сведения

Движение грузика на пружинке, маятника, заряда в электрическом контуре, а
также эволюция во времени многих систем в физике, химии, биологии и других
науках при определенных предположениях можно описать одним и тем же
дифференциальным уравнением, которое в теории колебаний выступает в качестве
основной модели. Эта модель называется линейным гармоническим осциллятором.
Уравнение свободных колебаний гармонического осциллятора имеет
следующий вид:		

x'' + 2 g x' + w^2 x = 0

где x – переменная, описывающая состояние системы (смещение грузика, заряд конденсатора и т.д.),  – параметр, характеризующий потери энергии (трение в механической системе, сопротивление в контуре), w – собственная частота колебаний, t – время.


## Задача

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


## Код программы (Julia)

```
using Plots
using DifferentialEquations

#ПЕРВЫЙ СЛУЧАЙ


#Параметры осциллятора
#x'' + g* x' + w^2* x = f(t)
#w - частота
#g - затухание

w = 3;
g = 0.00;

#Правая часть уравнения f(t)

function f(t)
    f = 0;
    return f;
end

#Вектор-функция f(t, x)
#для решения системы дифференциальных уравнений
#x' = y(t, x)
#где x - искомый вектор

function F(du,u, p, t)
    du[1] = u[2];
    du[2] = -w.* w.* u[1] - g.* u[2] + f(t);
end


#Вектор начальных условий
#x(t0) = x0

v0 = [-0.7; 0.7];

#Интервал на котором будет решаться задача
t = (0; 37);

#Решаем дифференциальные уравнения с начальным условием x(t0) = x0 на интервале t
#с правой частью, заданной y и записываем решение в матрицу x

prob = ODEProblem(F, v0, t);
sol = solve(prob);

#Переписываем отдельно x в y1, x' в y2

y1 = [];
y2 = [];

for values in sol.u
    push!(y1, values[1]);
    push!(y2, values[2]);
end

#Рисуем фазовый портрет: зависимость x(x')
display(plot(y1, y2, legend=:topright, label= "Фазовый портрет №1"));

savefig("image1.png")


#ВТОРОЙ СЛУЧАЙ
w = sqrt(4.4);
g = 5.5;

#Правая часть уравнения f(t)

function f(t)
    f = 0;
    return f;
end

#Вектор-функция f(t, x)
#для решения системы дифференциальных уравнений
#x' = y(t, x)
#где x - искомый вектор

function F(du,u, p, t)
    du[1] = u[2];
    du[2] = -w.* w.* u[1] - g.* u[2] + f(t);
end


#Вектор начальных условий
#x(t0) = x0

v0 = [-0.7; 0.7];

#Интервал на котором будет решаться задача
t = (0; 37);

#Решаем дифференциальные уравнения с начальным условием x(t0) = x0 на интервале t
#с правой частью, заданной y и записываем решение в матрицу x

prob = ODEProblem(F, v0, t);
sol = solve(prob);

#Переписываем отдельно x в y1, x' в y2

y1 = [];
y2 = [];

for values in sol.u
    push!(y1, values[1]);
    push!(y2, values[2]);
end

#Рисуем фазовый портрет: зависимость x(x')
display(plot(y1, y2, legend=:topright, label= "Фазовый портрет №2"));

savefig("image2.png")


#ТРЕТИЙ СЛУЧАЙ

w = sqrt(6);
g = 1;

#Правая часть уравнения f(t)

function f(t)
    f = 2*cos(0.5*t);
    return f;
end

#Вектор-функция f(t, x)
#для решения системы дифференциальных уравнений
#x' = y(t, x)
#где x - искомый вектор

function F(du,u, p, t)
    du[1] = u[2];
    du[2] = -w.* w.* u[1] - g.* u[2] + f(t);
end


#Вектор начальных условий
#x(t0) = x0

v0 = [-0.7; 0.7];

#Интервал на котором будет решаться задача
t = (0; 37);

#Решаем дифференциальные уравнения с начальным условием x(t0) = x0 на интервале t
#с правой частью, заданной y и записываем решение в матрицу x

prob = ODEProblem(F, v0, t);
sol = solve(prob);

#Переписываем отдельно x в y1, x' в y2

y1 = [];
y2 = [];

for values in sol.u
    push!(y1, values[1]);
    push!(y2, values[2]);
end

#Рисуем фазовый портрет: зависимость x(x')
display(plot(y1, y2, legend=:topright, label= "Фазовый портрет №3"));

savefig("image3.png")

```

# Выводы

В результате проделанной лабораторной работы мы познакомились с моделем гармонических колебаний. 
Проверили, как работает модель в различных ситуациях, построили фазовые портреты в рассматриваемых случаях.

# Список литературы

1. [Гармонические_колебания](https://ru.wikipedia.org/wiki/Гармонические_колебания)