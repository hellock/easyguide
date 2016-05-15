# Install Qt5 and PyQt5 with Python3

## System
- OS X EI Capitan 10.11.4
- Ubuntu 16.04

## For OS X
1. Install Qt5 using Homebrew or official package.
2. `pip3 install PyQt5`

## For Ubuntu
1. Download the latest version of Qt5 from [https://www.qt.io/download/](https://www.qt.io/download/)
2. Run `qt-opensource-linux-x64-5.6.0.run` the Install Qt5.
3. Install PyQt5 using either of the following methods.
    - `sudo apt-get install python3-pyqt5`
    - `sudo pip3 install PyQt5`
    - compile from source, see the following

``` bash
wget http://sourceforge.net/projects/pyqt/files/sip/sip-4.18/sip-4.18.tar.gz
tar -xf sip-4.18.tar.gz
cd sip-4.18
python3 configure.py
make -j
sudo make install

wget http://sourceforge.net/projects/pyqt/files/PyQt5/PyQt-5.6/PyQt5_gpl-5.6.tar.gz
tar -xf PyQt5_gpl-5.6.tar.gz
cd PyQt5_gpl-5.6
python3 configure.py --qmake QMAKE_PATH
make -j
sudo make install
```
