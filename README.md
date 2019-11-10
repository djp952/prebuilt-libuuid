# LIBUUID 1.0.3 STATIC LIBRARIES   
[https://sourceforge.net/projects/libuuid/](https://sourceforge.net/projects/libuuid/)  

**TARGETS**   
* linux-i686 (gcc-4.9)   
* linux-x86_64 (gcc-4.9)   
* linux-armel (gcc-4.9)   
* linux-armhf (gcc-4.9)   
* linux-aarch64 (gcc-4.9)   
* android-21-armeabi-v7a (ndk-r20b/api-21)   
* android-21-arm64-v8a (ndk-r20b/api-21)   
* android-21-x86 (ndk-r20b/api-21)   
* android-28-armeabi-v7a (ndk-r20b/api-21)   
* android-28-arm64-v8a (ndk-r20b/api-21)   
* android-28-x86 (ndk-r20b/api-21)   
* rasbpian-armhf (gcc-4.8.3)   
* osx-x86_64 (apple-darwin15)   

**BUILD ENVIRONMENT**  
* Windows 10 x64 1809 (17763) "October 2018 Update"   
* Windows Subsystem for Linux   
* [Ubuntu on Windows 16.04 LTS](https://www.microsoft.com/store/productId/9PJN388HP8C9)   
* OSXCROSS Cross-Compiler (with Mac OSX 10.11 SDK)   
   
**CONFIGURE BASH ON UBUNTU ON WINDOWS**   
Open "Ubuntu"   
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install gcc-4.9 g++-4.9 libc6-dev:i386 libstdc++-4.9-dev:i386 lib32gcc-4.9-dev 
sudo apt-get install gcc-4.9-arm-linux-gnueabihf g++-4.9-arm-linux-gnueabihf gcc-4.9-arm-linux-gnueabi g++-4.9-arm-linux-gnueabi gcc-4.9-aarch64-linux-gnu g++-4.9-aarch64-linux-gnu
sudo apt-get install autoconf libtool make p7zip-full python
```
   
**CONFIGURE ANDROID TOOLCHAINS**   
Open "Ubuntu"   
```
wget https://dl.google.com/android/repository/android-ndk-r20b-linux-x86_64.zip
7z x android-ndk-r20b-linux-x86_64.zip
```
  
**CONFIGURE OSXCROSS CROSS-COMPILER**   
* Generate the MAC OSX 10.11 SDK Package for OSXCROSS by following the instructions provided at [PACKAGING THE SDK](https://github.com/tpoechtrager/osxcross#packaging-the-sdk).  The suggested version of Xcode to use when generating the SDK package is Xcode 7.3.1 (May 3, 2016).
* Open "Ubuntu"   
```
sudo apt-get install make clang zlib1g-dev libmpc-dev libmpfr-dev libgmp-dev
git clone https://github.com/tpoechtrager/osxcross --depth=1
cp {MacOSX10.11.sdk.tar.bz2} osxcross/tarballs/
UNATTENDED=1 osxcross/build.sh
GCC_VERSION=4.9.3 osxcross/build_gcc.sh
```
   
**BUILD LIBUUID (linux-i686)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export CC=gcc-4.9
export AR=gcc-ar-4.9
export RANLIB=gcc-ranlib-4.9
cd libuuid-1.0.3
aclocal
automake --add-missing
./configure --with-pic --host=i686-pc-linux-gnu CFLAGS="-m32 -I/usr/include/i386-linux-gnu" --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (linux-x86_64)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export CC=gcc-4.9
export AR=gcc-ar-4.9
export RANLIB=gcc-ranlib-4.9
cd libuuid-1.0.3
aclocal
automake --add-missing
./configure --with-pic CFLAGS="-I/usr/include/x86_64-linux-gnu" --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (linux-armel)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export CROSS_COMPILE=arm-linux-gnueabi-
export CC=arm-linux-gnueabi-gcc-4.9
export AR=arm-linux-gnueabi-gcc-ar-4.9
export RANLIB=arm-linux-gnueabi-gcc-ranlib-4.9
cd libuuid-1.0.3
./configure --with-pic --host=arm-linux-gnueabi --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (linux-armhf)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export CROSS_COMPILE=arm-linux-gnueabihf-
export CC=arm-linux-gnueabihf-gcc-4.9
export AR=arm-linux-gnueabihf-gcc-ar-4.9
export RANLIB=arm-linux-gnueabihf-gcc-ranlib-4.9
cd libuuid-1.0.3
./configure --with-pic --host=arm-linux-gnueabihf --disable-shared --enable-static
autoreconf -i -f
make
``` 
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (linux-aarch64)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export CROSS_COMPILE=aarch64-linux-gnu-
export CC=aarch64-linux-gnu-gcc-4.9
export AR=aarch64-linux-gnu-gcc-ar-4.9
export RANLIB=aarch64-linux-gnu-gcc-ranlib-4.9
cd libuuid-1.0.3
./configure --with-pic --host=aarch64-linux-gnu --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-21-armeabi-v7a)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/arm-linux-androideabi-ar
export AS=$TOOLCHAIN/bin/arm-linux-androideabi-as
export CC=$TOOLCHAIN/bin/armv7a-linux-androideabi21-clang
export CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi21-clang++
export LD=$TOOLCHAIN/bin/arm-linux-androideabi-ld
export RANLIB=$TOOLCHAIN/bin/arm-linux-androideabi-ranlib
export STRIP=$TOOLCHAIN/bin/arm-linux-androideabi-strip
cd libuuid-1.0.3
./configure --with-pic --host=arm-linux-androideabi --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-21-arm64-v8a)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/aarch64-linux-android-ar
export AS=$TOOLCHAIN/bin/aarch64-linux-android-as
export CC=$TOOLCHAIN/bin/aarch64-linux-android21-clang
export CXX=$TOOLCHAIN/bin/aarch64-linux-android21-clang++
export LD=$TOOLCHAIN/bin/aarch64-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/aarch64-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/aarch64-linux-android-strip
cd libuuid-1.0.3
./configure --with-pic --host=aarch64-linux-android --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-21-x86)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/i686-linux-android-ar
export AS=$TOOLCHAIN/bin/i686-linux-android-as
export CC=$TOOLCHAIN/bin/i686-linux-android21-clang
export CXX=$TOOLCHAIN/bin/i686-linux-android21-clang++
export LD=$TOOLCHAIN/bin/i686-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/i686-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/i686-linux-android-strip
cd libuuid-1.0.3
./configure --with-pic --host=i686-linux-android --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-28-armeabi-v7a)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/arm-linux-androideabi-ar
export AS=$TOOLCHAIN/bin/arm-linux-androideabi-as
export CC=$TOOLCHAIN/bin/armv7a-linux-androideabi28-clang
export CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi28-clang++
export LD=$TOOLCHAIN/bin/arm-linux-androideabi-ld
export RANLIB=$TOOLCHAIN/bin/arm-linux-androideabi-ranlib
export STRIP=$TOOLCHAIN/bin/arm-linux-androideabi-strip
cd libuuid-1.0.3
./configure --with-pic --host=arm-linux-androideabi --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-28-arm64-v8a)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/aarch64-linux-android-ar
export AS=$TOOLCHAIN/bin/aarch64-linux-android-as
export CC=$TOOLCHAIN/bin/aarch64-linux-android28-clang
export CXX=$TOOLCHAIN/bin/aarch64-linux-android28-clang++
export LD=$TOOLCHAIN/bin/aarch64-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/aarch64-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/aarch64-linux-android-strip
cd libuuid-1.0.3
./configure --with-pic --host=aarch64-linux-android --disable-shared --enable-static
autoreconf -i -f
make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-28-x86)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/i686-linux-android-ar
export AS=$TOOLCHAIN/bin/i686-linux-android-as
export CC=$TOOLCHAIN/bin/i686-linux-android28-clang
export CXX=$TOOLCHAIN/bin/i686-linux-android28-clang++
export LD=$TOOLCHAIN/bin/i686-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/i686-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/i686-linux-android-strip
cd libuuid-1.0.3
./configure --with-pic --host=i686-linux-android --disable-shared --enable-static
autoreconf -i -f
make
``` 
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (raspbian-armhf)**   
Open "Ubuntu"   
```
git clone https://github.com/raspberrypi/tools.git raspberrypi --depth=1
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export PATH=$(pwd)/raspberrypi/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin:$PATH
export CROSS_COMPILE=arm-linux-gnueabihf-
export CC=arm-linux-gnueabihf-gcc
export AR=arm-linux-gnueabihf-gcc-ar
export RANLIB=arm-linux-gnueabihf-gcc-ranlib
cd libuuid-1.0.3
./configure --with-pic --host=arm-linux-gnueabihf --disable-shared --enable-static
autoreconf -i -f
make
``` 
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (osx-x86_64)**   
Open "Ubuntu"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export PATH=$(pwd)/osxcross/target/bin:$PATH
export CROSS_COMPILE=x86_64-apple-darwin15-
export CFLAGS="-mmacosx-version-min=10.7 -stdlib=libc++"
cd libuuid-1.0.3
./configure --with-pic --host=x86_64-apple-darwin15 --disable-shared --enable-static
autoreconf -i -f
OSXCROSS_NO_EXTENSION_WARNINGS=1 make
```
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
## ADDITIONAL LICENSE INFORMATION
   
**XCODE AND APPLE SDKS AGREEMENT**   
The instructions provided above indirectly reference the use of intellectual material that is the property of Apple, Inc.  This intellectual material is not FOSS (Free and Open Source Software) and by using it you agree to be bound by the terms and conditions set forth by Apple, Inc. in the [Xcode and Apple SDKs Agreement](https://www.apple.com/legal/sla/docs/xcode.pdf).
