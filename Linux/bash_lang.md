locale 

sudo dpkg-reconfigure locales


ИЛИ


nano ~/.bashrc

export LANG=en_US.UTF-8
or
export LANG=ru_RU.UTF-8

source ~/.bashrc


Для отдельного

alias git = 'LANG=en_US.UTF-8 git'

alias nvim = 'LANG=en_US.UTF-8 nvim'

В конце главное выйти и зайти в профиль