# Шпаргалка с полезнымы знаниями по git

## Навигация

pwd (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;

ls (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;

ls -a — покажи также скрытые файлы и папки, названия которых начинаются с символа .;

cd first-project (от англ. change directory, «сменить директорию») — перейди в папку first-project;

cd first-project/html — перейди в папку html, которая находится в папке first-project;

cd .. — перейди на уровень выше, в родительскую папку;

cd ~ — перейди в домашнюю директорию (/Users/Username);

cd / — перейди в корневую директорию.


## Работа с файлами и папками

### Создание
touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;

touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;

mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.

### Копирование и перемещение
cp file.txt ~/my-dir (от англ. copy, «копировать») — скопируй файл в другое место;

mv file.txt ~/my-dir (от англ. move, «переместить») — перемести файл или папку в другое место.
### Чтение
cat file.txt (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.
### Удаление
rm about.html (от англ. remove, «удалить») — удали файл about.html;

rmdir images (от англ. remove directory, «удалить директорию») — удали папку images;

rm -r second-project (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.
## Полезные возможности

Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (&&).
У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (↑) и вниз (↓).
Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать Tab. Если файл или папка есть в текущей директории, командная строка допишет путь сама.
Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите Tab. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать Enter.

# Работа с репозиторием

## Основные шаги при работе с репозиторием

### 1. Инициализируем репозиторий  
```
cd ~/dev/first-project # перешли в нужную папку  

git init # создали репозиторий
```

Если нужно удалить:  
```
cd <папка с репозиторием>

rm -rf .git
```  
Разберём подробнее, что такое -rf:  
ключ -r (от англ. recursive — «рекурсивно») позволяет удалять папки вместе с их содержимым;  
ключ -f (от англ. force — «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?».  

### 2. Добавляем нужные для проекта файлы (например, через touch или nano) и проверяем статус
```
touch aboba.txt

nano amogus.txt

git status
```

Затем, используем команду git add <filename>, git add --all или git add . (последняя команда добавляет всю текущую папку)

### 3. Делаем коммит
```
git commit -m "Логичное описание коммита"
```  
Команда git commit выведет информацию о коммите.  
При желании можно посмотреть историю коммитов с помощью команды git log

### 4. Создаем удалённый репозиторий в GitHub

Заходим во вкладку "Your repositories", затем на New. Создаем репозиторий.

### 5. Связываем локальный и удалённый репозитории

Переходим в наш локальный репозиторий с проектом с помощю команды cd.  
Затем прописываем команду:  
```
git remote add origin git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ_ПРОЕКТА%.git
```   
Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используйте слово "origin". А URL копируется со страницы удалённого репозитория.  
Убедиться, что репозитории связаны можно с помощью команды:
```
git remote -v
```
Далее будут выведены строчки вида:
```
origin git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ_ПРОЕКТА%.git (fetch)

origin git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ_ПРОЕКТА%.git (push)
```

### 6. Синхонизируем локальный и удалённый репозитории

Загрузить содержимое локального репозитория на GitHub можно с помощью "git push".  
В первый раз эту команду нужно вызвать с флагом "-u" (флаг свяжет локальную ветку с одноимённой удалённой)
```
git push -u origin main
```  

В дальнейшем достаточно будет использовать команду "git push"

----  

[Полезный курс от Яндекс Практикума по git](https://practicum.yandex.ru/profile/git-basics)
