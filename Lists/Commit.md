# Работа с коммитами

Вы всегда будете делать коммиты, чтобы сохранить свои изменения!

Сделать коммит
``` bash
$ git commit -m <сообщение>
```

Откатить коммит
```bash
$ git reset --hard <hash>
```

Редактировать последний коммит
``` bash
$ git commit --amend --no-edit #no-edit - оставить старое сообщение коммита 
```

Просмотр изменений коммита
``` bash
$ git diff #Не учитывает файлы в staged
$ git diff --staged #Учитывать файлы в staged
$ git diff <hash> <hash> #Сравнить два коммита
```

> [**Вернуться назад**](https://github.com/ilezzov-code/GitCrib/)