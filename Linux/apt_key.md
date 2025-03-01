добавление по новому  
curl -s https://download.docker.com/linux/debian/gpg | sudo gpg --no-default-keyring --keyring gnupg-ring:/etc/apt/trusted.gpg.d/docker.gpg --import
sudo chmod 644 /etc/apt/trusted.gpg.d/docker.gpg

Добавление по старому
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

список по новому 
apt-key list

список по старому
gpg --list-keys --keyring /etc/apt/trusted.gpg.d/docker.gpg

Удаление ключей, созданных новым способом 
cd /etc/apt/trusted.gpg.d/
sudo rm docker.gpg

удаление всех ключей, добавленных apt-key add
sudo rm /etc/apt/trusted.gpg