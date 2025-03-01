Установка пользовательского MAC адреса

Может потребоваться перезагрузка перед действиями ниже

---
Обычно может без этой команды не работать
```bash
sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -z
```

Установка MAC адреса
```bash
sudo ifconfig en0 ether XX:XX:XX:XX:XX:XX
```