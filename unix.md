# Unix

Здесь только основы. <br>
Если вы опытный юниксоид, вряд ли вы здесь найдете интересное.

## 1. Терминал

|    Команда    | Комбинация клавиш | Действие                                                  |
|:-------------:|:-----------------:|:----------------------------------------------------------|
|     `exit`    |      Ctrl + D     | выйти из терминала                                        |
|               |      Ctrl + D     | символ ["конец файла"](https://ru.wikipedia.org/wiki/EOF) |
|               |      Ctrl + C     | прервать выполнение команды                               |
|    `clear`    |      Ctrl + L     | очистить экран                                            |
| `man command` |                   | справка о команде                                         |
|               |      Ctrl + S     | приостановить работу терминала                            |
|               |      Ctrl + Q     | возобновить работу терминала                              |

Просмотр истории: `history` <br>
Комбинации клавиш, связанные с историей

| Комбинация клавиш | Действие                    |
|:-----------------:|:----------------------------|
|         Up        | предыдущая команда          |
|        Down       | следующая команда           |
|      Ctrl + R     | поиск похожей команды       |
|  Alt + Shift + 3  | сохранить команду в историю |


Запуск команды в фоновом режиме: `команда &`

## 2. Навигация по файловой системе

Особые каталоги

| Обозначение | Значение                      |
|:-----------:|:------------------------------|
|     `/`     | корень (root)                 |
|     `~`     | домашний каталог (/home/user) |
|     `.`     | текущий каталог               |
|     `..`    | родительский каталог          |

Абсолютный путь — это полный путь начиная от корня, т.е `/`. <br>
Относительный путь — это путь, начинающийся от текущего каталога.

Символы подстановки в шаблонах <br>
*(могут использоваться в любых командах, принимающих путь к файлам / каталогам)*

| Обозначение | Значение                                        |
|:-----------:|:------------------------------------------------|
|     `?`     | один любой символ                               |
|     `*`     | любое количество любых символов                 |
|     `[]`    | один из символов в скобках                      |
|     `{}`    | одна из строк в скобоках, разделитель - запятая |

Базовые команды навигации

|    Команда    |             Расшифровка             | Действие                          |
|:-------------:|:-----------------------------------:|:----------------------------------|
|     `pwd`     | **p**rint **w**orking **d**irectory | вывести текущий каталог           |
|  `ls <path>`  |        **l**i**s**t (список)        | вывести содержимое каталога       |
| `tree <path>` |          **tree** (дерево)          | вывести дерево файлов / каталогов |
|  `cd <path>`  |       **c**hange **d**irectory      | перейти в другой каталог          |

`cd` без параметров переходит в домашний каталог, т.е в `~` <br>
`ls` / `tree` без параметров показывает содержимое текущего каталога

Опции команды `ls`

| Опция | Длинная форма (long) | Значение                                     |
|:-----:|:---------------------|:---------------------------------------------|
|   -a  | \-\-all              | показать все файлы и каталоги                |
|   -A  | \-\-almost-all       | показать все файлы и каталоги кроме . и \.\. |
|   -R  | \-\-recursive        | показать список для подкаталогов рекурсивно  |
|   -1  |                      | показать каждый элемент в отдельной строке   |

Примеры использования команды `ls`
1) Показать все текстовые файлы: `ls *.txt`
2) Показать все загруженные книги: `ls ~/Downloads/*.{pdf,djvu}`
3) Показать все (т.е и скрытые) файлы: `ls -A` 

## 3. Поиск файлов / каталогов

`find <directory>`

Опции команды find

|        Опция       | Значение                   |
|:------------------:|:---------------------------|
|       -type f      | искать только файлы        |
|       -type d      | искать только каталоги     |
|  -name <file-mask> | поиск по шаблону имени     |
| -iname <file-mask> | нечувствительно к регистру |
|  -path <path-mask> | поиск по шаблону пути      |
| -ipath <path-mask> | нечувствительно к регистру |
|     -a или -and    | логическое и               |
|     -o или -or     | логическое или             |
|     ! или -not     | логическое не              |

TO DO:
- [ ] Добавить примеры использования find

## 4. Создание файлов / каталогов

|       Команда       |         Расшифровка        | Действие                                |
|:-------------------:|:--------------------------:|:----------------------------------------|
| `mkdir <directory>` | **m**a**k**e **dir**ectory | создать каталог                         |
|  `mkdir -p <path>`  |       -p == --parents      | создать вложенные каталоги, напр. 1/2/3 |
|  `touch <filename>` |      “потрогать” файл      | создать файл / обновить время изменения |


