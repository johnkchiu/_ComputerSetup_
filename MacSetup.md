# Setup for Mac

## Development Tools

### aws-cli
```bash
brew install awscli
aws configure
```

### brew
```bash
# install brew - http://brew.sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### docker
```bash
# install docker
brew cask install docker
# setup completion
etc=/Applications/Docker.app/Contents/Resources/etc
ln -s $etc/docker.zsh-completion /usr/local/share/zsh/site-functions/_docker
ln -s $etc/docker-machine.zsh-completion /usr/local/share/zsh/site-functions/_docker-machine
ln -s $etc/docker-compose.zsh-completion /usr/local/share/zsh/site-functions/_docker-compose
```

### Go lang
```bash
# install go
brew install go
# go setup $GOPATH
# export GOPATH=$HOME/go
# export PATH=$PATH:$GOPATH/bin
```

### java / scala / sbt / gradle
```bash
# install sdkman + modify .bashrc/.zshrc
curl -s "https://get.sdkman.io" | bash
# isntall java
sdk install java
# install gradle
sdk install gradle
# install scala
sdk install scala
# isntall sbt
sdk install sbt
```

### mysql
```bash
brew install mysql
# mysql.server start
# mysql.server stop
```

### node.js / npm / nvm
```bash
# install nvm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
# install latest node.js
nvm install node
```

### python
```bash
# install python 3
brew install python
# install python 2
brew install python@2
```

### react-native
```bash
# install node (see above)
# install watchman
brew install watchman
# install reative-native-cli
npm install -g react-native-cli
```

### ruby / rbenv / rails
```bash
# install rbenv
brew install rbenv
rbenv init
# ruby should be installed
# install rails
gem install rails
rbenv rehash
```

### terraform
```bash
# install tfenv
brew install tfenv
# install terraform
tfenv install latest
```

### yarn
```bash
brew install yarn
```

### zsh / oh-my-zsh / antigen
```bash
# zsh zsh-completions
brew install zsh zsh-completions
# oh-my-zsh - http://ohmyz.sh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
# antigen (into home directory) - http://antigen.sharats.me
curl -L git.io/antigen > ~/antigen.zsh
# now setup your dotfiles
```

## Application Setup
```bash
# atom commandline
ln -s /Applications/Atom.app/Contents/Resources/app/atom.sh /usr/local/bin/atom

# sublime commandline
ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```

## Environment Setup
```bash
# show hidden files
defaults write com.apple.finder AppleShowAllFiles YES
killall Finder

# Markdown Preview
brew cask install qlmarkdown
```
