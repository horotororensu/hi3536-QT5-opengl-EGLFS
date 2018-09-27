## 1、编译依赖
### 1.1 bison
``` shell
./configure  --build=i686-build_pc-linux-gnu --host=i686-build_pc-linux-gnu --target=arm-hisiv400-linux --prefix=/usr/local/bison
make
make install
```
### 1.2 flex
``` shell
./configure  --build=i686-build_pc-linux-gnu --host=i686-build_pc-linux-gnu --target=arm-hisiv400-linux --prefix=/usr/local/flex
make
make install
```
### 1.3 gperf
``` shell
./configure  --build=i686-build_pc-linux-gnu --host=i686-build_pc-linux-gnu --target=arm-hisiv400-linux --prefix=/usr/local/gperf 
make
make install
```
### 1.4 Ruby
``` shell
./configure  --build=i686-build_pc-linux-gnu --host=i686-build_pc-linux-gnu --target=arm-hisiv400-linux --prefix=/usr/local/ruby  --with-static-linked-ext --disable-shared --disable-install-doc
make
make install
```

## 2、ICU
&emsp;&emsp;静态编译icu。<br>
``` shell
./configure  --enable-static --enable-shared=no 
```
<br>
&emsp;&emsp;编译ICU时需要再建两个目录： buildA、 buildB，在buildA中configue 、make ，在buildB中交叉编译。<br>

``` shell
mkdir buildA buildB 
cd  buildA
../icu/source/configure
make
```


``` shell
cd ../buildB
 ../icu/source/configure --host=arm-hisiv400-linux  --with-cross-build=/home/book/workplace/buildA  --prefix=/usr/local/icu/  --enable-static --enable-shared=no
```

&emsp;&emsp;设置环境变量<br>
``` shell
export PATH=/usr/local/bison/bin:$PATH ; export PATH=/usr/local/flex/bin:$PATH ; export PATH=/usr/local/gperf/bin:$PATH ; export PATH=/usr/local/ruby/bin:$PATH;export LD_LIBRARY_PATH=/usr/local/icu/lib ;
```
