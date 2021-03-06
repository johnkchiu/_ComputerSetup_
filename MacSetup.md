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
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

### docker
```bash
# install docker
brew cask install docker
# setup completion (for zsh)
etc=/Applications/Docker.app/Contents/Resources/etc
ln -s $etc/docker.zsh-completion /usr/local/share/zsh/site-functions/_docker
ln -s $etc/docker-machine.zsh-completion /usr/local/share/zsh/site-functions/_docker-machine
ln -s $etc/docker-compose.zsh-completion /usr/local/share/zsh/site-functions/_docker-compose
```

### fish + fzf
```bash
brew install fish
sudo vi /etc/shells
# add `/usr/local/bin/fish` for Intel (or `/opt/homebrew/bin/fish` for ARM)
chsh -s /usr/local/bin/fish
# install fisher + fzf
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
brew install fzf
fisher install jethrokuan/fzf
```

### Go lang
```bash
# install go
brew install go
# go setup $GOPATH
# export GOPATH=$HOME/Workspace/go
# export PATH=$PATH:$GOPATH/bin
```

### iterm2
```bash
#install
brew cask install iterm2
# use preferences directory
defaults write com.googlecode.iterm2.plist PrefsCustomFolder -string ~/iterm2
defaults write com.googlecode.iterm2.plist LoadPrefsFromCustomFolder -bool true
# after launch turn on Preferences -> General -> Preferences -> Save changes to folder when iTerm2 quits.
```

### java / scala / sbt / gradle / groovy
```bash
# install sdkman + modify .bashrc/.zshrc
curl -s "https://get.sdkman.io" | bash
# (for fish)
fisher add reitzig/sdkman-for-fish
# install java
sdk install java
# install gradle
sdk install gradle
# install scala
sdk install scala
# install sbt
sdk install sbt
# install groovy
sdk install groovy
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
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
# (for fish)
fisher add FabioAntunes/fish-nvm
fisher add edc/bass
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
tfenv use
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
