# Конфигурация системы

## Useradd

Команда **useradd** используется в дистрибутиве **Debian** для упрощения создания учетных записей пользователей, а также автоматической проверки их соотвествия политике упомянутого дистрибутива. Она реализована в виде обертки для таких утилит, как **useradd**, **passwd** и **chfn** и использует дополнительный файл конфигурации **/etc/adduser.conf** для хранения параметров, относящихся к политике дистрибутива **Debian.**

Команда, введенная без ключей создает нового пользователя без дополнительных действий.

| Команда | Ключи | Описание ключей |
|---|---|---|
| Useradd | -b | Этот ключ необходим для того, чтобы у пользователя был задан базовый каталог для домашнего |
| Useradd | -d | Создает полный путь к домашнему каталогу |
| Useradd | -e | Ключ нужен, чтобы установить дату устаревания |
| Useradd | -m/M | Указатель на то, что нужно(не нужно) создать домашний каталог |
| Useradd | -p | Создание пользователя с паролем |
| Useradd | -c | Создание пользователя с комментарием |
| Useradd | -u | Присвоение пользователю UID |
| Useradd | -h | Доступные опции |

**Создать пользователя <ins>Girls</ins> без дополнительных опций**

```
useradd Girls
```

С помощью данной команды **getent passwd** проверяем, создался ли пользователь

![sysconfig](../img/commands/sysconfig/1.jpg)
![sysconfig](../img/commands/sysconfig/passwd.jpg)
![sysconfig](../img/commands/sysconfig/2.jpg)

**Создать пользователя <ins>boys</ins> с заданным базовым каталогом, для домашнего.**

```
useradd boys –b /var/home
```

С помощью данной команды **getent passwd** проверяем, создался ли пользователь

![sysconfig](../img/commands/sysconfig/3.jpg)
![sysconfig](../img/commands/sysconfig/passwd.jpg)
![sysconfig](../img/commands/sysconfig/4.jpg)


**Добавить нового пользователя <ins>people</ins> с созданием полного пути к домашнему каталогу.**

```
useradd people –d /home/kursach
```

![sysconfig](../img/commands/sysconfig/5.jpg)
![sysconfig](../img/commands/sysconfig/passwd.jpg)
![sysconfig](../img/commands/sysconfig/6.jpg)

**Создать пользователя cars с датой устаревания.**

```
useradd cars –e 2018-08-17
chage –l cars
```

![sysconfig](../img/commands/sysconfig/7.jpg)
![sysconfig](../img/commands/sysconfig/8.jpg)
![sysconfig](../img/commands/sysconfig/9.jpg)

**Добавить пользователя dogs и указать, что нужно создать домашний каталог.**

```
useradd dogs -m
```

С помощью данной команды **getent passwd** проверяем, создался ли пользователь

![sysconfig](../img/commands/sysconfig/10.jpg)
![sysconfig](../img/commands/sysconfig/passwd.jpg)
![sysconfig](../img/commands/sysconfig/11.jpg)

**Добавить пользователя computer и указать, что не нужно создавать домашний каталог.**

```
useradd comp –M computer
ls –l /home/computer
```

В некоторых ситуациях мы не хотим, по соображениям безопасности, давать пользователям домашние директории. В таком случае, когда пользователь авторизуется в системе сразу после ее запуска, его домашней директорией будет **root**. Если такой пользователь использует команду **su**, то он авторизуется в домашней директории предыдущего пользователя.

![sysconfig](../img/commands/sysconfig/12.jpg)
![sysconfig](../img/commands/sysconfig/13.jpg)
![sysconfig](../img/commands/sysconfig/14.jpg)

**Создать пользователя с паролем.**

```
useradd chicken –p 1234
cat /etc/passwd
```

![sysconfig](../img/commands/sysconfig/15.jpg)
![sysconfig](../img/commands/sysconfig/etc_passwd.jpg)
![sysconfig](../img/commands/sysconfig/16.jpg)


