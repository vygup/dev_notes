# Установка сервиса для бесперебойной работы telegram бота в linux

```bash
vim /lib/systemd/system/tg_bot_aspire.service
```

```text
[Unit]
Description=tg aspire
After=network.target

[Service]
EnvironmentFile=/etc/environment
ExecStart=/home/serverx/py_dev/tg_bot/bin/python3 /home/serverx/py_dev/code/vyg_server/tg_bot_aspire/tg_bot.py
ExecReload=/home/serverx/py_dev/tg_bot/bin/python3 /home/serverx/py_dev/code/vyg_server/tg_bot_aspire/tg_bot.py
WorkingDirectory=/home/serverx/py_dev/code/vyg_server/tg_bot_aspire/
KillMode=process
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```


```bash
systemctl status tg_bot_aspire.service
```

```bash
systemctl daemon-reload
```

```bash
sudo systemctl restart tg_bot_aspire.service
systemctl status tg_bot_aspire.service
```