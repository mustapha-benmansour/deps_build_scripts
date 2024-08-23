
### Script usage


debian 11 (64)
mingw-w64 (cross compile for windows)
includes toolchains : 
    g++-mingw-w64-i686 
    g++-mingw-w64-x86-64 
    gcc-mingw-w64-i686 
    gcc-mingw-w64-x86-64 

gcc-multilib && g++-multilib are required to compile to linux32 on 64bit

debootstrap  && schroot (for chroot) to test in isolate env


sudo apt-get install debootstrap 
sudo apt-get install schroot