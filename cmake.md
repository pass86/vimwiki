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
