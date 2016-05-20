# Switching to a new Ubuntu machine

## System infomation
Ubuntu 16.04 (English).

## Update packages
``` bash
sudo apt-get update
sudo apt-get upgrade
```

##  Git
``` bash
sudo apt-get install git
git config --global user.name "Kai Chen"
git config --global user.email "chenkaidev@gmail.com"
```

Then generate private/public key pair and upload the public key to github, see [Configure SSH access to Github](https://github.com/hellock/easyguide/blob/master/github.md) for details.

## Zsh
``` bash
sudo apt-get zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Python 3
``` bash
sudo apt-get install python3-dev python-dev
wget https://bootstrap.pypa.io/get-pip.py
sudo python3 get-pip.py
sudo pip3 install numpy flake8
```

## Sublime Text 3
1. Download the latest sublime
2. `dpkg -i sublime.deb`
3. Install [package control](https://packagecontrol.io/installation)
4. Install `Sync Settings`
5. Download previous settings
6. Install `cppcheck`, `chktex`, `flake8`, `nodejs` if necessary.

## Others
``` bash
sudo apt-get install cmake htop tmux
```

## SSH access (if necessary)
1. Install OpenSSH server

    ``` bash
    sudo apt-get install openssh-server
    ```

2. If you want to allow password authentication, modify the file `/etc/ssh/sshd_config`, change `PasswordAuthentication no` to `PasswordAuthentication yes`.
3. Start SSH server

    ``` bash
    sudo service ssh start
    ```

## Chinese input method (if necessary)
1. Download Chinese language support
2. Set keyboard input method system to fcitx
3. Add text entry.

## Optional softwares
- [Chrome](https://www.google.com/chrome/browser/desktop/index.html)
- [Filezilla](https://filezilla-project.org/download.php?type=client)
- [WPS](http://wps-community.org/downloads)