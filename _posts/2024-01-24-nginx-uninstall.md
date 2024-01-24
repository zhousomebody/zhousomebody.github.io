---
layout: post_layout
title: nginx-uninstall
time: 2024年01月24日 星期三
location: beijing
pulished: ture
excerpt_separator: "##"
---
#### 卸载nginx安装方式
##### 先停止nginx命令
```
systemctl stop nginx
```
##### 通过apt-get命令卸载nginx
```
apt-get --purge autoremove nginx
```
##### 查看nginx的版本号
```
nginx -v
```

