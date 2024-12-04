---
title: 报错收录
layout: default
nav_order: 9
---

## Ninja

报错信息：

```vim
Command '['ninja', '-v']' returned non-zero exit status 1.
```

解决办法：

`setup.py` 编译安装时，禁用 Ninja：

```python
cmdclass={"build_ext": torch.utils.cpp_extension.BuildExtension.with_options(use_ninja=False)},
```

可能伴生的报错：

```vim
#error C++17 or later compatible compiler is required to use PyTorch. | ^~~~~
```

解决办法：

通常是由于指定编译的 C++ 版本过低，与 Torch 不兼容导致。需要手动在 `setup.py` 里指定 C++17：

```python
extra_compile_args = {"cxx": ['-O3', '-Wall', '-shared', '-std=c++17', '-fPIC', '-fopenmp']}
```

## imageio

报错信息：

```vim
TypeError: write_frames() got an unexpected keyword argument 'audio_path'
```

解决办法：

没有安装 imageio_ffmpeg 或者其版本过低（接近0.4.2），升级即可。

```shell
pip install -U imageio_ffmpeg
```
