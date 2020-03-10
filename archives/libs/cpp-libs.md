# boost
* build for windows
    * open VS2017 x64 Native Tools Command Prompt
    ```bat
    cd %USERPROFILE%\code\boost_1_67_0
    .\bootstrap.bat --without-libraries=python
    .\b2.exe -j8 address-model=64
    setx BOOST_ROOT %USERPROFILE%\code\boost_1_67_0
    ```
* build for macos
    ```sh
    cd ~/code/boost_1_67_0
    ./bootstrap.sh --without-libraries=python
    ./b2 -j8
    sudo ./b2 install
    ```
* build for linux
    ```sh
    cd ~/code/boost_1_67_0
    ./bootstrap.sh --without-libraries=python
    ./b2 -j8 cxxflags=-fPIC
    sudo ./b2 install
    ```
* install linux dependency
    ```sh
    sudo yum install -y zlib-devel bzip2-devel libquadmath-devel
    ```
* using by cmake
    ```cmake
    set(Boost_USE_STATIC_LIBS ON)
    set(Boost_USE_MULTITHREADED ON)
    set(Boost_USE_STATIC_RUNTIME OFF)
    find_package(Boost REQUIRED COMPONENTS unit_test_framework log_setup log filesystem program_options random system)
    set(inc_list ${Boost_INCLUDE_DIRS})
    if(${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU")
        set(lib_list ${Boost_LIBRARIES} pthread rt)
    elseif(${CMAKE_CXX_COMPILER_ID} STREQUAL "Clang")
        set(lib_list ${Boost_LIBRARIES})
    elseif(MSVC)
        set(lib_list ${Boost_LIBRARIES})
        set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /SAFESEH:NO Psapi.lib")
    endif()
    ```
* macos
    * /private/tmp/boost_interprocess

# protobuf
* build for windows
    * open VS2017 x64 Native Tools Command Prompt
    ```bat
    cd %USERPROFILE%\code\protobuf-3.4.1\cmake
    mkdir build
    cd build
    cmake -Dprotobuf_BUILD_TESTS=OFF -Dprotobuf_MSVC_STATIC_RUNTIME=OFF ..
    cmake --build .
    copy Debug\libprotobufd.lib Debug\libprotobuf.lib
    setx PROTOBUF_ROOT %USERPROFILE%\code\protobuf-3.4.1
    setx CMAKE_INCLUDE_PATH %USERPROFILE%\code\protobuf-3.4.1\src
    setx CMAKE_LIBRARY_PATH %USERPROFILE%\code\protobuf-3.4.1\cmake\build\Debug
    ```
    * add path %USERPROFILE%\code\protobuf-3.4.1\cmake\build\debug
* build for macos
    ```sh
    cd ~/code/protobuf-3.4.1/cmake
    mkdir build
    cd build
    cmake -Dprotobuf_BUILD_TESTS=OFF ..
    make
    sudo make install
    ```
* build for linux
    * cmake
        ```sh
        cd ~/code/protobuf-3.4.1/cmake
        mkdir build
        cd build
        cmake -Dprotobuf_BUILD_TESTS=OFF -DCMAKE_POSITION_INDEPENDENT_CODE=ON ..
        make
        sudo make install
        ```
    * make
        ```sh
        sudo yum install -y autoconf automake libtool curl make gcc-c++ unzip
        cd ~/code/protobuf-3.4.1
        ./autogen.sh
        ./configure CXXFLAGS=-fPIC
        make
        make check
        sudo make install
        sudo ldconfig
        ```
* using by cmake
    ```cmake
    find_package(Protobuf REQUIRED)
    set(inc_list ${Protobuf_INCLUDE_DIRS})
    set(lib_list ${Protobuf_LIBRARIES})
    ```
