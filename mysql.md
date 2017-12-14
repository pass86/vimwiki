# install
* linux
    ```sh
    sudo yum install mysql-community-server
    ```
* macos
    ```sh
    brew install mysql
    ```

# devel
* linux
    ```sh
    sudo yum install mysql-community-devel
    ```
* windows
    ```bat
    setx MYSQL_ROOT %USERPROFILE%\Library\mysql-connector-c-6.1.9-win32
    ```
    * add path MYSQL_ROOT %USERPROFILE%\Library\mysql-connector-c-6.1.9-win32\lib

# password
```mysql
alter user 'root'@'localhost' identified by 'foo';
```

# turn off password validation
```mysql
uninstall plugin validate_password;
```

# fix 1130
```mysql
update user set host = '%' where user = 'root';
```
```sh
sudo systemctl restart mysqld
```

# index
```mysql
show index from foo;
```
