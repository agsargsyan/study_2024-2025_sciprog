---
## Front matter
lang: ru-RU
title: Презентация по лабораторной работе №8
author:
  - Саргсян А. Г.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 30 ноября 2024

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

## Цели и задачи работы

Цель:

Освоить навыки работы со собственными значениями в Octave.

## Поиск собственных значений 
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
```
## Случайное блуждание
```
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
```

## Выводы

Я изучил алгоритмы с поиском собственных значений в 