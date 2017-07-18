# devel
* windows
    ```bat
    setx MYSQL_ROOT %USERPROFILE%\devel\mysql-connector-c-6.1.9-win32
    ```
    * add path MYSQL_ROOT %USERPROFILE%\devel\mysql-connector-c-6.1.9-win32\lib
* linux
    ```sh
    sudo yum install mysql-community-devel
    ```

# password
```mysql
alter user 'root'@'localhost' identified by 'foo';
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
