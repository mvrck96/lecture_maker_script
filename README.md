NB: Если файл начинается с указания типа **shebang** [link](https://en.wikipedia.org/wiki/Shebang_(Unix)) файла, то можно не писать `.sh` или `.py`

```bash
#!/bin/bash OR #!/bin/python3
```

# 1. Генерация шаблонов для записи лекций :robot:

Основная идея: перед началом конспектирования лекции, в директории предмета выполнить скрипт, который создаст файл вида `%current_dir_name%_%date%.md`, который автоматически открывается в `Typora`.

### Пример выполнения

```bash
user@host:~/University/SQL$ lecture_maker.sh s
user@host:~/University/SQL$ ls
SQL_sem_15.02.21.md
```
После того, как репозиторий клонирован надо выполнить `chmod 700 lecture_maker.sh`, для того чтобы скрипт можно было выполнить из шела.

> Если по ошибке была добавлена не та директория а `PATH` то восстановить предыдущее состояние можно так:
>   1. Выполнить echo $PATH
>   2. Скопировать всю строку вывода, кроме ошибочной директории
>   3. Выполнить `export PATH=%скопированная строка%`

Для корректной работы скрипта надо скопировать его в любую из директорий, которая добавлена в переменную`PATH`, или добавить директорию со скриптом в `PATH`

Добавить текущую директорию в `PATH` можно так: `export PATH=$PATH:$(pwd)`, однако таким способом переменная `PATH` будет изменена только внутри одной терминальной сессии. 



---

**Для того чтобы обновить `PATH` глобально**, необходимо открыть файл `~/.profile` и добавить следующий код `export PATH="$PATH:/path/to/your/dir"` 

---



Посмотреть директории которые глобально доступны: `echo $PATH`

### Шаблон файла

Текущий шаблон выглядит вот так

```markdown
# %Название_предмета% %семинар|лекция% 20.02.21


```

### Возможные дополнения

- Добавить автоматическую нумерацию :question:
- Написать скрипт который будет формировать словарь типа `subj_handler`: `subj_name` на основании гугл таблички
  - *забирать пайтоном табличку из гдиска, формировать файлик, читать файлик скриптом словарь*

# 2. Создание директории для блог поста :page_facing_up:

Создает шаблон для поста `HUGO`. Формат шаблона как в блоке ниже

```markdown
---
date: 2021.11.08
title: "my-best-title"
draft: true
tags: ["TAGS_HERE"]
cover:
    image: "pics/COVER_IMAGE.PNG"
    relative: true
    alt: "ALT TEXT HERE"
    caption: "CAPTION HERE"
---
```

Для вызова надо передать название поста или ничего. Если передано ничего, то будет создана директория `draft_post_TIMESTAMP`. Пример вызова:

```bash
user@host:~$ ./post_maker.sh my-best-title
user@host:~$ tree
.
└── my-best-title
    ├── index.md
    └── pics
```



