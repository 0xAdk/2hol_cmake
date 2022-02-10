This is a test to see how it would look if 2hol was built using cmake.

# Build instructions
This assumes you are compiling on linux

## Setup
pull down minorGems submodule
```sh
git submodule update --init --recursive
```

generate build directory

by default you can add `-DCMAKE_BUILD_TYPE=[Debug|Release|RelWithDebInfo|MinSizeRel]` to change how the binaray is built
### To compile for linux
```sh
cmake -B build
```

### To compile for windows
```sh
cmake -B build -DCMAKE_TOOLCHAIN_FILE=./toolchains/win32_cross_compile.cmake
```

## After Setup
you can tell cmake to only compile the client or the server with the `--target [server|client]` flag
and you can use the `-jN` flag to tell cmake to compile with more then one thread

this will compile the client using 8 threads
```sh
cmake --build build -j8 --target client
```

this will compile the client and the server using 1 thread
```sh
cmake --build build
```
