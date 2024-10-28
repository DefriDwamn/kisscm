# Практическое занятие №2. Менеджеры пакетов

## Задача 1

Вывести служебную информацию о пакете matplotlib (Python). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?

## Решение

```bash
pip show matplotlib
```
### Основные элементы информации о пакете:
- Name: Название пакета.
- Version: Версия пакета.
- Summary: Краткое описание пакета.
- Home-page: Домашняя страница проекта.
- Author: Автор(ы) пакета.
- Author-email: Адрес электронной почты авторов или поддержки пакета.
- License: Лицензия, под которой распространяется пакет.
- Location: Путь к установке пакета в системе.
- Requires: Список зависимостей пакета.
- Required-by: Пакеты, которые зависят от данного пакета.

![img](img/image.png)

Получение пакета без пакетного менеджера:
``` bash
git clone https://github.com/matplotlib/matplotlib.git
```
---
## Задача 2

Вывести служебную информацию о пакете express (JavaScript). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?

## Решение

```bash
npm show express
```

### Основные элементы файла со служебной информацией из пакета:
- name@version | license: Название пакета@Версия пакета | Лицензия.
- keywords: Ключевые слова, описывающие пакет.
- dist.tarball: Ссылка на архив пакета.
- dist.shasum: Контрольная сумма пакета.
- dist.integrity: Интегритетная контрольная сумма пакета.
- dist.unpackedSize: Размер распакованного пакета.
- dependencies: Зависимости пакета.
- maintainers: Список тех, кто поддерживает пакет.
- dist-tags: Теги версий пакета (например, latest и next).
- Published: Дата и автор последней публикации пакета.

![img](img/image1.png)

Получение пакета без пакетного менеджера:
```bash
git clone https://github.com/expressjs/express.git
```
---
## Задача 3

Сформировать graphviz-код и получить изображения зависимостей matplotlib и express.

## Решение

Формирование dot-файла пакета matplotlib для graphviz:
```bash
pipdeptree -p matplotlib --graph-output dot > matplot.dot
```
Содержание matplot.dot:
```
digraph {
        matplotlib [label="matplotlib\n3.9.2"]
        matplotlib -> pyparsing [label=">=2.3.1"]
        matplotlib -> packaging [label=">=20.0"]
        matplotlib -> fonttools [label=">=4.22.0"]
        matplotlib -> contourpy [label=">=1.0.1"]
        matplotlib -> kiwisolver [label=">=1.3.1"]
        matplotlib -> "python-dateutil" [label=">=2.7"]
        matplotlib -> numpy [label=">=1.23"]
        matplotlib -> pillow [label=">=8"]
        matplotlib -> cycler [label=">=0.10"]
        cycler [label="cycler\n0.12.1"]
        pillow [label="pillow\n10.4.0"]
        numpy [label="numpy\n2.1.1"]
        "python-dateutil" [label="python-dateutil\n2.9.0.post0"]
        "python-dateutil" -> six [label=">=1.5"]
        six [label="six\n1.16.0"]
        kiwisolver [label="kiwisolver\n1.4.7"]
        contourpy [label="contourpy\n1.3.0"]
        contourpy -> numpy [label=">=1.23"]
        fonttools [label="fonttools\n4.53.1"]
        packaging [label="packaging\n24.1"]
        pyparsing [label="pyparsing\n2.4.7"]
}
```
![img](img/matplot.png)

Формирование dot-файла пакета express для graphviz:
```bash
    sudo npm install npm2dot -g
    sudo apt install jq
    npm ls -a --json | jq '{name: .name, dependencies: {express: .dependencies.express}}' | npm2dot > express.dot
```

