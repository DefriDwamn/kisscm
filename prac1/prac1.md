# Практическое занятие №1. Введение, основы работы в командной строке

## Задача 1

Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep).

## Решение

```bash
cat /etc/passwd | grep -oE '^[^:]+'
```
![img1](img/Pasted%20image%2020240908183528.png)
---
## Задача 2

Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере ниже:

```
[root@localhost etc]# cat /etc/protocols ...
142 rohc
141 wesp
140 shim6
139 hip
138 manet
```

## Решение

```bash
tac /etc/protocols | head -5 | awk '{print $2, $1}'
```
![img2](img/Pasted%20image%2020240908183656.png)
---
## Задача 3

Написать программу banner средствами bash для вывода текстов, как в следующем примере (размер баннера должен меняться!):

```
[root@localhost ~]# ./banner "Hello from RTU MIREA!"
+-----------------------+
| Hello from RTU MIREA! |
+-----------------------+
```

Перед отправкой решения проверьте его в ShellCheck на предупреждения.

## Решение

```bash
#!/bin/bash
arg1=$1
size=${#arg1}
echo -n "+"
for ((i = -2; i < size; ++i)); do
    echo -n "-"
done
echo "+"
echo "| $arg1 |"
echo -n "+"
for ((i = -2; i < size; ++i)); do
    echo -n "-"
done
echo "+"
```
![img3](img/Pasted%20image%2020240908183758.png)
---
## Задача 4

Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений).

Пример для hello.c:

```
h hello include int main n printf return stdio void world
```

## Решение

```bash
grep -Eo '[_A-Za-z][_A-Za-z0-9]{0,30}' hello.c | sort | xargs
```
![img4](img/Pasted%20image%2020240908185233.png)
---
## Задача 5

Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

Например, пусть программа называется reg:

В результате для banner задаются правильные права доступа и сам banner копируется в /usr/local/bin.

## Решение

```bash
#!/bin/bash
chmod +x "$1"
sudo cp "$1" /usr/local/bin
```
![img5](img/Pasted%20image%2020240908190919.png)
---
## Задача 6

Написать программу для проверки наличия комментария в первой строке файлов с расширением c, js и py.

## Решение

```bash
#!/bin/bash
for filename in "$@";
do
        if [[ "$filename" =~ .*(c|js)$ ]]; then
                if [[ "$(head -1 "$filename")" =~ ^(\/\*|\/\/) ]]; then
                        echo "comment!"
                else
                        echo "comment not found!"
                fi
        elif [[ "$filename" =~ .*py$ ]]; then
                if [[ "$(head -1 "$filename")" =~ ^# ]]; then
                        echo "comment!"
                else
                        echo "comment not found!"
                fi
        fi
done
```
![img6](img/Pasted%20image%2020240908201821.png)
---
## Задача 7

Написать программу для нахождения файлов-дубликатов (имеющих 1 или более копий содержимого) по заданному пути (и подкаталогам).

## Решение

```bash
#!/bin/bash
find "$1" -type f -printf "%p\n" | xargs md5sum | sort | uniq -w32 --all-repeated=separate
```
![img7](img/image7.png)
---
## Задача 8

Написать программу, которая находит все файлы в данном каталоге с расширением, указанным в качестве аргумента и архивирует все эти файлы в архив tar.

## Решение

```bash
#!/bin/bash
find . -name "*.$1" -exec tar -rvf archive.tar {} \;
```
![img8](img/image8.png)
---
## Задача 9

Написать программу, которая заменяет в файле последовательности из 4 пробелов на символ табуляции. Входной и выходной файлы задаются аргументами.

## Решение

```bash
#!/bin/bash
sed 's/    /    /g' "$1" > "$2"
```
![img9](img/image9.png)
---
## Задача 10

Написать программу, которая выводит названия всех пустых текстовых файлов в указанной директории. Директория передается в программу параметром. 

## Решение

```bash
#!/bin/bash
find "$1" -type f -empty -name "*.txt"
```
![img10](img/image10.png)