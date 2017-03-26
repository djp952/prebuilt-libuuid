# LIBUUID 1.0.3 STATIC LIBRARIES   
[https://sourceforge.net/projects/libuuid/](https://sourceforge.net/projects/libuuid/)  

**TARGETS**   
* linux-i686 (gcc-4.9)   
* linux-x86_64 (gcc-4.9)   
* linux-armhf (gcc-4.9)   
* android-armeabi-v7a (ndk-r12b/api-21)   
* android-arm64-v8a (ndk-r12b/api-21)   
   
**BUILD ENVIRONMENT**  
* Windows 10 x64 15063   
* Bash on Ubuntu on Windows 16.04.1 LTS   

**CONFIGURE BASH ON UBUNTU ON WINDOWS**   
Open "Bash on Ubuntu on Windows"   
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install gcc-4.9 g++-4.9 libc6-dev:i386 libstdc++-4.9-dev:i386 lib32gcc-4.9-dev gcc-4.9-arm-linux-gnueabihf g++-4.9-arm-linux-gnueabihf
sudo apt-get install autoconf libtool make p7zip-full python
```

**CONFIGURE ANDROID TOOLCHAINS**   
Open "Bash on Ubuntu on Windows"   
```
wget https://dl.google.com/android/repository/android-ndk-r12b-linux-x86_64.zip
7z x android-ndk-r12b-linux-x86_64.zip
android-ndk-r12b/build/tools/make_standalone_toolchain.py --arch arm --api 21 --stl gnustl --install-dir ./arm-linux-androideabi
android-ndk-r12b/build/tools/make_standalone_toolchain.py --arch arm64 --api 21 --stl gnustl --install-dir ./aarch64-linux-android
android-ndk-r12b/build/tools/make_standalone_toolchain.py --arch x86 --api 21 --stl gnustl --install-dir ./i686-linux-android
```
  
**BUILD LIBUUID (linux-i686)**   
Open "Bash on Ubuntu on Windows"   
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
Open "Bash on Ubuntu on Windows"   
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
   
**BUILD LIBUUID (linux-armhf)**   
Open "Bash on Ubuntu on Windows"   
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
   
**BUILD LIBUUID (android-armeabi-v7a)**   
Open "Bash on Ubuntu on Windows"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export ANDROID_NDK_ROOT=$(pwd)/android-ndk-r12b
export PATH=$(pwd)/arm-linux-androideabi/bin:$PATH
export CROSS_COMPILE=arm-linux-androideabi-
cd libuuid-1.0.3
./configure --with-pic --host=arm-linux-androideabi --disable-shared --enable-static
autoreconf -i -f
make
```
   
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-arm64-v8a)**   
Open "Bash on Ubuntu on Windows"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export ANDROID_NDK_ROOT=$(pwd)/android-ndk-r12b
export PATH=$(pwd)/aarch64-linux-android/bin:$PATH
export CROSS_COMPILE=aarch64-linux-android-
cd libuuid-1.0.3
./configure --with-pic --host=aarch64-linux-android --disable-shared --enable-static
autoreconf -i -f
make
```
   
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   
   
**BUILD LIBUUID (android-x86)**   
Open "Bash on Ubuntu on Windows"   
```
wget https://sourceforge.net/projects/libuuid/files/libuuid-1.0.3.tar.gz
tar -xvf libuuid-1.0.3.tar.gz
export ANDROID_NDK_ROOT=$(pwd)/android-ndk-r12b
export PATH=$(pwd)/i686-linux-android/bin:$PATH
export CROSS_COMPILE=i686-linux-android-
cd libuuid-1.0.3
./configure --with-pic --host=i686-linux-android --disable-shared --enable-static
autoreconf -i -f
make
```
   
Get uuid.h from libuuid-1.0.3   
Get libuuid.a from libuuid-1.0.3/.libs   