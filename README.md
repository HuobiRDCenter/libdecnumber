# libdecnumber
huobi cpp sdk 依赖 

OS: centos 7 
可以使用gcc也可以使用clang

安装clang 最低3.4.2 最高5.0.1 此处使用5.0.1

````
$ sudo yum install centos-release-scl-rh centos-release-scl scl-utils-build scl-utils
$ sudo yum check-update
$ sudo yum install devtoolset-7-llvm
$ echo "source /opt/rh/llvm-toolset-7/enable" >> $HOME/.bashrc
$ source $HOME/.bashrc
````

安装gcc 最低4.9.2 最高7.3.1 此处使用7.3.1

````
$ sudo yum install centos-release-scl-rh centos-release-scl scl-utils-build scl-utils
$ sudo yum check-update
$ sudo yum install devtoolset-7-toolchain
$ echo "source /opt/rh/devtoolset-7/enable" >> $HOME/.bashrc
$ source $HOME/.bashrc
````

编译
````
$ git clone https://github.com/huobiapi/libdecnumber.git
$ cd libdecnumber 
$ mkdir build
$ cd build
#使用clang
$ cmake .. -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Release -DCMAKE_TOOLCHAIN_FILE=../linux.toolchain.cmake
#使用gcc
$ cmake .. -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Release 
$ make
$ sudo make install
````

