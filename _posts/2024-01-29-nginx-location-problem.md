---
layout: post_layout
title: nginx-locatin
time: 2024年01月29日 星期一
location: beijing
pulished: false
excerpt_separator: "##"
--- 

##### 反向代理
- 单个端口
```
server {
        listen 80;
        listen [::]:80;

        server_name 8.130.180.210;
#       root /var/www/example.com;
#       index index.html;
        location / {
                proxy_pass http://8.130.180.210:8080;  # 将请求转发给后端服务器
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
        }
}
```
完成后，可以通过现在目前所属serve的ip+端口访问`http://8.130.180.210:8080 `这个8.130.180.210的8080端口
- 多个端口
```
server {
        listen 80;
        listen [::]:80;

        server_name 8.130.180.210;
#       root /var/www/example.com;
#       index index.html;
        location /t2 {
                proxy_pass http://8.130.180.210:8080;  # 将请求转发给后端服务器
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
        }
        location /t3 {
                proxy_pass http://baidu.com;  # 将请求转发给后端服务器
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
        }
}
```
会在web broswer出现以下err

<img src="/assets/img/nginx/problem/1.png" width="400px">

因为nginx代理的网址要和代理名的配置一样，如果代理名后面加“/”，则代理的网址最后也要加“/”

```
server {
        listen 80;
        listen [::]:80;

        server_name 8.130.180.210;
#       root /var/www/example.com;
#       index index.html;
        location /t2/ {
                proxy_pass http://8.130.180.210:8080/;  # 将请求转发给后端服务器
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
        }
        location /t3/ {
                proxy_pass http://baidu.com/;  # 将请求转发给后端服务器
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
        }
}
```
##### 静态部署

