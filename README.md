# 2021-nosql-lsm
Курсовой проект 2021 года [курса](https://polis.mail.ru/curriculum/program/discipline/1169/) "Использование баз данных" в [Технополис](https://polis.mail.ru).

## Этап 1. In-memory (deadline 2021-05-12 00:00:00 MSK)
### Fork
[Форкните проект](https://help.github.com/articles/fork-a-repo/), склонируйте и добавьте `upstream`:
```bash
$ git clone git@github.com:<username>/2021-nosql-lsm.git
Cloning into '2021-nosql-lsm'...
...
$ cd 2021-nosql-lsm
$ git remote add upstream git@github.com:polis-mail-ru/2021-nosql-lsm.git
$ git fetch upstream
From github.com:polis-mail-ru/2021-nosql-lsm
 * [new branch]      master     -> upstream/master
```

### Make
Так можно запустить тесты (ровно то, что делает CI):
```
$ ./gradlew test
```

### Develop
Откройте в IDE -- [IntelliJ IDEA Community Edition](https://www.jetbrains.com/idea/) нам будет достаточно.

В своём Java package `ru.mail.polis.lsm.<username>` реализуйте интерфейс [`DAO`](src/main/java/ru/mail/polis/lsm/DAO.java), используя одну из реализаций `java.util.SortedMap`.

Возвращайте свою реализацию интерфейса в [`DAOFactory`](src/main/java/ru/mail/polis/lsm/DAOFactory.java#L57).

Продолжайте запускать тесты и исправлять ошибки, не забывая [подтягивать новые тесты и фиксы из `upstream`](https://help.github.com/articles/syncing-a-fork/). Если заметите ошибку в `upstream`, заводите баг и присылайте pull request ;)

### Report
Когда всё будет готово, присылайте pull request в ветку `stage1` со своей реализацией на review. Не забывайте **отвечать на комментарии в PR** и **исправлять замечания**!

## Этап 2. Persistence (deadline 2021-05-19 00:00:00 MSK)
### Update
Находясь в той ветке, где находится ваш код из Этапа 1, выполните:
```bash
$ git fetch upstream
$ git merge upstream/stage2
```

### Make
Запускаем обновленные тесты
```
$ ./gradlew test
```

### Fix
Преведите код в состояние, удовлетворяющее новым тестам. А именно: при конструировании DAO следует восстановить состояние, персистентно сохраненное в методе close.
Следует иметь ввиду, что в дальнейшем в этом файле будет происходить бинарный поиск без полной загрузки в память (но на данном этапе, это можно игнорировать).

### Report
Когда всё будет готово, присылайте pull request в ветку `stage2` со своей реализацией на review. Не забывайте **отвечать на комментарии в PR** и **исправлять замечания**!
