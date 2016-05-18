# Install TeX Live

1. Install

    ```
    wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
    tar -xf install-tl-unx.tar.gz
    cd install-tl-20160405
    sudo ./install-tl
    ```

2. Add some paths

    - Add `/usr/local/texlive/2015/texmf-dist/doc/info` to INFOPATH
    - Add `/usr/local/texlive/2015/texmf-dist/doc/man` to MANPATH
    - Add `/usr/local/texlive/2015/bin/x86_64-linux` to PATH