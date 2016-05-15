# Install dlib with Python 3

## System
- OS X EI Capitan 10.11.4
- Ubuntu 16.04

## For OS X

``` bash
brew install boost-python --with-python3 --without-python
pip3 install git+git://github.com/davisking/dlib.git
```

## For Ubuntu
``` bash
wget https://sourceforge.net/projects/boost/files/boost/1.60.0/boost_1_60_0.tar.bz2/download
tar -xf boost_1_60_0.tar.bz2
cd boost_1_60_0
./bootstrap.sh --with-python=python3
./b2
sudo ./b2 install

sudo pip3 install dlib
```