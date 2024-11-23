---
## Front matter
lang: ru-RU
title: Презентация по лабораторной работе №6
author:
  - Саргсян А. Г.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 23 ноября 2024

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

Освоить навыки работы с интегралами в Octave.

## Расчет определенного интеграла
```
>> function y = f(x)
y = exp (x .^ 2) .* cos (x);
end
>> quad ('f',0,pi/2)
ans = 1.8757
```
## Частичные суммы

![Частичные суммы](image/l6_1.png){#fig:001 width=50%}

## Выводы

Я изучил алгоритмы с интегралами на Octave