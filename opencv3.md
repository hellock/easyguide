# Install OpenCV 3 with Python 3.x

## System
* OS X EI Capitan 10.11.4
* Ubuntu 16.04

## For OS X
``` bash
brew install opencv3 --with-python3
```

## For Ubuntu

``` bash
sudo pip3 install numpy

sudo apt-get install ffmpeg libjpeg-dev libtiff-dev libjasper-dev libpng-dev libavcodec-dev libavformat-dev libswscale-dev libavutil-dev libgtk-3-dev

git clone https://github.com/Itseez/opencv.git
cd opencv
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local/ \
-D INSTALL_PYTHON_EXAMPLES=ON \
-D WITH_OPENGL=ON \
-D WITH_TBB=ON \
-D WITH_IPP=ON \
..
make -j
sudo make install
sudo ldconfig
```
If the python3 lib path cannot be found:
``` bash
-D PYTHON3_INCLUDE_DIR=$(python3 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
-D PYTHON3_PACKAGES_PATH=$(python3 -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())") \
```