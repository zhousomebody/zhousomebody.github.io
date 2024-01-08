---
layout: post_layout
title: ssh-connect
time: 2024年01月05日 星期五
location: bj
pulished: false
excerpt_separator: "##"
--- 
### 端口映射
命令：ssh 用户名@主机ip -p 映射的端口号

例子：比如要远程到主机22.22.22.22的12345端口，但是12345端口被映射到了54321端口，所以要访问12345端口的命令为
ssh root@22.22.22.22 -p 54321

'''sudo docker ps -a'''

在 Docker 中以管理员权限列出所有容器的命令。sudo 表示以管理员身份运行命令，docker ps 用于显示正在运行的容器，而 -a 参数则显示所有的容器，包括正在运行和已经停止的容器。

sudo docker run --shm-size 1g --runtime=nvidia --gpus all -itd --privileged --gpus all -p <ssh_port>:22 --security-opt seccomp=unconfined -e NVIDIA_DRIVER_CAPABILITIES=all -v /mnt/sda/data/<name>:/data -v /mnt/sda/data/public:/public --name <name> continuumio/miniconda3 /bin/bash

这行代码是在 Docker 中以管理员权限运行一个镜像，并设置一些参数和选项。

具体解释如下：

- `sudo` 表示以管理员身份运行命令。
- `docker run` 是运行 Docker 容器的命令。
- `--shm-size 1g` 设置共享内存的大小为 1GB。
- `--runtime=nvidia` 指定 Docker 使用 Nvidia 运行时环境。
- `--gpus all` 指定容器中可以使用全部可用的 GPU。
- `-itd` 设置容器的交互式终端、后台运行和分离模式。
- `--privileged` 开启容器的特权模式。
- `-p <ssh_port>:22` 将容器的 SSH 端口映射到宿主机的指定端口。
- `--security-opt seccomp=unconfined` 关闭容器的 seccomp 安全机制。
- `-e NVIDIA_DRIVER_CAPABILITIES=all` 设置 NVIDIA 驱动的能力为全部。
- `-v /mnt/sda/data/<name>:/data` 将宿主机的 `/mnt/sda/data/<name>` 目录挂载到容器的 `/data` 目录。
- `-v /mnt/sda/data/public:/public` 将宿主机的 `/mnt/sda/data/public` 目录挂载到容器的 `/public` 目录。
- `--name <name>` 指定容器的名称为 `<name>`。
- `continuumio/miniconda3` 是要运行的镜像名称。
- `/bin/bash` 是容器启动后进入的默认命令行终端。

请注意，上述命令中的 `<ssh_port>` 和 `<name>` 都是占位符，需要替换为实际的值。
