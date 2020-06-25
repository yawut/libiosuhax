# This is only really intended for submodule use - if you want to compile a
# standalone library, see the Makefile and README.md
cmake_minimum_required(VERSION 3.2)

project(libiosuhax
    LANGUAGES C
    VERSION 1.0.0
)

add_subdirectory(source)
