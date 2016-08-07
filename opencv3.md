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

sudo apt-get install ffmpeg libjpeg-dev libtiff-dev libjasper-dev libpng-dev libavcodec-dev libavformat-dev libv4l-dev libswscale-dev libavutil-dev libgtk-3-dev libtbb-dev

git clone https://github.com/Itseez/opencv.git
cd opencv
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local/ \
-D INSTALL_PYTHON_EXAMPLES=ON \
-D WITH_OPENGL=ON \
-D WITH_V4L=ON \
-D WITH_TBB=ON \
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

## Issues when compiling with CUDA 8.0
When compiling with CUDA 8.0, you may encounter some issues. Here are the solutions.

### GCC version is not supported

The default gcc version of Ubuntu 16.04.1 is 5.4.0, and an error will be thrown out like this
>error -- unsupported GNU version! gcc versions later than 5.3 are not supported!

The solution is to comment the corresponding line in the file `/usr/local/cuda/include/host_config.h`.

```
#if __GNUC__ > 5 || (__GNUC__ == 5 && __GNUC_MINOR__ > 3)
// #error -- unsupported GNU version! gcc versions later than 5.3 are not supported!
#endif /* __GNUC__ > 5 || (__GNUC__ == 5 && __GNUC_MINOR__ > 1) */
```

### Thrust error

If you see this error
>no default constructor exists for class "thrust::detail::execute_with_allocator

follow these steps:

1. clone the repository

``` shell
git clone https://github.com/thrust/thrust.git
git checkout cuda-next-release
```

2. replace the thrust folder in cuda directory

``` shell
cd /usr/local/cuda/include
sudo mv thrust thrust_bak
sudo ln -s /path_to_thrust_git_repo/thrust thrust
```

