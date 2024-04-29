---
title: 常用命令&脚本
layout: default
nav_order: 3
---

## 命令

系统

```shell
export PYTHONPATH=$PWD
ls -l | grep "^-" | wc -l
find . -maxdepth 1 -type d | wc -l
du -h --max-depth=1 ./
```

Git 相关：

```shell
git rm --cached log/
git reset --hard HEAD^
git reset --hard hash
```

Python 调试

```shell
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple py-spy
py-spy dump --nonblocking --pid xxx	# 查看进程当前调用栈
py-spy top -p xxx 					# 实时查看进程各部分用时
```

## 脚本

递归删除当前目录及其所有子目录下文件：

```shell
#!/bin/bash

files_to_delete=("optimizer.bin" "scheduler.bin" "scaler.pt" "random_states_0.pkl")

for filename in "${files_to_delete[@]}"; do
    find . -type f -name "$filename" -exec rm -v {} \;
done
```

可以将`rm -v`替换为`echo`检查匹配是否正确。

