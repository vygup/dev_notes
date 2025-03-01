sudo apt install -y python3-venv

mkdir environments

cd environments 

python3 -m venv server_env 

source server_env/bin/activate

~/environments/server_env/bin/jupyter lab

deactivate
## Создание kernel-ов в Jupyter

1. предварительно создаем и активируем виртуальную среду

2. устанавливаем пакет **ipykernel**:

**pip install ipykernel**

1. сохраняем **kernel**:

**python -m ipykernel install --user --name _myenv_ --display-name "_Python (myenv)_"**

--**name** используется для внутренних нужд, а --**display-name** отображается в меню выбора ядер.

Следует отметить, что в некоторых случаях может понадобится дополнительно установить в окружение **kernel**-а пакет **jupyter**. 

Для отображения списка установленных ядер воспользуйтесь командой:

**jupyter kernelspec list**

На **Mac** ядра создаются в папке - **_папка_пользователя/Library/Jupyter/kernels/_**

_в **Windows** - **папка_пользователя**_**\AppData\Roaming\jupyter\kernels**




------------
pip install pipenv

pipenv install jupyterlab 

~/.local/bin - дир pipenv

pipenv run jupyter lab

