# Install Caffe

## System
Ubuntu 16.04

## Prerequisites
The following are supposed to have been installed, otherwise please refer to the previous guidance.

- [CUDA 7.5 and cuDNN 5](https://github.com/hellock/easyguide/blob/master/cuda.md)
- [OpenCV 3.1](https://github.com/hellock/easyguide/blob/master/opencv3.md)

## Install dependency
```shell
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential cmake git pkg-config python3-dev
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libhdf5-serial-dev protobuf-compiler
sudo apt-get install libatlas-base-dev
sudo apt-get install --no-install-recommends libboost-all-dev
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
sudo pip3 install numpy scipy
```

## Install Caffe

```shell
git clone git@github.com:BVLC/caffe.git
cd caffe
cp Makefile.config.example Makefile.config
```

Modify (and uncomment) the following lines in config file
```
USE_CUDNN := 1

OPENCV_VERSION := 3

WITH_PYTHON_LAYER := 1

PYTHON_LIBRARIES := boost_python3 python3.5m
PYTHON_INCLUDE := /usr/include/python3.5m \
/usr/local/lib/python3.5/dist-packages/numpy/core/include

INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial
LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial/
```

Also modify the `Makefile`, replace the line
```
NVCCFLAGS += -ccbin=$(CXX) -Xcompiler -fPIC $(COMMON_FLAGS)
```
with
```
NVCCFLAGS += -D_FORCE_INLINES -ccbin=$(CXX) -Xcompiler -fPIC $(COMMON_FLAGS)
```

Execute
```shell
find . -type f -exec sed -i -e 's^"hdf5.h"^"hdf5/serial/hdf5.h"^g' -e 's^"hdf5_hl.h"^"hdf5/serial/hdf5_hl.h"^g' '{}' \;

cd /usr/lib/x86_64-linux-gnu
sudo ln -s libhdf5_serial.so libhdf5.so
sudo ln -s libhdf5_serial_hl.so libhdf5_hl.so
sudo ln -s libboost_python-py35.so libboost_python3.so
```

return to the directory of caffe source codes
```shell
cd python
sudo -H pip3 install -r requirements.txt
cd ..
```

then build and test (add -jxx according to the number of CPU cores)
```shell
make all
make test
make runtest
```

To have caffe work with python 3, some additional work need to be done.
```shell
sudo apt-get install libffi-dev
sudo -H pip3 install cairocffi
sudo -H pip3 install protobuf --pre
make pycaffe
```

To build the Matlab interface
```
make matcaffe
```

Add the following line to your shell config file.
```shell
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libstdc++.so.6
```


