# GroupSourcesByFolder.cmake

## About

When using CMake to generate Visual Studio/Xcode targets, source organization can become very convoluted as by default CMake creates two single source groups for all headers and for source files, completely ignoring any organization in the local file structure.
GroupSourcesByFolder.cmake automatically re-groups the source files into a structure resembling the original file structure.
The script is based on [this](http://blog.audio-tk.com/2015/09/01/sorting-source-files-and-projects-in-folders-with-cmake-and-visual-studioxcode/) blog post by Matthieu Brucher.

## Example

| Before  | After |
| ------------- | ------------- |
| ![](https://user-images.githubusercontent.com/4437447/67684391-fb64c880-f98a-11e9-8ea1-e153a747f288.png)  | ![](https://user-images.githubusercontent.com/4437447/67684394-fd2e8c00-f98a-11e9-8261-86e410a04e40.png)  |


## Usage

[Integrate](#how-to-integrate) GroupSourcesByFolder.cmake into your project and call `GroupSourcesByFolder` with your target as an argument.

```cmake
add_library(MyLibrary ${sources})
GroupSourcesByFolder(MyLibrary)
```

## How to integrate

### Using [CPM.cmake](https://github.com/TheLartians/CPM.cmake) (recommended)

Run the following from the project's root directory to add CPM to your project.

```bash
mkdir -p cmake
wget -O cmake/CPM.cmake https://raw.githubusercontent.com/TheLartians/CPM.cmake/master/cmake/CPM.cmake
```

Add the following lines to the project's `CMakeLists.txt` after calling `project(...)`.

```CMake
include(cmake/CPM.cmake)

CPMAddPackage(
  NAME GroupSourcesByFolder.cmake
  GITHUB_REPOSITORY TheLartians/GroupSourcesByFolder.cmake
  VERSION 1.0
)
```

### Using git submodules (not suited for libraries)

Run the following from the project's root directory.

```bash
git submodule add https://github.com/TheLartians/GroupSourcesByFolder.cmake 
```

In add the following lines to the project's `CMakeLists.txt` after calling `project(...)`.

```CMake
add_subdirectory(GroupSourcesByFolder.cmake)
```

## See also

- [Format.cmake](https://github.com/TheLartians/Format.cmake) - clang-format targets for CMake
- [Ccache.cmake](https://github.com/TheLartians/Ccache.cmake) - a Ccache integration for CMake with Xcode support
