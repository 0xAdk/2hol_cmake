This is a test to see how it would look if 2hol was built using cmake.

This currently only builds the linux binaries for the client and server

# Build instructions
pull down minorGems submodule and generate build directory (this only has to be done once)
```sh
git submodule update --init --recursive
cmake -B build
```

compile the client and server
```sh
cmake --build build
```

if you only want to compiler one of either the server or the client you can use the `--target` flag
```sh
cmake --build build --target [server|client]
```
