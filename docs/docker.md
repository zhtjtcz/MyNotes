---
title: Docker 相关
layout: default
nav_order: 7
---

## 镜像打包参考

```dockerfile
# 基本镜像，提供cuda/torch的基本环境
FROM vemlp-cn-beijing.cr.volces.com/preset-images/pytorch:2.0.1
     
ENV DEBIAN_FRONTEND=noninteractive

# 设置时区
RUN apt-get update && apt-get install -y tzdata
RUN ln -fs /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && dpkg-reconfigure -f noninteractive tzdata

# 配置 pip 镜像源
ENV PIP_INDEX="https://mirrors.ivolces.com/pypi/simple/"

RUN pip3 install --no-cache-dir \
accelerate==0.23.0 \
-i ${PIP_INDEX}

# remove wandb, brought by kdiff
RUN pip3 uninstall -y wandb

RUN pip3 install --no-cache-dir \
 basicsr==1.4.2 \
 realesrgan==0.3.0 \
-i https://mirrors.aliyun.com/pypi/simple

# 设置火山的pip源
RUN pip3 config set global.index-url https://mirrors.volces.com/pypi/simple/

```
