sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

тема
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

open ~/.zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"

git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting

open ~/.zshrc
plugins=(
git
zsh-syntax-highlighting
zsh-autosuggestions
)

p10k configure

del
sh ~/.oh-my-zsh/tools/uninstall.sh
