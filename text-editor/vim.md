# esc
```
* ctrl+[
```

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

# new tab
```
:tabnew
```

# next tab
```
g t
```

# prev tab
```
g T
```

# clear last search highlighting
```
:noh
```

# move half-page
* ctrl+d move half-page down
* ctrl+u move half-page up

# set syntax
```
:set syntax=lua
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
    ./install.py --clang-completer --system-libclang --cs-completer --go-completer
    ```
    * fix "the imp module is deprecated in favour of importlib"
    ```sh
    brew reinstall --with-python@2
    ```
* linux
    * require gcc 4.9
    ```sh
    ./install.py --clang-completer --go-completer
    ```
    * fix libtinfo.so.5: cannot open shared object file
    ```sh
    pacman -S clang
    ```
* windows
    * automatic, but maybe "The C compiler identification is unknown"
        ```bat
        python install.py --clang-completer --cs-completer --go-completer
        ```
    * manual
        * remove cygwin bin from path
        * llvm
            * Download llvm & clang
            * Move cfe-9.0.0.src llvm-9.0.0.src/tools
            ```bat
            cd %USERPROFILE%
            mkdir llvm_build
            cd llvm_build
            cmake %USERPROFILE%/code/llvm-9.0.0.src -A Win32
            cmake --build . --config Release
            cmake -DCMAKE_INSTALL_PREFIX=%USERPROFILE%/libs/llvm-9.0.0 -P cmake_install.cmake
            ```
        * cpp
            * Add C:\Python27\libs to Path
            ```bat
            cd %USERPROFILE%
            mkdir ycm_build
            cd ycm_build
            cmake -DPATH_TO_LLVM_ROOT=%USERPROFILE%/libs/llvm-9.0.0 -A Win32 %USERPROFILE%/dotfiles/vim/bundle/YouCompleteMe/third_party/ycmd/cpp
            cmake --build . --target ycm_core --config Release
            ```
        * csharp
            ```bat
            cd %USERPROFILE%/dotfiles/vim/bundle/YouCompleteMe/third_party/ycmd/third_party/OmniSharpServer
            msbuild /property:Configuration=Release /property:TargetFrameworkVersion=v4.5
            ```
        * revert cygwin bin to path
