# Работа с файлами

Работа с файлами — одно из самых частых действий, которые Вы будете выполнять. Вам постоянно придется фиксировать изменения или откатываться к предыдущим изменениям.

Зафиксировать изменения файла
``` bash
$ git add <file>
$ git add --all #Добавить все файлы директории
$ git add . #Добавить все файлы директории
```

Удалить файл из staged
```bash
$ git restore --staged <file>
```

Откатить файл, который ни в staging, ни в коммит
```bash
$ git restore <file>
```

> [**Вернуться назад**](https://github.com/ilezzov-code/GitCrib/)