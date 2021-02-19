# Маленький скрипт для генерации `.md` файлов для конспектирования лекций

Основная идея: перед началом конспектирования лекции, в директории предмета выполнить скрипт, который создаст файл вида `%current_dir_name%_%date%.md`.

## Пример выполнения

```bash
me@pc:~/Nextcloud/University/SQL$ lecture_maker.sh
me@pc:~/Nextcloud/University/SQL$ ls
SQL_15.02.2021.md
```

Для корректной работы срипта надо скопировать его в любую из папок которая добавлена в `PATH` или добавить папку со скриптом в `PATH`. Посмотреть папки которые глобально доступны: `echo $PATH`

## Шаблон файла

Текущий шаблон выглядит вот так

```markdown
# %current_date%


```

## Возможные дополнения

- Добавить автоматическую нумерацию (??)
- ~~Добавить полное название предмета на русском в первую строку файла~~
- Переписать всё на `python` и посмотреть в чем будет разница (??)
- ~~Сразу передавать созданный файл в `Typora`~~
- ~~Сделать модуль для лекция и для семинаров~~
- Написать скрипт который будет формировать словарь типа `subj_handler`: `subj_name` на основании гугл таблички
