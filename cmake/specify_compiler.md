# Run CMake with a specific compiler

In order to build a CMake project with a specific compiler (instead of CMake finding the best compiler automatically), say ```g++-5```, you can build the project via

```zsh
mkdir -p build
cd build
cmake -G "Unix Makefiles" -D CMAKE_C_COMPILER=gcc-5 -D CMAKE_CXX_COMPILER=g++-5  ..
make install
```

## Source
[https://stackoverflow.com/questions/45933732/how-to-specify-a-compiler-in-cmake](https://stackoverflow.com/questions/45933732/how-to-specify-a-compiler-in-cmake)