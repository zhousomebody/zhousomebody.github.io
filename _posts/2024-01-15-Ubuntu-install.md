---
layout: post_layout
title: Ubuntu-install
time: 2024年01月15日 星期一
location: bj
pulished: ture
excerpt_separator: "##"
---

#### 需要安装的软件
- Vmware
  - 关注微信公众号软件管家
- Diskgenius
  - [官网](https://www.diskgenius.cn/)
- Ubuntu
  - [官网](https://ubuntu.com/)
    - 选择 Ubuntu 20.04.6 LTS<img src="/assets/img/Ubuntu/1.png" width="400px">
    <img src="/assets/img/Ubuntu/2.png" width="400px">
##### Diskgenius操作
- 插上硬盘、打开diskgenius.exe
- 找到硬盘SanDisk
- 若为MBR <img src="/assets/img/Ubuntu/3.png" width="400px">
  - 选择磁盘->转化分区表类型为GUID(格式)p
- 若为GBT <img src="/assets/img/Ubuntu/4.png" width="400px">
  - 不用改变
- 删除所有分区->保存更改
- 选择分区 -> 建立ESP/MSR分区(ESP分区大小：2048 建立MSR分区：去掉) -> 保存更改<img src="/assets/img/Ubuntu/5.png" width="400px">
##### Vmware操作



