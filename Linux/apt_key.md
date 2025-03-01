Добавление по новому
```bash
curl -s https://download.docker.com/linux/debian/gpg | sudo gpg --no-default-keyring --keyring gnupg-ring:/etc/apt/trusted.gpg.d/docker.gpg --import
```
```bash
sudo chmod 644 /etc/apt/trusted.gpg.d/docker.gpg
```

Добавление по старому
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```

---
Список по новому 
```bash
apt-key list
```

Список по старому
```bash
gpg --list-keys --keyring /etc/apt/trusted.gpg.d/docker.gpg
```

---
Удаление ключей, созданных новым способом 
```bash
cd /etc/apt/trusted.gpg.d/
```
```bash
sudo rm docker.gpg
```

Удаление всех ключей, добавленных apt-key add
```bash
sudo rm /etc/apt/trusted.gpg
```