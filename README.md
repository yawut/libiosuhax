[![Build Status](https://travis-ci.org/dimok789/libiosuhax.svg)](https://travis-ci.org/dimok789/libiosuhax)
# libiosuhax
A PPC library to access IOSUHAX from PPC and a devoptab for any device or path.
It's only compatible to RPX-Files.

## Using (wut - submodule)
If you're using git, you already have good support for submodules - [read up here](https://github.blog/2016-02-01-working-with-submodules/). Quick start:
```
mkdir -p ext
git submodule add <libiosuhax url> ext/libiosuhax
git submodule update --init --recursive
```
The following examples assume the libiosuhax source is located at `ext/libiosuhax`, though you can have it wherever you'd like.

### wut+make (devkitPro-style)
If you're using a devkitPro-style makefile (like [this one](https://github.com/devkitPro/wut/blob/master/samples/make/helloworld/Makefile)), you need to add libiosuhax's `source` directory to `SOURCES` and the `include` directory to `INCLUDES`.

For example, this:
```make
SOURCES := src \
           src/gui
#...
INCLUDES := src
```
becomes this:
```make
SOURCES := src \
           src/gui \
           ext/libiosuhax/source
#...
INCLUDES := src \
            ext/libiosuhax/include
```
With that, you should be good to go!

### wut+CMake
If your project uses CMake (like [this one](https://github.com/devkitPro/wut/blob/master/samples/cmake/helloworld/CMakeLists.txt)), you need to add the following lines to your `CMakeLists.txt`:
```cmake
add_subdirectory(ext/libiosuhax)
target_link_libraries(<target> libiosuhax::libiosuhax)
```
Replace `<target>` with the name of your binary, as passed to `add_executable`. You're good to go!

## Using (wut - static library)
Make you to have [wut](https://github.com/devkitPro/wut/) installed and use the following command for build:
```
make install
```
This installs to `$DEVKITPRO/wut`, so the includes should Just Work, and you can add `-liosuhax` to your build flags where appropriate.

## Using (dynamic_libs - submodule)
For legacy dynamic_libs homebrew, like [this one](https://github.com/dimok789/hello_world), you should be able to follow the same steps as [wut+make (devkitPro style)](#wut+make (devkitPro-style)). Make sure you're using an updated version of dynamic_libs, like [Maschell's](https://github.com/Maschell/dynamic_libs), or you'll get errors about missing functions (like `IOS_Open`). The dynamic_libs compatibility of this library is not well tested, and not all supported CFWs can even run such homebrew - so consider moving to wut as a matter of priority.
