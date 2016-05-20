# Install Neovim
Neovim is a vim-fork focused on extensibility and agility. According to its [official website](https://neovim.io/), it is literally the future of vim.

## For OS X
``` bash
brew install neovim/neovim/neovim
```

## For Ubuntu
``` bash
sudo add-apt-repository ppa:neovim-ppa/unstable
sudo apt-get update
sudo apt-get install neovim
```

## Configuration

### Config files
The configuration file is `~/.config/nvim/init.vim`, bundle path is `~/.config/nvim/bundle`. The `init.vim` for neovim is the same as `.vimrc` for vim.

### Python 2/3 support
``` bash
pip install neovim
```
or
``` bash
pip3 install neovim
```