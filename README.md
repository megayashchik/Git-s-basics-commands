# Git-s-basics-commands

## Основные команды Git


**Навигация:**

+	**pwd** (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
+	**ls** (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
+	**ls -a** — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
+	**cd first-project** (от англ. change directory, «сменить директорию») — перейди в папку first-project;
+	**cd first-project/html** — перейди в папку html, которая находится в папке first-project;
+	**cd ..** — перейди на уровень выше, в родительскую папку;
+	**cd ~** — перейди в домашнюю директорию (/Users/Username);
+	**cd /** — перейди в корневую директорию.


**Работа с файлами и папками**


**Создание**

+	**touch index.html** (англ. touch, «коснуться») — создай файл index.html в текущей папке;
+	**touch index.html style.css script.js** — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
+	**mkdir second-project** (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.


**Копирование и перемещение**

+	**cp file.txt ~/my-dir** (от англ. copy, «копировать») — скопируй файл в другое место;
+	**mv file.txt ~/my-dir** (от англ. move, «переместить») — перемести файл или папку в другое место.


**Чтение**

+	**cat file.txt** (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.


**Удаление**

+	**rm about.html** (от англ. remove, «удалить») — удали файл about.html;
+	**rmdir images** (от англ. remove directory, «удалить директорию») — удали папку images;
+	**rm -r second-project** (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.


**работа с репозиторием**

+ 	**git init** - сделать папку репозиторием 
+ 	**— rm -rf .git** - «_разгитить_» папку, если что-то пошло не так
+ 	**git status** - проверить состояние репозитория
+ 	**git add** - подготовить файлы к сохранению
+ 	**git commit** - выполнить коммит
+ 	**git log** - просмотреть историю коммитов
+ 	**git remote add** - привязать удалённый репозиторий к локальному
+ 	**git push** - отправить изменения на удалённый репозиторий
+ 	**git remote -v** - убедиться, что репозитории связаны
+ 	**git push** - отправить изменения на удалённый репозиторий
+ 	**git clone** - клонировать репозиторий


## Хеш

**Хеш — идентификатор коммита**

Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на  
предыдущий, или родительский (англ. parent), коммит. Git хеширует (преобразует) эту информацию с помощью алгоритма SHA-1  
(от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого коммита свой уникальный хеш —  
результат хеширования.
В то время, как результат работы метода hashCode() — это целое число, результат хеширования в Git — символьная строка. Она  
относительно коротка (40 символов в случае SHA-1) и состоит из цифр 0—9 и латинских букв A—F (неважно, заглавных или  
строчных). Хеш обладает следующими важными свойствами:

+    если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;
+    если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).


## Лог

После вызова git log появляется список коммитов с их описанием.

Вот из каких элементов состоит описание:

    1. Строка из цифр и латинских букв после слова **commit** — это уже знакомый вам хеш коммита.
    2. **Author** — имя автора и его электронная почта.
    3. **Date** — дата и время создания коммита.
    4. Сообщение к коммиту.
	
Если в репозитории уже много коммитов — например, сотни или тысячи, — пригодится сокращённый лог. С ним можно быстро найти нужный  
коммит по описанию.
Сокращённый лог вызывают командой git log с флагом --oneline (англ. «одной строкой»). При этом в терминале появятся только первые  
несколько символов хеша каждого коммита и комментарии к ним.

Сокращённый хеш (первые несколько символов полного) можно использовать точно так же, как и полный. Для этого команда  
git log --oneline автоматически подбирает такую длину сокращённых хешей, чтобы они были уникальными в пределах репозитория и Git  
всегда мог понять, о каком коммите идёт речь.

:bulb: Обратите внимание: если выход из просмотра логов не произошёл автоматически, нажмите клавишу Q (от англ. Quit — «выйти») в  
английской раскладке клавиатуры.


## Head

Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним  
(то есть на самый новый).

Внутри HEAD — ссылка на служебный файл: refs/heads/master (или refs/heads/main в зависимости от названия ветки). Если заглянуть в  
этот файл, можно увидеть хеш последнего коммита.

Когда вы делаете коммит, Git обновляет refs/heads/master — записывает в него хеш последнего коммита. Получается, что HEAD тоже  
обновляется, так как ссылается на refs/heads/master.

При работе с Git указатель HEAD используется довольно часто. Мы уже упоминали, что многие команды Git принимают в качестве  
параметра хеш коммита. Если нужно передать последний коммит, то вместо его хеша можно просто написать слово HEAD — Git поймёт,  
что вы имели в виду последний коммит.