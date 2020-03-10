# install
```sh
sudo yum install nginx
```

# reverse proxy
```sh
sudo vi /etc/nginx/nginx.conf
```
```nginx
location /transmission {
    proxy_pass http://localhost:9091;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
```

# git server
```sh
brew install nginx fcgiwrap
export PATH=$PATH:/usr/local/sbin
vim /usr/local/etc/nginx/nginx.conf
```
```nginx
    server {
        listen       8080;
        server_name  localhost;

        location ~ /git(/.*) {
            auth_basic "Restricted";
            auth_basic_user_file /usr/local/etc/nginx/passwd;
            fastcgi_pass unix:/usr/local/var/run/fcgiwrap.socket;
            fastcgi_param SCRIPT_FILENAME /Applications/Xcode.app/Contents/Developer/usr/libexec/git-core/git-http-backend;
            fastcgi_param GIT_HTTP_EXPORT_ALL "";
            fastcgi_param GIT_PROJECT_ROOT /usr/local/var/repo;
            fastcgi_param PATH_INFO $1;
            fastcgi_param REMOTE_USER $remote_user;
            include fastcgi_params;
        }
    }
```
```sh
htpasswd -c /usr/local/etc/nginx/passwd user01
mkdir /usr/local/var/repo
git init --bare /usr/local/var/repo/test.git
fcgiwrap -s unix:/usr/local/var/run/fcgiwrap.socket
brew services start nginx
git clone http://localhost:8080/git/test.git
```