## 5. Копирование, перемещение, удаление

|            Команда            |   Расшифровка  | Действие                    |
|:-----------------------------:|:--------------:|:----------------------------|
|   `cp <path_from> <path_to>`  |  **c**o**p**y  | копировать файл             |
| `cp -r <path_from> <path_to>` |  \-\-recursive | копировать каталог          |
|   `mv <path_from> <path_to>`  |  **m**o**v**e  | переместить / переименовать |
|        `rm <filename>`        | **r**e**m**ove | удалить файл                |
|      `rm -r <directory>`      |  \-\-recursive | удалить каталог             |

Опции команды `rf`

|        Опция       | Значение                         |
|:------------------:|:---------------------------------|
|   -f / \-\-force   | удалять без подтверждения        |
| -r / \-\-recursive | удалять каталоги с их содержимым |
|  -v / \-\-verbose  | показывать явно удаленные файлы  |

## 6. Просмотр текстовых файлов

|           Команда           | Действие                         |
|:---------------------------:|:---------------------------------|
|       `cat <filename>`      | вывести файл                     |
|  `head -<count> <filename>` | вывести первые count строк       |
|  `tail -<count> <filename>` | вывести последние count строк    |
| `tail -n +<num> <filename>` | вывести все строки начиная с num |
|     `tail -f <filename>`    | показывать файл с обновлениями   |

less -- в отличии от предыдущих команд, показывает файл постранично.

|      Команда      | Действие                         |
|:-----------------:|:---------------------------------|
|         q         | выйти                            |
|     Up / Down     | прокрутка                        |
|         b         | назад на страницу                |
|         f         | вперед на страницу               |
| /\<text\> + Enter | поиск                            |
| ?\<text\> + Enter | поиск в обратном направлении     |
|         n         | переход к следующему совпадению  |
|         N         | переход к предыдущему совпадению |

## 7. Поиск по тексту

`grep <text> <filename>` (**g**lobal **re**gex**p** search)

`grep <text> -r <path>` -- рекурсивный поиск по всем файлам каталога

`grep <text>` -- поиск по содержимому stdin (можно искать по выводу другой утилиты)

## 8. Вывода информации о файле

Тип файла: `file <filename>` <br>
Общая информация: `stat <filename>`

Размер файла: `du <filename>` (**d**isk **u**sage) <br>
Полезные опции команды `du`:
| Short | Long                | Значение                               |
|:-----:|---------------------|----------------------------------------|
|   -s  | \-\-summarize       | показать общий размер                  |
|   -h  | \-\-human-readeable | показать размер в человеческом формате | - -s / --summarize       показать общий размер

## 9. Работа с архивами

|        Команда        | Действие                  |
|:---------------------:|:--------------------------|
|   `gzip <filename>`   | добавить в архив .gz      |
|  `gunzip <filename>`  | распаковать архив .gz     |
|  `tar -xf <filename>` | распаковать архив .tar    |
| `tar -xzf <filename>` | распаковать архив .tar.gz |


# 10. Разное

|       Команда       | Действие                         |
|:-------------------:|----------------------------------|
| `apropos <command>` | поиск команды                    |
|  `which <command>`  | показать путь к команде          |
|         `bc`        | калькулятор (**b**asic **c**alc) |
|  `factor <number>`  | разложение числа на множители    |
|        `cal`        | календарь (**cal**endar)         |
|        `date`       | текущая дата и время             |
|       `uptime`      | время работы системы             |

# 11. Tmux

Утилита которая позволяет
использовать несколько терминалов в одном окне

Создать сессию: `tmux new-session -s <name>`

Вернуться к сессии: `tmux attach -t <name>`

Вернуться к единственной сесии: `tmux attach`

Список сессий: `tmux ls` (**l**i**s**t-sessions)

|     Команда     | Действие                              |
|:---------------:|---------------------------------------|
|   Ctrl + B, C   | создать новое окно (**c**reate)       |
|   Ctrl + B, %   | разделить активное окно вертикально   |
|   Ctrl + B, "   | разделить активное окно горизонтально |
| Ctrl + B, Arrow | переместиться в нужную часть окна     |
|  Ctrl + B, num  | переключиться на окно с номером num   |
|   Ctrl + B, D   | отсоединиться от сесии (**d**etach)   |

# 12. Пакетный менеджер. TODO

[Ликбез о том, почему не стоит использовать make install](https://habr.com/ru/articles/130868)

Всё просто, но важно помнить что `make install` это плохо.
Если и делать make install, то хотя бы не ставить софт в систему.
Чтобы не делать make install, существует пакетный менеджер...
