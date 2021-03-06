<h1 align="center">Горячие команды Git</h1>

## Начало работы

### Базовые настройки:
Перед началом работы следует зарегистрировать себя на рабочей машине, так git сможет получать ваши данные о коммитаx:
```sh
$ git config --global user.name "Your Name"

$ git config --global user.email "your_email@whatever.com"
 ```
 Создание репозитория:

git init - Эта команда создаёт в текущем каталоге новый подкаталог с именем .git содержащий все необходимые файлы репозитория — основу Git-репозитория.(Появляется скрытая папка). Проще говоря создает локальный репозиторий.

```sh
$ git clone "url" - скачивает удаленный репозиторий(например с github).

$ git clone https://github.com/Eclerrr/readme.git(тестовый url)
 ```




## Базавые операции:

### Рабочая схема:

1) Создать локальный репозиторий.(клонировать удаленный или создать новый).

2) Выбрать версию проекта. "git checkout хеш"(если нужна свежая скачанная версия, пропускаем этот пункт).

3) Внести изменения в файлах.

4) Проверить изменнения с помощью "git status". Если все хорошо, надписи красные , продолжаем работу.

5)$ git add имя файла  - проиндексировать изменненые файлы, зафиксировать.

6) Пришло время создать коммит $ git commit -m"комментарий". После этого появится новая версия вашего проекта.

7) Проверить новый коммит командой  $ git log. Если все нормально переходим дальше.

8) Самое время отправить на сервер.
```sh
$ git push https://github.com/Eclerrr/readme.git master.
```
Ссылка примерная

### Работа с историей:
Эти команды помогут избежать ошибок в будущем.

```sh
$ git log - показывает все создынные коммиты на текущей версии.
```
Отображается примерно так:

```sh
commit 903badab46602ecfdd504e16f099f837901789b7
Author: Eclerr <eclerrrr@yandex.ru>
Date:   Tue Jan 19 18:24:50 2016 +0300
Создан файл commands.txt. Добавлен абзац 'Начало работы'
```
903badab46602ecfdd504e16f099f837901789b7 - хеш коммита(Имя коммита)

Если ***изменения нужно откатить до индексации***, поможет команды:
```sh
$ git checkout файл.
```

По факту эта команда переместит вас в последнию версию файла, без каких либо изменений. Данная операция напоминает ctrl + z в обычном редакторе. Естественно, нужно находится в тойже ветке, что и изменяемый файл.

Если ***изменения были индексированны*** и нужно откатиться перед самим коммитом.
```sh
$ git reset HEAD файл
```
Команда отменяет индексацию , а затем можно опять воспользоваться checkout.

### Работа с коммитами:

После создания локального репозитория можно начинать в нем работу(создание, удаление, редактирование файлов). Как только вы ввели в консоль $ git init или $ git clone,git сразу начинает отслеживать папку в которой лежит скрытый файлик .git. Любые изменения фиксируются в гите.
```sh
$ git status - Определить состояние файлов.

$ git add - Многофунциональная команда.

$ git add имя файла - Фиксирует измененный файл в гите. Предворительная фаза перед коммитом(подстраховка).

$ git add . - фиксирует все файлы в каталоге.(Использовать с осторожностью).
```
После фиксирования, файлы можно коммитеть(Сохранять).
```sh
$ git commit -m"комментарий" - Создает коммит (версию) вашего проекта.
```
Метка -m добавляет комментарий к комиту. Можно коммитеть без метки , но тогда git выведет редактор по умолчанию(Редактор linux). Настройка редактора будет описана в другом разделе. Лучше делать логичные коммeнтарии, типа "Добавлен файл index.html".
```sh
$ git shortlog -s -n  - количество сделанных коммитов у данного пользователя
```
### Перемещение по коммитам:

Когда ваш проект набирает обороты и появляется большое количество коммитов, может возникнуть потребность в откате версии(или простого просмотра старых версий).

```sh
$ git checkout 903ba - переходит на указанный коммит. 
```
903ba в данном случае 5 первых символов хеша коммита. checkout возвращает вас назад во времени, а это значит что коммиты, созданные после указанного не будут отображаться в git log(их по факту еще не создали).
```sh
$ git checkout master - переместит на последний коммит(вернет в настоящие).
```
### Редактирование коммитов:

Если возникла потребность изменить сделать небольшую поправочку в каком либо файле, при этом не делать новый коммит(К примеру добавить комментарий), можно перезаписать коммит:

```sh
$ git commit --amend -m"Перезапись коммита", При этом перезапишется последний коммит.
```

### Работа с ветками:

 	$ git branch - просмотреть список веток

 	$ git checkout -b имя ветки -  создать ветку и срузу же перейти в нее(с помощью ключа -b)

 	$ git branch имя ветки - создать ветку

	$ git checkout имя ветки - перейти в ветку.

	$ git checkout master - перейти в начальную ветку вашего проекта.


### Работа с удаленным репозиторием

После того, как вы сделали достаточное количество коммитов, самое время отправить ваш проект со всеми сохранениями на удаленный репозиторий(к примеру GitHub).
```sh
$ git push https://github.com/Eclerrr/readme.git master   -  отправляет проиндексированные и закоммиченные изменения вашего проекта на сервер.
```
url репозитория указан тестовый

master - начальная ветка удаленного репозитория(Можно использовать любую другую ветку)
	
Если во время работы ваш локальный репозиторий устаревает(К примеру, кто-то другой уже запушил изменения на сервер), можно обновить вашу версию локального проекта:

$ git ************************************************

Для удобства url можно поместить в короткое имя:
```sh
$ git remote add pb git://github.com/paulboone/ticgit.git
```
pb - короткое имя url, в дальнейшем с ним можно работать.
```sh
$ git remote -v - позволяет вывести все имена url.
```





## Вопросы на будущие:
	
Тут будут копится мои вопросы на будущие:

1) Как удалить ветку.

2) Обновление удаленного репозитория.

3) Перезапись коммита.
