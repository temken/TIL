# Handle the include path of an imported library

Say we are building a library via

```CMake
add_library(library <SOURCES>)
```

and we want to build e.g. another executable that uses this library (could also be in a different project that imports this library.)

```CMake
add_executable(exec <SOURCES>)
target_link_library(exec PRIVATE library)
```

While this links the library correctly, it might be unknown where the library header files of *library* are located.
To specify the path of the library's header files directly, adjust the first code block by adding one line:

```CMake
add_library(library <SOURCES>)
target_include_directories(library PUBLIC ${INCLUDE_DIR})
```

where ${INCLUDE_DIR} is the path of the header files.
After this line was added, the include-path is a public property that gets inherited. I.e. the *target_link_library* command automatically involves knowledge of the header files' location.

## Source
[https://kubasejdak.com/19-reasons-why-cmake-is-actually-awesome](https://kubasejdak.com/19-reasons-why-cmake-is-actually-awesome) 

(see point 6.)