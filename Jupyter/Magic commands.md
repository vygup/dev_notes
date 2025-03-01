```python
# list available python magics
%lsmagic
```


```python
#magic command
!ls 
%ls
```

```bash
%%bash
ls
#с указанием языка
#Над командами %% нельзя писать коменты 
```


```python
%quickref #This displays a quick-reference for the IPython shell.
```


```python
#документация по функции 
%pdoc print
```


```python
#просмотр подписи вызова функции или другого вызываемого объекта Python:
%pdef print
```


```python
#Для просмотра файла, в котором определен объект:
import pandas
%pfile pandas
```

---
```
%env
```
Можно управлять переменными среды для вашего блокнота без перезапуска Jupyter-сервера. Некоторые библиотеки (такие, как theano) используют переменные среды, чтобы контролировать поведение, и `%env` — самый удобный способ.

`%env` без переменной будет перечислять все переменные среды.

`%env` с одной переменной вернет значение для указанного параметра.

`%env variable value` задаст значение для указанного имени переменной.


```python
#without arguments lists environmental variables
%env
```

---
### Подробная информация об объекте

`%pinfo` предоставляет подробную информацию об объекте, который передается вместе с ним. Она похожа на функцию `object?`.

В следующем фрагменте я указал простую строку `“a”` вместе с `%pinfo`, чтобы получить подробную информацию о ней.


```python
a = "The World Makes Sense!"
%pinfo a
```

Иногда вывод не нужен, и в этом случае можно или использовать команду `pass` с новой строки, или поставить точку запятой в конце строки:


```python
asd = 1
asd;
# or
asd
pass
```

Просмотр исходников функций/классов/чего угодно с помощью вопросительного знака (?, ??)


```python
import pandas
??pandas
# or
?pyspark
```

---
Используйте `%run` для выполнения кода на Python
как .py так и .ipynb


```python
# this will execute all the code cells from different notebooks
%run ./myprint.py
%run myprint.py
```

---
`%load`

Загрузит код напрямую в ячейку. Можно выбрать файл локально или из сети.


```python
# %load http://matplotlib.org/mpl_examples/pylab_examples/contour_demo.py
```


```python
# %load myprint.py
def myprint():
    print('Hello')
myprint()
```

---
`%store` — ленивая передача данных между блокнотами


```python
data = 'this is the string I want to pass to different notebook'
%store data
del data # deleted variable
print (data)
```


```python
# in second notebook I will use:
%store -r data
print (data)
```


```python
del data # deleted variable
print (data)
```


```python
%store -d data
%store -r data
print (data)
```

---
`%who` для анализа переменных глобального пространства имен


```python
# pring names of string variables
%who int
print('------')
%whos int
print('------')
%who 
print('------')
%whos
print('------')
%who function
```


```python
%pip list
```

---
`%%time` - показывает время одной отработки

`%%timeit` - Запускает данный код много раз, а затем возвращает скорость самого быстрого результата.


```python
import time
%time time.sleep(2) 
print('-------- \n')
%timeit time.sleep(2)
```

---


```python
%%writefile writefile_test.py
#для переноса кода из ячейки в файл (если там уже есть код, файл будет перезаписан)
```


```python

```


```python
!jupyter nbconvert Jupyter.ipynb --to markdown 
# Конвертация в python file
```

    [NbConvertApp] Converting notebook Jupyter.ipynb to python
    [NbConvertApp] Writing 5512 bytes to Jupyter.py



```python
%pycat myprint.py
#Она позволяет просматривать содержимое любого файла в любом каталоге.
```

---


### Магия prun

`%prun` показывает, сколько времени ваша программа потратила на каждую функцию. Использование `%prun statement_name` даёт упорядоченную таблицу, показывающую, сколько раз каждая внутренняя функция была вызвана в блоке. А также время, которое потребовалось на каждый вызов, и суммарное время всех запусков функции.

Профилирование: `%prun`, `%lprun`, `%mprun` !!!Разобрать!!!


```python
# shows how much time program spent in each function
def myprint():
    print('Hello')

def ran():
    for i in range (10000):
        a=0
        a = a + i**2
#        print(a)

%prun ran()
#Не видит переменные созданные в ноутбуке, а не в функции
#%prun myprint()
```


