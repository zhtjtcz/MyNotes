---
title: Python 代码片段
layout: default
nav_order: 4
---

## Torch 相关

```python
torch.cuda.empty_cache() 		# 回收显存
torch.cuda.memory_allocated() 	# 查看显存使用情况
```

## 其他

修改 Gradio 缓存路径

```python
import tempfile
tempfile.tempdir = './tmp'
```

修改镜像节点

```python
import os
os.environ['CUDA_VISIBLE_DEVICES'] = '2'
os.environ['HF_ENDPOINT'] = 'hf-mirror.com'
```
