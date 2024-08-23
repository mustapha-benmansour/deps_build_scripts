

* ### Commun
```sh
cd LuaJIT
```
```sh
# update dep repo
```

```sh
SYSROOT=$HOME/my_sysroot &&\
```

#
* ### Windows

```sh
# win64 
ARCH=x86_64 &&\
HOST_CC=gcc &&\
CROSS=x86_64-w64-mingw32- &&\
```

```sh
# win32 
ARCH=x86 &&\
HOST_CC="gcc -m32" &&\
CROSS=i686-w64-mingw32- &&\
```



```sh
# win make install
make clean ;\
USR_LOCAL=$SYSROOT/windows/$ARCH &&\
sudo mkdir -vp $USR_LOCAL &&\
X=/usr/local &&\
sudo mount --bind $USR_LOCAL $X &&\
make \
    HOST_CC="$HOST_CC" \
    CROSS=$CROSS \
    CC=gcc \
    TARGET_SYS=Windows \
    PREFIX=$X &&\
sudo mkdir -vp $X/{include/luajit-2.1,bin,lib/pkgconfig,share/luajit-2.1/jit,share/man/man1} &&\
sudo cp -vf ./src/{lauxlib.h,luaconf.h,lua.h,lua.hpp,luajit.h,lualib.h} $X/include/luajit-2.1 &&\
sudo cp -vf ./src/lua51.dll $X/bin/lua51.dll &&\
sudo cp -vf ./src/luajit.exe $X/bin/luajit.exe &&\
sudo cp -vf ./src/libluajit-5.1.dll.a $X/lib/libluajit-5.1.dll.a &&\
sudo mkdir -vp $X/share/luajit-2.1/jit &&\
sudo cp -vrf ./src/jit/*lua $X/share/luajit-2.1/jit &&\
sudo cp -vrf ./etc/luajit.1 $X/share/man/man1/luajit.1 &&\
sudo cp -vrf ./etc/luajit.pc $X/lib/pkgconfig/luajit.pc &&\
sudo umount $X
```

#
* ### Linux

```sh
# linux64
ARCH="x86_64" &&\
HOST_CC="gcc" &&\
CC="gcc" &&\
```

```sh
# linux32
ARCH="x86" &&\
HOST_CC="gcc -m32" &&\
CC="gcc -m32" &&\
```

```sh
# linux make
make clean ;\
USR_LOCAL=$SYSROOT/linux/$ARCH &&\
sudo mkdir -vp $USR_LOCAL &&\
X=/usr/local &&\
sudo mount --bind $USR_LOCAL $X &&\
make \
    HOST_CC="$HOST_CC" \
    CC="$CC" \
    TARGET_SYS=Linux &&\
    PREFIX=$X &&\
sudo install -D -m 0644 -v ./src/libluajit.a $X/lib/libluajit.a &&\
sudo install -D -m 0755 -v ./src/libluajit.so $X/lib/libluajit.so &&\
sudo install -D -m 0755 -v ./src/luajit $X/bin/luajit &&\
sudo install -D -m 0644 -v ./etc/luajit.1 $X/share/man/man1/luajit.1 &&\
sudo install -D -m 0644 -v ./etc/luajit.pc $X/lib/pkgconfig/luajit.pc &&\
sudo sudo mkdir -vp $X/{include/luajit-2.1,share/luajit-2.1/jit} &&\
sudo cp -vf ./src/{lauxlib.h,luaconf.h,lua.h,lua.hpp,luajit.h,lualib.h} $X/include/luajit-2.1 &&\
sudo cp -vf ./src/jit/*lua $X/share/luajit-2.1/jit &&\
sudo umount $X
```

#
* #### android
```sh
# linux make
```
```sh
TARGET=armv7a-linux-androideabi &&\
ARCH=armeabi-v7a &&\
HOST_CC="gcc -m32" &&\
```
```sh
TARGET=aarch64-linux-android &&\
ARCH=arm64-v8a &&\
HOST_CC=gcc &&\
```
```sh
TARGET=i686-linux-android &&\
ARCH=x86 &&\
HOST_CC="gcc -m32" &&\
```
```sh
TARGET=x86_64-linux-android &&\
ARCH=x86_64 &&\
HOST_CC=gcc &&\
```
```sh
API=21 &&\
NDK_BIN=$HOME/android-ndk-r27/toolchains/llvm/prebuilt/linux-x86_64/bin &&\
make clean ;\
USR_LOCAL=$SYSROOT/android/$ARCH &&\
sudo mkdir -vp $USR_LOCAL &&\
X=/usr/local &&\
sudo mount --bind $USR_LOCAL $X &&\
make \
    HOST_CC="$HOST_CC" \
    CROSS=$NDK_BIN/$TARGET- \
    CC=clang \
    STATIC_CC="$NDK_BIN/$TARGET$API-clang -fPIC" \
    DYNAMIC_CC="$NDK_BIN/$TARGET$API-clang -fPIC" \
    TARGET_LD=$NDK_BIN/$TARGET$API-clang \
    TARGET_AR="$NDK_BIN/llvm-ar rcus" \
    TARGET_STRIP=$NDK_BIN/llvm-strip \
    TARGET_SYS=Linux \
    PREFIX=$X &&\
sudo install -D -m 0644 -v ./src/libluajit.a $X/lib/libluajit.a &&\
sudo install -D -m 0755 -v ./src/libluajit.so $X/lib/libluajit.so &&\
sudo install -D -m 0755 -v ./src/luajit $X/bin/luajit &&\
sudo install -D -m 0644 -v ./etc/luajit.1 $X/share/man/man1/luajit.1
sudo install -D -m 0644 -v ./etc/luajit.pc $X/lib/pkgconfig/luajit.pc
sudo mkdir -vp $X/include/luajit-2.1 &&\
sudo cp -vf ./src/{lauxlib.h,luaconf.h,lua.h,lua.hpp,luajit.h,lualib.h} $X/include/luajit-2.1 &&\
sudo mkdir -vp $X/share/luajit-2.1/jit &&\
sudo cp -vf ./src/jit/*lua $X/share/luajit-2.1/jit &&\
sudo umount $X
```

```sh
cd ../..
```
