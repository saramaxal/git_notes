# Git заметки
*Заметки по работе с Git.*

Ссылка на классную и подробную инструкцию по установке и использованию Git, по которой были составлены заметки: [git-scm.com/book/ru/v2](https://git-scm.com/book/ru/v2/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E-%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B5-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D1%8F-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B9) (большое спасибо автору!)

[Установка Git для Windows](https://git-scm.com/download/win)

Github CLI - инструмент для использования GitHub из командой строки

[Установка Github CLI](https://github.com/cli/cli#installation) \
[Инструкция по GitHub CLI](https://cli.github.com/manual/)

## Термины
- **Working tree** - рабочая копия, файлы, которые можно редактировать
- **Staging area** - область отслеживаемых файлов, или файлы подготовленные для <u>фиксации</u>
- **Git directory** - подкаталог `.git`
- **Индексировать** - делать файл отслеживаемым на изменения (отправляет в `Staging area`)
- **Tracked, Untracked** - отслеживаемый / неотслеживаемый файл
- **Modified** - файл изменен (состояние, если файл `tracked`)
- **Снимок** - запись состояния репозитория
- **Snapsot** - последовательность снимков состояния (все версии проекта)
- **Commit** - <u>фиксация</u> в Snapsot
- **HEAD** - указатель на снимок последнего комита


## Основные команды 

`git config --global user.name "user name"` - предназначено для авторства в комите

`git config --global user.email <email>` - предназначено для авторства в комите

`git init` - создать репозиторий в существующем каталоге (создастся подкаталог `.git`)

`git clone <url>` - клонирование репозитория 

`git add file_name.txt`:
- добавить файл "file_name.txt" в `Staging area`
- Обновить файл в `Staging area`

`git status` - отображение отслеживаемых измененных файлов. Ключ `-s` или `--short` - короткая запись. 

`git diff` - просмотр непроиндексированных изменений. Ключ `--staged`- просмотр проиндексированного для следующего комита. 

`git commit -m "message"` - добавление файла в `Snapshot`. `message` - сообщение об изменениях с прошлого комита.  Ключ `-a` позволяет не использовать `git add`, однако это <u>не безопасно</u>. 

`git log` - список комитов

`git rm file_name.txt` - удалить файл. Без ключа `-f` не получится удалить файл со статусом `Untracked` или добавленным в `Staging area`

`git remote` - список удаленных подключений к репозиториям. Ключ `-v` включает URL-адрес каждого подключенения.

`git remote add <name> <url>` - создание подключения к репозиторию. `name`(обычно `origin`) - имя, по которому потом можно обращаться к централизованному репозиторию вместо `url`. 

`git remote get-url <name>` - просмотр подключенного репозитория

`git push <name> <branch>` - отправить в репозиторий последний снимок

`git pull <name> <branch>` - загрузить с репозитория в текущую ветку

`git fetch <name> <branch>` - загрузить с репозитория в новую локальную ветку `name/branch`

`git merge <branch>` - слияние текущей ветки и `branch`



## Git статусы
*Сокращенные статусы выделены*
- **nothing to commit, working tree clean** - отслеживаемые измененные файлы отсутствуют.
- `A_` **Changes to be committed** - файл проиндексирован.
- `_M` **Changes not staged for commit** - отслеживаемый файл изменен, но не проиндексирован.
- `M_` - модифицирован и проиндексирован.
- `MM` - есть изменения, которые не попадут в коммит (что бы не потерять изменения, нужно проиндексировать)
- `??` **Untracked** - неотслеживаемый файл. Git видит файл, которого не было в предыдущем коммите. 

## Git файлы
`.gitignore` - в нем перечисляются файлы, которые не должны попасть в комиты (пример: автоматически генерируемые файлы). Использует Glob шаблоны. 

Пример файла `.gitignore`:
```
*.txt
*.[oad]
*~
save/
#cat.md
!setting.json
```
[Генерация gitignore файла: toptal.com](https://www.toptal.com/developers/gitignore/)

[Описанием шаблонов: atlassian.com](https://www.atlassian.com/ru/git/tutorials/saving-changes/gitignore)