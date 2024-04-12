---
title: 代码规范
layout: default
nav_order: 6
---

环境配置：

```shell
pip install pre-commit
```

编写`Makefile`：

```makefile
format:
	pre-commit run --all-files
```

编写`.pre-commit-config.yaml`：

```yaml
repos:
  - repo: https://github.com/PyCQA/flake8.git
    rev: 5.0.4
    hooks:
      - id: flake8
  - repo: https://github.com/PyCQA/autoflake.git
    rev: v1.5.3
    hooks:
      - id: autoflake
        args: ["--exclude=__init__.py", "--in-place", "--recursive"]
  - repo: https://github.com/psf/black.git
    rev: 22.8.0
    hooks:
      - id: black
        args: ["--line-length=120"]
  - repo: https://github.com/pycqa/isort
    rev: 5.11.5
    hooks:
      - id: isort
        name: isort (python)
        args: ["--profile", "black", --line-length=120]
  - repo: https://github.com/pre-commit/pre-commit-hooks.git
    rev: v4.3.0
    hooks:
      - id: check-added-large-files
        args: ["--maxkb=2000"]
      - id: check-docstring-first
      - id: check-executables-have-shebangs
      - id: check-json
      - id: check-merge-conflict
      - id: check-yaml
        args: ["--unsafe"]
      - id: debug-statements
      - id: end-of-file-fixer
      - id: requirements-txt-fixer
      - id: trailing-whitespace
```

编写`.flake8`：

```shell
[flake8]
ignore = E501, F401, E731, W503, E722, E712, E203, F841, E265, E266, E262, E402, E741, W605
```

执行代码规范检查：

```shell
make format
```

