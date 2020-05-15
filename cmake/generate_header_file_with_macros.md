# Generate a header file with git property and directory macros using CMake

## Generate a header file

In order for CMake to generate a version header **version.hpp**, which contains useful macros, we start by defining the location of generated files inside the **build/** folder. Add the following line to **CMakeLists.txt**.
```cmake
set(GENERATED_DIR ${PROJECT_BINARY_DIR}/generated)
```
The generated header will follow a template we call **version.hpp.in**, which we store in the standard **/include/** folder together with the other headers.
```cpp
// version.hpp.in
#ifndef VERSION_HPP
#define VERSION_HPP

#define AUTHOR "Timon Emken"
#define YEAR "2020"

#define PROJECT_NAME "@PROJECT_NAME@"
#define PROJECT_VERSION  "@PROJECT_VERSION@"
#define PROJECT_VERSION_MAJOR "@PROJECT_VERSION_MAJOR@"
#define PROJECT_VERSION_MINOR "@PROJECT_VERSION_MINOR@"
#define PROJECT_VERSION_PATCH "@PROJECT_VERSION_PATCH@"

#define PROJECT_DIR "@PROJECT_SOURCE_DIR@/"
#define TOP_LEVEL_DIR "@CMAKE_SOURCE_DIR@/"

#endif
```
Anything between the **@** signs will get replaced by the corresponding CMake variables. By further adding
```cmake
configure_file(
  ${INCLUDE_DIR}/version.hpp.in
  ${GENERATED_DIR}/version.hpp )
```
we tell CMake to generate an actual header based on that template. Lastly, we also have to tell our targets to include the **/build/generated/** folder.
```cmake
target_include_directories(<target>
	PRIVATE
		${GENERATED_DIR} )
```

Now, we can include this header in our code via

```cpp
#include "version.hpp"
```

and use the macros in our projects.

## Fetch and include the git branch and commit

One of the most useful macros one can define in such a version header is the git information, such as the most recent commit's hash and the branch we are working on. These can be fetched and stored in CMake variables via
```cmake
execute_process( # Git commit hash
  COMMAND git rev-parse --abbrev-ref HEAD
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  OUTPUT_VARIABLE GIT_BRANCH
  OUTPUT_STRIP_TRAILING_WHITESPACE )
execute_process( # Git commit hash
  COMMAND git log -1 --format=%h
  WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
  OUTPUT_VARIABLE GIT_COMMIT_HASH
  OUTPUT_STRIP_TRAILING_WHITESPACE )
```
Now, we simply add corresponding macros to the **version.hpp.in** file above,
```cpp
#define GIT_BRANCH "@GIT_BRANCH@"
#define GIT_COMMIT_HASH "@GIT_COMMIT_HASH@"
```
and now we are able to include e.g. the git commit hash in our computations' results. This is immensly useful if we want to reproduce old results later-on.

## Source
[http://xit0.org/2013/04/cmake-use-git-branch-and-commit-details-in-project/](http://xit0.org/2013/04/cmake-use-git-branch-and-commit-details-in-project/)