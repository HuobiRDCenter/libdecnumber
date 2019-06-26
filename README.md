# libdecnumber
huobi cpp sdk 依赖 

OS: centos 7 

安装clang 最低3.4.2 最高5.0.1 此处使用5.0.1

````
$ sudo yum install centos-release-scl-rh centos-release-scl scl-utils-build scl-utils
$ sudo yum check-update
$ sudo yum install devtoolset-7-llvm
$ echo "source /opt/rh/llvm-toolset-7/enable" >> $HOME/.bashrc
$ source $HOME/.bashrc
````

编译
````
$ git clone https://github.com/huobiapi/libdecnumber.git
$ cd libdecnumber 
$ mkdir build
$ cd build
$ cmake .. -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Release -DCMAKE_TOOLCHAIN_FILE=../linux.toolchain.cmake
$ make
$ sudo make install
````

