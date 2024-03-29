# Скрипты

## Xargs

Программа берет данные стандартного ввода или из файла, разбивает их в соответствии с указанными параметрами, а затем передает другой программе в качестве аргумента.
Задача: найти файлы с названием ‘a\*’ в заданной директории и вывести количество строк в них, запрашивая подтверждение перед выполнением.

```
find kursovaya/ -name ‘a*’ | xargs -p wc –l !!!
```

![scripting](../img/commands/scripts/1.png)

**Найти файлы с названием ‘a\*’ в заданной директории, отсортировать по имени и вывести первые три строки.**

```
find kursovaya/ -name ‘a*’ | sort | xargs -n3 head
```

![scripting](../img/commands/scripts/2.png)

## Yes

Команда **yes** многократно выводит строку **STRING** разделяемую символом новой строки (**newline**) на стандартный вывод, до тех пор, пока не будет принудительно завершена. Если строка не задана, выводится символ y и символ новой строки. Может использоваться для ответа **“yes”** командам, запрашивающим подтверждение на выполнение. Пример этого указан далее. Такая конструкция использовалась ранее, когда не было ключа **–f**, игнорирующего запросы и ошибки.

**Удалить файлы из заданной директории.**

**rm** удаляет заданные файлы, каждый раз запрашивая подтверждение 

```
yes | rm -i kursovaya/yes/*.txt
yes ab
```

![scripting](../img/commands/scripts/3.png)
![scripting](../img/commands/scripts/4.png)

## Watch

С заданной периодичностью запускает другие программы, указанные в качестве аргументов.

### Ключи
---

| Ключ | Описание |
|---|---|
| -d | подсвечивает изменения (при выводе на экран большого кол-ва данных, сразу видны те, которые изменились) |
| -n | позволяет указать время обновления в секундах |

**Пронаблюдать за расходом оперативной памяти в режиме реального времени, подсвечивая изменения.**

```
watch -d free
```

![scripting](../img/commands/scripts/5.png)

**Пронаблюдать за расходом оперативной памяти в режиме реального времени с частотой обновления данных 5 с.**

```
watch –n 5 free
```

![scripting](../img/commands/scripts/6.png)

## Export

Экспорт переменных и функций текущего процесса в дочерний процесс.

* **-p** – выводит список всех имен, экспортированных в текущей оболочке
* **-n** – удаляет имена из списка экспорта
* **-f** – имена экспортируются как функции

**Создать переменную a, экспортировать ее, создать функцию printstring и также экспортировать, проверить работоспособность вышеуказанных имен в дочерних процессах, затем удалить функцию и вывести на экран все экспортированные имена, дабы убедиться в том, что функция удалена, а переменная все еще существует.**

```
a=debian
export a
printstring () { echo “debian”; }
export –f printstring
bash
export –n printstring
export –p
```

Export http_proxy=”http://...”

![scripting](../img/commands/scripts/7.png)
![scripting](../img/commands/scripts/8.png)

**Настроить прокси-сервер для работы через него в командной строке.**

```
export http_proxy=http://USERNAME:PASSWORD@proxy-server.mycorp.com:3128
```

![scripting](../img/commands/scripts/9.png)

В переменную окружения записываются все данные прокси-сервера. *http://имя_пользователя:пароль@адрес_сервера:порт*

```
export -p
```

![scripting](../img/commands/scripts/10.png)


## Env

**Окружение или среда** – набор пар переменная=значение, доступный каждому 
пользовательскому процессу.

**Записать MYSQL_PWD в окружение и вывести окружение на экран.**

```
export MYSQL_PWD=password
env
```

![scripting](../img/commands/scripts/11.png)

## Seq

**Вывести последовательность чисел от 2 до 20 с шагом 2.**

```
seq 2 2 20
```

seq [от] [шаг] [до]

![scripting](../img/commands/scripts/12.png)

**Вывести числа от 2 до 4 с шагом 0.5 в:**

а. формате f
б. формате g
в. формате e

```
seq –f “%f” 2 0.5 4
seq –f “%g” 2 0.5 4
seq –f “%e” 2 0.5 4
```

-f – задаёт формат (по умолчанию %g).

![scripting](../img/commands/scripts/13.png)

**Вывести числа от 2 до 12, разделив их запятой в первом случае, пробелом - во втором.**

```
seq –s , 2 12
seq –s “ “ 2 12
```

-s – данный ключ позволяет записывать числа, используя разделяющий символ.

![scripting](../img/commands/scripts/14.png)

**Вывести числа от 1 до 20 в столбец равной ширины.**

```
seq –w 20
```

-w – выравнивает ширину, заполнив пробелы нулями слева.

![scripting](../img/commands/scripts/15.png)

## Sed

Редактор потока данных для автоматического редактирования текстов.

**Заменить первые встретившиеся в указанном файле прописные буквы «a» и «b» на заглавные.**

```
sed –e ‘s/a/A/’ –e ‘s/b/B/’
```

-e – способ выполнения нескольких команд.

![scripting](../img/commands/scripts/16.png)

**Заменить прописные гласные буквы на заглавные.**

```
sed –f “script” “file”
```

-f – применяет команды из указанного файла (скрипта).

Скрипт:

```
s/a/A/g
s/e/E/g
s/i/I/g
s/o/O/g
s/u/U/g
```

![scripting](../img/commands/scripts/17.png)


**Из указанного файла вывести только строку, содержащую букву «b».**

```
sed –n ‘s/b/&/p’
```

-n – ничего не выводит на стандартный выход. Можно использовать с модификатором /p для вывода отдельных строк из файла.

![scripting](../img/commands/scripts/18.png)

**Заменить все буквы «b» на буквы «c» с заменой исходного файла.**

```
sed –i ‘s/b/c/g’
```

![scripting](../img/commands/scripts/19.png)


## Sleep

Приостанавливает скрипт на указанное время. По умолчанию время указывается в секундах, для минут после числа пишут **m**, для часов **h**, для дней **d**.

**Приостановить работу терминала на 5 секунд, минут, часов, дней.**

```
sleep 5
sleep 5m
sleep 5h
sleep 5d
```

## base64

Кодирует или декодирует файл и выводит на стандартный выход

**Закодировать и декодировать строку, закодированную строку разбить на строки по 10 символов.**

```
echo ‘gooses are a nice birds’ | base64
echo ‘gooses are a nice birds’ | base64 –w 10
echo ‘Z29vc2VzIGFyZSBhIG5pY2UgYmlyZHMK’ | base64 –d
```

-w – переносит закодированную строку через указанное количество символов (по умолчанию 76). Для отключения переноса использовать 0
-d – декодирует данные

![scripting](../img/commands/scripts/20.png)
