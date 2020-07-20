# Setup for Raspberry Pi

## fish shell
```shell
sudo api-get install fish
chsh -s $(which fish)

```

## zsh / oh-my-zsh
```shell
sudo apt-get update # optional
sudo apt-get install zsh
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
