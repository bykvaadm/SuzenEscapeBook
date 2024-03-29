# Работа с архивами 

## Tar

**Tar** — это стандартная утилита, с помощью которой выполняется архивирование файлов Linux. Постепенно из небольшой программы архивации она превратилась в мощный инструмент, поддерживающий работу со многими вариантами архивов и алгоритмами сжатия. Программа поддерживает большое количество параметров. Первоначально она означала **«Tape Archive»** («Архив на магнитной ленте»), но это было тогда, когда ленты были основным носителем для переноса данных. Команда tar является очень гибкой и она может создавать, сжимать, обновлять, распаковывать и тестировать архивные файлы. По умолчанию расширением для несжатого архива tar (иногда называемым файлом tar или архивом tarball) является расширение **.tar**, тогда как для сжатых архивов tar чаще всего используют расширение **.tgz** (означающее, что архив tar сжат с помощью команды GNU zip). В действительности в архивах tar предлагается несколько различных методов сжатия, в том числе **bzip2, zip, LZW и LZMA**. Рассмотрим ее синтаксис и основные параметры:

**$ tar опции f файл_для_записи /папка_c_файлами_для_архива**

### Ключи:
---

* **c** — создать новый архив 
* **d** — сравнить файлы архива и распакованные файлы в файловой системе
* **r** — добавить файлы в конец архива
* **t** — показать содержимое архива
* **u** — обновить архив относительно файловой системы
* **x** — извлечь файлы из архива
* **f** — файл для записи архива

**Создать архив из указанных файлов**
```
tar –czvf archive1.tar.gz  file1 file2
```

![arcives](../img/commands/archives/1.png)

**Извлечь файлы из архива**
```
tar –xvf archive1 file3 file4
```

![arcives](../img/commands/archives/2.png)


**Получить список файлов архива**
```
tar –tf archive1.tar.gz
```

![arcives](../img/commands/archives/3.png)


**Сравнение архива с его источником в файловой системе**
```
tar –df archive1.tar.gz
```

![arcives](../img/commands/archives/4.png)


**Дописать файл в конец архива**
```
tar -rf archive3.tar file7
```

![arcives](../img/commands/archives/5.png)


**Обновить существующий архив**
```
tar -uf archive3.tar file8
```

![arcives](../img/commands/archives/6.png)


Команда **tar**  используется для архивации файлов и поставляется по умолчанию во всех дистрибутивах. В её возможности входит создание и распаковка архива файлов без их сжатия. Для сжатия утилита применяется в связке с популярными компрессорами **bzip2** и **gzip**.


## Gzip

Инструмент **gzip** использует алгоритм сжатия **DEFLATE** (который также используется другими популярными технологиями, такими как **PNG, HTTP, SSH**).

### Ключи:
---

* **-c** — выводить архив в стандартный вывод
* **-d** — распаковать
* **-l** — показать информацию об архиве
* **-r** — рекурсивно перебирать каталоги
* **-0** — минимальный уровень сжатия
* **-9** — максимальный уровень сжатия

**Сжатие файла и его распаковка**
```
gzip –c file19 > foo.gz
gunzip –c >foo
```

![arcives](../img/commands/archives/7.png)


**Показать информацию об архиве**
```
gzip –l archive1.gzip
```

![arcives](../img/commands/archives/8.png)


**Сжать файл с максимальным уровнем сжатия**
```
gzip -9 file29
```

![arcives](../img/commands/archives/9.png)

**Распаковать файл в стандартный вывод  и посчитать количество строк в распакованном потоке**
```
gzip –d –c file_1.gz | wc –l
```

![arcives](../img/commands/archives/10.png)


**Выполнить рекурсивный переход по структуре каталогов и сжать найденные там файлы**
```
gzip –r qwert
```

![arcives](../img/commands/archives/11.png)

Одно из главных преимуществ инструмента **gzip** – его скорость. Он может сжимать и распаковывать данные с гораздо более высокой скоростью, чем некоторые другие популярные технологии. Он также очень эффективен в плане использования памяти при сжатии и распаковке и не требует больше памяти при оптимизации сжатия. Ещё одним преимуществом gzip является совместимость. Поскольку **gzip** – очень старый инструмент, почти все системы Linux независимо от возраста  поддерживают **gzip**.

## Gunzip.

