# Решение предоставлено XXX

### Перемещение в домашнюю директорию пользователя.

Сделать это можно несколькими способами. 

Просто **cd**.

```
┌[misshelly☮misshelly]-(/)
└> pwd
/
┌[misshelly☮misshelly]-(/)
└> cd  
┌[misshelly☮misshelly]-(~)
└> pwd
/home/misshelly 
```

Можно **cd ~**.

```
┌[misshelly☮misshelly]-(/)
└> pwd
/
┌[misshelly☮misshelly]-(/)
└> cd ~
┌[misshelly☮misshelly]-(~)
└> pwd 
/home/misshelly
```

А можно и прописать путь. 

```
┌[misshelly☮misshelly]-(~)
└> cd /              
┌[misshelly☮misshelly]-(/)
└> pwd
/
┌[misshelly☮misshelly]-(/)
└> cd /home/misshelly
┌[misshelly☮misshelly]-(~)
└> pwd
/home/misshelly
```

### Cоздание в домашней директории папки со своей фамилией.

//деанониться не хочу, потому папка будет называться **nyasha**

```
┌[misshelly☮misshelly]-(~)
└> ls
5l  6lab  CLionProjects  Documents  Downloads  lab3  mai_oop  Music  octave  opapa  OS4  OSI5  Pictures  Public  Templates  Videos  VirtualBox VMs  дичь разное
┌[misshelly☮misshelly]-(~)
└> mkdir nyasha
┌[misshelly☮misshelly]-(~)
└> ls          
5l  6lab  CLionProjects  Documents  Downloads  lab3  mai_oop  Music  nyasha  octave  opapa  OS4  OSI5  Pictures  Public  Templates  Videos  VirtualBox VMs  дичь разное

```

Папочка появилась, магия работает!) Продолжаем.

### Переместиться в созданную в п2. папку.

Утилитой **cd** мы уже умеем пользоваться:

```
┌[misshelly☮misshelly]-(~)
└> cd nyasha 
```

### Cоздать в домашней директории 3 папки с именами друзей. Выполнить в одну команду.

Вначале продемонстрирую, что в директории **nyasha** пусто. Дальше **mkdir** и немного волшебства.

```
┌[misshelly☮misshelly]-(~/nyasha)
└> ls
┌[misshelly☮misshelly]-(~/nyasha)
└> mkdir stekov_me refeaime angelina
┌[misshelly☮misshelly]-(~/nyasha)
└> ls
angelina  refeaime  stekov_me
```

### Cоздать в текущей директории файл с любым содержимым.

Создать файл можно многими способами. Я сделаю так. 
// vim - ван лав.

```
┌[misshelly☮misshelly]-(~/nyasha)
└> vim FAUST
┌[misshelly☮misshelly]-(~/nyasha)
└> ls
angelina  FAUST  refeaime  stekov_me
┌[misshelly☮misshelly]-(~/nyasha)
└> cat FAUST 
… так кто ж ты, наконец? – Я – часть той силы, что вечно хочет зла и вечно совершает благо. Гете. «Фауст»
```

### Переместить созданный ФАУСТА в директорию с именем какого-либо друга 1. Использовать абсолютный путь.

// Много разных ls, но я это делаю, чтобы продемонстрировать изменения.

```
┌[misshelly☮misshelly]-(~/nyasha)
└> ls
angelina  FAUST  refeaime  stekov_me
┌[misshelly☮misshelly]-(~/nyasha)
└> ls stekov_me 
┌[misshelly☮misshelly]-(~/nyasha)
└> mv FAUST /home/misshelly/nyasha/stekov_me 
┌[misshelly☮misshelly]-(~/nyasha)
└> ls stekov_me 
FAUST
```

### Копирование папки друга 1 в текущую директорию.

Копирование папок осуществляется с помощью ключа **-r**:

```
┌[misshelly☮misshelly]-(~/nyasha)
└> cp -r angelina stekov_me  
┌[misshelly☮misshelly]-(~/nyasha)
└> ls stekov_me 
angelina  FAUST
```

