Пример батника, который запускает виртульную машину
```bat
@echo off

rem >NUL - чтобы вывода сообщения не было о смене кодировки
rem chcp 65001>NUL

rem echo Запускаем VM

rem chcp 1251 >NUL

rem перерыв секунда и не помешает нажатие
rem timeout /T 1 /NOBREAK

rem говорим где VB находится 
SET PATH=%PATH%;;C:\Oracle\VirtualBox

rem запускаем машину 
rem VBoxManage startvm KaliX
VBoxManage startvm name_vm --type=headless >NUL

```

