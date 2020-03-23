QEMU Windows Build
==================

Setup
-----

Install MSYS2
pacman -Syu

Start mingw64 shell
pacman -Su
pacman -S base-devel mingw-w64-x86_64-toolchain git python
pacman -S mingw-w64-x86_64-glib2 mingw-w64-x86_64-gtk3 mingw-w64-x86_64-SDL2

Initialize Repo
---------------

git clone url dest
cd dest
git submodule update --init ui/keycodemapdb
git submodule update --init capstone
git submodule update --init dtc

Build
-----

./configure --enable-gtk --enable-sdl --disable-werror --disable-capstone --prefix=/usr/local/qemu
make -j8
make copydlls
make installer
