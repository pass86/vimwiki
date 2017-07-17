# boost
* build on windows
    * open Developer Command Prompt for VS2015
    * cd %USERPROFILE%/code/boost_1_64_0
    * ./bootstrap.bat
    * ./b2.exe
    * setx BOOST_ROOT %USERPROFILE%\code\boost_1_64_0
* build on macos & linux
    * cd ~/code/boost_1_64_0
    * ./bootstrap.sh
    * ./b2
    * sudo ./b2 install
* install linux dependency
    * sudo yum install -y zlib-devel bzip2-devel libquadmath-devel
* using by cmake
    * set(Boost_USE_STATIC_LIBS ON)
    * set(Boost_USE_MULTITHREADED ON)
    * set(Boost_USE_STATIC_RUNTIME OFF)
    * find_package(Boost REQUIRED COMPONENTS unit_test_framework log_setup log filesystem program_options random system)
    * set(inc_list ${Boost_INCLUDE_DIRS})
    * if(${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU")
    *     set(lib_list ${Boost_LIBRARIES} pthread rt)
    * elseif(${CMAKE_CXX_COMPILER_ID} STREQUAL "Clang")
    *     set(lib_list ${Boost_LIBRARIES})
    * elseif(MSVC)
    *     set(lib_list ${Boost_LIBRARIES})
    *     set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /SAFESEH:NO Psapi.lib")
    * endif()

# protobuf
* build on windows
    * open Developer Command Prompt for VS2015
    * cd %USERPROFILE%/code/protobuf-3.3.0/cmake
    * mkdir build\debug
    * cd build/debug
    * cmake -G "NMake Makefiles" -DCMAKE_BUILD_TYPE=Debug -Dprotobuf_BUILD_TESTS=OFF -Dprotobuf_MSVC_STATIC_RUNTIME=OFF ../..
    * nmake
    * copy libprotobufd.lib libprotobuf.lib
    * setx PROTOBUF_ROOT %USERPROFILE%\code\protobuf-3.3.0
    * setx CMAKE_INCLUDE_PATH %USERPROFILE%\code\protobuf-3.3.0\src
    * setx CMAKE_LIBRARY_PATH %USERPROFILE%\code\protobuf-3.3.0\cmake\build\debug
    * add path %USERPROFILE%\code\protobuf-3.3.0\cmake\build\debug
* build on macos
    ```shell
    cd ~/code/protobuf-3.3.0/cmake
    mkdir build
    cd build
    cmake -Dprotobuf_BUILD_TESTS=OFF ..
    make
    sudo make install
    ```
* build on linux
    * sudo yum install -y autoconf automake libtool curl make g++ unzip
    * cd ~/code/protobuf-3.3.0
    * ./autogen.sh
    * ./configure
    * make
    * make check
    * sudo make install
    * sudo ldconfig
* using by cmake
    * find_package(Protobuf REQUIRED)
    * set(inc_list ${Protobuf_INCLUDE_DIRS})
    * set(lib_list ${Protobuf_LIBRARIES})
* build csharp's Google.Protobuf.dll
    * need .NET Core

# openssl
* build on windows
    * install nasm http://www.nasm.us
    * add path %USERPROFILE%\tools\nasm-2.12.02
    * install perl http://strawberryperl.com
    * open Developer Command Prompt for VS2015
    * cd %USERPROFILE%/code/openssl-1.1.0e
    * perl Configure VC-WIN32
    * nmake
    * nmake test
    * setx OPENSSL_ROOT %USERPROFILE%\code\openssl-1.1.0e
    * add path %USERPROFILE%\code\openssl-1.1.0e
* build on macos & linux
    * cd ~/code/openssl-1.1.0e
    * ./config
    * make
    * sudo make install
* fix linux issue
    * sudo ln -s /usr/local/lib64/libssl.so.1.1 /usr/lib64/libssl.so.1.1
    * sudo ln -s /usr/local/lib64/libcrypto.so.1.1 /usr/lib64/libcrypto.so.1.1
* fix windows issue
    * no OPENSSL_Applink...
        * add include path for applink.c
        * #ifdef _WIN32
        * #include <ms/applink.c>
        * #endif
* using by cmake
    * if(${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU")
    *     set(lib_list crypto)
    *     link_directories("/usr/local/lib64")
    * elseif(${CMAKE_CXX_COMPILER_ID} STREQUAL "Clang")
    *     find_package(OpenSSL REQUIRED)
    *     set(inc_list ${OPENSSL_INCLUDE_DIR})
    *     set(lib_list ${OPENSSL_CRYPTO_LIBRARY})
    * elseif(MSVC)
    *     set(lib_list libcrypto)
    *     include_directories($ENV{OPENSSL_ROOT})
    *     include_directories($ENV{OPENSSL_ROOT}/include)
    *     link_directories($ENV{OPENSSL_ROOT}/lib)
    *     link_directories($ENV{OPENSSL_ROOT})
    * endif()
* generating ec keys
    * openssl ecparam -list_curves
    * openssl ecparam -name prime256v1 -param_enc named_curve -genkey -noout -out pri.pem
    * openssl ec -in pri.pem -pubout -out pub.pem