С помощью команды **su chicken** заходим от пользователя **chicken**

![sysconfig](../img/commands/sysconfig/17.jpg)
![sysconfig](../img/commands/sysconfig/18.jpg)


**Создать пользователя Polya с комментарием.**

```
useradd Polya –c “Polina”

```

С помощью команды **cat /etc/passwd** проверяем, создался ли пользователь с комментарием

![sysconfig](../img/commands/sysconfig/19.jpg)
![sysconfig](../img/commands/sysconfig/etc_passwd.jpg)
![sysconfig](../img/commands/sysconfig/20.jpg)


В Linux каждый пользователь имеет свой собственный **UID** (*Unique Identification Number*). По умолчанию при создании нового пользователя ему присваивается **userid 500, 501, 502** и т.д. Но можно присвоить свой.


**Создать пользователя Yulia с уникальным UID номером.**

```
useradd Yulia –u 8888
```

С помощью команды **cat /etc/passwd** проверяем, создался ли пользователь с UID.

![sysconfig](../img/commands/sysconfig/21.jpg)
![sysconfig](../img/commands/sysconfig/etc_passwd.jpg)
![sysconfig](../img/commands/sysconfig/22.jpg)

**Проверить все возможные опции с помощью ключа –h.**

```
useradd -h
```

![sysconfig](../img/commands/sysconfig/23.jpg)
![sysconfig](../img/commands/sysconfig/24.jpg)

## Groupadd

Команда **groupadd** создает новую учетную запись группы, используя значения, указанные в командной строке, плюс значения по умолчанию из системы. Новая группа будет добавлена в системные файлы. 

Команда, введенная без аргументов, создает новую группу в Linux.

Команда

| Ключ | Описание ключей |
|---|---|
| groupadd | -g | С помощью ключа можно присвоить группе GID |
| groupadd | -K | Создание группы пользователей с идентификатором из диапазона | 

**Создать группу students без дополнительных опций.**

```
groupadd students
```
С помощью команды **cat /etc/group** проверяем, создалась ли группа.

![sysconfig](../img/commands/sysconfig/25.jpg)
![sysconfig](../img/commands/sysconfig/etc_group.jpg)
![sysconfig](../img/commands/sysconfig/26.jpg)

**Создать группу bbso с уникальным GID.**

```
groupadd –g 4444 bbso
```

С помощью команды **cat /etc/group** проверяем, создалась ли группа с индивидуальным GID (Group Identification Number).

![sysconfig](../img/commands/sysconfig/27.jpg)
![sysconfig](../img/commands/sysconfig/etc_group.jpg)
![sysconfig](../img/commands/sysconfig/28.jpg)

**Создать группу flowers с идентификатором из заданного диапазона.**

```
groupadd  –K GID_MIN=2031 –K GID_MAX=2052 flowers
```

С помощью команды **cat /etc/group** проверяем, действительно ли группе **flowers** присвоился идентификатор от 2031 до 2052. Первый свободный.

![sysconfig](../img/commands/sysconfig/29.jpg)
![sysconfig](../img/commands/sysconfig/etc_group.jpg)
![sysconfig](../img/commands/sysconfig/30.jpg)

## Usermod

**Usermod (groupmod)**-для изменения учетной записи пользователя (**account**) используется команда **usermod.** Изменять можно любые атрибуты, но имя пользователя и код UID изменять нужно лишь в случае крайней необходимости, поскольку такое изменение может иметь общесистемные последствия.

Команда **usermod**, введенная без ключей, изменяет учётную запись пользователя. 

| Команда | Ключи | Описание ключей |
|---|---|---|
| usermod | -l | Смена имени пользователя |
| usermod | -a -G | Добавление пользователя в группу |
| usermod | -n | Смена названия группы |
| usermod | -p -l | Смена пароля при каждом входе |

**Сменить имя пользователя girls на sweet.**

```
usermod –l sweet girls
```

