# fix error
```sh
compinit
cp .zcompdump .zcompdump-$HOSTNAME-$ZSH_VERSION
```

# clipboard
```sh
cat id_rsa.pub | clip
```

# zsh plugins
```sh
vim ~/.oh-my-zsh/plugins/git/git.plugin.zsh
alias gcam='git commit -am'
```

# package
```sh
pact install the_silver_searcher
```

# fix prompt slow
* set theme newly
    ```sh
    ZSH_THEME="agnoster"
    ```
* set theme back
    ```sh
    ZSH_THEME="robbyrussell"
    ```
