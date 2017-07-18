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