```python
# tracking memory consumption (show in the pop-up)
%mprun -f ran()
#Не рабтает
```









---
Дебаг с помощью `%debug`

У Jupyter есть собственный интерфейс для ipdb, что позволяет зайти внутрь функции и посмотреть, что в ней происходит.


```python
#%%debug filename:line_number_for_breakpoint
# Here some code that fails. This will activate interactive context for debugging
```


```python
# дебаг 2, через терминал
%pdb

def pick_and_take():
    a = input('asd')
    b = 'asd'
    a + b
    return a + b
    
pick_and_take()
```


Для настройки макроса используется магия `%macro` и `%load`. Обычно принято имена макросов начинать с двойного подчеркивания, чтобы отличать их от других переменных.

```
%macro -q __hello_you 32
```

Магия `%macro` принимает имя и номер ячейки (или несколько номеров), а специальный ключ `-q` делает магию менее подробной. `%store` позволяет сохранить любую переменную для использования в других сессиях. В коде выше передаётся имя созданного макроса, чтобы можно было использовать его снова после выключения ядра или в других документах.

Чтобы загрузить макрос, достаточно выполнить следующее.

```
%load __hello_you
```

Чтобы выполнить макрос, можно просто запустить ячейку, которая содержит имя макроса.

```
__hello_you
Hello, Kitten!
```

Для наглядного примера измените переменную, использованную в макросе.

```
name = 'Muffins'
```

При запуске макроса захватывается измененное значение.

```
__hello_you
Hello, Muffins!
```

Это работает, потому что макросы выполняют сохраненный код в пространстве имён ячейки. Если `name` будет не определено, вы получите ошибку.

Если вы хотите использовать один и тот же макрос во всех своих документах, в этом может помочь `%store`.

`%store` позволяет хранить макрос и использовать его во всех Jupyter Notebook.
```py
%store -r __hello_you name = 'Rambo' %load __hello_you Hello, Rambo!
```


`%autosave` определяет, как часто ваш документ будет автоматически сохранять контрольные точки в файл.

```
%autosave 60
```

После данной команды автосохранение будет происходить каждые 60 секунд.


### Отображение графиков

```
%matplotlib inline
```

Эта команда отобразит графики Matplotlib прямо в выводе ячейки. Это означает, что диаграммы и графики Matplotlib можно включать прямо в свои документы. Имеет смысл запустить команду в начале вашего документа, прямо в первой ячейке.


### Запуск кода из другого ядра

Можно запустить выполнение ячейки с использованием указанного языка. Существуют расширения для нескольких языков. Есть опции вроде:

- `%%HTML`,
- `%%python`,
- `%%python2`,
- `%%python3`,
- `%%ruby`,
- `%%perl`,
- `%%capture`,
- `%%javascript`,
- `%%js`,
- `%%latex`,
- `%%markdown`,
- `%%pypy`.

Например, для рендеринга HTML в вашем документе вы должны выполнить следующее:

```
%%HTML
This is really neat!
```

Вы также можете использовать LaTeX напрямую когда угодно:

```
%%latex
This is an equation: $E = mc^2$
```


### Графики высокого разрешения

Одна простая магическая строка IPython может предоставит вам на выводе график с двойным разрешением для экранов Retina. Стоит отметить, что на других экранах график может не отображаться.

```
%config InlineBackend.figure_format ='retina'
```

### Пропуск ячейки для выполнения

Просто добавьте `%%script false` в начале ячейки:

```
%%script false --no-raise-error
%%script true
Можете поместить здесь длинный код,
который вы хотите исключить из выполнения
прямо сейчас
```

## Оповещения

Оповещения могут пригодиться, когда вы запускаете код, требующий долгого выполнения. Вы можете настроить уведомление, которое будет отправлено, когда код выполнится.

### На Linux и Mac

```
import os
duration = 1 # секунды
freq = 440 # Гц
os.system('play --no-show-progress --null --channels 1 synth %s sine %f' % (duration, freq))
```

### На Windows

```
import winsound
duration = 1000 # миллисекунды
freq = 440 # Гц
winsound.Beep(freq, duration)
```

Чтобы использовать такое оповещение, у вас должен быть установлен `sox`. Установить его можно с помощью следующей строки:

```
$ brew install sox
```

Но это сработает, только если вы пользуетесь Homebrew.