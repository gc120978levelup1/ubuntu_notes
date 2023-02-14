sudo curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh
sudo curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
source ~/.bashrc
nvm list-remote
nvm install v18.12.1
nvm use v18.12.1
node -v
