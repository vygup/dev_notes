vi /etc/systemd/system/jupyter.service  

[Unit]
Description=JupyterLab service

[Service]
Type=simple
#PIDFile=/run/jupyterlab.pid
WorkingDirectory=/home/vladx/dev
#ExecStart=/home/vladx/.local/bin/pipenv run jupyter lab
ExecStart=/home/vladx/environments/server_env/bin/jupyter lab
User=vladx
Group=vladx
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target


systemctl daemon-reload

systemctl enable jupyter

systemctl start jupyter

systemctl status jupyter 