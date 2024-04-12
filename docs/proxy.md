---
title: 代理与网络
layout: default
nav_order: 2
---

## 代理

基于 Clash

```shell
# 开启 Git 代理（clash版）
git config --global http.proxy 127.0.0.1:7890
git config --global https.proxy 127.0.0.1:7890

# 关闭 Git 代理
git config --global --unset http.proxy
git config --global --unset https.proxy

# 使用自己搭建的 clash 代理
export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890

# 关闭 http 代理
unset  http_proxy && unset https_proxy
```

## 镜像

火山外网 && 内网镜像源与清华源

```shell
pip install numpy -i https://mirrors.ivolces.com/pypi/simple/
pip install torch -i https://mirrors.volces.com/pypi/simple/
pip install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple
```

## Google Drive 下载

单文件：

```shell
# 打开要下载到的路径
cd /nas/xxx

# 填入要下载的文件的文件名
filename='DM_MHAD.pth'

# 填入要下载文件的id
fileid='xx'

wget --load-cookies /tmp/cookies.txt "https://drive.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://drive.google.com/uc?export=download&id=${fileid}' -O- | sed -rn 's/.confirm=([0-9A-Za-z_]+)./\1\n/p')&id=${fileid}" -O ${filename} && rm -rf /tmp/cookies.txt
```

文件夹：

```shell
gdown https://drive.google.com/drive/folders/xxx -O ./ --folder
```

## Hugging Face 下载

准备工作：

```shell
pip install -U huggingface_hub
export HF_ENDPOINT=https://hf-mirror.com
```

下载：

```shell
huggingface-cli download --resume-download bigscience/bloom-560m --local-dir bloom-560m --local-dir-use-symlinks False
```

加上`--local-dir-use-symlinks False` 会不使用链接，直接下载到指定目录。