Проверяем, действительно ли поменялось имя с помощью команды **vi /etc/group**

![sysconfig](../img/commands/sysconfig/31.jpg)
![sysconfig](../img/commands/sysconfig/vi_group.jpg)
![sysconfig](../img/commands/sysconfig/32.jpg)

**Добавить пользователя Yulia в группу bbso.**

```
usermod –a –G bbso Yulia
```

Проверяем, действительно ли теперь Yulia находится в группе bbso команды **cat /etc/group**

![sysconfig](../img/commands/sysconfig/33.jpg)
![sysconfig](../img/commands/sysconfig/etc_group.jpg)
![sysconfig](../img/commands/sysconfig/34.jpg)

**Сменить название группы flowers.**

```
groupmod –n roses flowers
cat /etc/group
```

Изначальная группа:

![sysconfig](../img/commands/sysconfig/35.jpg)
![sysconfig](../img/commands/sysconfig/etc_group.jpg)
![sysconfig](../img/commands/sysconfig/36.jpg)


**Заставить пользователя менять пароль при каждом входе в систему.**

```
usermod Polya –p -l
```

![sysconfig](../img/commands/sysconfig/37.jpg)

```
Su Polya
passwd
```

Чтобы проверить, что при каждом входе компьютер будет запрашивать пароль, нужно войти от пользователя **Polya** и ввести команду **passwd**.

![sysconfig](../img/commands/sysconfig/38.jpg)

## Sudo (su)

**Sudo (su)**- предположим, что нужно выполнить нестандартную задачу, где графические инструменты нам не помогут. К тому же командная строка является очень гибким инструментом, здесь можно увидеть вывод команд и понять, что происходит не так как нужно. А самое главное, команды в терминале являются стандартными для всех дистрибутивов Linux.

Итак, существует два основных способа получить права суперпользователя **(Root)** это — **sudo** или **su**.

Без дополнительных опций команды **sudo** и **su** дают право работать от суперпользователя.

| Команда | Ключ | Описание ключей |
|---|---|---|
| Sudo | -l | Cписок прав пользователя |
| Sudo | -s | Оболочка SHELL |
| Sudo | -h | Опции | 
| Su | -l | Переход в домашнюю директорию |
| Su | -h | Опции |

**Зайти в систему под именем суперпользователя.**

```
sudo
```

![sysconfig](../img/commands/sysconfig/39.jpg)
![sysconfig](../img/commands/sysconfig/40.jpg)

**Показать список прав пользователя или проверить заданную команду.**

```
sudo -l
```
![sysconfig](../img/commands/sysconfig/41.jpg)

**Запустить оболочку от имени конечного пользователя.**

```
sudo -s
```

Работаем от имени user

Чтобы проверить окружение данного пользователя,мы используем команду

```
env(enviroment)
```

![sysconfig](../img/commands/sysconfig/42.jpg)

Видим, что мы находимся в домашней директории пользователя **user**

![sysconfig](../img/commands/sysconfig/43.jpg)

С помощью **sudo –s** начинаем работу от привелегированного пользователя **root**, проверяем окружение данного пользователя, с помощью **env**

![sysconfig](../img/commands/sysconfig/44.jpg)
![sysconfig](../img/commands/sysconfig/45.jpg)

**Посмотреть опции sudo.**

```
sudo -h
```

![sysconfig](../img/commands/sysconfig/46.jpg)
![sysconfig](../img/commands/sysconfig/47.jpg)

**Зайти под другой учетной записью**

```
su boys
```

С помощью команды whoami узнаем под каким пользователем мы работаем

![sysconfig](../img/commands/sysconfig/48.jpg)

**Перейти в домашнюю директорию.**

```
su -l
```

![sysconfig](../img/commands/sysconfig/49.jpg)

Ничего не поменялось, т.к. пользователь уже находился в домашней директории.

**Посмотреть опции su.**

```
su -h
```

![sysconfig](../img/commands/sysconfig/50.jpg)