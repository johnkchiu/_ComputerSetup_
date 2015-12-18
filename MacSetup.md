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

## Application Setup
```shell
# atom commandline
ln -s /Applications/Atom.app/Contents/Resources/app/atom.sh /usr/local/bin/atom
```

## Environment Setup
```shell
# show hiddent files
defaults write com.apple.finder AppleShowAllFiles YES
killall Finder


```
