```bash
sudo apt install -y python3-venv
```

```bash
mkdir environments
```

```bash
cd environments 
```

```bash
python3 -m venv server_env 
```

```bash
source server_env/bin/activate
```

```bash
~/environments/server_env/bin/jupyter lab
```

```bash
deactivate
```

## Создание kernel-ов в Jupyter

1. предварительно создаем и активируем виртуальную среду

2. устанавливаем пакет **ipykernel**:

```bash
pip install ipykernel
```

1. сохраняем **kernel**:

```bash
python -m ipykernel install --user --name _myenv_ --display-name "_Python (myenv)_"
```
    **name** используется для внутренних нужд, а **display-name** отображается в меню выбора ядер.

Следует отметить, что в некоторых случаях может понадобится дополнительно установить в окружение **kernel**-а пакет **jupyter**. 

Для отображения списка установленных ядер воспользуйтесь командой:


```bash
jupyter kernelspec list
```

На **Mac** ядра создаются в папке - **_папка_пользователя/Library/Jupyter/kernels/_**

_в **Windows** - **папка_пользователя**_**\AppData\Roaming\jupyter\kernels**




------------
```bash
pip install pipenv
```

```bash
pipenv install jupyterlab 
```

```bash
~/.local/bin - дир pipenv
```

```bash
pipenv run jupyter lab
```
