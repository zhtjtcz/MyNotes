---
title: 配置文件
layout: default
nav_order: 5
---

## Vim

```vim
"设置编码
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
set termencoding=utf-8
set encoding=utf-8

"显示行号
set nu
set number

"启用语法高亮
syntax enable

"突出显示当前行
set cursorline
set cul          "cursorline的缩写形式
hi CursorLine   cterm=NONE ctermbg=LightCyan ctermfg=Lightgreen guibg=NONE guifg=NONE

"启用鼠标
set mouse=a
set selection=exclusive
set selectmode=mouse,key

"显示括号匹配
set showmatch

"设置Tab长度为4空格
set tabstop=4
"设置自动缩进长度为4空格
set shiftwidth=4
"继承前一行的缩进方式，适用于多行注释
set autoindent

"设置粘贴模式
set paste

"显示空格和tab键
set listchars=tab:>-,trail:- ",eol:$
set list

"总是显示状态栏
set laststatus=2
"显示光标当前位置
set ruler

"进入插入模式后自动进入粘贴模式
set pastetoggle=
au InsertEnter * set paste
au InsertLeave * set nopaste

filetype plugin indent on

"让vimrc配置变更立即生效
autocmd BufWritePost $MYVIMRC source $MYVIMRC
```

## .condarc

```vim
show_channel_urls: true

ssl_verify: false
proxy_servers:
  http: http://127.0.0.1:10032
  https: http://127.0.0.1:10032
```

## pip.conf

```vim
[global]
index-url = https://mirrors.ivolces.com/pypi/simple/
```

## bashrc

```vim
alias ep='export PYTHONPATH=$PWD'
alias G0='CUDA_VISIBLE_DEVICES=0'
alias G1='CUDA_VISIBLE_DEVICES=1'
alias G2='CUDA_VISIBLE_DEVICES=2'
alias G3='CUDA_VISIBLE_DEVICES=3'
alias G4='CUDA_VISIBLE_DEVICES=4'
alias G5='CUDA_VISIBLE_DEVICES=5'
alias G6='CUDA_VISIBLE_DEVICES=6'
alias G7='CUDA_VISIBLE_DEVICES=7'
```

## editorconfig

```
# 设为true时，才会停止查找.editorconfig文件
root = true

# 对于 py 文件  始终在文件末尾插入一个新行
[*.py]
end_of_line = lf
insert_final_newline = true


# 设置 py 文件的缩进
[*.py]
indent_style = space
indent_size = 4
```

## VSCode Debug

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Train Debug",
            "type": "debugpy",
            "request": "launch",
            "program": "train.py",
            "console": "integratedTerminal",
            "args": [
                "projects/a.yaml",
            ],
            "env": {"CUDA_VISIBLE_DEVICES": "2"}
        },
    ]
}
```
