# install
* centos
    * sudo yum install python34-pip python34-devel
    * sudo pip3 install --upgrade pip
    * pip3 install --user thefuck
    * vi ~/.bashrc
        * export PATH=$PATH:~/.local/bin
        * eval $(thefuck --alias)