* build csharp's Google.Protobuf.dll
    * need [.NET Core](https://github.com/dotnet/core)
    * fix The reference assemblies for framework ".NETFramework,Version=v3.5" were not found.
    * add this to Google.Protobuf.csproj
    ```
    <PropertyGroup>
      <FrameworkPathOverride Condition="'$(TargetFramework)' == 'net35'">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\.NETFramework\v3.5\Profile\Client</FrameworkPathOverride>
    </PropertyGroup>
    ```

# openssl
* build for windows
    * install nasm x64 http://www.nasm.us
    * add path %USERPROFILE%\tools\nasm-2.13.01
    * install perl http://strawberryperl.com
    * open VS2017 x64 Native Tools Command Prompt
    ```bat
    cd %USERPROFILE%\code\openssl-1.1.0f
    perl Configure VC-WIN64A
    nmake
    nmake test
    setx OPENSSL_ROOT %USERPROFILE%\code\openssl-1.1.0f
    ```
    add path %USERPROFILE%\code\openssl-1.1.0f
* build for macos & linux
    ```sh
    cd ~/code/openssl-1.1.0f
    ./config
    make
    sudo make install
    ```
* build for ios
    ```sh
    export CC="clang -fembed-bitcode"
    export CROSS_TOP=/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer
    export CROSS_SDK=iPhoneOS.sdk
    export PATH="/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin:$PATH"
    ./Configure ios64-cross no-shared no-dso no-hw no-engine --prefix=/usr/local/openssl-ios64
    make
    sudo make install
    ```
* build for android arm
    ```sh
    export ANDROID_NDK_ROOT=$HOME/Library/Android/android-ndk-r14b
    export CROSS_SYSROOT=$ANDROID_NDK_ROOT/platforms/android-14/arch-arm
    export CROSS_COMPILE=arm-linux-androideabi-
    export PATH=$ANDROID_NDK_ROOT/toolchains/arm-linux-androideabi-4.9/prebuilt/darwin-x86_64/bin:$PATH
    ./Configure android-armeabi no-shared no-dso no-hw no-engine no-unit-test --prefix=/usr/local/openssl-android-armeabi
    make
    sudo make install
    ```
* build for android x86
    ```sh
    export ANDROID_NDK_ROOT=$HOME/Library/Android/android-ndk-r14b
    export CROSS_SYSROOT=$ANDROID_NDK_ROOT/platforms/android-14/arch-x86
    export CROSS_COMPILE=i686-linux-android-
    export PATH=$ANDROID_NDK_ROOT/toolchains/x86-4.9/prebuilt/darwin-x86_64/bin:$PATH
    ./Configure android-x86 no-shared no-dso no-hw no-engine no-unit-test --prefix=/usr/local/openssl-android-x86
    make
    sudo make install
    ```
* fix linux issue
    ```sh
    sudo ln -s /usr/local/lib64/libssl.so.1.1 /usr/lib64/libssl.so.1.1
    sudo ln -s /usr/local/lib64/libcrypto.so.1.1 /usr/lib64/libcrypto.so.1.1
    ```
* fix windows issue
    * no OPENSSL_Applink...
        * add include path for applink.c
        ```cpp
        #ifdef _WIN32
        #include <ms/applink.c>
        #endif
        ```
* using by cmake
    ```cmake
    if(${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU")
        set(lib_list crypto)
        link_directories("/usr/local/lib64")
    elseif(${CMAKE_CXX_COMPILER_ID} STREQUAL "Clang")
        find_package(OpenSSL REQUIRED)
        set(inc_list ${OPENSSL_INCLUDE_DIR})
        set(lib_list ${OPENSSL_CRYPTO_LIBRARY})
    elseif(MSVC)
        set(lib_list libcrypto)
        include_directories($ENV{OPENSSL_ROOT})
        include_directories($ENV{OPENSSL_ROOT}/include)
        link_directories($ENV{OPENSSL_ROOT}/lib)
        link_directories($ENV{OPENSSL_ROOT})
    endif()
    ```
* FIPS
    * Federal Information Processing Standards

* generating ec keys
    ```sh
    openssl ecparam -list_curves
    openssl ecparam -name prime256v1 -param_enc named_curve -genkey -noout -out pri.pem
    openssl ec -in pri.pem -pubout -out pub.pem
    ```
