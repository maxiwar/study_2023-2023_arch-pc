﻿







**Лабораторная работа 8**
### **Команды безусловного и условного переходов в Nasm.**
### **Программирование ветвлений**

## герра гарсия максимиано антонио




**Содержание**

1. [Цель работы](#_bookmark0)	5**
1. [**Задание](#_bookmark1)	**6**
1. [**Теоретическое введение](#_bookmark2)	**7**
1. [**Выполнение лабораторной работы](#_bookmark3)	**8**
1. [**Выводы](#_bookmark19)	**24**

[**Список литературы](#_bookmark20)	**25**





**Список иллюстраций**
[4.1	Файл lab8-1.asm:](#_bookmark4)  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .	9

2. [Программа lab8-1.asm:](#_bookmark5)	10
2. [Файл lab8-1.asm:](#_bookmark6)	11
2. [Программа lab8-1.asm:](#_bookmark7)	12
2. [Файл lab8-1.asm](#_bookmark8)	12
2. [Программа lab8-1.asm](#_bookmark9)	13
2. [Файл lab8-2.asm](#_bookmark10)	14
2. [Программа lab8-2.asm](#_bookmark11)	15
2. [Файл листинга lab8-2](#_bookmark12)	16
2. [ошибка трансляции lab8-2](#_bookmark13)	18
2. [файл листинга с ошибкой lab8-2](#_bookmark14)	19
2. [Файл lab8-3.asm](#_bookmark15)	20
2. [Программа lab8-3.asm](#_bookmark16)	21
2. [Файл lab8-4.asm](#_bookmark17)	22
2. [Программа lab8-4.asm](#_bookmark18)	23






1. # **Цель работы**

Целью работы является изучение команд условного и безусловного перехо- дов. Приобретение навыков написания программ с использованием переходов. Знакомство с назначением и структурой файла листинга.







1. # **Задание**

1. Изучите примеры программ.

1. Изучите файл листинга.

1. Напишите программу нахождения наименьшей из 3 целочисленных пере- менных a,b и c. Значения переменных выбрать из табл. 8.5 в соответствии с вариантом, полученным при выполнении лабораторной работы № 7. Со- здайте исполняемый файл и проверьте его работу
1. Напишите программу, которая для введенных с клавиатуры значений x и a вычисляет значение заданной функции f(x) и выводит результат вы- числений. Вид функции f(x) выбрать из таблицы 8.6 вариантов заданий в соответствии с вариантом, полученным при выполнении лабораторной ра- боты № 7. Создайте исполняемый файл и проверьте его работу для значений X и a из 8.6.







1. # **Теоретическое введение**

Для реализации ветвлений в ассемблере используются так называемые ко- манды передачи управления или команды перехода. Можно выделить 2 типа переходов:

- условный переход – выполнение или не выполнение перехода в определен- ную точку программы в зависимости от проверки условия.
- безусловный переход – выполнение передачи управления в определенную точку программы без каких-либо условий.

Листинг (в рамках понятийного аппарата NASM) — это один из выходных файлов, создаваемых транслятором. Он имееттекстовый вид и нужен при отладке программы, так как кроме строк самой программы он содержит дополнительную информацию.







1. # **Выполнение лабораторной работы**

1. Создайте каталог для программам лабораторной работы № 8, перейдите в него и создайте файл lab8-1.asm
1. Инструкция jmp в NASM используется для реализации безусловных пере- ходов. Рассмотрим пример программы с использованием инструкции jmp. Введите в файл lab8-1.asm текст программы из листинга 8.1. (рис. [4.1)](#_bookmark4)

![lab8](/home/gagerra/загрузки/1.jpg )
Рис. 4.1: Файл lab8-1.asm: Создайте исполняемый файл и запустите его. (рис. [4.2)](#_bookmark5)


![lab8](/home/gagerra/загрузки/2.jpg )
Рис. 4.2: Программа lab8-1.asm:

Инструкция jmp позволяет осуществлять переходы не только вперед но и назад. Изменим программу таким образом, чтобы она выводила сначала ‘Сообщение

№ 2’, потом ‘Сообщение № 1’ и завершала работу. Для этого в текст программы после вывода сообщения № 2 добавим инструкцию jmp с меткой \_label1 (т.е. переход к инструкциям вывода сообщения № 1) и после вывода сообщения № 1 добавим инструкцию jmp с меткой \_end (т.е. переход к инструкции call quit). Измените текст программы в соответствии с листингом 8.2. (рис. [4.3, ](#_bookmark6)[4.4)](#_bookmark7)

![lab8](/home/gagerra/загрузки/3.jpg )
Рис. 4.3: Файл lab8-1.asm:

![lab8](/home/gagerra/загрузки/4.jpg )
Рис. 4.4: Программа lab8-1.asm:

Изменитетекст программы добавив или изменив инструкции jmp, чтобы вывод программы был следующим (рис. [4.5, ](#_bookmark8)[4.6):](#_bookmark9)

Сообщение № 3

Сообщение № 2

Сообщение № 1

![lab8](/home/gagerra/загрузки/5.jpg )
Рис. 4.5: Файл lab8-1.asm

![lab8](/home/gagerra/загрузки/6.jpg )
Рис. 4.6: Программа lab8-1.asm

1. Использование инструкции jmp приводит к переходу в любом случае. Од- нако, часто при написании программ необходимо использовать условные переходы, т.е. переход должен происходить если выполнено какое-либо условие. В качестве примера рассмотрим программу, которая определяет и выводит на экран наибольшую из 3 целочисленных переменных: A,B и

C. Значения для A и C задаются в программе, значение B вводиться с кла- виатуры. Создайте исполняемый файл и проверьте его работу для разных значений B. (рис. [4.7, ](#_bookmark10)[4.8)](#_bookmark11)


![lab8](/home/gagerra/загрузки/7.jpg )
Рис. 4.7: Файл lab8-2.asm

![lab8](/home/gagerra/загрузки/8.jpg )
Рис. 4.8: Программа lab8-2.asm

1. Обычно nasm создаёт в результате ассемблирования только объектный файл. Получить файл листинга можно, указав ключ -l и задав имя файла листинга в командной строке. Создайте файл листинга для программы из файла lab8-2.asm (рис. [4.9)](#_bookmark12)

![lab8](/home/gagerra/загрузки/9.jpg )
Рис. 4.9: Файл листинга lab8-2

Внимательно ознакомиться с его форматом и содержимым. Подробно объяс- нить содержимое трёх строк файла листинга по выбору.

строка 144

- 144 - номер строки

- 000000BB - адрес

- 80EB30 - машинный код

- sub bl, 48 - код программы строка 145
- 145 - номер строки

- 000000BE - адрес

- 01D8 - машинный код

- add eax, ebx - код программы строка 146
- 146 - номер строки

- 000000C0 - адрес

- BB0A000000 - машинный код

- mov ebx, 10 - код программы

Откройте файл с программой lab8-2.asm и в любой инструкции с двумя опе- рандами удалить один операнд. Выполните трансляцию с получением файла листинга (рис. [4.10,4.11)](#_bookmark14)

![lab8](/home/gagerra/загрузки/10.jpg )
Рис. 4.10: ошибка трансляции lab8-2

![lab8](/home/gagerra/загрузки/11.jpg )
Рис. 4.11: файл листинга с ошибкой lab8-2

1. Напишите программу нахождения наименьшей из 3 целочисленных пере- менных a,b и c. Значения переменных выбрать из табл. 8.5 в соответствии с вариантом, полученным при выполнении лабораторной работы № 7. Со- здайте исполняемый файл и проверьте его работу (рис. [4.12,4.13)](#_bookmark16)

для варианта 10 - 41,62,35


![lab8](/home/gagerra/загрузки/12.jpg )
Рис. 4.12: Файл lab8-3.asm

![lab8](/home/gagerra/загрузки/13.jpg )
Рис. 4.13: Программа lab8-3.asm

1. Напишите программу, которая для введенных с клавиатуры значений x и a вычисляет значение заданной функции f(x) и выводит результат вы- числений. Вид функции f(x) выбрать из таблицы 8.6 вариантов заданий в соответствии с вариантом, полученным при выполнении лабораторной ра- боты № 7. Создайте исполняемый файл и проверьте его работу для значений X и a из 8.6. (рис. [4.14,4.15)](#_bookmark18)

для варианта 10

#### ⎧{𝑎 − 7, 𝑎 ≥ 7
#### ⎨{⎩𝑎𝑥, 𝑎 < 7


![lab8](/home/gagerra/загрузки/14.jpg )
Рис. 4.14: Файл lab8-4.asm

![lab8](/home/gagerra/загрузки/15.jpg )
Рис. 4.15: Программа lab8-4.asm







1. # **Выводы**

В заключение мы изучили команды условного и безусловного перехода и узнали о файле листинга.







# **Список литературы**

1. [Расширенный ассемблер: NASM](https://www.opennet.ru/docs/RUS/nasm/)
1. [MASM, TASM, FASM, NASM под Windows и Linux](https://habr.com/ru/post/326078/)
