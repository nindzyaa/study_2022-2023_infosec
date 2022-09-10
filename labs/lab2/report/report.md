---
## Front matter
title: "Лабораторная работа №2"
subtitle: "Основы информационной безопасности"
author: "Царитова Нина"

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
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
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
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы
- Получение практических навыков работы в консоли с атрибутами файлов
- Закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.


# Выполнение лабораторной работы

## Выполнение задания

Создаём новую учётную запись guest, используя команду useradd guest-f
Задаем пароль с помощью команды passwd guest, используя учетную запись администратора.

![Создание учётной записи](image/1.jpg){ #fig:001 width=70% }

Входим в систему от имени пользователя guest и определяем директорию, в которой находимся, с помощью команды pwd. Сравнивая с приглашением командной строки, определяем сходство и факт, что это наша домашнаяя директория. 

Командой whoami уточняем имя пользователя - guest.

Уточним имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Получаем результат 1001.

Сравним вывод id c приглашением командной строки - имя пользователя повторяется. 

Просмотрим файл /etc/passwd командой cat /etc/passwd.

![whoami](image/2.jpg){ #fig:002 width=70% }

Найдём в нём свою учётную запись. Определим uid пользователя - 1000. Определим gid пользователя - 1000.

Определим существующие в системе директории командой ls -l /home/. 
Нам удалось получить список поддиректорий. У каждой из них установлены права на чтение, запись и выполнение только для самого пользователя.

Проверяем, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home

Нам удалось увидеть расширенные атрибуты директории, но не удалось увидеть расширенные атрибуты директорий других пользователей.

Создадим в домашней директории поддиректорию dir1 командой mkdir dir1

Определим командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1.

Снимем с директории dir1 все атрибуты командой chmod 000 dir1 и проверим с её помощью правильность выполнения команды ls -l. 

![Снятие аттрибутов](image/3.jpg){ #fig:003 width=70% }

Попытаемся создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1, но получим отказ от выполнения, так как шагом ранее сняли все атрибуты с директории. Проверим, действительно ли файл не создался, с помощью команды ls -l /home/guest/dir1.

Заполним таблицу «Установленные права и разрешённые действия». (рис. -@fig:004)

![Права на действия](image/4.jpg){ #fig:004 width=100% }

Заполним таблицу «Минимальные права для совершения операций». (рис. -@fig:005)

![Минимальные права](image/5.jpg){ #fig:005 width=100% }

# Выводы

Получил практические навыки работы в консоли с атрибутами файлов, закрепил теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.
