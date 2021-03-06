# PreLoad.cmake
```cmake
if(MSVC)
    set(CMAKE_GENERATOR_PLATFORM x64 CACHE INTERNAL "" FORCE)
endif()
```

# build target
```sh
cmake --build . --target INSTALL
```

# install target
```cmake
install(TARGETS foo RUNTIME DESTINATION bar)
```

# kinds of target
* ARCHIVE
    * *.lib, *.a
* LIBRARY
    * *.lib, *.a, *.dylib
* RUNTIME
    * *.exe, *.dll, executables
* FRAMEWORK
    * marked with the FRAMEWORK property
* BUNDLE
    * marked with the MACOSX_BUNDLE property

# build release
```cmake
* cmake . -DCMAKE_BUILD_TYPE=Release
```

# Fix "iphoneos is not an iOS SDK"
```sh
sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer
```
