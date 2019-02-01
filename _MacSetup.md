# Setup for Mac

## brew
```bash
# install brew - http://brew.sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## zsh / oh-my-zsh / antigen
```bash
# zsh zsh-completions
brew install zsh zsh-completions
# oh-my-zsh - http://ohmyz.sh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
# antigen (into home directory) - http://antigen.sharats.me
curl -L git.io/antigen > ~/antigen.zsh
# now setup your dotfiles
```

## node.js / npm / nvm
```bash
# install nvm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
# install latest node.js
nvm install node
```

## yarn
```bash
brew install yarn
```

## react-native
```bash
# install node (see above)
# install watchman
brew install watchman
# install reative-native-cli
npm install -g react-native-cli
```

## rbenv / ruby / rails
```bash
# install rbenv
brew install rbenv
rbenv init
# ruby should be installed
# install rails
gem install rails
rbenv rehash
```

## Go lang
```bash
# install go
brew install go
# go setup $GOPATH
# export GOPATH=$HOME/go
# export PATH=$PATH:$GOPATH/bin
```

## java / scala / sbt / gradle
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

## mysql
```bash
brew install mysql
# mysql.server start
# mysql.server stop
```

## aws-cli
```bash
brew install awscli
aws configure
```

## Application Setup
```bash
# p4merge commandline
alias p4merge='/Applications/p4merge.app/Contents/MacOS/p4merge'

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
