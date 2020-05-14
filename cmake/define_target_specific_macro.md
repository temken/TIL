# Define a target-specific macro

We can define a preprocessor macro in a target-specific way.

For example, to define a macro **BASE_DIRECTORY** as a string that contains the path to the project, which is available when building the CMake **target**, add this line

```cmake
target_compile_definitions(<target>
	PRIVATE 
		BASE_DIRECTORY="${PROJECT_SOURCE_DIR}/")
```

## Source
[https://cmake.org/cmake/help/v3.0/command/target_compile_definitions.html](https://cmake.org/cmake/help/v3.0/command/target_compile_definitions.html)