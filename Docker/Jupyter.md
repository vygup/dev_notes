## Установка
Сначала запускаем образ чистой `Debian`:
```bash
sudo docker run -dit --name jupyter debian
```

Входим в командную строку контейнера:
```bash
sudo docker exec -u root -it jupyter bash
```

## Настройка контейнера:
Для автозапуска от лица `jupyter` добавляем в `/root/.bashrc` следующее:
```bash
echo '/bin/su -c "/home/jupyter/.local/bin/jupyter-lab --ip 0.0.0.0 >/dev/null 2>&1 &" - jupyter' >> /root/.bashrc
```

Устанавливаем `python`:
```bash
apt update

apt install -y python3-pip python3-dev
```

Меняем пароль `root`, по умолчанию его нет:
```bash
passwd root
```

Добавляем пользователя и заходим в него:
```bash
useradd -m jupyter
sed -i 's|jupyter:/bin/sh|jupyter:/bin/bash|' /etc/passwd
su - jupyter
cd ~
```

Устанавливаем `jupyter-lab` через `pip`:
```bash
pip install jupyterlab 
```

- если error `externally-managed-environment`: 
	```bash
	pip install jupyterlab --break-system-packages --user jupyter
	```

Делаем исполняемый файл по запуску `jupyter`:
```bash
echo 'export PATH=/home/jupyter/.local/bin:$PATH' >> ~/.bashrc
```

Чтобы загрузить добавленные переменные оболочки:
> можно перелогиниться, но легче запустить новый `bash`:
```bash
bash
```

Ставим пароль:
```bash
jupyter lab password
```

После чего стоит выйти из контейнера и проверить работу, перезапустив его:
```bash
sudo docker restart jupyter
```
\
Находим `ip` контейнера:
```bash
sudo docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' jupyter
```

Коммитим контейнер, чтобы в случае ЧП при будущих правках, можно было откатить изменения :
```bash
sudo docker commit -m "" jupyter my/jupyter:1.0.0
```
\
Перезапускаем контейнер:
```bash
sudo docker run -it --restart=always -p 88:8888 --name jupyter my/jupyter:1.0.0
```

Чтобы удалить все `pip` пакеты кроме `jupyterlab`, можно использовать команду:
```bash
pip freeze | grep -v jupyter | xargs pip uninstall -y; pip install jupyterlab
```

Для обновления `jupyterlab`, установленного через `pip`, можно выполнить команду:
```bash
pip install --upgrade jupyterlab
```

## Дополнительно

### Подключение локального каталога к контейнеру `Docker`
> Тома `Docker` — это каталоги (или файлы), которые находятся за пределами файловой системы `Docker` по умолчанию и существуют как обычные каталоги и файлы в файловой системе хоста. Том не увеличивает размер используемых контейнеров, и содержимое тома существует вне жизненного цикла данного контейнера.

Мы можем создать том, используя параметр `-v`:
```bash
docker run -p 8888:8888 -v /Users/yourname/yourdirectory:/home/jovyan/work jupyter/minimal-notebook
```

Если вы хотите использовать текущий рабочий каталог, используйте `$ (pwd)`:
```bash
docker run -p 8888:8888 -v $(pwd):/home/jovyan/work jupyter/minimal-notebook
```

Чтобы дать права на директорию:
```bash
sudo chown -R jupyter ~/dev
```

В `.jupyter/jupyter...json` лежит конфиг, чтобы привязать директорию нужно использовать конфигурацию:
```json
{
  "IdentityProvider": {
    "hashed_password": "argon2:$argon2id$v=19$m=10240,t=10,p=*******"
  }
  , "NotebookApp": {
   "notebook_dir": "/home/jupyter/dev"
  }
}
```
- Можно создать конфиг командой:
	```bash
	jupyter server --generate-config
	```

> [Доп инфо по параметрам конфига](https://jupyter-server.readthedocs.io/en/latest/other/full-config.html#other-full-config)
----------------------------------------------------------------------------

## Удаление

```bash
sudo docker kill jupyter
sudo docker rm -f jupyter
```
