/lib/systemd/system/tg_bot_aspire.service

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



systemctl status tg_bot_aspire.service

systemctl daemon-reload

sudo systemctl restart tg_bot_aspire.service
systemctl status tg_bot_aspire.service
