# Состояния в Git 

<p>У Git есть несколько состояний, которые нужны знать:</p>
<ul>
    <li>не отслеживаемое (untracked)</li>
    <li>измененное (modified)</li>
    <li>подготовленное (staged)</li>
    <li>закомиченное (commited)</li>
</ul>

## Подробнее про состояния

<p>Это состояния, в которых находятся файлы вашего проекта. Жизненный путь файлов выглядит так:</p>
<ol>
<li>Файл, который вы создали, но не добавили в git-репозиторий, 
будет в состоянии <code>untracked</code>.</li>
<li>После внесения изменений в файл, который уже добавлен в git-репозиторий, он перейдет в состояние <code>modified</code>.</li>
<li>Из тех файлов, которые были изменены, выбираем те (или все), которые нам нужны (например, файл Базы данных мы не добавляем). Эти файлы попадают в состояние <code>staged</code>.</li>
<li>Из заготовленных файлов из состояния <code>staged</code> создается <code>commit</code> и переходит уже в репозиторий. После этого <code>staged</code> состояние - пустое. А вот <code>modified</code> еще может что-то содержать.</li>
</ol>

## Коммит
<p>Коммит - это основной объект в управлении контроля версий. Он содержит все изменения за время этого коммита. Коммиты связаны между собой как односвязный список.
Также у коммита есть метаданные (собственная информация):</p>
<ul>
<li>Уникальный идентификатор коммита, по которому его можно найти;</li>
<li>имя автора коммита, который его создал;</li>
<li>дата создания коммита;</li>
<li>комментарий (сообщение), который описывает, что было сделано во время этого коммита;</li>
</ul>

# Работа с git 
<p>Для того, чтобы узнать, что происходит в вашем Git репозитории, используется команда <code>git status</code>. Она отдает всю информацию о файлах вашего репозитория (кто изменен, кто не отслеживается, кто закоммичен и т.д.)</p>

<p>Чтобы добавить файл в репозиторий, используем команду <code>git add</code>:</p>
<ul>
<li><code>git add -A</code> - добавить ВСЕ файлы из состояния в <code>staged</code>.</li>
<li><code>git add .</code> - добавить все файлы из этой папки и все внутренние.</li>
<li><code>git add &lt;имя_файла&gt;</code> - добавляет только конкретный файл. Можно использовать регулярное выражение, чтобы добавлять файлы по шаблону. Например: <code>git add *.py</code> - добавит ВСЕ файлы, расширение которых - .py</li>
</ul>

<p>Чтобы сделать коммит, пишем команду <code>git commit -m "сообщение коммита"</code></p>
<p>Чтобы увидеть изменения, пишем <code>git log</code></p>

## Работа c .gitignore

<p>Ясно, что мы хотим оставить в репозитории только нужные нам файлы (исходный код проекта). В проекте могут быть файлы с переменными среды, файлы БД, техническая/мета-информация, папка .venv - всего этого в репозитории быть не должно.</p>
<p>Вы можете игнорировать ненужные файлы и папки при помощи специального файла, который нужно создать. Файл называется <code>.gitignore</code>. Его нужно создать в папке проекта (корневой), в этом файле каждая строка будет шаблоном для игнорирования.</p>

<p>Например:</p>
<pre><code>
.idea
.venv
*.txt
</code></pre>
<p>В этом файле говорится, что в git-репозиторий не нужно добавлять папку .idea, папку .venv и ВСЕ файлы с расширением .txt.</p>
<p>После добавления файла с игнором в проект, его также нужно добавить в Git-репозиторий командой <code>git add .gitignore</code> и сделать коммит.</p>

<p>Файл позволяет вам сделать так, чтобы не все, а только необходимые файлы, попадали в репозиторий в том числе с командой <code>git add -A</code>.</p>