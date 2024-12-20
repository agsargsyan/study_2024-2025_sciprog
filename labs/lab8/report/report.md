---
## Front matter
title: "Отчета по лабораторной работе №8"
author: "Арам Грачьяевич Саргсян"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Освоить алгоритмы работы с задачами на собственные значения.


# Выполнение лабораторной работы

1. Я выполнил все дейсвия с подгонкой полиномиальной кривой и матричными преобразованиями.

```
>> A =[1 2 -3; 2 4 0; 1 1 1]
A =

   1   2  -3
   2   4   0
   1   1   1

>> [v lambda] = eig(A)
v =

  -0.2400 +      0i  -0.7920 +      0i  -0.7920 -      0i
  -0.9139 +      0i   0.4523 + 0.1226i   0.4523 - 0.1226i
  -0.3273 +      0i   0.2322 + 0.3152i   0.2322 - 0.3152i

lambda =

Diagonal Matrix

   4.5251 +      0i                  0                  0
                  0   0.7374 + 0.8844i                  0
                  0                  0   0.7374 - 0.8844i

>> C = A' * A
C =

    6   11   -2
   11   21   -5
   -2   -5   10

>> [v lamda] = eig(C)
v =

   0.876137   0.188733  -0.443581
  -0.477715   0.216620  -0.851390
  -0.064597   0.957839   0.279949

lamda =

Diagonal Matrix

    0.1497         0         0
         0    8.4751         0
         0         0   28.3752

>> T = [1 0.5 0 0 0; 0 0 0.5 0 0; 0 0.5 0 0.5 0; 0 0 0.5 0 0; 0 0 0 0.5 1]
T =

   1.0000   0.5000        0        0        0
        0        0   0.5000        0        0
        0   0.5000        0   0.5000        0
        0        0   0.5000        0        0
        0        0        0   0.5000   1.0000

>> a = [0.2; 0.2; 0.2; 0.2; 0.2];
>> b = [0.5; 0; 0; 0; 0.5];
>> c = [0; 1; 0; 0; 0];
>> d = [0; 0; 1; 0; 0];
>> T^5 * a
ans =

   0.450000
   0.025000
   0.050000
   0.025000
   0.450000

>> T^5 * b
ans =

   0.5000
        0
        0
        0
   0.5000

>> T^5 * c
ans =

   0.6875
        0
   0.1250
        0
   0.1875

>> T^5 * d
ans =

   0.3750
   0.1250
        0
   0.1250
   0.3750

>> T = [0.48 0.51 0.14; 0.29 0.04 0.52; 0.23 0.45 0.34]
T =

   0.480000   0.510000   0.140000
   0.290000   0.040000   0.520000
   0.230000   0.450000   0.340000

>> [v lamda] = eig(T)
v =

  -0.6484  -0.8011   0.4325
  -0.5046   0.2639  -0.8160
  -0.5700   0.5372   0.3835

lamda =

Diagonal Matrix

   1.0000        0        0
        0   0.2181        0
        0        0  -0.3581

>> x = v(:,1)/sum(v(:,1))
x =

   0.3763
   0.2929
   0.3308

>> T^10 * x
ans =

   0.3763
   0.2929
   0.3308

>> T^50 * x
ans =

   0.3763
   0.2929
   0.3308

>> T^50 * x - T^10 * x
ans =

   2.2204e-16
   1.6653e-16
   1.1102e-16

>> diary off

```



# Выводы

Я изучил все представленные алгоритмы для работы с задачами на собственные значения.