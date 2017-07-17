# fix error
* compinit
* cp .zcompdump .zcompdump-$HOSTNAME-$ZSH_VERSION

# clipboard
* cat id_rsa.pub | clip

# zsh plugins
* vim ~/.oh-my-zsh/plugins/git/git.plugin.zsh
    * alias gcam='git commit -am'

# package
* pact install the_silver_searcher

# fix prompt slow
* set theme newly
    * ZSH_THEME="agnoster"
* set theme back
    * ZSH_THEME="robbyrussell"