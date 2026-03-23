# 2Boost Toolchain

This repository contains toolcahin needed to build [2Boost](https://github.com/aalesv/2boost). It is based on [Cygwin](https://cygwin.com) version 2.935 (x86_64). It contains only minimal set of programs needed to successfully build [2Boost](https://github.com/aalesv/2boost).

### It consists of:

- Cygwin binaries, including python 3.9 and lxml bindings
- [Binutils](https://www.gnu.org/software/binutils/) version 2.40
- [GCC](https://gcc.gnu.org/) version 12.3.0 with C language support **only**.
- [Swiss File Knife](https://sourceforge.net/projects/swissfileknife/)

### Binutils configuration

`../binutils-2.40/configure --target=sh-elf --disable-nls --prefix=/usr/local/sh-toolchain`

### Custom patches applied to Binutils

- None.

### GCC configuration

`../gcc-12.3.0/configure --target=sh-elf --with-endian=big,little --disable-bootstrap --enable-languages=c --disable-nls --with-gnu-as --with-gnu-ld --prefix=/usr/local/sh-toolchain --without-headers --without-newlib --disable-libquadmath --disable-libquadmath-support --with-pkgversion='2Boost Toolchain version 12.3.0-0'`

### Custom patches applied to GCC

- ashrsi3 late expanding patch taken from [GCC PR #54089](https://gcc.gnu.org/bugzilla/attachment.cgi?id=55543&action=diff).

### How to use

- Download archive from [Releases](https://github.com/aalesv/2boost-toolchain/releases) section.
- Unpack to a directory. Full path should not contain non-ASCII symbols and spaces.
- Add path to the 'bin' directory to your PATH variable. Ensure there's no other 'make' are on the path. For example, if toolchain is unpacked to `c:\2boost-toolchain` directory, a path `c:\2boost-toolchain\bin` should be added to the PATH variable.
- Build 2Boost according to its manual.