###Удаление папки друга 1 из текущей директории.

```
┌[misshelly☮misshelly]-(~/nyasha)
└> rmdir /home/misshelly/nyasha/stekov_me/angelina 
┌[misshelly☮misshelly]-(~/nyasha)
└> ls stekov_me 
FAUST
```

###Вывести на экран текущее местоположение.

```
┌[misshelly☮misshelly]-(~/nyasha)
└> pwd
/home/misshelly/nyasha
```

### Переместимся в папку друга 2.

```
┌[misshelly☮misshelly]-(~/nyasha)
└> cd refeaime 
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> pwd 
/home/misshelly/nyasha/refeaime
```

### Cоздадим в одну команду 10 файлов в папке друга 3.

```
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> touch ../angelina/file{1,2,3,4,5,6,7,8,9,10}
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> cd ../angelina 
┌[misshelly☮misshelly]-(~/nyasha/angelina)
└> ls
file1  file10  file2  file3  file4  file5  file6  file7  file8  file9
```

### Наполним разным содержимым созданные файлы.

Наполню через echo.

```
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> echo 1234 > ../angelina/file{1..10}
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> cd ../angelina 
┌[misshelly☮misshelly]-(~/nyasha/angelina)
└> ls
file1  file10  file2  file3  file4  file5  file6  file7  file8  file9
┌[misshelly☮misshelly]-(~/nyasha/angelina)
└> cat file1
1234
```

### Выполним поиск по некоторой маске среди созданных файлов.

```
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> find ../angelina -name "file*" -type f
../angelina/file3
../angelina/file7
../angelina/file2
../angelina/file6
../angelina/file5
../angelina/file1
../angelina/file10
../angelina/file4
../angelina/file8
../angelina/file9
```

### Запишем информацию о текущей системе в файл, расположенный в папке друга stekov_me.

```
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└>  uname -a >> /home/misshelly/nyasha/stekov_me/sys
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> cd ../stekov_me; ls; cat sys
FAUST  sys
Linux misshelly 4.10.0-32-generic #36~16.04.1-Ubuntu SMP Wed Aug 9 09:19:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

### Записашем информацию о текущем пользователе в файл, расположенный в папке stekov_me.

```
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> whoami >> /home/misshelly/nyasha/stekov_me/whoami
┌[misshelly☮misshelly]-(~/nyasha/refeaime)
└> cd ../stekov_me; ls; cat whoami                  
FAUST  sys  whoami
misshelly
```

### Выполним переход в папку друга 3 (он же stekov_me).

По идее, командой выше я уже перешла в ту папку. Покажу:

```
┌[misshelly☮misshelly]-(~/nyasha/stekov_me)
└> pwd
/home/misshelly/nyasha/stekov_me
```

### Выведем на экран созданные файлы в пунктах 14,15

```
┌[misshelly☮misshelly]-(~/nyasha/stekov_me)
└> cat sys whoami 
Linux misshelly 4.10.0-32-generic #36~16.04.1-Ubuntu SMP Wed Aug 9 09:19:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
misshelly
```

### Выполним переход в предыдущую директорию, не используя в команде пути.

Не поняла задание. Имеется в виду cd ..? Вернемся в няшу, да. А в рефайми не вернемся без пути. 

###Используем абсолютный путь. Возвращаемся в домашнюю директорию.

```
┌[misshelly☮misshelly]-(~/nyasha/stekov_me)
└> cd /home/misshelly 
┌[misshelly☮misshelly]-(~)
└> pwd
/home/misshelly
```

### Удалим созданные в п1-19 файлы.

```
┌[misshelly☮misshelly]-(~)
└> rm -rf nyasha  
┌[misshelly☮misshelly]-(~)
└> ls
5l  6lab  CLionProjects  Documents  Downloads  konsolka.md  lab3  mai_oop  Music  octave  opapa  OS4  OSI5  Pictures  Public  Templates  Videos  VirtualBox VMs  дичь разное
```

### Выполним завершение работы.

```
#sudo shutdown -h now
```

решеточка для игнора