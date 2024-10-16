# Игнорирование файлов в Git

Чтобы Git игнорировал файлы, которые не требуют отслеживания и не пытался добавить их в репозиторий, нужно создать файл *.gitignore* (от англ. ignore — «игнорировать») и записать в него названия игнорируемых файлов.  

#### Комментарии

Если строка начинается с #, то Git не будет его учитывать

``` bash
#это строка будет проигнорированная
#и эта тоже
```

#### Просто название файла

Допустим, нужно, чтобы Git игнорировал все файлы *.DS_Store.* Для этого достаточно добавить в *.gitignore* строку с названием файла.

``` bash
#Файл ниже будет игнорироваться
.DS_Store
```

В таком случае Git будет игнорировать файлы с именем *.DS_Store*, причём не только в корне репозитория, но и во всех вложенных папках.

#### Звездочка (*)

Символ звёздочки (*) соответствует любой строке, включая пустую. Если такой символ используется в шаблоне в *.gitignore*, значит, файл будет проигнорирован вне зависимости от того, что будет на месте звёздочки.

``` bash
# игнорировать все файлы, которые заканчиваются на .jpeg
*.jpeg

# игнорировать все файлы "tmp" во всех подпапках папки docs
docs/*/tmp
```

Теперь Git будет игнорировать все файлы, которые заканчиваются на .jpeg — пригодится тем, кто не любит картинки. А также все временные файлы tmp (от англ. temporary — «временный») в подпапках папки docs. Например, Git проигнорирует файл docs/current/tmp.

#### Вопросительный знак (?)

Вопросительный знак ? соответствует одному любому символу.

``` bash
file?.txt
```

Если сохранить такую запись в *.gitignore*, то будут проигнорированы, например, файлы fileA.txt и file1.txt. А вот файл *file12.txt* не будет проигнорирован, потому что в его названии два символа после *file*, а не один.

#### Квадратные скобки ([])

Квадратные скобки, как и вопросительный знак, соответствуют одному символу. При этом символ не любой, а только из списка, который указан в скобках.

``` bash
# игнорировать файлы file0.txt, file1.txt и file2.txt
# при этом не игнорировать file3.txt, file4.txt, ...
file[0-2].txt
```

В скобках можно либо перечислить символы ([abc]), либо задать диапазон ([a-z]).

#### Слеш (/)

Косая черта, или слеш (/), указывает на каталоги. Если шаблон в *.gitignore* начинается со слеша, то Git проигнорирует файлы или каталоги только в корневой директории.

``` bash
# игнорировать todo.txt в корне репозитория
/todo.txt

# для сравнения: spam.txt будет игнорироваться во всех папках
spam.txt 
```

Теперь файл *todo.txt* в корневом каталоге будет проигнорирован. При этом, например, файл *subdir/todo.txt* по-прежнему отслеживается.  
Если шаблон заканчивается слешем, то правило применится только к папке.

``` bash
# игнорировать папку build
build/ 
```

Обратите внимание: если *build* — это папка, то она будет проигнорирована. Если *build* — обычный файл, то он не подпадёт под правило и не будет игнорироваться.

#### Двойные звездочки (**)

Функция парных звёздочек (**) похожа на функцию одинарной (*). Отличие в том, как они работают с вложенными папками. Двойная звёздочка может соответствовать любому количеству таких папок (в том числе нулю). Одинарная может соответствовать только одной.

``` bash
# игнорировать файлы "docs/current/tmp", "docs/old/tmp",
# а также "docs/old/saved/a/b/c/d/tmp"
# и даже "docs/tmp", потому что ноль вложенных папок тоже подходит
docs/**/tmp

# игнорировать только "docs/current/tmp" и "docs/old/tmp"
# файл "docs/old/saved/a/b/c/d/tmp" не попадает в правило
docs/*/tmp 
```

#### Восклицательный знак (!)

Любое правило в файле *.gitignore* можно инвертировать с помощью восклицательного знака (!).

``` bash
# игнорировать все JPEG-файлы
*.jpeg

# но только не мем с Doge
!doge.jpeg
```

Теперь файл doge.jpeg будет отслеживаться, хотя остальные jpeg-файлы будут проигнорированы. Такие правила удобны для добавления исключений из других правил *.gitignore*.

#### Отображение игнорируемых файлов

``` bash
$ git status --ignored #Отобразить игнориуремые файлы
```

> [**Вернуться назад**](https://github.com/ilezzov-code/GitCrib/)
