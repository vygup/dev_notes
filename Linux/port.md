чтобы отобразить tcp и udp одновременно 
    ss -lntu

проверка прослушиваемых портов 
    ss -tl

проверка, используется ли порт
    ss -na | grep :4000

вывести все соединения между сокетами
    ss

sudo apt install ufw
sudo ufw enable

Открытие порта
sudo ufw allow 4000

Отключить и сбросить настройки UFW
sudo ufw disable
