# Установка

```bash
mkdir -p ~/miniconda3

curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh -o ~/miniconda3/miniconda.sh

bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3

rm -rf ~/miniconda3/miniconda.sh
```

```bash
~/miniconda3/bin/conda init bash

~/miniconda3/bin/conda init zsh
```

```bash
source ~/miniconda3/bin/activate

conda init
```


# Команды 

```
conda info --envs
```

```
conda create -n myenvironment 
```
or

```
conda create -n myenvironment python numpy pandas
```

Via environment activation:
```
conda activate myenvironment
conda install matplotlib
```

Via command line option:
```
conda install --name myenvironment matplotlib
```

[Подробнее](https://python.ivan-shamaev.ru/guide-conda-environments-anaconda-python-data-science-platform/)

----

# Информация

**Miniconda** — это минимальный дистрибутив, включающий в себя conda, Python, пакеты, от которых они зависят, и минимум самых полезных дополнительных пакетов, таких как _pip_ или _zlib_. Все остальное (в том числе Anaconda Navigator) вы можете установить самостоятельно.


Чтобы узнать, что именно входит в Miniconda, выполните команду `condalist` после установки Miniconda.


## Просмотр основной информации о conda[](http://miniconda.geekwriter.ru/conda-commands.html#conda-basics "Link to this heading")

Показать информацию об установленной версии conda:

`conda info`

Показать список пакетов, установленных вместе с conda:

`conda list`



## Базовые команды для управления средой[](http://miniconda.geekwriter.ru/conda-commands.html#environment-management "Link to this heading")

Создадим, активируем и деактивируем виртуальную среду с именем _docdev_:

- Создать виртуальную среду _docdev_:
    
    `conda create --name docdev python`
    
- Активировать среду _docdev_:
    
    `conda activate docdev`
    
    Примечание
    
    Для версии Miniconda более ранней, чем 4.6, в Windows вместо `condaactivate` используйте `activate`.
    
- Деактивировать активную среду (в нашем случае деактивируется среда _docdev_и активируется среда по умолчанию _base_):
    
    `conda deactivate`

Сделать точную копию окружения

conda create -n flowers --clone snowflakes

Удалить среду

conda remove -n flowers --all

Сохранить текущую среду в файл

conda env export > puppies.yml

Загрузить среду из файла

conda env create -f puppies.yml



## Базовые команды для управления пакетами[](http://miniconda.geekwriter.ru/conda-commands.html#package-management "Link to this heading")

Установим, обновим и удалим пакет _sphinx_:

- Установить пакет _sphinx_ в активной среде:
```
conda install sphinx
```
    
- Установить пакет _sphinx_ в среде _docdev_:
```
conda install -n docdev sphinx
```
    
- Обновить пакет _sphinx_ в среде _docdev_:
```
conda update -n docdev sphinx
```
    
- Удалить пакет _sphinx_ из активной среды:
    
    `conda remove sphinx`
    

Более подробную информацию см. в [документации conda](https://docs.conda.io/projects/conda/en/latest/commands.html).


```bash
conda remove --name myenv --all
```



```bash
conda install jupyterlab
```



# Как безопасно удалить Anaconda и восстановить Python на Mac

## Быстрый ответ

Для удаления Anaconda воспользуйтесь командой **`anaconda-clean`**, которая позволит очистить конфигурационные файлы. Затем следует удалить корневую папку. Процедура выглядит следующим образом:

1. **Очищаем конфигурации** при помощи `anaconda-clean`:
    
    ```
    conda install anaconda-clean && anaconda-clean --yes  # Очищаем настройки!
    ```
    
2. **Удаляем** корневую папку Anaconda (для Unix-подобных систем это `~/anaconda3`, а для Windows — `C:\Users\<Имя пользователя>\Anaconda3`):
    
    ```
    rm -rf ~/anaconda3  # Для Unix-подобных систем
    rmdir /S /Q C:\Users\<Имя пользователя>\Anaconda3  # Для Windows
    ```
    
3. **Обновляем переменную** PATH в вашей системе, чтобы избавиться от ссылок на папки Anaconda.
    

Не забудьте создать **резервные копии** для сохранения важных данных перед началом работы.

## Очистка конфигураций после удаления

После удаления **папки Anaconda** важно избавиться от **остатков конфигураций**. Проверьте и, при необходимости, измените файлы инициализации оболочки, такие как `~/.bash_profile` или `~/.bashrc` на Unix-подобных системах и `C:\Users\<Имя пользователя>\.bash_profile` на Windows, чтобы удалить упоминания о Anaconda из PATH.

Также стоит просмотреть скрытые директории `.condarc`, `.conda` и `.continuum` на предмет **устаревших настроек** или данных о предыдущем использовании и при необходимости удалить их.

Чтобы убедиться, что стандартный интерпретатор Python не связан с Anaconda, выполните команду `which python` (для Unix-подобных систем) или `where python` (для Windows). Затем перезагрузите оболочку, используя команду `source ~/.bashrc`, или откройте новое окно командной строки на Windows, чтобы изменения вступили в силу.

## Проверка полного удаления Anaconda

Чтобы убедиться в полном удалении Anaconda, попробуйте воспользоваться командой `conda` или другим инструментом, связанным с ней. Если команда не найдена и возникает ошибка, значит, удаление прошло успешно!

Используйте команду `rm -rf` с осторожностью, поскольку она может удалить важные данные.

## Обеспечение будущего без конфликтов

После удаления Anaconda очистите PATH от всех упоминаний о ней, просмотрев файлы `.bash_profile` или `.bashrc`. Создайте резервные копии этих файлов перед внесением изменений – это поможет избежать ошибок.

## Визуализация

Процесс удаления Anaconda можно сравнить с прочисткой заросшего леса:

Markdown

Скопировать код

```markdown
До: 🎢🔧 [Anaconda с засорёнными зависимостями]
```

Безопасная процедура удаления:

Python

Скопировать код

```python
conda remove --name myenv --all        # Удаление конкретного окружения
conda env remove --name myenv          # Альтернативная команда для этого
anaconda-clean --yes                   # Глубокая очистка
rm -rf ~/anaconda3                     # Полное удаление
```

После того, как вы выполнили все действия:

Markdown

Скопировать код

```markdown
После: 🏗️🧹 [Система в порядке и ослепляет чистотой]
```

**Главное правило** : будьте внимательны на каждом этапе. Это позволит систематически удалить все элементы, избегая серьёзных ошибок.

## Сценарий работы: Резервное копирование и anaconda-clean

Даже если вы временно прощаетесь с Anaconda, сохраните резервную копию, которая может пригодиться в будущем. `anaconda-clean` поможет удалить файлы и папки, связанные с Anaconda.

## Восстановление системного python

После удаления Anaconda установите системный Python как стандартный интерпретатор или при необходимости переустановите его. Если вы используете macOS, помните о разнице между `python` для версии 2.7 и `python3` для версий 3.x.