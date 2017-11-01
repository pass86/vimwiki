# esc
* ctrl+[

# sudo write
```
:w !sudo tee %
```

# display unprintable characters
```
:set list
```

# cmdline window
```
q:
```

# tab to spaces
```
:retab
```

# swap window
```
ctrl+w, x
```

# build
```sh
./configure --enable-pythoninterp
```

# nerdtree
* press m to manage file
 
# ycm
* macos
    ```sh
    ./install.py --clang-completer --system-libclang --omnisharp-completer
    ```
* linux
    * require gcc 4.9
    ```sh
    ./install.py --clang-completer
    ```
    * fix libtinfo.so.5: cannot open shared object file
    ```sh
    pacman -S clang
    ```
* windows
    * automatic, but maybe "The C compiler identification is unknown"
        ```bat
        python install.py --clang-completer --omnisharp-completer
        ```
    * manual
        * remove cygwin bin from path
        * llvm
            * download llvm & clang
            * move cfe-4.0.0.src llvm-4.0.1.src/tools
            ```bat
            cd %USERPROFILE%
            mkdir llvm_build
            cd llvm_build
            cmake %USERPROFILE%/code/llvm-4.0.1.src
            cmake --build . --config Release
            cmake -DCMAKE_INSTALL_PREFIX=%USERPROFILE%/Library/llvm -P cmake_install.cmake
            ```
        * cpp
            ```bat
            cd %USERPROFILE%
            mkdir ycm_build
            cd ycm_build
            cmake -DPATH_TO_LLVM_ROOT=%USERPROFILE%/Library/llvm %USERPROFILE%/dotfiles/vim/bundle/YouCompleteMe/third_party/ycmd/cpp
            cmake --build . --target ycm_core --config Release
            ```
        * csharp
            ```bat
            cd %USERPROFILE%/dotfiles/vim/bundle/YouCompleteMe/third_party/ycmd/third_party/OmniSharpServer
            msbuild /property:Configuration=Release /property:TargetFrameworkVersion=v4.5
            ```
        * revert cygwin bin to path
