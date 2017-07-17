# devel
* windows
    * setx MYSQL_ROOT %USERPROFILE%\devel\mysql-connector-c-6.1.9-win32
    * add path MYSQL_ROOT %USERPROFILE%\devel\mysql-connector-c-6.1.9-win32\lib
* linux
    * sudo yum install mysql-community-devel

# password
* alter user 'root'@'localhost' identified by 'foo';

# fix 1130
* update user set host = '%' where user = 'root';
* sudo systemctl restart mysqld

# index
* show index from foo;