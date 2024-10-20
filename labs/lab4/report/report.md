---
## Front matter
title: "Отчет по лабораторной работе №4"
subtitle: "Системы линейных уравнений"
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
lot: false # List of tables
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

Освоить навыки работы с системой линейных уравнений в Octave.

# Теоретическое введение

## Метод Гаусса__

Запишем исходную систему

$$
 \begin{cases}
   a_{1}^{1}x^{1}+...+ a_{n}^{1}x^{n} = b^{1} \\
   ... \\
   a_{1}^{m}x^{1}+...+ a_{n}^{m}x^{n} = b^{m}
 \end{cases}
$$

в матричном виде: $Ax=b$. Матрица A называется основной матрицей системы, b — столбцом свободных членов. 
Алгоритм решения СЛАУ методом Гаусса подразделяется на два этапа:

- на первом этапе осуществляется так называемый прямой ход, когда путём элементарных преобразований над строками 
систему приводят к ступенчатой или треугольной форме, либо устанавливают, что система несовместна;

- на втором этапе осуществляется так называемый обратный ход, суть которого заключается в том, чтобы выразить 
все получившиеся базисные переменные через небазисные и построить фундаментальную систему решений, либо, если все 
переменные являются базисными, то выразить в численном виде единственное решение системы линейных уравнений.

Для приведения матрицы к треугольному виду для системы уравнений $Ax=b$ используют расширенную матрицу.

## LU-разложение

LU-разложение — это вид факторизации матриц для метода Гаусса. Цель состоит в том,
чтобы записать матрицу A в виде $A = LU$, где L — нижняя треугольная матрица, а U — верхняя треугольная матрица. 
Эта факторизованная форма может быть использована для решения уравнения $Ax=b$.

Если известно LU-разложение матрицы A, то исходная система может быть записана как $LUx=b$. 
Эта система может быть решена в два шага. На первом шаге решается система $Ly=b$. 
Поскольку L — нижняя треугольная матрица, эта система решается непосредственно прямой подстановкой. На втором шаге решается система $Ux=y$. 
Поскольку U — верхняя треугольная матрица, эта система решается непосредственно обратной подстановкой.

## LUP-разложение

Если используются чередования строк, то матрица A умножается на матрицу переста-
новок, и разложение принимает форму $PA=LU$.


# Выполнение лабораторной работы

1. Я выполнил все дейсвия с для решения системы линейных уравнений.

```
octave:2> diary on
octave:2> B = [ 1 2 3 4 ; 0 -2 -4 6 ; 1 -1 0 0 ]
B =

   1   2   3   4
   0  -2  -4   6
   1  -1   0   0

octave:3> B (2, 3)
ans = -4
octave:4> B (1, :)
ans =

   1   2   3   4

octave:5> B(3,:) = (-1) * B(1,:) + B(3,:)
B =

   1   2   3   4
   0  -2  -4   6
   0  -3  -3  -4

octave:6> B(3,:) = -1.5 * B(2,:) + B(3,:)
B =

    1    2    3    4
    0   -2   -4    6
    0    0    3  -13

octave:7> rref(B)
ans =

   1.0000        0        0   5.6667
        0   1.0000        0   5.6667
        0        0   1.0000  -4.3333

octave:8> format long
octave:9> rref(B)
ans =

   1.000000000000000                   0                   0   5.666666666666667
                   0   1.000000000000000                   0   5.666666666666666
                   0                   0   1.000000000000000  -4.333333333333333

octave:10> format short
octave:11> A = B(:,1:3)
A =

   1   2   3
   0  -2  -4
   0   0   3

octave:12>  b = B (:,4)
b =

    4
    6
  -13

octave:13>  b = B(:,4)
b =

    4
    6
  -13

octave:14> A\b
ans =

   5.6667
   5.6667
  -4.3333

octave:15> A = [1 2 3; 0 -2 -4; 1 -1 0]
A =

   1   2   3
   0  -2  -4
   1  -1   0

octave:16> rref(A)
ans =

   1   0   0
   0   1   0
   0   0   1

octave:17> lu(A)
ans =

   1.0000   2.0000   3.0000
   1.0000  -3.0000  -3.0000
        0   0.6667  -2.0000

octave:18> [L U P] = lu (A)
L =

   1.0000        0        0
   1.0000   1.0000        0
        0   0.6667   1.0000

U =

   1   2   3
   0  -3  -3
   0   0  -2

P =

Permutation Matrix

   1   0   0
   0   0   1
   0   1   0

octave:19> diary off

```

# Выводы

Я изучил встроенные в Octave алгоритмы, необходимые для решения систем линейных уравнений.

