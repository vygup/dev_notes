чтобы отобразить tcp и udp одновременно 
```bash
ss -lntu
```

проверка прослушиваемых портов 
```bash
ss -tl
```

проверка, используется ли порт
```bash
ss -na | grep :4000
```

вывести все соединения между сокетами
```bash
ss
```

Установка `ufw`
```bash
sudo apt install ufw
sudo ufw enable
```

Открытие порта
```bash
sudo ufw allow 4000
```

Отключить и сбросить настройки UFW
```bash
sudo ufw disable
```