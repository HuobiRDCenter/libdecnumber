# libdecnumber
huobi cpp sdk 依赖 

OS: centos 7 

安装clang

````
$ sudo yum install epel-release
$ sudo yum install clang
````

````
$ git clone https://github.com/huobiapi/libdecnumber.git
$ cd libdecnumber 
$ mkdir build
$ cd build
$ cmake .. -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Release -DCMAKE_TOOLCHAIN_FILE=../linux.toolchain.cmake
$ make
$ sudo make install
````

