Mac S etup for web development(2022)

https://www.robinwieruch.de/mac-setup-web-development/

Install Homebrew as package manager for macOS:

# paste in terminal and follow the instructions

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew update

brew install --cask bitwrden google-chrome  iterm2 visual-studio-code \ 
    sublime-txt	docker  discord rectangle signal vlc maccy 

brew install wget git exa nvm graohicsmagic cmatrix

install OH MY ZSH

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

omz update

source ~/.zshrc

brew install starship

echo 'eval "$(starship init zsh)"' >> ~/.zshrc

brew tap homebrew/cask-fonts

brew install --cask font-hack-nerd-font

in ~/.zshrc

plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)

# use nvm
source /opt/homebrew/opt/nvm/nvm.sh

# use starship theme (needs to be at the end)
eval "$(starship init zsh)"

source ~/.zshrc

git :

git config --global user.name "Your Name"

git config --global user.email "you@your-domain.com"

git config --global alias.log "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

git log


git config --list

SSH:

# in case the folder is not there yet
mkdir ~/.ssh

cd ~/.ssh

ssh-keygen -t ed25519 -C "github"

ssh-keygen -y -f gitHub
# confirm with passphrase


# in case the file is not there yet
touch ~/.ssh/config

Host github
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/github
  

  ssh-add --apple-use-keychain ~/.ssh/github

# copy public key and add it to https://github.com/
cat ~/.ssh/id_rsa.pub | pbcopy

# or use GitHub's CLI
gh auth login
# for the first login I think the SSH key gets added
# without the next command, but if not:

gh ssh-key add ~/.ssh/id_rsa.pub -t github

NVM FOR NODE/NPM:

echo "source $(brew --prefix nvm)/nvm.sh" >> ~/.zshrc

source ~/.zshrc
# or alias
# zshsource

nvm install <latest LTS version from https://nodejs.org/en/>

node -V && npm -v


npm install -g npm@latest


And set defaults for npm:

npm set init.author.name "your name"
npm set init.author.email "you@example.com"
npm set init.author.url "example.com"

If you are a library author, log in to npm too:

npm adduser
That's it. If you want to list all your Node.js installation, type the following:

nvm list
If you want to install a newer Node.js version, then type:

nvm install <version> --reinstall-packages-from=$(nvm current)
nvm use <version>
nvm alias default <version>
Optionally install yarn if you use it as alternative to npm:

npm install -g yarn
yarn -v
If you want to list all globally installed packages, run this command:

npm list -g --depth=0
That's it. You have a running version of Node.js and its package manager.