**Gunzip** принимает список файлов из командной строки и заменяет каждый файл, имя которого заканчивается **.gz, -gz, .z, -z**, или **_z** (игнорируя случай) и который начинается с правильным магическим числом с несжатым файлом без oригинального расширения. Gunzip также распознает специальные расширения .tgz и .taz как сокращения .tar.gz и .tar.Z соответственно. При сжатии, GZIP использует расширение .tgz в случае необходимости вместо усечения  в файл с расширением .tar. 

## Md5sum.

**Контрольная сумма** — это цифра или строка, которая вычисляется путем суммирования всех цифр нужных данных. Ее можно использовать в дальнейшем для обнаружения ошибок в проверяемых данных при хранении или передаче. Тогда контрольная сумма пересчитывается еще раз и полученное значение сверяется с предыдущим.

Эта утилита позволяет не только подсчитывать контрольные суммы linux, но и проверять соответствие. Она поставляется в качестве стандартной утилиты из набора GNU

### Ключи:
---

* **-t** --text — читать данные файлов в текстовом режиме (по умолчанию). Перед именем файла выводится пробел.
* **-b** --binary — читать данные файлов в двоичном режиме. Перед именем файла выводится символ ** * ** .
* **-c** --check — сверять вычисленные значения MD5 со значениями из файла

**Прочитать данные файла в двоичном режиме**
```
md5sum –b sums.md5
```

![arcives](../img/commands/archives/12.png)


**Проверить контрольную сумму со значением из файла**
```
md5sum –c sums.md5
```

![arcives](../img/commands/archives/13.png)


**Прочитать данные файла в текстовом режиме**
```
md5sum –t file_2.md5
```

![arcives](../img/commands/archives/14.png)


Проверка целостности файлов Linux — это очень важный аспект использования системы. Контрольная сумма файла Linux используется не только вручную при проверке загруженных файлов, но и во множестве системных программ, например, в менеджере пакетов.


## Unzip.

Утилита для распаковки ZIP называется **unzip**, она не всегда установлена по умолчанию. Но можно очень просто добавить её в свою систему из официальных репозиториев. Для этого в Debian  надо выполнить:

```
$ sudo apt install unzip
```

Но этой утилите не нужны дополнительные оболочки для распаковки архива. Можно сделать всё прямо из консоли. 

**Синтаксис утилиты:**

```
$ unzip опции файл_архива.zip файлы -x исключить -d папка
```

* **файл архива** — это тот файл, с которым нам предстоит работать;
* **файлы** — здесь вы можете указать файлы, которые нужно извлечь, разделять имена файлов пробелом;
* **исключить** — файлы, которые извлекать не нужно;
* **папка** — папка, в которую будет распакован архив.

Теперь рассмотрим опции утилиты, поскольку она позволяет не только распаковывать архивы, но и выполнять с ними определённые действия:

* **-l** — вывести список файлов в архиве;
* **-t** — протестировать файл архива на ошибки;
* **-u** — обновить существующие файлы на диске;
* **-z** — вывести комментарий к архиву;
* **-d** – извлечь конкретный файл из архива;
* **-v** — вывести всю доступную информацию;
* **-P** — указать пароль для расшифровки архива;
* **-j** — игнорировать структуру архива и распаковать всё в текущую папку.

**Вывести всю доступную информацию об архиве**
```
unzip –v archive3.zip
```

![arcives](../img/commands/archives/15.png)

**Вывести список файлов в архиве**
```
unzip –l archive3.zip
```

![arcives](../img/commands/archives/16.png)
 
**Протестировать файлы архива на ошибки**
```
unzip –t archive3.zip
```
![arcives](../img/commands/archives/17.png)

**Распаковать архив в текущую папку**
```
unzip –j archive3.zip
```

![arcives](../img/commands/archives/18.png)


**Распаковать архив c помощью пароля**
```
unzip –P 1234qwer archive3.zip
```

![arcives](../img/commands/archives/19.png)

**Извлечь конкретный файл из архива**
```
unzip archive4.zip –d file29.gz
```

![arcives](../img/commands/archives/20.png)

**Вывести комментарий к архиву**
```
unzip –z archive228.zip
```

![arcives](../img/commands/archives/21.png)
![arcives](../img/commands/archives/22.png)



**Обновить существующие файлы на диске**
```
unzip –u \*.zip
```

![arcives](../img/commands/archives/23.png)


Утилита **unzip** выполняет вывод списка, тестирование или извлечение файлов из архива ZIP. Стандартное поведение (без опций) заключается в извлечении в текущий каталог (и подкаталоги) всех файлов из указанного архива ZIP.