<details>
<summary>Содержание matplot.dot</summary>
<br>
<pre>
digraph{
 root="defri@undefined"
 "defri@undefined" -> "N_1"
 "N_1"[label="express@4.21.0",style="filled",fillcolor="0.06666666666666667 1 1"]
 "N_1" -> "N_2"
 "N_2"[label="accepts@1.3.8",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_2" -> "N_3"
 "N_3"[label="mime-types@2.1.35",style="filled",fillcolor="0.2 1 1"]
 "N_3" -> "N_4"
 "N_4"[label="mime-db@1.52.0",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_2" -> "N_5"
 "N_5"[label="negotiator@0.6.3",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_6"
 "N_6"[label="array-flatten@1.1.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_7"
 "N_7"[label="body-parser@1.20.3",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_7" -> "N_8"
 "N_8"[label="bytes@3.1.2",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_9"
 "N_9"[label="content-type@1.0.5",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_10"
 "N_10"[label="debug@2.6.9",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_11"
 "N_11"[label="depd@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_12"
 "N_12"[label="destroy@1.2.0",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_13"
 "N_13"[label="http-errors@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_14"
 "N_14"[label="iconv-lite@0.4.24",style="filled",fillcolor="0.2 1 1"]
 "N_14" -> "N_15"
 "N_15"[label="safer-buffer@2.1.2",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_7" -> "N_16"
 "N_16"[label="on-finished@2.4.1",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_17"
 "N_17"[label="qs@6.13.0",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_18"
 "N_18"[label="raw-body@2.5.2",style="filled",fillcolor="0.2 1 1"]
 "N_18" -> "N_19"
 "N_19"[label="bytes@3.1.2",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_18" -> "N_20"
 "N_20"[label="http-errors@2.0.0",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_18" -> "N_21"
 "N_21"[label="iconv-lite@0.4.24",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_18" -> "N_22"
 "N_22"[label="unpipe@1.0.0",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_7" -> "N_23"
 "N_23"[label="type-is@1.6.18",style="filled",fillcolor="0.2 1 1"]
 "N_7" -> "N_24"
 "N_24"[label="unpipe@1.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_25"
 "N_25"[label="content-disposition@0.5.4",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_25" -> "N_26"
 "N_26"[label="safe-buffer@5.2.1",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_27"
 "N_27"[label="content-type@1.0.5",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_28"
 "N_28"[label="cookie-signature@1.0.6",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_29"
 "N_29"[label="cookie@0.6.0",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_30"
 "N_30"[label="debug@2.6.9",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_30" -> "N_31"
 "N_31"[label="ms@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_32"
 "N_32"[label="depd@2.0.0",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_33"
 "N_33"[label="encodeurl@2.0.0",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_34"
 "N_34"[label="escape-html@1.0.3",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_35"
 "N_35"[label="etag@1.8.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_36"
 "N_36"[label="finalhandler@1.3.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_36" -> "N_37"
 "N_37"[label="debug@2.6.9",style="filled",fillcolor="0.2 1 1"]
 "N_36" -> "N_38"
 "N_38"[label="encodeurl@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_36" -> "N_39"
 "N_39"[label="escape-html@1.0.3",style="filled",fillcolor="0.2 1 1"]
 "N_36" -> "N_40"
 "N_40"[label="on-finished@2.4.1",style="filled",fillcolor="0.2 1 1"]
 "N_36" -> "N_41"
 "N_41"[label="parseurl@1.3.3",style="filled",fillcolor="0.2 1 1"]
 "N_36" -> "N_42"
 "N_42"[label="statuses@2.0.1",style="filled",fillcolor="0.2 1 1"]
 "N_36" -> "N_43"
 "N_43"[label="unpipe@1.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_44"
 "N_44"[label="fresh@0.5.2",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_45"
 "N_45"[label="http-errors@2.0.0",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_45" -> "N_46"
 "N_46"[label="depd@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_45" -> "N_47"
 "N_47"[label="inherits@2.0.4",style="filled",fillcolor="0.2 1 1"]
 "N_45" -> "N_48"
 "N_48"[label="setprototypeof@1.2.0",style="filled",fillcolor="0.2 1 1"]
 "N_45" -> "N_49"
 "N_49"[label="statuses@2.0.1",style="filled",fillcolor="0.2 1 1"]
 "N_45" -> "N_50"
 "N_50"[label="toidentifier@1.0.1",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_51"
 "N_51"[label="merge-descriptors@1.0.3",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_52"
 "N_52"[label="methods@1.1.2",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_53"
 "N_53"[label="on-finished@2.4.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_53" -> "N_54"
 "N_54"[label="ee-first@1.1.1",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_55"
 "N_55"[label="parseurl@1.3.3",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_56"
 "N_56"[label="path-to-regexp@0.1.10",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_57"
 "N_57"[label="proxy-addr@2.0.7",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_57" -> "N_58"
 "N_58"[label="forwarded@0.2.0",style="filled",fillcolor="0.2 1 1"]
 "N_57" -> "N_59"
 "N_59"[label="ipaddr.js@1.9.1",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_60"
 "N_60"[label="qs@6.13.0",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_60" -> "N_61"
 "N_61"[label="side-channel@1.0.6",style="filled",fillcolor="0.2 1 1"]
 "N_61" -> "N_62"
 "N_62"[label="call-bind@1.0.7",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_62" -> "N_63"
 "N_63"[label="es-define-property@1.0.0",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_63" -> "N_64"
 "N_64"[label="get-intrinsic@1.2.4",style="filled",fillcolor="0.4 1 1"]
 "N_62" -> "N_65"
 "N_65"[label="es-errors@1.3.0",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_62" -> "N_66"
 "N_66"[label="function-bind@1.1.2",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_62" -> "N_67"
 "N_67"[label="get-intrinsic@1.2.4",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_62" -> "N_68"
 "N_68"[label="set-function-length@1.2.2",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_68" -> "N_69"
 "N_69"[label="define-data-property@1.1.4",style="filled",fillcolor="0.4 1 1"]
 "N_69" -> "N_70"
 "N_70"[label="es-define-property@1.0.0",style="filled",fillcolor="0.4666666666666667 1 1"]
 "N_69" -> "N_71"
 "N_71"[label="es-errors@1.3.0",style="filled",fillcolor="0.4666666666666667 1 1"]
 "N_69" -> "N_72"
 "N_72"[label="gopd@1.0.1",style="filled",fillcolor="0.4666666666666667 1 1"]
 "N_68" -> "N_73"
 "N_73"[label="es-errors@1.3.0",style="filled",fillcolor="0.4 1 1"]
 "N_68" -> "N_74"
 "N_74"[label="function-bind@1.1.2",style="filled",fillcolor="0.4 1 1"]
 "N_68" -> "N_75"
 "N_75"[label="get-intrinsic@1.2.4",style="filled",fillcolor="0.4 1 1"]
 "N_68" -> "N_76"
 "N_76"[label="gopd@1.0.1",style="filled",fillcolor="0.4 1 1"]
 "N_76" -> "N_77"
 "N_77"[label="get-intrinsic@1.2.4",style="filled",fillcolor="0.4666666666666667 1 1"]
 "N_68" -> "N_78"
 "N_78"[label="has-property-descriptors@1.0.2",style="filled",fillcolor="0.4 1 1"]
 "N_78" -> "N_79"
 "N_79"[label="es-define-property@1.0.0",style="filled",fillcolor="0.4666666666666667 1 1"]
 "N_61" -> "N_80"
 "N_80"[label="es-errors@1.3.0",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_61" -> "N_81"
 "N_81"[label="get-intrinsic@1.2.4",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_81" -> "N_82"
 "N_82"[label="es-errors@1.3.0",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_81" -> "N_83"
 "N_83"[label="function-bind@1.1.2",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_81" -> "N_84"
 "N_84"[label="has-proto@1.0.3",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_81" -> "N_85"
 "N_85"[label="has-symbols@1.0.3",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_81" -> "N_86"
 "N_86"[label="hasown@2.0.2",style="filled",fillcolor="0.3333333333333333 1 1"]
 "N_86" -> "N_87"
 "N_87"[label="function-bind@1.1.2",style="filled",fillcolor="0.4 1 1"]
 "N_61" -> "N_88"
 "N_88"[label="object-inspect@1.13.2",style="filled",fillcolor="0.26666666666666666 1 1"]
 "N_1" -> "N_89"
 "N_89"[label="range-parser@1.2.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_90"
 "N_90"[label="safe-buffer@5.2.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_91"
 "N_91"[label="send@0.19.0",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_91" -> "N_92"
 "N_92"[label="debug@2.6.9",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_93"
 "N_93"[label="depd@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_94"
 "N_94"[label="destroy@1.2.0",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_95"
 "N_95"[label="encodeurl@1.0.2",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_96"
 "N_96"[label="escape-html@1.0.3",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_97"
 "N_97"[label="etag@1.8.1",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_98"
 "N_98"[label="fresh@0.5.2",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_99"
 "N_99"[label="http-errors@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_100"
 "N_100"[label="mime@1.6.0",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_101"
 "N_101"[label="ms@2.1.3",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_102"
 "N_102"[label="on-finished@2.4.1",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_103"
 "N_103"[label="range-parser@1.2.1",style="filled",fillcolor="0.2 1 1"]
 "N_91" -> "N_104"
 "N_104"[label="statuses@2.0.1",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_105"
 "N_105"[label="serve-static@1.16.2",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_105" -> "N_106"
 "N_106"[label="encodeurl@2.0.0",style="filled",fillcolor="0.2 1 1"]
 "N_105" -> "N_107"
 "N_107"[label="escape-html@1.0.3",style="filled",fillcolor="0.2 1 1"]
 "N_105" -> "N_108"
 "N_108"[label="parseurl@1.3.3",style="filled",fillcolor="0.2 1 1"]
 "N_105" -> "N_109"
 "N_109"[label="send@0.19.0",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_110"
 "N_110"[label="setprototypeof@1.2.0",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_111"
 "N_111"[label="statuses@2.0.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_112"
 "N_112"[label="type-is@1.6.18",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_112" -> "N_113"
 "N_113"[label="media-typer@0.3.0",style="filled",fillcolor="0.2 1 1"]
 "N_112" -> "N_114"
 "N_114"[label="mime-types@2.1.35",style="filled",fillcolor="0.2 1 1"]
 "N_1" -> "N_115"
 "N_115"[label="utils-merge@1.0.1",style="filled",fillcolor="0.13333333333333333 1 1"]
 "N_1" -> "N_116"
 "N_116"[label="vary@1.1.2",style="filled",fillcolor="0.13333333333333333 1 1"]
}
</pre>
</details>

![img](img/express.jpg)
---
## Задача 4

Изучить основы программирования в ограничениях. Установить MiniZinc, разобраться с основами его синтаксиса и работы в IDE.

Решить на MiniZinc задачу о счастливых билетах. Добавить ограничение на то, что все цифры билета должны быть различными (подсказка: используйте all_different). Найти минимальное решение для суммы 3 цифр.

## Решение

```mzn
include "alldifferent.mzn";
array[1..6] of var 0..9: digits; 

constraint sum(digits[1..3]) = sum(digits[4..6]);

constraint all_different(digits);

constraint digits[1] < digits[2];
constraint digits[2] < digits[3];

constraint digits[4] < digits[5];
constraint digits[5] < digits[6];

var int: sumall = sum(digits[1..3]);
solve minimize sum(digits[1..3]);
```
![img](img/image2.png)
---
## Задача 5

Решить на MiniZinc задачу о зависимостях пакетов для рисунка, приведенного ниже.    

![img](img/pubgrub.png)

## Решение

```
int: menu_count = 6;
int: dropdown_count = 5;
int: icons_count = 2;

array[1..menu_count] of tuple(int, int, int): menu_versions = 
  [(1,0,0), (1,1,0), (1,2,0), (1,3,0), (1,4,0), (1,5,0)];

array[1..dropdown_count] of tuple(int, int, int): dropdown_versions = 
  [(1,8,0), (2,0,0), (2,1,0), (2,2,0), (2,3,0)];

array[1..icons_count] of tuple(int, int, int): icons_versions = 
  [(1,0,0), (2,0,0)];

tuple(int, int, int): root_version = (1,0,0);
  
var 1..menu_count: menu;
var 1..dropdown_count: dropdown;
var 1..icons_count: icons;

constraint (menu_versions[menu] == (1,0,0) \/ menu_versions[menu] == (1, 5, 0) /\ icons_versions[icons] == (1, 0, 0));

constraint (menu_versions[menu].2 >= 1 /\ menu_versions[menu].2 <= 5) -> (dropdown_versions[dropdown] == (2, 3, 0) \/ dropdown_versions[dropdown] == (2, 0, 0));

constraint menu_versions[menu] == (1, 0, 0) -> dropdown_versions[dropdown] == (1, 8, 0);

constraint (dropdown_versions[dropdown].2 >= 0 /\ dropdown_versions[dropdown].2 <= 3) -> icons_versions[icons] == (2, 0, 0);

solve satisfy;

output [
  "Menu version: ", show(menu_versions[menu]), "\n",
  "Dropdown version: ", show(dropdown_versions[dropdown]), "\n",
  "Icons version: ", show(icons_versions[icons]), "\n"
];

```
![img](img/image3.png)
---
## Задача 6

Решить на MiniZinc задачу о зависимостях пакетов для следующих данных:

```
root 1.0.0 зависит от foo ^1.0.0 и target ^2.0.0.
foo 1.1.0 зависит от left ^1.0.0 и right ^1.0.0.
foo 1.0.0 не имеет зависимостей.
left 1.0.0 зависит от shared >=1.0.0.
right 1.0.0 зависит от shared <2.0.0.
shared 2.0.0 не имеет зависимостей.
shared 1.0.0 зависит от target ^1.0.0.
target 2.0.0 и 1.0.0 не имеют зависимостей.
```

## Решение

```
int: foo_count = 2;
int: left_count = 1;
int: right_count = 1;
int: shared_count = 2;
int: target_count = 2;

array[1..foo_count] of tuple(int, int, int): foo_versions = 
[(1,0,0), (1,1,0)];

array[1..left_count] of tuple(int, int, int): left_versions = 
[(1,0,0)];

array[1..right_count] of tuple(int, int, int): right_versions = 
[(1,0,0)];

array[1..shared_count] of tuple(int, int, int): shared_versions = 
[(1,0,0), (2,0,0)];

array[1..target_count] of tuple(int, int, int): target_versions = 
[(1,0,0), (2,0,0)];

tuple(int, int, int): root_version = (1,0,0);


var 1..foo_count: foo;
var 1..left_count: left;
var 1..right_count: right;
var 1..shared_count: shared;
var 1..target_count: target;


constraint (foo_versions[foo].1 == 1 /\ foo_versions[foo].2 >= 0) 
/\ (target_versions[target].1 == 2 /\ target_versions[target].2 >= 0); 

constraint foo_versions[foo] == (1, 1, 0) -> 
(left_versions[left].1 == 1 /\ left_versions[left].2 >= 0) 
/\ (right_versions[right].1 == 1 /\ right_versions[right].2 >= 0); 


constraint left_versions[left] == (1, 0, 0) ->
(shared_versions[shared].1 >= 1);

constraint right_versions[right] == (1, 0, 0) ->
(shared_versions[shared].1 < 2);

constraint shared_versions[shared] == (1, 0, 0) ->
(target_versions[target].1 == 1 /\ target_versions[target].2 >= 0);

solve satisfy;

output [
"Root version: ", show(root_version), "\n",
"Foo version: ", show(foo_versions[foo]), "\n",
"Left version: ", show(left_versions[left]), "\n",
"Right version: ", show(right_versions[right]), "\n",
"Shared version: ", show(shared_versions[shared]), "\n",
"Target version: ", show(target_versions[target]), "\n"
];
```

![img](img/image4.png)
---
## Задача 7

Представить задачу о зависимостях пакетов в общей форме. Здесь необходимо действовать аналогично реальному менеджеру пакетов. То есть получить описание пакета, а также его зависимости в виде структуры данных. Например, в виде словаря. В предыдущих задачах зависимости были явно заданы в системе ограничений. Теперь же систему ограничений надо построить автоматически, по метаданным.

## Решение

```python
import re, sys
from collections import defaultdict


def parse_dependencies(file_path):
    dependencies = defaultdict(dict)

    with open(file_path, 'r') as file:
        for line in file:
            if ' - ' not in line:
                continue

            package_info, deps = line.split(" - ")
            package, version = package_info.split()

            dep_dict = {}
            if deps.strip():
                for dep in deps.split():
                    match = re.match(r'([a-zA-Z0-9_]+)\s*([^\s]*)', dep)
                    if match:
                        dep_name = match.group(1)
                        dep_version = match.group(2)
                        dep_dict[dep_name.strip()] = dep_version.strip()

            dependencies[package] = {
                "version": version,
                "dependencies": dep_dict
            }

    return dependencies


def find_solution(dependencies):
    resolved_versions = {}
    solution = {}

    def can_resolve(package, current_versions):
        if package in solution:
            return True
        package_info = dependencies.get(package)
        if not package_info:
            return False

        package_version = package_info["version"]
        package_deps = package_info["dependencies"]

        for dep_name, dep_version_constraint in package_deps.items():
            if dep_name in current_versions:
                if not version_satisfies_constraint(current_versions[dep_name], dep_version_constraint):
                    return False
            else:
                current_versions[dep_name] = dep_version_constraint

                if not can_resolve(dep_name, current_versions):
                    return False

        solution[package] = package_version
        return True

    for package in dependencies:
        if not can_resolve(package, resolved_versions):
            print(f"Не удалось разрешить зависимости для пакета {package}")
            return None

    return solution


def version_satisfies_constraint(version, constraint):
    constraint_version = constraint.lstrip('^>=')
    if constraint.startswith('>='):
        return version >= constraint_version
    elif constraint.startswith('^'):
        return version >= constraint_version
    elif constraint.startswith('<'):
        return version < constraint_version
    else:
        return version == constraint_version


file_path = sys.argv[1]
dependencies = parse_dependencies(file_path)
solution = find_solution(dependencies)

if solution:
    print("Найдено решение:")
    for package, version in solution.items():
        print(f"{package}: {version}")
else:
    print("Решение не найдено")
```
![img](img/image5.png)
---
