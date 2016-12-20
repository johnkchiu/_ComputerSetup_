# Setup for Mac

## brew - http://brew.sh/
```shell
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## zsh
```shell
# zsh zsh-completions
brew install zsh zsh-completions
# oh-my-zsh - http://ohmyz.sh/
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## node.js / npm / nvm
```shell
# install nvm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
# install latest node.js
nvm install node
```

## yarn
```shell
brew install yarn
```

## p4merge
```shell
# install p4merge
brew install Caskroom/cask/p4merge
# setup shell script
echo $'#!/bin/sh\n/Applications/p4merge.app/Contents/Resources/launchp4merge $*' > /usr/local/bin/p4merge
chmod +x '/usr/local/bin/p4merge'
# setup git config
git config --global merge.tool p4merge
git config --global mergetool.keepTemporaries false
git config --global mergetool.prompt false
```

## Application Setup
```shell
# atom commandline
ln -s /Applications/Atom.app/Contents/Resources/app/atom.sh /usr/local/bin/atom

# sublime commandline
ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```

## Environment Setup
```shell
# show hidden files
defaults write com.apple.finder AppleShowAllFiles YES
killall Finder

# Markdown Preview
brew cask install qlmarkdown
```
